
1. Introduction and Context (Quentin)

“Hello everyone, and thank you for being here. Today, we’re addressing an issue that commonly arises when trying to run multiple SSH commands in a PowerShell script using the Renci SSH.NET library. In this case, the script runs the first command without issues, but it begins to lag and eventually crashes when attempting to send a second command. This was reported by a user trying to connect to a Cisco switch. Understanding this issue will help us find a reliable fix, ensuring a stable and efficient script execution.”

2. Explanation of the Issue (Alix)

“The problem comes from using the RunCommand() method, which wasn’t designed for handling multiple commands in one SSH session. Every time RunCommand() runs, it starts a new SSH connection. When we try to send many commands in sequence, these multiple connections slow down the script, causing it to lag and sometimes crash. The constant reconnecting makes the network unstable, leading to this issue.”

3. Technical Solution with Code Explanation (Ethan)

“To resolve this, we should switch from the RunCommand() method to the ShellStream method. ShellStream is different because it keeps the SSH session open, allowing us to run several commands consecutively without reconnecting each time. Here’s a quick look at the code:


```bash
using (var client = new SshClient("host", "username", "password"))
{
    client.Connect();
    var shellStream = client.CreateShellStream("CLI", 0, 0, 0, 0, 1024);
    
    shellStream.WriteLine("first command");
    shellStream.WriteLine("second command");
    // Add more commands as needed
    client.Disconnect();
}
```

In this code, we use CreateShellStream() instead of RunCommand(). This keeps our SSH session active, so we can send multiple commands like first command and second command without needing to reconnect. This approach minimizes delays, prevents packet loss, and ensures a stable session.”

4. Benefits of Using ShellStream (Adrien)

“Using ShellStream is better because it keeps the SSH connection open, so we don’t have to start a new connection each time we send a command. This makes the connection faster and avoids crashes. It’s very useful when we need to send several commands one after another.”

5. Conclusion and Best Practices (Lou)

“In conclusion, by switching to ShellStream, we avoid the delays and crashes caused by reconnecting each time. ShellStream helps our script run smoothly, especially when working with multiple commands in PowerShell. To keep things secure, it’s also important to check for errors and log any issues after executing the commands. This ensures the script stays reliable and the connection remains stable.”


![[English_presentation.pptx]]
