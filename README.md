Documentation of pygame by TheBestia2

- base template
	```Python
	import pygame
	from sys import exit

	pygame.init()
	SCREEN = pygame.display.set_mode((width, height))
	clock = pygame.time.Clock()

	while True:
	    for event in pygame.event.get():
	        if event.type == pygame.QUIT:
	            pygame.quit()
	            exit()
	        
	    pygame.display.update()
	    clock.tick(60)
	```

	analyze each instruction:

	import of some lib
	```Python
	import pygame
	from sys import exit
	```

	inizialize pygame, with the screen and the clock
	```Python
	pygame.init()
	SCREEN = pygame.display.set_mode((width, height))
	clock = pygame.time.Clock()
	```

	basic loop to run the game
	* the first part close the game when the user close the window
	* the second one, update the changes of the screen (in this case there aren't) and the clock
	```Python
	while True:
	    for event in pygame.event.get():
	        if event.type == pygame.QUIT:
	            pygame.quit()
	            exit()
	        
	    pygame.display.update()
	    clock.tick(60)
	```

---
- collisions with rectangles


```Python
#pygame.MOUSEMOTION -> event that say if the mouse is moving
#event.pos -> returns the position of the mouse (x,y)

for event in pygame.event.get():
    if event.type == pygame.MOUSEMOTION:
        print(event.pos)
```
with event, we can also check if mouse button is pressed or is released (every mouse buttons)
* pygame.MOUSEBUTTONUP -> if the button is release
* pygame.MOUSEBUTTONDOWN -> if the button is pressed
```Python
for event in pygame.event.get():
    if event.type == pygame.MOUSEBUTTONUP:
        print('mouse up')
    if event.type == pygame.MOUSEBUTTONDOWN:
        print('mouse down')
```
---
- draw

---
---
- add image
	* 'dir/image.png' -> directory of the image
	* .convert() -> convert the image so pygame can handle it easily
		* if the image is a png, we can use .convert_alpha()
	```Python
	test_image = pygame.image.load('dir/image.png').convert()

	while True:
	    #other code
	    SCREEN.blit(test_image, (pos_x, pos_y))
	    #other code
	```

	### IMPORTANT:
	the image needs to be placed into a rectangle in this way
	* position -> is the position where we want to place the rectangle (and the image inside it) example -> (midbottom = (80,300))
		* to see other possibilites, check the image under this code
	```Python
	player_surf = pygame.image.load('dir/image.png').convert_alpha()
	player_rect = player_surf.get_rect(position)

	while True:
	    #other code
	    SCREEN.blit(player_surf, player_rect)
	    #other code
	```

	Image:
	* left image -> wants a tuple (x and y position)
	* right image -> use int values (can be used in if statement)
	int values can be used also to assign the position of the element (for that purpose is better the tuple but not recommended)
	![](/home/lorenzo/.var/app/io.appflowy.AppFlowy/data/AppFlowy/data/images/9b64af99-8521-44e0-aa43-f600aacf01b0.png)
- add text
	* 'My Game' -> is just the text that we want to be display
	* False -> is the AA (if is pixel set False, otherwise set True bc make the text more soft)
	* 'Black' -> is the color of the text
	```Python
	text_surface = test_font.render('My game', False, 'Black')

	while True:
	    #other code
	    SCREEN.blit(text_surface, (pos_x, pos_y))
	    #other code
	```

	we can also use our font
	* 'dir/fontName.ttf' -> is the directory of our font
	* 50 -> is the size of the font
	```Python
	text_font = pygame.font.Font('dir/fontName.ttf', 50)
	```