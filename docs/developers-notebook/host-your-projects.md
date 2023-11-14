# Host Your Projects via Cloudflared Tunnel

This is a showcase of **hosting** your services from **localhost to internet** via **Cloudflare tunnel** managed locally and the local operating system is **macOS**.

During this road there a few choices [localtonet](https://localtonet.com/) or [ngrok](https://ngrok.com/) or [serveo](https://serveo.net/).

In my humble opinion Cloudflare Tunnel is the best option out there. It is free, easy to setup and you can use custom domains.

## Cloudflare Tunnel

This is a free feature of Cloudflare introduced by <https://blog.cloudflare.com/tunnel-for-everyone/>. You can find docs by <https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/>. Docs were sufficent in my case except for running the tunnel as service. I had to add configure daemon agent of macOS.

![Cloudflare Tunnel](https://developers.cloudflare.com/assets/handshake_hufad68abf6107ffc2ef859ebe1b42b6e2_299675_1768x1102_resize_q75_box-3f75968f.jpg)

## Set up your tunnel

!!! note

    This chapter is exactly same from Get started to create a locally-managed tunnel of official documentation.
    <https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/get-started/create-local-tunnel/>

### Create a Cloudflare Account

I am also using Cloudflare DNS services for my custom domains and I suggest this to easily create custom domain to your local services.

### Install cloudflared CLI and Create Tunnel 

```bash
brew install cloudflare/cloudflare/cloudflared
```

```bash
cloudflared tunnel login
```

```bash
cloudflared tunnel create <tunnel-name>
```

!!! note

    You can use one tunnel to host more than one service from your localhost so this name does not need to be a service specific name

```bash
cloudflared tunnel create <tunnel-name>
```

### Configure Tunnel in macOS

```bash
cloudflared tunnel route dns <tunnel-id/tunnel-name> <host-name>
```

```bash
ls /Users/<user-name>/.cloudflared
>   <tunnel-id>.json
    cert.pem
    config.yml
```

```yml
tunnel: <tunnel-id>
credentials-file: /Users/<user-name>/.cloudflared/<tunnel-id>.json

ingress:
    - hostname: <custom-domain-name>
      service: http://localhost:<port>
    - hostname: <custom-domain-name-2>
      service: http://localhost:<port>
```

### Run the Tunnel

- Run tunnel manually
```bash
cloudflared tunnel run  <tunnel-id/tunnel-name>
cloudflared tunnel --config /Users/<user-name>/.cloudflared/config.yml run <tunnel-id/tunnel-name>
```

- Run tunnel as a user (not system) service in macOS
```bash
cloudflared service install
```

!!! note
    Extra steps are required to run service according to config file we created. Even though documentation explicitly states it uses automatically the user config file. However in mycase the installed service only created quick try tunnel.

1. Edit plist config
```bash
cat com.cloudflare.cloudflared.plist
```
```xml
<><?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
	<dict>
		<key>Label</key>
		<string>com.cloudflare.cloudflared</string>
		<key>ProgramArguments</key>
		<array>
			<string>/usr/local/bin/cloudflared</string>
			<string>tunnel</string>
			<string>run</string>
		</array>
		<key>RunAtLoad</key>
		<true/>
		<key>StandardOutPath</key>
		<string>/Users/<user-name>/Library/Logs/com.cloudflare.cloudflared.out.log</string>
		<key>StandardErrorPath</key>
		<string>/Users/<user-name>/Library/Logs/com.cloudflare.cloudflared.err.log</string>
		<key>KeepAlive</key>
		<dict>
			<key>SuccessfulExit</key>
			<false/>
		</dict>
		<key>ThrottleInterval</key>
		<integer>5</integer>
	</dict>
</plist>
```

2. Check **launchctl** service && Boot the com.cloudflare.cloudflared
```bash
launchctl list | grep 'com.cloudflare*'
launchctl bootout com.cloudflare.cloudflared
launchctl bootstrap com.cloudflare.cloudflared
sudo launchctl start com.cloudflare.cloudflared
```

3. Check Output and Error files
```bash
cat /Library/Logs/com.cloudflare.cloudflared.err.log
cat /Library/Logs/com.cloudflare.cloudflared.out.log
```

3.2 Manually Start/Stop the service
```bash
sudo launchctl stop com.cloudflare.cloudflared
sudo launchctl start com.cloudflare.cloudflared
launchctl list | grep 'com.cloudflare*'
```

## Extra Step: Monitoring Services

I have started using [Uptime Robot](https://uptimerobot.com/) to monitor my services as it is free up to 50 monitors and easy to set up.

Just add the http health url and it is good to go with 5 min. intervals.

## References

- <https://blog.cloudflare.com/tunnel-for-everyone/>
- <https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/>
