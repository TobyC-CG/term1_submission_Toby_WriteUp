# term1_submission_Toby_WriteUp
## Devils in the detail
Unreal Project
 
![nightmarescreenshot](https://user-images.githubusercontent.com/32567755/35228245-291a8390-ff88-11e7-8c5f-de38291a2a2c.JPG)

#Art 

•	Modular design and textures


o	Lightmaps


o	Normal Map issues


•	Initial Maze Design


•	Creating one of the gnomes


•	Creating the Monster


# Modular Assets
At the beginning I started out blocking modular maze pieces for the maze. My plan was to create pieces that could be interchanged and altered afterwards, allowing for early drafts of the maze to be made in engine; allowing geometry to be updated later down the pipeline and for easier layout alterations.
 
 
 ![hedgeuv](https://user-images.githubusercontent.com/32567755/35229163-9e6b0eba-ff8a-11e7-8790-f4ec9a063baa.png)
 

![modularbaic01](https://user-images.githubusercontent.com/32567755/35236522-8b0de864-ff9f-11e7-88a5-0827a3a58c95.JPG)
Initial Prototype Modular assets
![modularsmooth02](https://user-images.githubusercontent.com/32567755/35236521-8af22c28-ff9f-11e7-8764-71fbdc5f6c6a.JPG)
Final modular assets. I made them smoother to create a more organic form
 
# Example of A modular asset
I divided the UV’s space into quarters, so that after creating the base materials I could composite them in photoshop in such a way to maintain tillable modular pieces while not using multiple material ID’s.
I initially created the modular assets without being water tight, but light would bleed from the opposite side of the mesh. To correct this, I created a Lightmap.
I used based/ reference textures from Textures and from these images I derived Normal, and Roughness maps through BitMaps2Material. I then added these newly created textures into substance Painter to create the desired tiling size. For the ground I used two different materials grass and dirt, blending them together within Substance Painter, I used the mirror symmetry to keep the textures tillable.


![grass](https://user-images.githubusercontent.com/32567755/35236583-bd6a1170-ff9f-11e7-8f32-37da36312e5c.JPG)
I used bitmap to material to make the initial materials, which I resized and further edited in substance painter.
![paintermodual design](https://user-images.githubusercontent.com/32567755/35229229-c65ed226-ff8a-11e7-9d4e-7e8896812797.JPG) 



# Original textures
The hedge textures were taken from https://www.textures.com/ . I used the following textures as a base to edit and create the textures I needed (all Royalty free, free to use textures).
![texturescom_grass0184_1_seamless_s](https://user-images.githubusercontent.com/32567755/35229268-e2bd102c-ff8a-11e7-837a-49dc3f41ccbf.png)

 

 



# Initial Maze Design
I created the original maze design, and showed my group how the modular design works together. I also tried to experiment with maze designs, to created disorientation in the player. Luis remade the maze for the final project, but some of the level design made it into the final design.
The red maze pieces were an idea to make the maze react to completing objectives, by reorganising its lay out (turning to close off routes and create new ones. This idea was later scrapped but turned into the portcullis idea.

![initial design](https://user-images.githubusercontent.com/32567755/35236642-eb83a314-ff9f-11e7-8dc6-89c1a109f9ce.png)
My initial Maze design



# Characters
# Gnome- https://skfb.ly/6uWTt 
I created one of the gnomes, used in the puzzle (look below). I made him in Z-brush from dynamic mesh in a T-Pose, I then re-topologised the mesh in Maya, and then created the textures in Substance Painter (including baking normal and ambient occlusion maps). As part of the initial design/ idea each gnome focused on a hear no evil, see no evil, and speak no evil; my model was the see no evil.

![gnome](https://user-images.githubusercontent.com/32567755/35229292-f396366c-ff8a-11e7-909a-47092c5a4ba9.JPG)
![gnome_texture](https://user-images.githubusercontent.com/32567755/35229293-f3b4314e-ff8a-11e7-88e5-cdc45352d32e.jpg)
  



# Monster- https://skfb.ly/6voYM 
I created the main antagonist in Z-brush, re-topologise and UV unwrapped in Maya, and textured in Substance Painter. I created hollow eye sockets for eyes to re-create a nightmare I use to have, and took further inspiration from Death stranding, creating a metallic oil effect seeping from its body using the particle brush


![monsteruv](https://user-images.githubusercontent.com/32567755/35229314-ff1b00c6-ff8a-11e7-8efa-8ee88c147800.JPG)
![monster_texture](https://user-images.githubusercontent.com/32567755/35229315-ff39a346-ff8a-11e7-99f9-a727ee09eb2d.jpg)

 











# Misc.
Lever Rigging and Animation- https://skfb.ly/6vQqT 
As part of the portcullis (see more down in the blueprint section) I had to rig, animate and export an FBX animation of the activation of a lever. I rigged the lever in Maya, initially creating a contrain parent controller which I had to remove as the exported animation didn’t show in unreal. So I created an origin (Root) joint and a binding joint atop the root that drives the deformation; this means that the joint on top its parent is on its origin and has 0’s on its attribute editor and so is much easier to use as a control.
 
![leverjoints](https://user-images.githubusercontent.com/32567755/35229332-1041c24a-ff8b-11e7-837c-1adfd880f749.JPG)







## Coding

•	Pause

•	Portcullis
 
 ![nightmarescreenshot02](https://user-images.githubusercontent.com/32567755/35229412-46f87cfc-ff8b-11e7-8995-102bd1d8b379.JPG)

# Pause
Implementing the pause system was first blueprint I have created. This was meant to be a minimalistic pause, where it would just pause the game

1.	I had to use a sequence node to split the Event BeginPlay as the node was already in use for other blueprints.

2.	I then used the Event BeginPlay Sequence to ready the custom pause widget, which I create, and set to Invisible (Event Pre-Construct->Set Visibility{Hidden})

3.	Set an event to the player pressing the “P” Key- which is connected to a branch node, which checks if the game is paused.

4.	If the game is not paused, then the blueprint is paused and the widget (Which is set to the player) is made visible. If the game is already paused, then the game un-pauses.

 ![pause](https://user-images.githubusercontent.com/32567755/35229440-5911c088-ff8b-11e7-8b70-b9185650c50a.JPG)
![pause visibility](https://user-images.githubusercontent.com/32567755/35229442-5a78d376-ff8b-11e7-8e8c-f7998929ec58.JPG)



 





#Portcullis
Part way through development we saw that the monster was too relentless, and hard to shake off as a player. We decided that an object needed to be created to block the monster during a close chase.

The portcullis is formed of three meshes (Lever (Modelled by Gabby), Gate (Modelled by Gabby, textured by myself), and the wooden block the gate appears from (modelled and textured by me. In gameplay you approach a lever where a prompt will come up telling you can “Press E to raise the portcullis”. The blueprint was divided into trigger, widget, and animation.

#Trigger
Run on a trigger box start and end overlap, which triggers the widget to be visible (set up similarly to the pause widget above), the triggers are also connected to a gate node, the start overlap opens the gate and the end overlap closes the gate, with the “Interact” button press activating the gate and the Gate animations. The interact button was added by going Project Settings -> Engine -> Input -> Action Mapping. Defining these inputs would be good to use in future game development workflows as it’ll make it easier to re-map a lot of game mechanics, instead of re-entering various blueprints to individually alter them.

#Widget
I reused the Pause widget method, but with a new widget.

#Gate
I used a sequence to split the triggered action, one triggers the lever animation (which I rigged and animated), another to play the timeline (animation for the gate), and the last for the sound. The timeline is linked drives the SetRelativeLocation of the gate, causing it to raise, which in turn is linked to a delay node which drives the reverse of the same timeline resetting the gate to open, and making it easier to iterate how long the gate stays close for.
![portculis](https://user-images.githubusercontent.com/32567755/35229497-7a04353c-ff8b-11e7-8367-735f6e8aac6d.JPG)
 

 
