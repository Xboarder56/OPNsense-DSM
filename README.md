# OPNSense
OPNSense DSM for QRadar

This DSM config will support parsing and alerting for the following, DHCP events and Firewall events. If you have any questions you can create an issue for the GitHub project or open a question/reply on the IBM QRadar CE forms located at: https://ibm.biz/qradarceforums

# OPNSense Changes
1. Enable VPN logging by selecting System - Settings - Logging and selecting the check box next to Firewall events and DHCP service Events.

Note: on the blog post listed below (whatthesec.com) they have fields for unbound DNS. Because you have a choice of DNSMASQ and unbound in OPNSense I did not include these in this repo. I have created parsing/events for DNSMASQ but I run this on it's own log source thus I never included it. If there is people that are looking for this I will work to parse DNSMASQ events in OPNSense and include them with this repo.

# QRCE Changes
1. Create a new custom DSM called (OPNSense) using the DSM editor option under the admin settings window.
2. Once the custom DSM has been created close the window and click the Log Source Extensions option in the admin settings.
3. Click Add near the top right corner
4. Enter a name of "OPNSenseCustom_ext"
5. Select your newly created log source (OPNSense) that you created earlier.
6. Click the upload button and select the file "OPNSenseCustom_ext.xml"
7. Click done and proceed to open the DSM menu and select your log source (OPNSense) that you created earlier.
8. You will need to select Event Mappings tab in the DSM editor and create the manual entries located in the file "Event Mappings.txt"
9. Finally, you will need to create a new log source selecting the custom Log source type we just created.

# Change Log
  - 02-02-2019 - Tweaked event category parsing to avoid false positives. Parsed destination IP from dhclient logs. Mapped 13 new events for dhclient logs.
  - 01-26-2019 - Initial support for parsing dhclient logs. I still have to map them but they will be parsed under the correct event ID and category. Additionally, the log source time has been updated to 2019.
  - 12-17-2018 - Initial Upload of the source code.

# Sources/References
- https://www.whatthesec.com/index.php/2018/07/13/sending-pfsense-logs-to-qradar/ (Created the original DSM I have only made small modifications for parsing additional fields and the Log Source Time. All the credit for this goes to him.)
