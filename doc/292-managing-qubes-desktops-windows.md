

## Use devilspie2



## Use KDE activities

For example: 
[unman's solution here](https://forum.qubes-os.org/t/using-kde-plasma-activities-with-qubes-os/31561/9)


## messing with window properties

The visible window manager (WM):

sudo apt install x11-utils
$ xprop -root _NET_SUPPORTING_WM_CHECK
_NET_SUPPORTING_WM_CHECK(WINDOW): window id # 0x400002
$ xprop -id 0x400002 _NET_WM_NAME
_NET_WM_NAME(UTF8_STRING) = "Qubes"

xprop -id 0x400002 -format _NET_WM_NAME 8u -set _NET_WM_NAME 'dwm'
