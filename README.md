download link: https://www.mediafire.com/folder/spzuxl8xne6ay/cosmic+zone
🌌 CØSMIC ZØNE




CØSMIC ZØNE is a self-hosted gaming and social website with accounts, chat, parties, profiles, online presence, games, and WebRTC voice/video calls.



This version uses users.json for accounts and does not require Supabase.



✨ Features



👤 CØSMIC accounts



🆔 Unique CØSMIC IDs



🔐 Hashed passwords



💬 Global chat



✉️ Direct messages



👥 Friends



🎉 Parties



🟢 Online presence



🖼️ Profile pictures



🎮 Game invites



📞 Voice calls



📹 Video calls



🎙️ Party calls



🔫 CØSMIC Shot



🛡️ Admin tools



🌐 Local, LAN, tunnel, or custom-domain hosting



🚀 Installation



1\. Download CØSMIC ZØNE



Click:



Code → Download ZIP



Then extract the ZIP.



Or clone it:



git clone YOUR\_REPOSITORY\_URL

cd gamzone



2\. Install Python



Install Python 3.



Check that it works:



python --version



On Windows you can also use:



py -3 --version



3\. Install Requirements



Open a terminal inside the CØSMIC ZØNE folder.



Run:



python -m pip install -r chat-server/requirements.txt



Or on Windows:



py -3 -m pip install -r chat-server/requirements.txt



🖥️ Run Locally



CØSMIC ZØNE uses two servers:



Main Website  -> Port 8000

Chat/API      -> Port 5000



Main Website



Run:



python gamezone\_server.py



or:



py -3 gamezone\_server.py



The website runs at:



http://localhost:8000



Chat + Account Server



Open another terminal inside:



chat-server



Run:



python server.py



or:



py -3 server.py



The API runs at:



http://localhost:5000



Then open:



http://localhost:8000



🌐 Domains — How CØSMIC ZØNE Works



CØSMIC ZØNE normally uses two addresses:



MAIN SITE DOMAIN

&#x20;       ↓

&#x20;  Port 8000



CHAT/API DOMAIN

&#x20;       ↓

&#x20;  Port 5000



For example:



https://your-main-domain.example

&#x20;       ↓

localhost:8000



https://your-chat-domain.example

&#x20;       ↓

localhost:5000



The main website loads the UI.



The chat/API server handles things such as:



accounts



online presence



global chat



direct messages



parties



profiles



call signaling



WebRTC signaling



🔧 You Do NOT Have to Use ngrok



ngrok is only one way to expose the two servers.



You can use:



localhost



your computer's LAN IP



ngrok



Cloudflare Tunnel



your own reverse proxy



your own VPS/server



your own HTTPS domains



another tunnel provider



You only need to make sure:



your main address points to port 8000

your chat/API address points to port 5000



and then change the URLs in the CØSMIC ZØNE code.



🏠 Option 1 — Localhost Only



If you only want to use CØSMIC ZØNE on the computer hosting it, you do not need any public domain or tunnel.



Use:



Main:

http://localhost:8000



Chat:

http://localhost:5000



The project already detects localhost in several places.



Open:



http://localhost:8000



📡 Option 2 — Use It on Your Local Network



You can also use your computer's LAN IP.



Example:



Main:

http://192.168.1.50:8000



Chat:

http://192.168.1.50:5000



Replace:



192.168.1.50



with the LAN IP of the computer running CØSMIC ZØNE.



You may also need to allow Python/ports 8000 and 5000 through your operating system firewall.



If you use LAN addresses, update the frontend chat/API URL and add the main LAN origin to the server's allowed origins.



🚇 Option 3 — ngrok



ngrok can give both servers public HTTPS addresses.



Example:



Main:

https://your-main-domain.ngrok.app

&#x20;       ↓

localhost:8000



Chat:

https://your-chat-domain.ngrok.app

&#x20;       ↓

localhost:5000



Connect your ngrok account:



ngrok config add-authtoken YOUR\_NGROK\_AUTHTOKEN



Then create two tunnels.



The included:



gamezone starter.bat



can be configured to start:



Main Python server



Chat Python server



Main ngrok tunnel -> port 8000



Chat ngrok tunnel -> port 5000



☁️ Option 4 — Cloudflare Tunnel or Another Tunnel



You can use another tunneling service instead of ngrok.



Example:



https://cosmic.example.com

&#x20;       ↓

localhost:8000



https://chat.cosmic.example.com

&#x20;       ↓

localhost:5000



The tunnel provider does not matter to CØSMIC ZØNE as long as the URLs are reachable and the code points to the correct chat/API address.



🌍 Option 5 — Your Own Domains / Reverse Proxy



You can host CØSMIC ZØNE behind your own reverse proxy.



Example:



https://cosmic.example.com

&#x20;       ↓

127.0.0.1:8000



https://api.cosmic.example.com

&#x20;       ↓

127.0.0.1:5000



You can use any compatible reverse proxy or hosting setup.



For voice/video on devices other than localhost, using HTTPS is strongly recommended and is normally required by browsers for microphone/camera access.



✏️ Changing the Domains in the Code



The original project may contain development URLs.



Search the project for the old main and chat domains.



Important files may include:



index.html

script.js

calls.js

chat-server/server.py

gamezone starter.bat



You are mainly changing two values:



MAIN\_URL

CHAT\_URL



Example



If your addresses are:



Main:

https://cosmic.example.com



Chat:

https://chat.cosmic.example.com



then the frontend should use:



const CHAT\_SERVER =

&#x20; \['localhost', '127.0.0.1'].includes(location.hostname)

&#x20;   ? 'http://localhost:5000'

&#x20;   : 'https://chat.cosmic.example.com';



Your chat server must also allow the main website origin.



Example in chat-server/server.py:



ALLOWED\_ORIGINS = {

&#x20;   "http://localhost:8000",

&#x20;   "http://127.0.0.1:8000",

&#x20;   "https://cosmic.example.com",

}



If your main domain changes, update ALLOWED\_ORIGINS.



🔁 Simple Domain Rule



Think of it like this:



Browser

&#x20;  │

&#x20;  ├── opens MAIN\_URL

&#x20;  │        ↓

&#x20;  │      :8000

&#x20;  │

&#x20;  └── sends account/chat/call requests to CHAT\_URL

&#x20;           ↓

&#x20;         :5000



The frontend and API do not have to use ngrok.



They just have to be able to reach each other using the URLs configured in the project.



❤️ Test the Chat Server



After starting the chat server, open:



YOUR\_CHAT\_URL/health



Example:



https://chat.cosmic.example.com/health



You should receive something similar to:



{

&#x20; "ok": true,

&#x20; "service": "cosmic-chat"

}



If you open:



YOUR\_CHAT\_URL/



you may see:



ACCESS DENIED



That is intentional.



The chat server is an API, not the main website.



👤 Accounts



Accounts are stored in:



chat-server/users.json



The file starts as:



{}



When someone signs up, their account is automatically added.



Passwords are stored as salted password hashes rather than readable plaintext passwords.



🔐 PRIVATE FILES



Do NOT upload private server data to a public GitHub repository.



Keep files such as these private:



chat-server/users.json

chat-server/auth\_secret.json

chat-server/sessions.json

chat-server/direct\_messages.json

chat-server/party\_messages.json

chat-server/visitors.json

chat-server/ip\_cache.json



The included .gitignore should protect them.



Always check:



git status



before pushing.



📞 Voice \& Video Calls



CØSMIC ZØNE uses WebRTC for voice/video.



The chat server handles WebRTC signaling.



The actual media normally attempts to connect directly between the two devices.



For calls to work:



both users must be online



both users must reach the chat/API server



microphone permission must be allowed



camera permission must be allowed for video



the browser/network must allow WebRTC



public deployments should use HTTPS



Some networks cannot establish a direct WebRTC connection.



If signaling works but a call remains on:



Connecting...



a TURN relay may be required.



🧪 Testing Two Accounts



For the best test:



Device 1 -> Account A

Device 2 -> Account B



Check that:



both accounts appear online



Global chat loads



Direct chat works



a call can be started



the other device receives the call



the call connects



audio/video permissions are allowed



Two physical devices are recommended when testing calls.



📁 Project Structure



gamzone/

│

├── index.html

├── script.js

├── calls.js

├── calls.css

├── gamezone\_server.py

├── gamezone starter.bat

├── README.md

├── .gitignore

│

├── assets/

├── games/

│

└── chat-server/

&#x20;   ├── server.py

&#x20;   ├── requirements.txt

&#x20;   ├── users.json

&#x20;   └── profile\_pictures/



❓ Troubleshooting



Chat says Loading



Open:



YOUR\_CHAT\_URL/health



If it does not work, make sure:



chat-server/server.py is running



port 5000 is reachable



your chat URL is correct



your tunnel/reverse proxy points to port 5000



Site works but chat does not



Check the frontend's CHAT\_SERVER URL.



Also make sure the chat server allows your main site in:



ALLOWED\_ORIGINS



Browser shows a CORS error



Add the exact main-site origin to:



ALLOWED\_ORIGINS



For example:



"https://cosmic.example.com"



Then restart server.py.



Another user does not appear online



Make sure:



both users are logged in



both devices can reach the chat/API domain



the API URL is correct



the server was restarted after changing domains



Call stays on Connecting



Check the chat-server terminal.



If you see the WebRTC:



offer

answer



being exchanged but the peer connection never connects, the network may require TURN.



Python command does not work



Try:



py -3



instead of:



python



📤 Uploading to GitHub



When creating the repository and GitHub asks:



Add .gitignore



choose:



None



because CØSMIC ZØNE uses its own custom .gitignore.



Then upload the files or run:



git init

git add .

git commit -m "Initial CØSMIC ZØNE release"

git branch -M main

git remote add origin YOUR\_GITHUB\_REPOSITORY\_URL

git push -u origin main



Before every push:



git status



Make sure private server data is not being committed.



⚠️ Important



If you fork or host CØSMIC ZØNE yourself:



use your own domains or local addresses



ngrok is optional



update the chat/API URL in the project



update ALLOWED\_ORIGINS



never publish private account data



never publish auth\_secret.json



keep .gitignore enabled



use HTTPS for public voice/video deployments



🌌 CØSMIC ZØNE



Run it locally, on your network, through a tunnel, or on your own domains.
(THE MEDIA PLAYER NEEDS A API PLEASE FIX IT)

