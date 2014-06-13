xwinreg-move-to-desk(1) -- move windows of specified regions to another desktop.
========================================================================

## XWINREG
Part of `xwinreg`(1).
## SYNOPSIS
xwinreg-move-to-desk [-T] (-h|-r|-v) -D [-W]
## REQUIREMENT
GNU bash, grep, wmctrl, xprop
## DESCRIPTION
`xwinreg-move-to-desk`(1) reads variables of a Tmp File and moves windows to a desktop. The Tmp File is not updated after that action.
## OPTIONS
* `-D` <DESK>:
 Move windows to desktop <DESK>

* `-h`:
 Display a short help.

* `-r` <REG>:
 Select, which regions should be processed.

* `-T` <FILE>:
 Specify a nonregular Tmp file.

* `-v`:
 Print current version of `xwinreg-move-to-desk`(1).

* `-W`:
 Switch to <DESK> after moving.

## ARGUMENTS
* <DESK>:
 `curr` or relative to the current desktop `next` or `preview`. To specify a desktop number (starts at 0) use the prefix `i:`; a desktop name is prefixed with `s:`. Examples: `i:1`; `s:web`; `"s:some stuff"`.

* <FILE>:
 Regular file or named pipe.

* <REG>:
 Up to this sample: `1` or `1,3` or `1-3` or `1,2-3`. Additional: `active` or `all`.

## EXAMPLES
 xwinreg-move-to-desk -r active -D next -W

 xwinreg-move-to-desk -r 2 -D curr

 xwinreg-move-to-desk -r active -D i:1 -W

 xwinreg-move-to-desk -r active -D s:internet -W

## ENVIROMENT
* <TMPDIR>:
 By default, Tmp File will be written as **TMPDIR/xwinreg_default.tmp**, otherwise as **/tmp/xwinreg_default.tmp**.

* <XWINREG_TMP_FILE>:
 Specify this instead default setting and instead using <XWINREG_TMP_FILE> in a Conf File.

## BUGS & REQUESTS
Report it on **https://github.com/D630/xwinreg/issues**
## LICENSE
`xwinreg-move-to-desk`(1) is licensed with GNU GPLv3. You should have received a copy of the GNU General Public License along with this program. If not, see for more details **http://www.gnu.org/licenses/gpl-3.0.html**.
## SEE ALSO
`bash`(1), `grep`(1), `wmctrl`(1), `x`(7), `xprop`(1), `xwinreg`(1), `xwinreg-calculate`(1), `xwinreg-close`(1), `xwinreg-cycle`(1), `xwinreg-focus`(1), `xwinreg-focus-toggle`(1), `xwinreg-hide`(1), `xwinreg-id`(1), `xwinreg-layout`(1)