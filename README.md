# purevpn-pptp-scatter
I found it annoying to use tools such as nmtui to manually drop and reconnect VPN connections (I'm sure there's other ways).
So decided to write a simple bash script to drop any existing VPN connection and then randomly pick a new one to re-establish VPN.
The script is run from cron.hourly.
My bash is simple - so any improvements are welcome.


I'm using this with:

-- Arch Linux on an Raspberry Pi2
  -- 4.14.22-1-ARCH #1 SMP Tue Feb 27 06:45:49 UTC 2018 armv7l GNU/Linux

With the following installed

-- purevpn-networkmanager
-- networkmanager-pptp

Before you run it, you need to generate the NetworkManager PPTP/VPN configurations.
This can be done using the generate.nm.pptp

Running the generate script will prompt for your purevpn username and password - this is then used as variable to run:
  purevpn -t pptp -c <city name found from the $(purevpn -l)> -u <username> -p <password>
  
This will setup a new VPN config for every city purevpn has (with 1 exception... Korea South"... I think the output is not correct)
There is surely a more elegant way to achieve the same result - but this worked for me and is re-runable.

vpn_scatter is very simple, it drops any existing VPN
Then it asks NM for a list of VPN connections, uses shuf and awk to pick a random UUID, which is then connected.
It then outputs your IP's geo info (this is more for logging and debugging)

I've got it restarting squid too, might not be needed, but hey...
