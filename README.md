# popcon

`popcon` is a command that combines searching for Debian packages with
[popularity contest](https://popcon.debian.org) results.

## Quick Examples

What are the popular window managers?

```Shell
> popcon ~Gx11::window-manager
```

What are the popular Bluetooth managers?

```Shell
> popcon ~dbluetooth
```

What are the popular video players?

```Shell
> popcon ~svideo
```

What are the popular notification daemons?

```Shell
> popcon ~Pnotification-daemon
```

## Understanding the Output

```Shell
> popcon ~Gx11::window-manager
[...]
i   xmonad                           449   958   107     0
p   fluxbox                          680  1918   135     1
p   awesome                          764  1638   143     0
p   i3-wm                           1366  1389   183     0
i A openbox                         5896  6919  1704    11
p   kde-window-manager              8313  5907  2098   789
p   metacity                       11769 35948 11571    62
p   metacity-common                11769 35946 11572  1543
p   xfwm4                          13377 10205  2774     8
p   mutter                         30230  7419  7052    32
>
```

The columns on the left are the same as
[the output from `aptitude`](https://www.debian.org/doc/manuals/aptitude/rn01re01#cmdlineSearch).
The columns on the right are the popularity contest results, namely:

<table>
  <tr><th>vote:</th><td>The number of people who use this package regularly</td></tr>
  <tr><th>old:</th><td>The number of people who installed, but don't use this package regularly</td></tr>
  <tr><th>recent:</th><td>The number of people who upgraded this package recently</td></tr>
  <tr><th>no-files:</th><td>The number of people whose entry didn't contain enough information (atime and ctime were 0)</td></tr>
</table>

**Note:** The docs mention one more statistic: **inst**, the number of
people who installed this package. It's the sum of **vote** + **old**.

The results are sorted by the following keys, in this order: **vote**,
**old**, **recent**, **no-files**.

## Searching

You can search for anything
[that `aptitude` understands](https://www.debian.org/doc/manuals/aptitude/ch02s04s05).
