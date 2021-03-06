# Fail2Ban Blacklist for Repeat Offenders of Apache (action.d)
[![gitcheese.com](https://api.gitcheese.com/v1/projects/bc50574f-b6dc-4f08-80d4-f6ba5baf0d43/badges)](https://www.gitcheese.com/app/#/projects/bc50574f-b6dc-4f08-80d4-f6ba5baf0d43/pledges/create)
### Author: Mitchell Krog <mitchellkrog@gmail.com>
### Version: 1.1

# Add on for Apache Ultimate Bad Bot and Spam Referrer Blocker
GitHub: https://github.com/mitchellkrogza/apache-ultimate-bad-bot-blocker


##### Tested On: Fail2Ban 0.9.3
##### Server: Ubuntu 16.04
##### Firewall: IPTables

### Dependancies: 
#####requires apacherepeatoffender.conf in /etc/fail2ban/filter.d folder
#####requires apacherepeatoffender.conf in /etc/fail2ban/action.d folder
#####requires jail settings called [apacherepeatoffender]
#####requires apache.repeatoffender file in /etc/fail2ban
`create with sudo touch /etc/fail2ban/apache.repeatoffender`

`chmod +x /etc/fail2ban/apache.repeatoffender`

#### Drawbacks: 
Only works with IPTables


#### Based on: 
The Recidive Jail from Fail2Ban

This custom filter and action for Fail2Ban will monitor your Apache logs and perma-ban
any IP address that has generated far too many 403 errors over a 1 week period
and ban them for 1 day. This works like a charm as an add-on for my Apache Bad
Bot Blocker which takes care of generating the 403 errors based on the extensive
list of Bad Referers, Bots, Scrapers and IP addresses that it covers. This provides short
block periods of one day which is enough to keep agressive bots from filling up your log files.
See - https://github.com/mitchellkrogza/apache-ultimate-bad-bot-blocker for more info on the Apache Bad Bot and Spam Referrer Blocker

This custom action requires a custom jail in your jail.local file for Fail2Ban

Your jail file would be configured as follows

```
[apacherepeatoffender]
enabled = true
logpath = %(apache_access_log)s
filter = apacherepeatoffender
banaction = apacherepeatoffender
bantime  = 86400   ; 1 day
findtime = 604800   ; 1 week
maxretry = 20
```

### If this helped you [You can buy me a beer](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=TNCNMH8QVM78J):beer: or send some cheese for my mouse [![gitcheese.com](https://api.gitcheese.com/v1/projects/bc50574f-b6dc-4f08-80d4-f6ba5baf0d43/badges)](https://www.gitcheese.com/app/#/projects/bc50574f-b6dc-4f08-80d4-f6ba5baf0d43/pledges/create)