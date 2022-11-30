---
description: A walkthrough for resolving Handshake domains with NextDNS.io
---

# 如何访问使用Handshake域名的网站

## Windows

Estimated setup time: 1-2 minutes

{% tabs %}
{% tab title="Text" %}
1. Visit [https://nextdns.io/](https://my.nextdns.io/) and click "Try it now for free".
2. Scroll down to the "How To Setup" section and note the two 9 digit bold addresses under the "IPv4 (with linked IP)" section.
3. Open the Start menu to open Settings or Control Panel.
4. Open Network & Internet and then Change adapter options.
5. Right click the network you are connected to and open its Properties to select Internet Protocol Version 4 > Properties and then "Use the following DNS server addresses" to add the two 9 digit addresses you noted in step 2. _If you have existing addresses you’ll need to replace them with your 2 new DNS addresses._
6. Return to your browser and go to the Settings tab of your NextDNS to turn on "Resolve Handshake domains".
7. Try visiting our welcome page here: [http://welcome.nb./](http://welcome.nb/) If it doesn't work, you may need to click the refresh button by “Currently linked IP” in the Setup tab.
{% endtab %}

{% tab title="Picture" %}
![Step 1: Visit nextdns.io and click "Try it now for free"](<../.gitbook/assets/Windows 1.png>)

![Step 2: Note the 2 highlighted addresses](<../.gitbook/assets/Windows 2.png>)

![Step 3: Open Control Panel and Network & Internet](<../.gitbook/assets/Windows 3.png>)

![Step 4: Change adapter options](<../.gitbook/assets/Windows 4.png>)

![Step 5: Add the two addresses from before](<../.gitbook/assets/Windows 5.png>)

![Step 6: Return to your browser, go to Settings, turn on "Resolve Handshake domains" ](<../.gitbook/assets/Windows 6.png>)

![Step 7: You may need to link your IP](<../.gitbook/assets/Windows 7.png>)
{% endtab %}
{% endtabs %}

## macOS

Estimated setup time: 1-2 minutes

{% tabs %}
{% tab title="Text" %}
1. Visit [https://nextdns.io/](https://my.nextdns.io/) and click "Try it now for free".
2. Scroll down to the "How To Setup" section and note the two 9 digit bold addresses under the "IPv4 (with linked IP)" section.
3. Go to Network through Apple Logo -> System Preferences and click Advanced....
4. Select the DNS tab, and click + to add the two 9 digit addresses you noted in step 2, and then click OK and Apply. _If you have other addresses, just drag your 2 new DNS addresses to the top of the list._
5. Return to your browser and go to the Settings tab of your NextDNS to turn on "Resolve Handshake domains".
6. Try visiting our welcome page here: [http://welcome.nb./](http://welcome.nb/) If it doesn't work, you may need to click the refresh button by “Currently linked IP” in the Setup tab.
{% endtab %}

{% tab title="Picture" %}
![Step 1: Visit nextdns.io and click "Try it now for free"](<../.gitbook/assets/macOS 1.png>)

![Step 2: Note the 2 highlighted addresses](<../.gitbook/assets/macOS 2.png>)

![Step 3: Go to Network through Apple Logo -> System Preferences and click Advanced.... ](<../.gitbook/assets/macOS 3.png>)

![Step 4: In the DNS tab, add the two addresses from before](<../.gitbook/assets/macOS 4.png>)

![Step 5: Return to your browser, go to Settings, turn on "Resolve Handshake domains" ](<../.gitbook/assets/macOS 5.png>)

![Step 6: You may need to link your IP](<../.gitbook/assets/macOS 6.png>)
{% endtab %}
{% endtabs %}

## Mobile

Estimated setup time: 2-3 minutes

{% tabs %}
{% tab title="Text" %}
1. Download and install the NextDNS app for either [Android](https://play.google.com/store/apps/details?id=io.nextdns.NextDNS) or [iOS](https://apps.apple.com/app/nextdns/id1463342498).
2. &#x20;Visit [https://nextdns.io/](https://my.nextdns.io/) and tap Try it now for free .
3. Scroll down to the "How To Setup" section and copy the six-character ID under the "NextDNS Official App" section.
4. Open the NextDNS app's settings and turn on Use custom configuration. When prompted for the Configuration ID, paste the six-character ID you copied earlier.
5. Connect the NextDNS app and tap OK when prompted for a VPN Connection request.
6. Return to your browser and go to the Settings tab of your NextDNS to turn on "Resolve Handshake domains".
7. Try visiting our welcome page here: [http://welcome.nb./](http://welcome.nb/) If it doesn't work, you may need to click the refresh button by “Currently linked IP” in the Setup tab.
{% endtab %}

{% tab title="Picture" %}
![Step 1: Download the NextDNS app ](<../.gitbook/assets/Mobile 1.PNG>)

![Step 2: Visit nextdns.io and click "Try it now for free"](<../.gitbook/assets/Mobile 2.PNG>)

![Step 3: Copy the six-character ID ](<../.gitbook/assets/Mobile 3.PNG>)

![Step 4: Paste the six-character ID](<../.gitbook/assets/Mobile 4.PNG>)

![Step 5: Allow VPN connection](<../.gitbook/assets/Mobile 5.PNG>)

![Step 6: Return to your browser, go to Settings, turn on "Resolve Handshake domains" ](<../.gitbook/assets/Mobile 6.PNG>)

![Step 7: You may need to link your IP](<../.gitbook/assets/Mobile 7.png>)
{% endtab %}
{% endtabs %}

## More

Share a screenshot of a resolvable Handshake website in the [Namer Community ](https://discord.gg/BrApKfA)to earn the \<Resolver> role.

To learn more about DNS, try [DNS refresher](../about-handshake/dns-refresher.md).

{% hint style="info" %}
The following procedures are setup instructions provided by NextDNS. Though these have yet to be tested by Namebase staff, they should still work.&#x20;
{% endhint %}

### Linux

Change your DNS servers to **45.90.28.187** and **45.90.30.187**. Make sure you have linked the IP of the network you will setup.

### Router

1. Open the preferences for your router. Usually you can access it from your browser via a URL (like http://192.168.0.1/ or http://192.168.1.1/).
2. Locate the DNS settings inside the interface.
3. Remove all addresses (if any) then add **45.90.28.187** and **45.90.30.187**.
4. Click Save (or similar).

