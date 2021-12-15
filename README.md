# Smooth-Camera-Follow
Tutorial on how to get a camera to smoothly follow the player in 3D

# 1) The Setup
To get started before coding, first placeholder objects for the player (with physics based movement), a plane, and a camera should be set up:

![image](https://user-images.githubusercontent.com/91538155/146240087-e3219e79-df9b-456e-86b0-c5b752fe2fab.png)

The player also needs a child object called lookTarget, which will be what the camera will eventually point at in game:

![image](https://user-images.githubusercontent.com/91538155/146240127-6bc4d28f-0f02-4806-8337-50364d09e2fc.png)

# 2) Quick look at the player movement code
Before getting into the camera, the player must be able to move. As this tutorial isn't focused on the player movement, but having an idea on how to move the player in a 3D space is always a good idea, here's a quick look at how to get the player to move:

First, the player needs these decralations:

![image](https://user-images.githubusercontent.com/91538155/146240401-16eabbd3-6867-42af-b158-0f1224765f84.png)

The Horrizontal and Vertical floats are there to make sure that the movement, unlike in 2D, isn't based on just the X and Y axis, and takes into accounrtr pivoting on the Z axis. 

The Rigidbody is in order to apply velocity to the player:

![image](https://user-images.githubusercontent.com/91538155/146240694-2817cf44-ef7e-4484-9df9-10c9eec583c8.png)

Next, these lines of code get the player to follow the arrows in unity as their sense of direction, and factor in velocity to keep things smooth:

![image](https://user-images.githubusercontent.com/91538155/146240837-897eb8ab-bec4-4a65-8646-0f5f9a8cae9a.png)

# 3) The Camera Coding
For this part, another set of declarations need to be made:

![image](https://user-images.githubusercontent.com/91538155/146240970-0bc51a3c-12aa-4128-95a2-618832f76ce8.png)

The transforms worry about the position of certain objects, the first being the player (target) and the second being the lookTarget game object slightly above the player (looktarget)

The public Vector3 is to do with the offset of the camera from the player, so that the camera remains at a fixed distance from the player in a set position and rotation.

The float is to do with the smoothness of the movement, so that there is a slight delay in stopping the camera once the player stops moving rather than at the same time. The line above is to make the smoothness a slider in the editor to make it easier to adjust to liking.

Finally, the bool is a tick box to allow for choosing whether the camera should target the child or not.

Next, we create a FixedUpdate void:

![image](https://user-images.githubusercontent.com/91538155/146241568-0667da7e-1b78-4bfa-b6f8-6c931c9caea6.png)

The desiredpos is where the camera should be, the players position including the offset

the Lerp function moves the camera between two points given a defined rate (in this case I went with 0.125f)

the smootherpos is to get the desired position of the camera and add this Lerp function, which is what makes the camera movement slightly behind the player and allows for that smooth follow.

Finally, the Update void:

![image](https://user-images.githubusercontent.com/91538155/146243345-0adcaebf-59af-4d02-869d-0b19f01bf371.png)

This line is simply to get the camera to look at an empty game object (lookTarget) that is placed slightly above the player object, while still following the player.

# Congrats, your camera is smooth now!
