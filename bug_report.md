# HTML5 Networking Plugin Servers Break and Can't Accept Connections
I've noticed what I think might be a bug with the HTML5 Networking plugin, although it also could be that I'm not using it correctly. Basically, the problem seems to be that there are several ways the WebSockets server can get a "broken" state where it won't accept any new connections. For a simple test, I created a blank C++ project and adjusted my DefaultEngine.ini config to enable the HTML5 Networking plugin. For reference, I've posted this project on GitHub [here](https://github.com/Quadtree/BasicWebSocketTest). Here are the tests I ran:

## Test 1: All Desktop
For this one, I built a Win64 version and started 3 instances, one running with these parameters: `?listen -windowed ResX=800 ResY=600` and 2 clients started with these params: `127.0.0.1 -windowed ResX=640 ResY=480`. The first client connected okay, but the second couldn't connect. If the first dropped, the second still couldn't connect, making me think this is the "broken" issue mentioned above.

## Test 2: Desktop Server, HTML5 Clients
For this one I started a Win64 instance with no arguments, and then ran this command in the console: `open ?listen`. Then I connected a single HTML5 client. That worked, so I connected a second one. That also worked, so I tried disconnecting the first one, and then connecting a third. That did not work. So it looks like disconnecting an HTML5 client causes the "broken" issue as well.

## Test 3: Desktop Server, HTML WebSockets Test and Client
To simplify, I created a simple HTML page that opened a WebSocket on localhost:8889, sent the word "test" and then closed it. This also put the server in the "broken" state where it couldn't accept any new connections. While this isn't really a supported case, it is a very simple way to reproduce this issue, so I thought I'd include it.

Is this behavior I'm seeing a bug or am I just not using the WebSockets plugin correctly?
