
See \@ben-grande at  https://forum.qubes-os.org/t/is-4-3-sluggish-for-you/38816/32

There are ways to time startup of a qube, you can do this for a stopped anon-whonix:
```
time qvm-run -p --service anon-whonix qubes.WaitForSession
```
And from a running anon-whonix:
```
time qvm-run -a --service anon-whonix qubes.StartApp+janondisttorbrowser
```
( Corrected by \@barto )
