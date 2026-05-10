<Window x:Class="Part2_3.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="Cybersecurity Chatbot"
        Height="600"
        Width="700">

    <Grid>

        <!-- NAME SCREEN -->
        <Grid x:Name="NamePanel"
              Background="White">

            <StackPanel HorizontalAlignment="Center"
                        VerticalAlignment="Center">

                <TextBlock Text="Enter your name:"
                           FontSize="18"
                           Margin="0,0,0,10"
                           HorizontalAlignment="Center"/>

                <TextBox x:Name="NameBox"
                         Width="200"
                         Height="30"
                         Margin="0,0,0,10"/>

                <Button Content="Start Chat"
                        Width="200"
                        Height="30"
                        Click="StartChat_Click"/>
            </StackPanel>

        </Grid>

        <!-- CHAT SCREEN -->
        <Grid x:Name="ChatPanel"
              Visibility="Hidden"
              Margin="10">

            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="120"/>
                <ColumnDefinition Width="*"/>
            </Grid.ColumnDefinitions>

            <!-- SIDE PANEL -->
            <StackPanel Grid.Column="0"
                        Background="#2D2D30"
                        Margin="0,0,10,0">

                <Button x:Name="PersonaButton"
                        Content="Switch Persona"
                        Height="50"
                        Margin="5"/>

                <Button x:Name="VoiceButton"
                        Content="Switch Voice"
                        Height="50"
                        Margin="5"/>

                <Button x:Name="ThemeButton"
                        Content="Change Theme"
                        Height="50"
                        Margin="5"/>

                <Button x:Name="HelpButton"
                        Content="Help"
                        Height="50"
                        Margin="5"/>
            </StackPanel>

            <!-- MAIN CHAT AREA -->
            <Grid Grid.Column="1">

                <Grid.RowDefinitions>
                    <RowDefinition Height="*"/>
                    <RowDefinition Height="Auto"/>
                </Grid.RowDefinitions>

                <!-- CHAT BOX -->
                <ListBox x:Name="ChatBox"
                         Grid.Row="0"
                         FontSize="14"
                         Background="#1E1E1E"
                         Foreground="White"/>

                <!-- INPUT AREA -->
                <StackPanel Grid.Row="1"
                            Orientation="Horizontal"
                            Margin="0,10,0,0">

                    <TextBox x:Name="InputBox"
                             Width="300"
                             Height="35"
                             FontSize="14"/>

                    <Button Content="Send"
                            Width="100"
                            Height="35"
                            Margin="10,0,0,0"
                            Background="#007ACC"
                            Foreground="White"
                            Click="Send_Click"/>
                </StackPanel>

            </Grid>

        </Grid>

    </Grid>

</Window>
