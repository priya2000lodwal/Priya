# Priya
Conversation
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chatbot</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f4;
        }
        #chatbox {
            width: 360px;
            height: 500px;
            border: 1px solid #ccc;
            border-radius: 8px;
            background: #fff;
            display: flex;
            flex-direction: column;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }
        #messages {
            flex: 1;
            padding: 10px;
            overflow-y: auto;
            border-bottom: 1px solid #ccc;
        }
        .message {
            margin-bottom: 10px;
        }
        .message.bot {
            color: #007bff;
        }
        #input {
            display: flex;
            border-top: 1px solid #ccc;
        }
        #input input {
            flex: 1;
            padding: 10px;
            border: none;
            border-radius: 0 0 0 8px;
            font-size: 16px;
        }
        #input button {
            padding: 10px;
            border: none;
            background-color: #007bff;
            color: white;
            cursor: pointer;
            border-radius: 0 0 8px 0;
        }
    </style>
</head>
<body>
    <div id="chatbox">
        <div id="messages"></div>
        <div id="input">
            <input type="text" id="userInput" placeholder="Type a message..." autofocus>
            <button onclick="sendMessage()">Send</button>
        </div>
    </div>

    <script>
        function sendMessage() {
            const userInput = document.getElementById('userInput').value;
            if (userInput.trim() === '') return;

            // Display user message
            const messages = document.getElementById('messages');
            const userMessage = document.createElement('div');
            userMessage.className = 'message user';
            userMessage.textContent = `You: ${userInput}`;
            messages.appendChild(userMessage);

            // Generate bot response
            const botMessage = document.createElement('div');
            botMessage.className = 'message bot';
            botMessage.textContent = `Bot: ${getBotResponse(userInput)}`;
            messages.appendChild(botMessage);

            // Clear user input
            document.getElementById('userInput').value = '';

            // Scroll to bottom
            messages.scrollTop = messages.scrollHeight;
        }

        function getBotResponse(input) {
            const lowerInput = input.toLowerCase();
            if (lowerInput.includes('hello')) return 'Hi there!';
            if (lowerInput.includes('how are you')) return 'I am good, thank you!';
            if (lowerInput.includes('bye')) return 'Goodbye!';
            return 'I am not sure how to respond to that.';
        }
    </script>
</body>
</html>
