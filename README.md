<Window x:Class="CybersecurityChatbot.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="Cybersecurity Chatbot" Height="450" Width="800"
        Background="#1E1E1E">

    <Grid>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="180"/>
            <ColumnDefinition Width="*"/>
        </Grid.ColumnDefinitions>

        <!-- Left Panel - Buttons -->
        <StackPanel Grid.Column="0" 
                    Background="#2D2D30" 
                    Margin="5">
            
            <Button Content="Switch Persona"
                    Height="50"
                    Margin="5"
                    Background="#3E3E42"
                    Foreground="White"
                    BorderThickness="0"/>
            
            <Button Content="Switch Voice"
                    Height="50"
                    Margin="5"
                    Background="#3E3E42"
                    Foreground="White"
                    BorderThickness="0"/>
            
            <Button Content="Change Theme"
                    Height="50"
                    Margin="5"
                    Background="#3E3E42"
                    Foreground="White"
                    BorderThickness="0"/>
            
            <Button Content="Help"
                    Height="50"
                    Margin="5"
                    Background="#3E3E42"
                    Foreground="White"
                    BorderThickness="0"/>
        </StackPanel>

        <!-- Right Panel - Chat Area -->
        <Grid Grid.Column="1" Margin="5">
            <Grid.RowDefinitions>
                <RowDefinition Height="*"/>
                <RowDefinition Height="50"/>
            </Grid.RowDefinitions>

            <!-- Chat Display -->
            <TextBlock Grid.Row="0"
                       Text="Bot: Hello! What is your name?"
                       Foreground="White"
                       FontSize="14"
                       Background="#2D2D30"
                       Padding="10"
                       TextWrapping="Wrap"/>

            <!-- Input Area -->
            <TextBox Grid.Row="1"
                     Height="50"
                     Background="#3E3E42"
                     Foreground="White"
                     BorderThickness="0"
                     FontSize="14"
                     Padding="10,0"
                     VerticalContentAlignment="Center"/>
        </Grid>
    </Grid>
</Window>
