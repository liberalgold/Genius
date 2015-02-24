Website: http://liberalgold.com<br>
<br>
GENIUS is a PoS based cryptocurrency with physical gold coin value.<br>
<br>
GENIUS wallets can download from http://liberalgold.com<br>
<br>
Building GENIUS from sourcecode.<br><br>
<b>Debian GENIUS-QT</b><br>
Make sure that the required packages for Qt5 development of your distribution are installed, for Debian and Ubuntu these are:
apt-get install qt5-default qt5-qmake qtbase5-dev-tools qttools5-dev-tools \
    build-essential libboost-dev libboost-system-dev \
    libboost-filesystem-dev libboost-program-options-dev libboost-thread-dev \
    libssl-dev libdb++-dev libminiupnpc-dev git
	<br><br>
Download latest GENIUS git source: GIT CLONE https://github.com/liberalgold/genius.git<br>
<br>
then execute the following:<br>
qmake<br>
make<br>
<br>
Alternatively, install Qt Creator and open the genius-qt.pro file.<br>
An executable named genius-qt will be built.<br>
<br>
<b>GENIUS serverside daemon (geniusd)</b><br>
Download latest GENIUS git source: GIT CLONE https://github.com/liberalgold/genius.git<br>
<br>
Compile daemon:<br>
cd genius-master/src/<br>
chmod 777 leveldb/build_detect_platform<br>
make -f makefile.unix USE_UPNP=-<br>
cp geniusd /usr/bin/geniusd<br>
<br>
Start daemon once: <br>
geniusd<br>
<br>
Make config file genius.conf:<br>
nano /root/.genius/genius.conf<br>
<br>
Example conf file:<br>
port=12001<br>
rpcport=12000<br>
rpcuser=user<br>
rpcpassword=x<br>
rpcallowip=127.0.0.1<br>
server=1<br>
listen=1<br>
daemon=1<br>
txindex=1<br>
addnode=178.62.154.31:12001<br>
addnode=95.85.33.193:12001<br>
<br>
Start daemon with new config file:<br>
geniusd<br>
After checkpoint (block 1000) is synch, restart daemon.<br>
More info's about daemon, type:<br>
geniusd help<br>
<br>
<b>Windows build instructions:</b><br>
Download the QT Windows SDK and install it. You don't need the Symbian stuff, just the desktop Qt.<br>
Compile openssl, boost and dbcxx.<br>
Open the .pro file in QT creator and build as normal (ctrl-B)<br>
<br>
<b>Mac OS X</b><br>
Download and install the Qt Mac OS X SDK. It is recommended to also install Apple's Xcode with UNIX tools.<br>
Download and install MacPorts.<br>
Execute the following commands in a terminal to get the dependencies:<br>
sudo port selfupdate<br>
sudo port install boost db48 miniupnpc<br>
Open the .pro file in Qt Creator and build as normal (cmd-B)<br>
Build configuration options<br>
<br>
UPNnP port forwarding<br>
To use UPnP for port forwarding behind a NAT router (recommended, as more connections overall allow for a faster and more stable genius experience), pass the following argument to qmake:<br>
qmake "USE_UPNP=1"<br>
(in Qt Creator, you can find the setting for additional qmake arguments under "Projects" -> "Build Settings" -> "Build Steps", then click "Details" next to qmake)<br>
This requires miniupnpc for UPnP port mapping. It can be downloaded from http://miniupnp.tuxfamily.org/files/. UPnP support is not compiled in by default.<br>
Set USE_UPNP to a different value to control this:<br>
USE_UPNP=-	no UPnP support, miniupnpc not required;<br>
USE_UPNP=0	(the default) built with UPnP, support turned off by default at runtime;<br>
USE_UPNP=1	build with UPnP support turned on by default at runtime.<br>
Notification support for recent (k)ubuntu versions<br>
<br>
QR codes<br>
To see desktop notifications on (k)ubuntu versions starting from 10.04, enable usage of the FreeDesktop notification interface through DBUS using the following qmake option:<br>
qmake "USE_DBUS=1"<br>
Generation of QR codes<br>
libqrencode may be used to generate QRCode images for payment requests. It can be downloaded from http://fukuchi.org/works/qrencode/index.html.en, or installed via your package manager. Pass the USE_QRCODE flag to qmake to control this:<br>
USE_QRCODE=0	(the default) No QRCode support - libarcode not required<br>
USE_QRCODE=1	QRCode support enabled<br>
<br>
<br>
Homepage: liberalgold.com<br>