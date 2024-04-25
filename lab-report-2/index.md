# Part 1

ChatServer.java Code:
```
class Handler implements URLHandler {
    private StringBuilder chatLog = new StringBuilder();
    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return chatLog.length() == 0 ? "Chat is empty." : chatLog.toString();
        } else if (url.getPath().equals("/add-message")) {
            String query = url.getQuery();
            String user = null;
            String message = null;
            for (String param : query.split("&")) {
                String[] entry = param.split("=");
                if (entry.length > 1) {
                    if (entry[0].equals("user")) {
                        user = entry[1];
                    } else if (entry[0].equals("s")) {
                        message = entry[1];
                }   }
            }
            if (user != null && message != null) {
                chatLog.append(user).append(": ").append(message).append("\n");
                return chatLog.toString();
            } else {
                return "Invalid request! Parameters 's' and 'user' are required.";
            }
        }
        return "404 Not Found!";
} }
class ChatServer {
    public static void main(String[] args) throws IOException {
        if (args.length == 0) {
            System.out.println("Missing port number!)
            return;
        }
        int port = Integer.parseInt(args[0]);
        Server.start(port, new Handler());
} }
```

![Image 1](https://ayshaiqbal04.github.io/cse15l-lab-reports/lab-report-2/images/Image-1.jpeg)

![Image 2](https://ayshaiqbal04.github.io/cse15l-lab-reports/lab-report-2/images/Image-2.jpeg)

`handleURL()` method is called to parse the URL for paths and queries.

Args and Fields:
- `url` - `http://localhost:4000/add-message?s=Hello&user=Aysha`
- `chatLog` - Starts as an empty string but then all the chats get added here.

The `chatLog` field changes. The URI is first passed and all the text is added to the `StringBuilder`.

![Image 3](https://ayshaiqbal04.github.io/cse15l-lab-reports/lab-report-2/images/Image-3.jpeg)

The  `handleURL()` method is called again.

Args and Fields:
- `url` - `http://localhost:4000/add-message?s=Wassup&user=Joe`
- `chatLog` - Before this it contained previous chats (Aysha: Hello in this case)

The URL now gets parsed again and the next chats get appended to the `StringBuilder`.

# Part 2
Path to private key on local device:
![Image 4](https://ayshaiqbal04.github.io/cse15l-lab-reports/lab-report-2/images/Image-4.jpeg)

Path to public key on remote device:
![Image 5](https://ayshaiqbal04.github.io/cse15l-lab-reports/lab-report-2/images/Image-5.jpeg)

No password login:
![Image 6](https://ayshaiqbal04.github.io/cse15l-lab-reports/lab-report-2/images/Image-6.jpeg)

# Part 3
I have learned mutliple new concepts throughout my first half of the quarter in CSE15L. Before enrolling in this class I had little experience with git hub, remtote servers bash and so much more. Along with these concepts, I have learned to adopt a different outlook on coding all together, for example, the skill demo taught me to face challenges and adapt. Most of my coding and computer science experience has involved strategic planning and research. I had yet to face real time challenges where I had a deadline to meet and no idea how to solve them. I look forward to learning what else this class can teach me.