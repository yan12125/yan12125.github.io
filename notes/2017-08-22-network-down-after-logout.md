Recently I got a mysterious bug. I have a server, and whenever I logouts all sessions, its network is broken. I can neither ping it nor ssh into it.

The culprit is NetworkManager. "All users may connect to this network" is not checked, so only my account can access the network.

Reference: https://www.centos.org/forums/viewtopic.php?t=49267
