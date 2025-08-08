# Notes to Phceac

If you're here, you're probably lost... this is just a vague notion right now.

As a long time Gentoo linux user, I have always found the Gentoo Handbook to be a model of accessible documentation for a free project. 

The official Qubes docs are not always accessible/complete.
The Qubes community forum has a lot of useful information, but it is not always easy to find.

I'm currently expecting to put a lot of ordered lists and oneliners here.

Todo: 
* investigate best way to mark up individual lines with a "AppliesToQubesVersion" metadata.
* Decide how much to split into small files/directories.
* Use sparse numeric prefix at each level. (simplifies shell navigation, sorting, and file insertion)

This is far from a handbook, but I find it good personal discipline to maintain:
* simple language
* careful structuring
* sections of limited length
* avoid or explain jargon
* usefulness for people with less knowledge than myself, or who are not native english speakers
* other guidelines?

20250807: considering use of a pandoc style yaml header containing (e.g.):
* AppliesToQubesVersion: <4.3 (or >4.2.2, =4.1.1, etc)
     * need something similar on a line-by-line basis.
* Other tags ?
