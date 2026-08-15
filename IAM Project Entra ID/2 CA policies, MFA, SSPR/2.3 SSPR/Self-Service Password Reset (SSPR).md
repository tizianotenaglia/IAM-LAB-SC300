# Self-Service Password Reset (SSPR)

## What I did

### Configured SSPR in Entra ID (Entra ID -> Password reset) across the 4 main tabs: Properties,Authentication methods, Registration, Notifications.

## Why SSPR is important

SSPR is important because help to reduce the overhead workload on admins, reduce the time that Helpdesk or User adminisistrator have to spend to reset 
passwords for users.
SSPR allow the user to reset their own passwords without having an admin involved.

###**NB**: a microsoft 365 business premium license or Microsoft P1/P2 license is required to unlock the full potential (eg psw writeback)

**1-Properties**

SSPR enabled for All users, with Number of methods required to reset set to 2, for stronger
verification before a password can be reset.

![SSPR Properties tab](imgs/1.png)

**2-Authentication methods**

Legacy tab, now mostly superseded by the unified Authentication methods policy configured earlier
(Module 3.1). Only "Number of methods required to reset" and the "Security questions" toggle remain
here - Security questions left disabled( very weak method).
All other methods (Authenticator, Passkey, Email OTP scoped to guests, etc.) are inherited from the main auth methods
policy.

![SSPR Authentication methods tab](imgs/2.png)

**3-Registration**

Requires users to register their SSPR methods the next time they sign in, so nobody is left without
a way to reset their own password later.

![SSPR Registration tab](imgs/3.png)

**4-Notifications**

Notifies users by email whenever their password is reset, and notifies all admins when another
admin resets their own password - both help spot unauthorized or suspicious resets quickly.

![SSPR Notifications tab](imgs/4.png)
