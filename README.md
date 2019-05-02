# AIComponent

## Instructions
Download the build folder and run Ink'd.exe

Select a level
Press A to start the AI running  
Press S to stop the AI at any time (Do this after completing a level to free your mouse)

Only Level 1 and 2 are currently avaliable

## First iteration
I have created an AI system that plays ink'd, my second year group project.  
Originally I started with a system where the AI would try random locations to grab then was rewarded by moving towards the goal. If it managed this it would store the grabbed location and build a list of grabs. Once a good new grab was found it would restart the level make it's way through the list then look for another rewarding grab.  
I ran into problems with this plan due to a couple of reasons, the first being that due to our physics in game, and how the octopus can bounce differently off of objects each time, the further into the level the AI got the less accurate it's list of grabs would be to the actual locations used when it was rewarded. The second issue is how unity wait times are not always frame perfect, leading to the same inaccuracies further into the level. Both of these problems compounded into making this approach not viable.  
  
## Current iteration 
The next route I tried and ended up sticking with is for the AI to raycast out from the player in different directions to look for a good grab, these rays are weighted towards better grabs where a 45 degree angle is best when available slowly decreasing weight as the angle changes away from this. In this form the AI does not remember any of its moves and every play through works it's way through the level fresh. I found that the AI would often get stuck if right next to an object choosing to grab it as the angle was best, to counteract this I added a check for minimum grab distance, and if an object is too close the AI will try to climb upwards.  
Goals for this AI have been created in the form of "gates" that are placed in the level. The AI aims to reach these gates and then aims to reach the next, this helps with more complicated level paths that go back on themselves and down or up.  
I have added the ability to change a lot of the controlling variables in the unity inspector so that designers and myself can easily edit how it plays.  

![alt text](https://raw.githubusercontent.com/HoaxShark/AIComponent/master/Images/inspector.PNG)

## Conclusion
Overall this final version is good as a proof of concept, however it currently struggles with levels that have hazards or slopes. I think the best way to handle these in the future to to move to a machine learning approach where the AI can discover the best routes to avoid hazards itself. 
