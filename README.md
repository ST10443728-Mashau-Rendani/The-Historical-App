using System;
using System.Speech.Synthesis;
using System.Windows;
using CybersecurityChatbot;

namespace Part2_3
{
    public partial class MainWindow : Window
    {
        private Chatbot bot = new Chatbot();

        private SpeechSynthesizer speaker = new SpeechSynthesizer();

        private string userName = "";

        private string currentPersona = "Friendly";

        public MainWindow()
        {
            InitializeComponent();

            // Button events
            PersonaButton.Click += PersonaButton_Click;
            VoiceButton.Click += VoiceButton_Click;

            // Startup speech
            speaker.SpeakAsync("Speech system activated");
        }

        // START CHAT BUTTON
        private void StartChat_Click(object sender, RoutedEventArgs e)
        {
            try
            {
                if (string.IsNullOrWhiteSpace(NameBox.Text))
                {
                    MessageBox.Show("Please enter your name.");
                    return;
                }

                userName = NameBox.Text;

                // Hide name screen
                NamePanel.Visibility = Visibility.Hidden;

                // Show chat screen
                ChatPanel.Visibility = Visibility.Visible;

                string welcome =
                    $"Hello {userName}! Welcome to the Cybersecurity Awareness Chatbot.";

                ChatBox.Items.Add("Bot: " + welcome);

                speaker.SpeakAsyncCancelAll();
                speaker.SpeakAsync(welcome);
            }
            catch (Exception)
            {
                MessageBox.Show("Error starting chat.");
            }
        }

        // SEND BUTTON
        private void Send_Click(object sender, RoutedEventArgs e)
        {
            try
            {
                string input = InputBox.Text;

                if (string.IsNullOrWhiteSpace(input))
                    return;

                ChatBox.Items.Add("You: " + input);

                string response = bot.GetResponse(input, userName);

                // Persona effect
                if (currentPersona == "Serious")
                {
                    response = "Security Notice: " + response;
                }

                ChatBox.Items.Add("Bot: " + response);

                // Speak response
                speaker.SpeakAsyncCancelAll();
                speaker.SpeakAsync(response);

                InputBox.Clear();
            }
            catch (Exception)
            {
                ChatBox.Items.Add("Bot: Something went wrong.");
            }
        }

        // PERSONA BUTTON
        private void PersonaButton_Click(object sender, RoutedEventArgs e)
        {
            if (currentPersona == "Friendly")
            {
                currentPersona = "Serious";

                ChatBox.Items.Add(
                    "Bot: Persona changed to Serious Security Expert.");
            }
            else
            {
                currentPersona = "Friendly";

                ChatBox.Items.Add(
                    "Bot: Persona changed to Friendly Assistant.");
            }
        }

        // VOICE BUTTON
        private void VoiceButton_Click(object sender, RoutedEventArgs e)
        {
            try
            {
                if (speaker.Voice.Name.Contains("David"))
                {
                    speaker.SelectVoiceByHints(VoiceGender.Female);

                    ChatBox.Items.Add("Bot: Female voice activated.");
                }
                else
                {
                    speaker.SelectVoiceByHints(VoiceGender.Male);

                    ChatBox.Items.Add("Bot: Male voice activated.");
                }
            }
            catch
            {
                ChatBox.Items.Add(
                    "Bot: Voice switching is not supported on this PC.");
            }
        }
    }
}
