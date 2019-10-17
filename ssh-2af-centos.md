Secure SSH with Google Authenticator Two-Factor Authentication on CentOS 7
- install epel-release. command belloew:

```
yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
```

- install google-authenticator, command bellow:
```
yum install google-authenticator
```
- runing _google-authenticator_ in your user, command bellow:
```
google-authenticator
```
> response

```
Do you want authentication tokens to be time-based (y/n) y
Warning: pasting the following URL into your browser exposes the OTP secret to Google:
  https://www.google.com/chart?chs=200x200&chld=M|0&cht=qr&chl=otpauth://totp/haryono@karangeurih%3Fsecret%3D6ZXQ2VCOLSDFDV5PMTXWLY3MNA%26issuer%3Dkarangeurih


Do you want me to update your "/home/haryono/.google_authenticator" file? (y/n) y

Do you want to disallow multiple uses of the same authentication
token? This restricts you to one login about every 30s, but it increases
your chances to notice or even prevent man-in-the-middle attacks (y/n) y

By default, a new token is generated every 30 seconds by the mobile app.
In order to compensate for possible time-skew between the client and the server,
we allow an extra token before and after the current time. This allows for a
time skew of up to 30 seconds between authentication server and client. If you
experience problems with poor time synchronization, you can increase the window
from its default size of 3 permitted codes (one previous code, the current
code, the next code) to 17 permitted codes (the 8 previous codes, the current
code, and the 8 next codes). This will permit for a time skew of up to 4 minutes
between client and server.
Do you want to do so? (y/n) n

If the computer that you are logging into isn't hardened against brute-force
login attempts, you can enable rate-limiting for the authentication module.
By default, this limits attackers to no more than 3 login attempts every 30s.
Do you want to enable rate-limiting? (y/n) y
```

> open link in your browser for the scan barcode authentication

- seting pamd ssh

vim /etc/pam.d/sshd
``` 
auth required pam_google_authenticator.so 
```

- setting sshd conf

vim /etc/ssh/sshd
``` 
ChallengeResponseAuthentication yes 
```
- restart sshd/ssh in your server/local
```
systemctl restart sshd
```










