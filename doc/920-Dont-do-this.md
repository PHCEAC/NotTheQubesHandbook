# Things not to do

* In general, parse or process any unsanitised data from less trusted qubes.
* qvm-features could contain data originating from untrusted qubes (? TBC: https://github.com/QubesOS/qubes-issues/issues/10595#issuecomment-3766510056 )
* In Dom0: ```fdisk -l``` 

    Parses all partition tables, including ones under control of the enemy.
