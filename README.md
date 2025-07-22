# P2P
P2P (Pahadi to Pahadi) Messaging App is a secure, peer-to-peer chat platform built for users of Himachal Pradesh. It works without central servers, syncing messages via Bluetooth. With QR code contact sharing and local data storage, P2P ensures true anonymity and offline communication.It's best to think of it as a hybrid, offline-first tool.
Here is a clear breakdown of what works offline versus what requires an internet connection:
What Works Perfectly Offline
Once you have loaded the application at least once, the following features are available completely offline, thanks to the Service Worker and local browser storage (IndexedDB):
✅ Loading the App: After your first visit, you can close the tab, turn off your internet, and reopen the app by visiting its URL. It will load instantly from the cache.
✅ Managing Your Identity: You can change your nickname, upload a new profile photo from your device, and switch themes. All these changes are saved directly in your browser.
✅ Viewing Your QR Code: You can open the app offline and navigate to the "Show QR Code" screen. The app will generate and display your personal QR code using your locally stored Peer ID.
✅ Scanning a QR Code: You can open the scanner and use your camera to read a friend's QR code. The app will successfully decode their Peer ID.
What Requires an Internet Connection
The core purpose of the app—communicating with another person—requires an internet connection for a brief, critical step.
❌ Establishing a Connection (The Handshake): This is the most important online step. To initiate a chat, both you and your peer must be online. The PeerJS service acts as a "digital switchboard" or an "introducer." Your app connects to this server to say, "I am here, and my ID is X." When you want to connect to peer "Y," the server helps your two browsers find each other on the internet.
❌ The Chat Itself: While the initial handshake requires the internet, once the connection is established, the messages flow directly between you and your peer (peer-to-peer). This is very data-efficient, but the underlying connection still relies on your active internet connection. If you go offline, the connection will drop.
❌ The Very First Visit: The first time you ever open the app, your browser needs to download the single HTML file. After that, the Service Worker takes over for offline access.
Summary Table
Feature	Status	Notes
Loading the App	🟢 Offline	Works after the first visit, thanks to caching.
Editing Nickname/Photo	🟢 Offline	All identity data is stored locally in the browser.
Generating Your QR Code	🟢 Offline	Uses your local Peer ID and a cached library.
Scanning a QR Code	🟢 Offline	The camera and decoding library work without internet.
Connecting to a Peer	🔴 Online	Requires a signaling server to perform the initial "handshake."
Sending/Receiving Messages	🔴 Online	Requires an active internet connection to maintain the peer-to-peer link.
In conclusion, I have built a powerful Progressive Web App (PWA). It uses modern web technologies to provide a fantastic, app-like experience that works offline for many tasks, while still relying on the internet for its primary function: connecting people.

