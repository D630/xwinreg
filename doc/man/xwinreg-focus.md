xwinreg-focus(1) -- focus all windows in specified regions.
====================================================

## XWINREG
Part of `xwinreg`(1).
## SYNOPSIS
xwinreg-focus [-T] (-h|-r|-v)
## REQUIREMENT
GNU bash, grep, wmctrl, xprop
## DESCRIPTION
`xwinreg-focus`(1) reads variables inside a Tmp File and focuses windows in specified regions. Therefore, it switches to the desktop containing the windows, raises the windows, and gives them focus. At the end, the active window will be focused again. The Tmp File will not have an update.
## OPTIONS
* `-h`:
 Display a short help.

* `-r` <REG>:
 Select, which regions should be processed.

* `-T` <FILE>:
 Specify a nonregular Tmp file.

* `-v`:
 Print current version of `xwinreg-focus`(1).

## ARGUMENTS
* <FILE>:
 Regular file or named pipe.

* <REG>:
 Up to this sample: `1` or `1,3` or `1-3` or `1,2-3`. Additional: `active` or `all`.

## EXAMPLES
 xwinreg-focus -r active

 xwinreg-focus -T ${Home}/tmp/xwinreg.tmp -r 2

## ENVIROMENT
* <TMPDIR>:
 By default, Tmp File will be written as **TMPDIR/xwinreg_default.tmp**, otherwise as **/tmp/xwinreg_default.tmp**.

* <XWINREG_TMP_FILE>:
 Specify this instead default setting and instead using <XWINREG_TMP_FILE> in a Conf File.

## BUGS & REQUESTS
Report it on **https://github.com/D630/xwinreg/issues**
## LICENSE
`xwinreg-focus`(1) is licensed with GNU GPLv3. You should have received a copy of the GNU General Public License along with this program. If not, see for more details **http://www.gnu.org/licenses/gpl-3.0.html**.
## SEE ALSO
`bash`(1), `grep`(1), `wmctrl`(1), `x`(7), `xprop`(1), `xwinreg`(1), `xwinreg-calculate`(1), `xwinreg-close`(1), `xwinreg-cycle`(1), `xwinreg-focus-toggle`(1), `xwinreg-hide`(1), `xwinreg-id`(1), `xwinreg-layout`(1), `xwinreg-move-to-desk`(1)