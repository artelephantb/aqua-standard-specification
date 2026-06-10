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

const STYLE = {
	title: <! // Kinda like a macro!
		text(TITLE_TEXT_SIZE) {
			$^body /* Gets from the body of the node */
		}
	!>
};


fn main() -> Webpage.Page {
	// Webpage.Page(content: Tree, title='My Webpage')
	return Webpage.Page(
		<<
			vcon {
				!STYLE.title { 'Welcome To My Webpage!' }
				text(PARAGRAPH_TEXT_SIZE) {
					'This is a paragraph.'
				}
			}
		>>,
		title = 'My Very Cool Webpage'
	)
}
```

### Games
```
from Game import { Sprite, Vector2, Texture, Keyboard };
use Process;


var imut player_texture = Texture.load('res://');
//  └─ Make the var immutable (stuck with initial value)

var player_reference: Sprite;


fn setup() -> Void {
	var scene = <<
		/* sprite(uid: int, pos: Vector2 texture: Texture) */
		sprite(0, Vector2(0.0, 0.0) player_texture)
	>>;

	// Process.replace_scene(new_scene: Tree)
	Process.replace_scene(scene);

	player_reference = Process.get_node_by_id(0);
}

fn process() -> Void {
	if Keyboard.is_key_pressed(Keyboard.Keys.SPACE) {
		player_reference.pos.x += 1;
	}
}
```
