# input-type "numeric" | "filename" | "filepath"
Keyboard/input filters to:

&nbsp; •make an HTML input accept only numeric input formats; conforms to any numerical base (2-36); only numerical characters for that base are allowed; except for base 10, only one decimal (.) allowed (if the input allows decimal values), and only one negative (-) sign (if the input allows negative values) and only as the first character.&nbsp; A positive (+) sign may be allowed as the first character if the input allows positive values and the input has an attribute: allow-plus-sign.

Units may also be defined as a post-fix text for the numerical value, using the input attribute: units='unit1, unit2, unit3' where the comma separated list of units are the allowed values; the user needs to only press the first key of the unit.  If the Boolean attribute auto-append-unit is present, the first unit listed becomes the default unit which is appended if the end-user does not explicitly choose one.

The min &amp; max attributes accept multiple comma-separated-values, with each value having its own unit, to support the units attribute.  The complete rules are:

/*     MIN / MAX   === VALUE RULES ===
 * if there is no value, there is no limit, as usual.
 * if there is a single value with no unit, that value applies to all input values with units and unitless numbers.
 *	if there is a single value with a unit, that value applies only when the input unit matches; otherwise no limit.
 *	if there are multiple values separated with commas, they apply when their unit matches the input unit,
 *	  or if a min/max value has no unit, it applies when the input value has no unit; otherwise, no limit.
 */


&lt;input type='numeric' min='-5' max='300' step='1.5' allow-plus-sign units='%, px, em, rem' auto-append-unit&gt;

If the value of the input is out of range (according to min/max above), an "out_of_range" event is fired on the input and bubbles.  
The Event is an instanceof OutOfRangeEvent (which is an extention of UIEvent), and has the properties .min &amp; .max which are
the min/max values with units matching the input value unit.
The Input"s value will be set to the correct min/max value, unless your event-handler uses event.preventDefault() on the OutOfRangeEvent

Special case: min='-∞' &amp; max='∞'
<br>
While simply leaving min & max blank ALSO allows "infinite" values (limited only by the computer), the user may want to actually signify the value "infinity".  They can do that by typing the ~ key when the input-field is blank, and the ∞ symbol will appear instead, when min or max matches ∞.  You can not use ∞ with a unit, nor can you include it in a comma-separated-list of min/max values.

&lt;input type='numeric' base='16'&gt;

&nbsp; •make an input to accept only filename (no directory separators) or filepath characters; but no formatting is enforced.

&lt;input type='filename'&gt;

&lt;input type='filepath'&gt;

Note these are simply textual inputs for users to create filenames, etc.  They do not load any files.
