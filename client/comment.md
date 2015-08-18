Comments on the client side must be compatible with JSDuck, is the API generator engine used for Chinook 2.

Here some useful link :  
* https://github.com/senchalabs/jsduck/wiki
* https://github.com/senchalabs/jsduck/wiki/Guide
* http://usejsdoc.org/tags-type.html

And some examples :

```javascript
	/**
	 * @class Chinook.component.ContextPanel
	 * Beginning of the description
	 * This text will be next "Beginning of the description" without new line
	 * 
	 * Here a new Voici un nouveau paragraph (dual carriage return)
	 *
	 * ## Section title
	 *
	 * Here the third paragraph.<br/>
	 * The second line of the thir paragraph
	 *
	 * @extends Chinook.parent.class
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
	 * Deuxième paragraphe de description
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
	 * Create a new Edit strategy.
	 *
	 * @param {Object} Parameter's comment
	 *
	 * @return {Type} Return's comment
	 */
```
