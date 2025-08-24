About Value Edit Labels:

For the valueedit labels to work they have to have a parent slider associated to them.
This association happens using the slider_child_ve_label_uiids and ve_labels_parent_sliders_uiid
arrays. 

For this to work properly, you have to have the declaration of the sliders contiguously
and the value edits declarations should follow, in the same order, also contiguously.
What if you have more sliders than value edits, meaning that some sliders don't have ve pairs?
put the independent sliders at the end of your sliders declaration list, but keep them grouped.
Same for value edits, then adjust the first and last elements base and last index in the
DECLARATIONS file.

This was an attempt in making it as generic as possible to be integrated in large projects.
I did use Figma to Kontakt to generate the UI implementation code.

Cheers!

Gabriel
