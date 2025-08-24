About Value Edit Labels:

For the valueedit labels to work they have to have a parent slider associated to them.
This association happens using the slider_child_ve_label_uiids and ve_labels_parent_sliders_uiid
arrays. 

There is a delicate uiid assignment in the DECLARATIONS file, that depends on
the actual UIID of the parent or child control and an offset, since the index
used to loop through the elements in the array is one value and the offset
from the first uiid of these paired controls is different than the index, but
parallel.

One potential problem to this system is the following cases:

1) Having a slider that doesn't have a child ve label associated to it
2) Having a valueedit without a parent slider

Solution:
Suppose we have 10 sliders and 9 value_edit controls.
From these 10 sliders, only 7 have paired child value edits.
This means that there are 3 independent sliders and 2 indenpendent value edits.
How to deal with this situation?
a) keep the paired declaration order intact, from first to last sliders the first
ones should be the paired ones. We put the independent ones at the end of the sliders list.
b) The order of value edits declarations follows the sliders', with the independent value edits
at the end of the ve list.
This way we will need independent offsets for sliders and value edits but the
loops won't break.

In short:
G1. Sliders in a feature group are declared as a single contiguous block in UIID order.
G2. The group’s valueedits are declared as a single contiguous block.
G3. The first N valueedits correspond 1:1 (in order) to the first N sliders. Any extra sliders or VEs live at the end as independent controls.
G4. Blocks may shift, but order must be preserved. Insert other control types outside these blocks.
