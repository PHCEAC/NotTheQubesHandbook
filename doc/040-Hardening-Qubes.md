
Todo: move to Securing your workflows section?




## What are you worried about?

* Loss of access to something you have:
  * your valuable or irreplacable data
  * your passwords or secrets
* Someone else gets access
  * to those passwords or data
  * ...
* or learns information:
  * personal information about you
  * about your activities
  * about an association between different activities
  * ...

What cause(s):

* User error and phishing
* hardware failure
* spying, eavesdropping on UI
* hacking + destruction
* hacking + extortion
* hacking + exfiltration

* valuables in:
  * static data
  * ram
  * swap
  * HID communication

## Hardening dom0

* Test your knowledge
  * Look at each every QSB : https://www.qubes-os.org/security/qsb/
  * What risk did it present?
  * Is there any change inside dom0 that could have protected
    against those risks?
* all your data should be in your qubes.
* Ask: is policy and personal workflow more relevant?



## Policy ideas

Prevention: what does it mean?
Cannot change? cannot start qube if value is wrong?

* Vaults:
  * prevent change of netvm, use as target/source of tcpconnect
  * prevent attachment of usb, other?
  * prevent gui (text console only?)
  * Limit copy-paste?
  * other channels
 * Privileged qubes (with some special access)
   * some of vaults' ideas
