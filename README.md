# input-type "numeric" | "filename" | "filepath"
Keyboard/input filters to:

&nbsp; •make an HTML input accept only numeric input formats; conforms to any numerical base (2-36); only numerical characters for that base are allowed; except for base 10, only one decimal (.) allowed (if the input allows decimal values), and only one negative (-) sign (if the input allows negative values) and only as the first character.&nbsp; A positive (+) sign may be allowed as the first character if the input allows positive values and the input has an attribute: allow-plus-sign.&nbsp; Units may also be defined as a post-fix text for the numerical value, using the input attribute: units='unit1, unit2, unit3' where the comma separated list of units are the allowed values and the first unit listed becomes the default; the user needs to only press the first key of the unit.

&lt;input type='numeric' min='-5' max='300' allow-plus-sign units='%, px, em, rem'&gt;

&lt;input type='numeric' base='16'&gt;

&nbsp; •make an input to accept only filename (no directory separators) or filepath characters; but no formatting is enforced.

&lt;input type='filename'&gt;
