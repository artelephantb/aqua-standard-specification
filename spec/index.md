# Aqua Standard Specification
The *Aqua Standard Specification* is a  programming language standard for how *Aqua files* (files with the `.aqu` and `.aqua` file extensions) are structured, defined, and behaved.

The *Aqua Programming Language* (defined through this specification) is mostly a general-purpose programming language; the main functionalities of this language, however, is to provide for a lower entry and a better experiance for but not limited to game developement, game engines, webpages, web-browsers, advanced slideshows, software with GUIs, and GUI frameworks.

## Why implement this standard?
The problem with with most programming languages is that they are not made with the thought of advanced UIs or GUIs, and many that are supposed to be made specifically for those purposes end up becoming too bare-bones, too confusing, and too difficult to use. The Aqua Programming Language aims to fix these problems, introducing better functionality, less confusing syntax, and simple to understand rules.

At the heart of it, this standard is still made to be able to fit any need. Some different use cases may include:

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
