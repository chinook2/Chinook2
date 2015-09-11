Comments on the client side must be compatible with JSDuck, is the API generator engine used for Chinook 2.

Here some useful link :  
* https://github.com/senchalabs/jsduck/wiki
* https://github.com/senchalabs/jsduck/wiki/Guide
* http://usejsdoc.org/tags-type.html

And some examples :

```javascript
	/**
	 * @class Chinook.component.ContextPanel
	 * Beginning of the description.
	 * This text will be next "Beginning of the description" with just a space (no new line).
	 * 
	 * Here a new paragraph (dual carriage return). Complete lines through a point everytimes.
	 *
	 * ## Section title
	 *
	 * Here the third paragraph.<br/>
	 * The second line of the thir paragraph
	 *
	 * @extends Chinook.parent.class
	 * @singleton
	 */ 
	 
	/**
	 * For a simple property just set the description. Everything is automatically (type, default value) <br/>
	 * Below it's reported as readonly
	 * @readonly
	 */
	emptyText : 'Choose a color ...',

	/**
	 * @property {First_type/Seconde_type} [example=default_value]
	 * Short description of a more complicated property.
	 * Complément qui ne s'affiche quand on déroule le bloc (est sur la même ligne que la description court)
	 *
	 * Second description paragraph with a list :
	 *
	 * - First item : empty line before is require to render a list
	 *	- Before "-" you have to put beetween 0 and 4 space or one (and only one) tabulation
	 */
	example: 'default_value'
	 
	/**
	 * @property {MyObj[]}
	 * Array of MyObj
	 */
	 
	/**
	 * @var {color}
	 * CSS property
	 */
	$base-color: red !default;

	/**
	 * @method initialize
	 * Create a new Edit strategy. Random list :
	 * 
	 * - 1
	 * - 2
	 *
	 * Now an highlight example. At least one non-empty line is mandatory between a list and a example !!
	 *
	 *     var example = "An empty line is required before the example";
	 *		example = example + "at least 5 space or 2 tabulation are needed to render highlight text";
	 *
	 *     var LF = "You can leave an empty line into the code, it don't break code box";
	 *
	 * @param {Object} Parameter's comment
	 *
	 * @return {Type} Return's comment
	 */
```
