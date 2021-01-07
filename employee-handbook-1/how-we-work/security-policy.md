# Security Practices

### Enable "Find My Mac" <a id="enable-find-my-mac"></a>

Apple’s iCloud service has a feature called Find My Mac which lets you see the location of your Apple device. As long as your lost Mac isn’t in sleep and is connected to a Wi-Fi network or tethered to a personal hotspot, you can locate it on a map. If it’s connected to the Internet via Ethernet, Wi-Fi, or a personal hotspot, you can play a sound on it, lock it, or erase it completely.

This location is not very precise, but it can be a useful piece of data if you accidentally leave your laptop somewhere. You should enable this for all your Apple devices, even MacBooks and iMacs.Find My Mac

![Find My Mac](https://i.imgur.com/nSHZFMb.png)

### Use a Password Manager <a id="use-a-password-manager"></a>

Given the current state of internet security, sensitive data leaking all the time is not even breaking news. Which means the security of your data, although should be the concern of the service, is also slightly in your hands. You must ensure it is as difficult as possible for someone to get access to your data.

One way to do this is to use different passwords on every website, and let them be completely random — and unrelated to your date of birth, first pet, aunt’s name, first crush etc. To do that entirely in your head and remember them all, is obviously impossible. The answer? A password manager!

Password managers like [1Password](https://1password.com/), [LastPass](https://www.lastpass.com/), and [KeePass](https://keepass.info/) let you generate and store random complex passwords — for example, 30 characters, mixed case, with numbers and symbols! Some of them also allow storing credit cards and personal identification details. Pretty much all the popular ones also let you auto-fill the relevant details in the login form of a website. Magic!

Once you change all your passwords to lengthy random ones, the only password you need to remember is the “master” password of the manager itself. This means that if a service gets hacked and passwords get leaked, only the password you used on that particular website gets compromised. All other passwords remains safe!

### Two-Factor Authentication <a id="two-factor-authentication"></a>

Whenever possible, you should use [two-factor authentication \(2FA\)](https://en.wikipedia.org/wiki/Multi-factor_authentication) for logging in to services. Normally, you only need a Username \(or an email\) and a Password to login to a service. Usernames are fairly easy to guess -- most people repeat email addresses and usernames across services, and many of those services publicly display this data. When it comes to passwords, most people repeat those too and \(unfortunately\) use something that is fairly easy to guess. Organisations have historically been bad at keeping user data safe. Passwords are stored using insecure methods, databases get hacked -- these are now normal occurrences in the news and it doesn't even surprise us.

2FA lets people use a second factor for authentication. Indian banks and cards use SMS OTPs as a second factor all the time. It ensures that the user must know the full details of a card, and must also possess the phone-number registered against the card. Similarly, popular services like Gmail, Github, Slack etc. allow a _randomly-generated number_ to be used as a second factor, just like a bank's OTP.

A very popular, free of cost, OTP generation app is [Authy](https://authy.com/). Authy has helpful guides to setup 2FA on most services, and you should turn on 2FA for every service. It benefits you!

### Enable FileVault \(encryption\) <a id="enable-filevault-encryption"></a>

Our devices \(computers, phones, tablets etc.\) contain a lot of private and confidential data belonging to us and our clients. If you’re logged into your Wednesday accounts \(email, drive, remote servers etc.\) on any device, you must take extra precaution that the data remains safe. As a general rule, you should try and limit the number of devices that have any work-related data.

Most modern Android and iOS devices support hardware encryption of data, and have it enabled by default. However, macOS computers do not have encryption enabled by default and you must enable it yourself — you should do this _as soon_ as you get your computer!

In macOS, open System Preferences. Go to Security and find the tab called “FileVault” — that’s what Apple calls full-disk encryption. Once you enable it, the system will generate a decryption key that you should note down \(ideally a physical medium; definitely not on the same computer!\) and store somewhere safely. If this key is lost and you ever forget your password, it will be impossible to recover any data. The encryption process should take less than 30 minutes to finish, and you can keep working while it happens.FileVault in macOS Mojave

![FileVault on macOS Mojave](https://i.imgur.com/TEfaYDh.png)

## OWASP Guidelines

The OWASP foundation works to improve the security of software. It's community driven and has hundreds of chapters world-wide.

If you're working on a web or mobile application and don't know about the top 10 OWASP guidelines for that platform please get in touch with Mac.

