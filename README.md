# purevpn-pptp-scatter
I found it annoying to use tools such as nmtui to manually drop and reconnect VPN connections (I'm sure there's other ways), so decided to make a simple bash script to drop any existing VPN connection and then randomly pick a new one to re-establish VPN.
The script is run from cron.hourly 

I'm using this with:
-- Arch Linux on an Raspberry Pi2
  -- 4.14.22-1-ARCH #1 SMP Tue Feb 27 06:45:49 UTC 2018 armv7l GNU/Linux

With the following installed
-- purevpn-networkmanager
-- networkmanager-pptp

Before you run it, you need to generate the NetworkManager PPTP/VPN configurations.
This can be done using the generate.nm.pptp
