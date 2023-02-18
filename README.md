# open TCP connection

# peer1
import socket

host = ‘0.0.0.0’
port = 1234

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind((host, post))
s.listen(1)

print(‘Listening on {}:{}’.format(host,port))

conn, addr = s.accpet()
print(‘Connected by {}:{}’.format(addr[0], addr[1])


# peer2
import socket

host = ‘152.7.177.238’  # peer1 ip address
port = 1234

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect((host,post))

print(‘Connected to {}:{}’.format(host,post))


# create a torrent
import sys
import time
import libtorrent as lt

fs = lt.file_storage()
lt.add_files(fs, “/home/sjo/test/bfiles/”)  
t = lt.create_torrent(fs)
t.add_tracker(“py3createtorrent -t udp://tracker.openbittorrent.com:80/announce”, 0)
t.set_creator(‘libtorrent %s’ % lt.version)
t.set_comment(“Test”)
lt.set_piece _hashes(t, “/home/sjo/test/”)  
torrent = t.generate()
f = open(“B.torrent”, “wb”)  
f.write(lt.bencode(torrent))
f.close()


# seed a torrent
Import libtorrent as lt
Import sys
Import time

ses = lt.session({‘listen_interfaces’ : ‘0.0.0.0:6881’})
print(sys.argv)
info = lt.torrent_info(‘B.torrent’)
H = ses.add_torrent({‘ti’:info, ‘save_path’: ‘/home/sjo/com1/data’})
s = h.status()
print(‘starting’, s.name)

while(not s.is_seeding):
    s = h.status()

   print(‘\r%.2f%% complete (down: %.1f kB/s up: %.1f kB/s peers: %d) %s’ % (
        s.progress * 100, s.download_rate / 1000, s.upload_rate / 1000,
        s.num_peers, s.state), end = ‘ ‘)

   Alerts = ses.pop_alerts()
   For a in alerts:
     If a.category() & lt.alert.category_to.error_notification:
        print(a)

   sys.stdout.flush()
  
   time.sleep(1)
print(h.status().name, ‘complete’)


# download
from torrentp import TorrentDownloader

torrent _file = TorrentDownloader(“B.torrent”, ‘test/’)
torrent_file.start_download()


