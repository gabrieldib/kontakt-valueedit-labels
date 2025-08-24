About Value Edit Labels:

In an effort to make labels editable, I did this experiment.
Instead of using the default regular ui_label, I picked value_edit ui controls.

For the whole pairing system to work, value edit controls have to have a (parent) slider associated to them.
This association happens using the slider_child_ve_label_uiids and ve_labels_parent_sliders_uiid
arrays. 

For this to work properly, you have to have the declaration of the sliders contiguously
and the value edits declarations should follow, in the same order, also contiguously.
What if you have more sliders than value edits, meaning that some sliders don't have ve pairs?
put the independent sliders at the end of your sliders declaration list, but keep them grouped.
Same for value edits, then adjust the first and last elements base and last index in the
DECLARATIONS file.

This was an attempt in making it as generic as possible to be integrated in large projects.
However you will notice that in the ui controls callback the in_range function is only 
scanning the UIID_ADSR_sliders and UIID_ADSR_ves arrays. You could add the first and
last elements of the slider/value_edit pairs here and treat the independent sliders
and value edits separately.
Also a better pattern could be combining these ranges in an if / else if flow. Maybe.

I did use Figma to Kontakt to generate the UI implementation code.

Extra: 
Because I am obsessed with UX, I added a couple functions to take care
of control transformation curves, that transform the linear ranges of the
sliders to a curved one, to make certain portions of the range more accesible.
For example, on the attack slider you will notice that when you get to the middle
of the knob, which would be control value 500000 and engine label value 7500,
the value edit label is only showing around 525ms. That's because of the 
curved slider value.
On the callbacks for these knobs (sliders) I store the curved value in the 
control_curve_value array.


Cheers!

Gabriel
