xwinreg-layout(1) -- build layouts inside arranged regions and fill them rule-based with windows.
=======================================================================================

## XWINREG
Part of `xwinreg`(1).
## SYNOPSIS
 xwinreg-layout (-h|-v)

 xwinreg-layout [-T] -L ...

 xwinreg-layout [-T] (-l -A -e -g -G -r -x) ...

## REQUIREMENT
bc, GNU bash, wmctrl
## DESCRIPTION
After processing of `xwinreg-id`(1) and `xwinreg-calculate`(1), `xwinreg-layout`(1) reads their variables from a Tmp File and builds layouts in specified regions and fill them rule-based with windows. After layouting, the Tmp File will has been updated with new variables. Without layout-actions, `xwinreg-layout`(1) just reads the Tmp File and reruns the last documented layout.

All layouting takes place in only one frame. That one frame may have the geometry of the workspace or any other. To work with more than one frame, you need to create more than one Tmp File. See `xwinreg-calculate`(1).
## ACTIONS
* `-l`:
 Build layout. Specify the layout with options `-r`, `-x`, `-A`, `-e`, `-G` and `-g`.

* `-L` <REGN>,<WINN>,<LACT>,<LENT>:<GRAV>,<GEO>:
 Write action `-l` in shorthand.

## OPTIONS
* `-A` <LACT>:
 Specify, how a region should be filled with windows.

* `-e` <LENT>:
  Specify the entity of <GEO>.

* `-g` <GEO>:
 Specify the geometry of a region.

* `-G` <GRAV>:
 Specify the gravity of windows in a region. If you are indecisive, use 0.

* `-h`:
 Display a short help.

* `-r` <REGN>:
 Specify, which region should be processed.

* `-T` <FILE>:
 Specify a nonregular Tmp file.

* `-v`:
 Print current version of `xwinreg-layout`(1).

* `-x` <WINN>:
 Maximal number of windows a region should contain.

## ARGUMENTS
* <FILE>:
 Regular file or named pipe.

* <GEO>:
 <X>: Pixel x size specified by an integer.
 <Y>: Pixel y size specified by an integer.
 <W>: Pixel width size specified by an integer.
 <H>: Pixel height size specified by an integer.
 <PRO>: Procent size specified by an integer.
 <REGALIAS>: `northwest`, `north`, `northeast`, `east`, `southeast`, `south`, `southwest` or `west`.
 Samples: "<REGALIAS>", "<PRO>,<PRO>,<PRO>,<PRO>", "<X>,<Y>,<W>,<H>".

* <GRAV>:
 `northwest`, `north`, `northeast`, `west`, `center`, `east`, `southwest`, `south`, `southeast` or `static`. Additional: `[0-10]`.

* <LACT>:
 `maximize`, `horizontal`, `vertical`, `grid-horizontal`, `grid-vertical`, `grid-square-horizontal` or `grid-square-vertical`.

* <LENT>:
 `alias`, `px` or `pro`.

* <REGN>:
 Region number specified by an integer.

* <WINN>:
 Window number specified by an integer or `max`.

## EXAMPLES
 xwinreg-layout -L 1,max,horizontal,alias:0,all

 xwinreg-layout -L 1,max,grid-horizontal,alias:0,all

 xwinreg-layout -L 1,max,grid-square-horizontal,alias:0,all

 xwinreg-layout -L 1,max,maximize,alias:0,all

 xwinreg-layout -L 1,1,maximize,alias:0,west -L 2,max,horizontal,alias:0,east

 xwinreg-layout -L 1,1,maximize,alias:0,west -L 2,1,maximize,alias:0,northeast -L 3,max,vertical,alias:0,southeast

## NOTES
 You can specify region aliases in a Conf File, which will be read by `xwinreg-calculate`(1) and written to a Tmp File. See section **CONFIGURATIONS** in its Manpage.

 If you use action `-l`, actually, the first option needs to be `-r`.

## ENVIROMENT
* <TMPDIR>:
 By default, Tmp File will be written as **TMPDIR/xwinreg_default.tmp**, otherwise as **/tmp/xwinreg_default.tmp**.

* <XWINREG_TMP_FILE>:
 Specify this instead default setting and instead using <XWINREG_TMP_FILE> in a Conf File.

## BUGS & REQUESTS
Report it on **https://github.com/D630/xwinreg/issues**
## LICENSE
`xwinreg-layout`(1) is licensed with GNU GPLv3. You should have received a copy of the GNU General Public License along with this program. If not, see for more details **http://www.gnu.org/licenses/gpl-3.0.html**.
## SEE ALSO
`bash`(1), `bc`(1), `wmctrl`(1), `x`(7), `xwinreg`(1), `xwinreg-calculate`(1), `xwinreg-close`(1), `xwinreg-cycle`(1), `xwinreg-focus`(1), `xwinreg-focus-toggle`(1), `xwinreg-hide`(1), `xwinreg-id`(1), `xwinreg-move-to-desk`(1)