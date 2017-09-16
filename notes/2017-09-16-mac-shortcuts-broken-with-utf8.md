I was trying to enable copying and pasting between Linux and macOS via SSH. I followed several [1][2][3] guides and set up a local server to handle exchanged clipboard data. OK, things look good.

However, soon I found that pasting CJK brings question marks. A tip [4] suggests setting ```__CF_USER_TEXT_ENCODING```, which doesn't work for me. I ended up changing the content of ```~/.CFUserTextEncoding``` to ```0x8000100:0x8000100```. After reboot, copying and pasting CJK just works (TM).

But something strange hits me. Quite a few shortcuts involving Command doesn't work in Firefox and KeePassXC. With some trial and error, it turns out modified ```~/.CFUserTextEncoding``` broke things. I have no choice but changing it back.

KeePassXC uses QShortcut and Firefox appears to use Cocoa directly. What stops them from working? Dunno.

0x8000100 is exactly UTF-8 [5]. So, another amazing story of macOS: using UTF-8 as the default encoding can break things!

[1] http://brettterpstra.com/2014/02/19/remote-pbcopy-on-os-x-systems/
[2] https://seancoates.com/blogs/remote-pbcopy/
[3] https://gist.github.com/burke/5960455
[4] http://hints.macworld.com/article.php?story=20081231012753422
[5] https://developer.apple.com/documentation/corefoundation/cfstringbuiltinencodings/1542603-utf8
