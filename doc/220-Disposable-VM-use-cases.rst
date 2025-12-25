
* work-email qube \[...] that opens all links in my work browsing qube


From Adrelanos https://github.com/QubesOS/qubes-issues/issues/1118#issuecomment-131395780
where View-in-DispVM behaviour was created.

So we have 4 use cases here.

* "View in Disposable VM with disabled networking"
* "View in Disposable VM with enabled networking"
* "Edit in Disposable VM with disabled networking"
* "Edit in Disposable VM with enabled networking"



## set a specific dvm template as the converter template?

https://forum.qubes-os.org/t/possible-to-set-a-specific-qube-only-for-converting-pdf-images/38012/2

* dicovered [dispvm_netvm property](https://github.com/marmarek/old-qubes-core-admin/commit/7516737fae3222e5d64acaad83cd26948a618025).

* I think it still exists (?), and it seems like it could be useful for some related use-cases, but I am having trouble finding some documentation.

* I also see an issue about DispVM inheriting firewall rules, which could prevent some applications of it, but I am not understanding the details [Issue 1296](https://github.com/QubesOS/qubes-issues/issues/1296)





