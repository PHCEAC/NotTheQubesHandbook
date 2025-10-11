# Policy

## what does policy do?
With no policy, it is impossible for any qube to communicate or interact with any other.
Policy allows interactions.
## Why change policy?

? todo Some use cases?

## How it works 

Like everything in QubesOS, the policy mechanism is designed to be as simple as possible.

1. a qube requests to be allowed to do something to another qube 
1. policy files are read in sort order (? todo: lexical or numeric? locale?)
2. the winning policy line is the first one which matches the fields of the policy line
4. if no line matches in any file, the default is to Deny.


## How to add policy

Some editing tips here:

https://forum.qubes-os.org/t/how-do-you-properly-create-a-policy-for-qubes-filecopy/36629/2

?? Issue needed for warning(s) in policy files, readme in policy dir?

