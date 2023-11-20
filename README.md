## Fail2Ban4Mosquitto: A simple setup to enable Fail2Ban for Mosquitto

Filter and jail that enables you to easily manage banning IPs on your internet facing MQTT broker.
Works well on Debian 12 and Mosquitto 2.0.11. 

Notes:
-------------
* This is tested on Debian 12 (Bookwork) and and Mosquitto 2.0.11 but will probably work on other distros as well.
* Have fail2ban installed (apt install fail2ban)
* Filter also works with IPv6

Check log compatibility:
------------------------
Please check if your log follows this pattern:

    1700479481: New connection from 1.1.1.1:54636 on port 8883.
    1700479481: Client <unknown> disconnected, not authorised.

If not, please contact me so I can add your pattern to filter. Or if you already did the modification yourself, please make a PR. Thanks!

Setup:
------
* Copy filter.d/mosquitto-auth.conf to the /etc/fail2ban/filter.d/ directory.
* Copy jail.d/mosquitto-auth.conf to the /etc/fail2ban/jail.d/ directory.
* Make sure to configure the correct ports for your setup. In the example 1883 is also included, but that one should be firewalled anyways and only be used on localhost.