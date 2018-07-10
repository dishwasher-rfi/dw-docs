==========
Flag table
==========

The first time that a flagging region is saved, DW creates a new table extension that is
appended to the data: the so-called *flag table*.
Each row in the flag table contains the parameters needed to define a flagged
region.
If an automatic flagging method creates more than one flagged region, all the regions are grouped in
a single item in the item list (one item for data type, i.e. L, R, Q, U) but they are eventually
saved as separate rows in the flag table.

The flag table is updated each time new flagged regions are saved.

Each entry in the flag table has the folowing elements:

* *nop:* unique id of a flagged area.
* *algorithm:* The algorithm used for the flag. If is a manual flag the value is "Manual"
* *params:* The parameters of the used algorithm. If algorithm is "Manual" is *None*.
* *flagresult:* A label indicating to which data type the flagged region belongs, i.e.
  L, R, Q or U. If "Manual", flagresult is *None*. **NOTE THIS HAS TO BE FIXED**
* *flag_data:* Contain an array of four elements describing the flagged rectangular area 
  (y_min, y_max, x_min, x_max).
* *feed:* The feed number to which the flagged area is attributed.
* *section:* The spectral section number to which the flagged area refers.
* *pola:* The polarization (L, R, Q or U) to which the flagged area refers.

If an algorithm produce a flagged region with irregular shape, the region is divided in a number of rectangles that are saved wiht the 
same *nop* number. This allows the subsequent deletion of the entire flagged region, if needed.
DW reconstruct a flagging matrix from the *flag_data* values of a given *nop*.
