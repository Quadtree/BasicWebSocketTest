# HTML5 Networking Plugin Only Connects Once
I've noticed what I think might be a bug with the HTML5 Networking plugin, although it also could be that I'm not using it correctly. For a simple test, I created a blank C++ project and adjusted my DefaultEngine.ini config to enable the HTML5 Networking plugin. For reference, I've posted this project on GitHub [here](https://github.com/Quadtree/BasicWebSocketTest). In the test I created a Win64 development build, and tried to connect two clients to the server.

The server was started with these params: `?listen -windowed ResX=800 ResY=600` .

The clients were started with: `127.0.0.1 -windowed ResX=640 ResY=480`

The first connection worked well, but the second client couldn't connect at all. Disconnecting the first client did nothing, the second client was still unable to connect. It looks like consistently only one client can ever connect to a websocket based server. Switching back to the normal net driver fixes the issue, but of course prevents HTML5 clients from connecting.

To make things more realistic, I also tried it with two actual HTML5 clients, running the game in Firefox 64-bit, made from the same project (I originally didn't because I thought that using libwebsockets for the client would be more likely to work). It had the exact same problem.

Is the behavior I'm seeing caused by something in the project, or is this a bug?
