xwinreg-calculate(1) -- calculate frame geos.
========================================

## XWINREG
Part of `xwinreg`(1).
## SYNOPSIS
xwinreg-calculate `[-C|-T|-n|-N|-a|-1|-2|-3|-4|-5|-6|-7|-8] (-h|-v)`
## REQUIREMENT
GNU bash, grep, X, xprop
## DESCRIPTION
Just as `xwinreg-id`(1), `xwinreg-calculate`(1) is required for layouting with `xwinreg-layout`(1). Its purpose is to set a frame relative to a workspace as scale base and to have base geometries; without that calculation `xwinreg-layout`(1) is not able to arrange regions and fill those with windows. All variables are written to a Temp File, and will then be processed in the course of layouting. You can here also determine the number of rows and columns for grid layouting or specify a Conf File with variables and frame aliases.

In the wrapper script `xwinreg`(1) you may not call the calculation directly; it will be called, before you build layouts with action `-l` and `-L`.
## OPTIONS
* `-1` <PX>:
 Specify the <WIDTH> of the frame.

* `-2` <PX>:
 Specify the <HEIGHT> of the frame.

* `-3` <PX>:
 Specify the left edge of the frame.

* `-4` <PX>:
 Specify the top edge of the frame.

* `-5` <PX>:
 Specify the left edge of the workarea.

* `-6` <PX>:
 Specify the top edge of the workarea.

* `-7` <PX>:
 Specify the <WIDTH> of the workarea.

* `-8` <PX>:
 Specify the <HEIGHT> of the workarea.

* `-a` <FRAMEALIAS>:
 Instead of options `-1`, `-2`, `-3` and `-4` specify an alias. See section **CONFIGURATIONS** in this Manpage.

* `-C` <FILE>:
 Read variables in a Conf File from <FILE>. See section **CONFIGURATIONS** in this Manpage.

* `-h`:
 Display a short help.

* `-n` <INT>:
 Specify number of rows for grid layouting, which is used later by `xwinreg-layout`(1).

* `-N` <INT>:
 Specify number of columns for grid layouting, which is used later by `xwinreg-layout`(1).

* `-T` <FILE>:
 Specify a nonregular Tmp file.

* `-v`:
 Print current version of `xwinreg-calculate`(1).

## ARGUMENTS
* <FILE>:
 Regular file or named pipe.

* <FRAMEALIAS>:
 `northwest`, `north`, `northeast`, `east`, `southeast`, `south`, `southwest` or `west`. You can create your own aliases in a Conf File or overwrite those defaults.

* <INT>:
 Default is `2`.

* <PX>:
 Pixel size specified by an integer.

## EXAMPLES
 xwinreg-calculate

 xwinreg-calculate -n 4 -N 4

 xwinreg-calculate -F ${Home}/tmp/xwinreg.tmp

 xwinreg-calculate -5 0 -6 0 -7 1680 -8 1049

 xwinreg-calculate -1 0 -2 0 -3 840 -4 524

 xwinreg-calculate -C ${Home}/.config/xwinreg/xwinreg.conf

 xwinreg-calculate -C ${Home}/.config/xwinreg/xwinreg.conf -a new_frame_alias

## NOTES
 If no workarea geometry is set, `xwinreg-calculate`(1) uses <_NET_WORKAREA>.

 Currently, window decoration is not considered.

 If no frame geometry is set, <_NET_WORKAREA> is used as frame. Every new frame needs its own Tmp File. In other words: all layouting takes place in one frame. You can specify another Tmp File with option `-T`, or you may create several Conf Files. See section **CONFIGURATIONS** in this Manpage.

 Options on command line overwrites variables in a Conf File.

## CONFIGURATIONS
By default, `xwinreg-calculate`(1) needs no Conf File, because all important geometries will be calculated in the script. You can also use the relating options on command line. So, only use a Conf File, if you want to work with several frames (and several Tmp Files are needed) or if you need to set own aliases for frame and region geometries. Along with this programm comes an exemplary Conf File. Specify a Conf File with option `-C` or use <XWINREG_CONF_FILE>. You can set following parameters:

* enviroment variables:
 XWINREG_TMP_FILE=<FILE>; XWINREG_INPUT_FILE=<FILE>

* normal scalar variables:
 workarea_x=<PX>; workarea_y=<PX>; workarea_width=<PX>; workarea_height=<PX>; frame_x=<PX>; frame_y=<PX>; frame_width=<PX>; frame_height=<PX>; row_number=<INT>; col_number=<INT>

* associativ array variables:
 You can use it with above variables. You need to set them inside a function called `__xwr_xwinreg_calculate_calculating_frame_alias` respectively `__xwr_xwinreg_calculate_calculating_region_alias` and declare it with `declare -gA frames` respectively `declare -gA regions`: frames[<ALIAS>]="<X> <Y> <W> <H>"; regions[<ALIAS>]="<X> <Y> <W> <H>"

## ENVIROMENT
* <TMPDIR>:
 By default, Tmp File will be written as **TMPDIR/xwinreg_default.tmp**, otherwise as **/tmp/xwinreg_default.tmp**.

* <XWINREG_TMP_FILE>:
 Specify this instead default setting and instead using <XWINREG_TMP_FILE> in a Conf File.

* <XWINREG_CONF_FILE>:
 Use this instead of option `-C`, if you want to use a Conf File.

## BUGS & REQUESTS
Report it on **https://github.com/D630/xwinreg/issues**
## LICENSE
`xwinreg-calculate`(1) is licensed with GNU GPLv3. You should have received a copy of the GNU General Public License along with this program. If not, see for more details **http://www.gnu.org/licenses/gpl-3.0.html**.
## SEE ALSO
`bash`(1), `grep`(1), `x`(7), `xprop`(1), `xwinreg`(1), `xwinreg-close`(1), `xwinreg-cycle`(1), `xwinreg-focus`(1), `xwinreg-focus-toggle`(1), `xwinreg-hide`(1), `xwinreg-id`(1), `xwinreg-layout`(1), `xwinreg-move-to-desk`(1)