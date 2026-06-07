# Aqua Standard Specification
The *Aqua Standard Specification* is the programming language standard for how *Aqua files* (files with the `.aqu` and `.aqua` file extensions) are structured, defined, and how they behave.

*Aqua files* are scripts, this means that they run processes and evolve outputs; For example, if you have a variable called `x` with a value of `10`, at runtime, it can be manipulated and changed to have a value of `20`.

## Why implement this standard?
The *Aqua Standard Specification* is designed to have simpler syntax, easily nested data, and customizability for unique use cases.

This standard is made to be customizable. Here are some example use cases for why you should implement this standard:

### Websites
```
import Webpage;


// Webpage.px(amount: int)
//         └─ An amount counted in pixels
const TITLE_TEXT_SIZE = Webpage.px(40);
const PARAGRAPH_TEXT_SIZE = Webpage.px(16);

const style = {
	title: <<
		text(TITLE_TEXT_SIZE) {
			@% /* Gets from the body of the node */
		}
	>>
}


fn main() -> Webpage.page {
	// Webpage.page(content: Tree, title='My Webpage')
	return Webpage.page(
		<<
			vcon {
				&style.title { 'Welcome To My Webpage!' }
				text(PARAGRAPH_TEXT_SIZE) {
					'This is a paragraph.'
				}
			}
		>>,
		title = 'My Very Cool Webpage'
	)
}
```
