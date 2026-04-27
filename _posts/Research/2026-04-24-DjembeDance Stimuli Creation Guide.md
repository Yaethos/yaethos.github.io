---
title: DjembeDance Stimuli Creation GUide
categories: [Research]
date: 2026-04-24
tags: [research, academia, code]     # TAG names should always be lowercase
mermaid: true
---

# Introduction
This is a guide for creating experimentally-valid stimuli from the motion capture data present in the Djembe Dance corpus. Matlab will be required to create the animation from the raw data, and that's something that has already been documented inside the project.

Following this guide, the full animation will be turned into a 40s 8-bars loop. The loop will then be exported as audio-only, video-only and audiovisual versions. A small section on how to create delayed version will be present as well.

This guide only uses the FREE version of DaVinci Resolve. Many steps in the process can also be completed in other video-editing softwares, but some specific steps might be harder to replicate in them (for example movement tracking and interpolation).

This guide follows the creation of stimuli at 50FPS. This makes some calculations easier, since 1 frame is 20ms, which is a comfortable amount. Be sure to keep the FPS in mind when starting to do this, as anything other than 50FPS could lead to problems further down the line.

# Unit Selection
Start by creating a new DaVinci Resolve project. I opted for 1920x1080 (even though the full animations are 1x1) and 50FPS.
I suggest to start creating a media architecture that reflects what the stimuli set will look like. I did that by creating one folder for each actor, and then a folder for each basic movement. Inside those, there was a folder with each BPM version of the movement. I also created separate folders for Mali and Norway, further subdivided into the different dances.
![Desktop View](/assets/img/stimuli/0_architecture.png){: width="700" height="400" }

Create a new timeline inside the corresponding folder (the example shows M_120_Step). You can import the animation and the audio in this timeline, as shown in the image.
![Desktop View](/assets/img/stimuli/1_loadup.png){: width="700" height="400" }

The selection part is the part that feels more freeform. I usually handled this by randomly choosing an onset and then moving 8 onsets forward. The idea is to select an 8-bars loop that feels natural and is not too extreme in timing variation. I will refer to this 8-bars loop as an **Unit**. 
There are a list of things to be mindful of in this process.
- The number of frames between one onset and the next throughout the unit has to be somewhat consistent. Any irregularities greater than 2 frames is already risky (2 frames equal 40ms at 50FPS). For 50FPS, 25 frames between one onset and the next is ideal (25x20ms=500ms), and you can count those by alinging the playhead to one onset and pressing the right arrow key 25 times.
- You can press M to insert a marker. I used those to mark each onset in the complete recording, changing the color depending on the relationship with the previous one. If the onset came later than 25 frames I used red, if it came earlier I used green. I then used this "quality map" to choose the 8 beats that would form the Unit.
- The total time of the unit has to be consistent for every stimulus. At 50FPS, this is 4s (each beat is 0.5s, 8 beats is 4s).
- If the audio needs to be normalized, you can cut each onset in the audio track, then select all of them, right click and choose normalize audio
![Desktop View](/assets/img/stimuli/4_audionorm2.png){: width="700" height="400" }

You can normalize to -6dBFS, making sure to check independent.
![Desktop View](/assets/img/stimuli/5_audionorm3.png){: width="700" height="400" }
- In order for the Unit to smoothly loop, make sure that the body shape and position is similar in the first and last frame of the unit. This will require some trial and error, and we'll see some techniques on how to smooth the transition. However, if the first and last frames are too different nothing will work.

To mathematically check the time between each onset of the stimulus (thus controlling the regularity of the pulse), you can use manual markings in Audacity, or a Matlab script for extracting the onsets.

# Creating the Core
In order to create what we'll define the core, create a new timeline in the working folder. Here, paste the unit you've copied from the other timeline 10 times.
![Desktop View](/assets/img/stimuli/6_newtimeline.png){: width="700" height="400" }

The next step will allow us to extend the background in order for the stimulus to cover up the whole screen. Create a new track by right-clicking on the track section.
![Desktop View](/assets/img/stimuli/7_newtrack.png){: width="700" height="400" }

Click the effects tab on the upper-left corner and search for "Solid Color". Click on it and drag it onto the second track just created.

![Desktop View](/assets/img/stimuli/10_colore.png){: width="700" height="400" }

You can change the color by double clicking the solid color track, a menu will appear on the right and you can change the color by clicking the corresponding section.
Extend the track to the end of the stimulus, then right click on the track (where "Video 2" is, not on the solid color effect) and click on "Move Track Down"
![Desktop View](/assets/img/stimuli/11_movetrack.png){: width="700" height="400" }

If the looping point between two consecutive units is already smooth enough, you can skip to the next section.

If some easing is necessary we have two main tools to do this. The first one allows for small-scale easing between two or more frames. To use it delete every repetition of the unit except the first two, open the effects panel and search for "Smooth Cut", then drag it where the two unit meet. Double click it and change the duration to 2 or 4 frames.

![Desktop View](/assets/img/stimuli/99_smoothcut.png){: width="700" height="400" }

You can move frame by frame in order to see how it works. Avoid the ambition to have perfect loops and try to evalue it in context and not frame by frame. If it feels smooth enough when played then that's okay, even if there's some weird linework caused by the smooth cut. You can duplicate the units, remembering to add the smooth cut transition where it's missing.

The second tool is a bit more complex, and allows us to stabilize the movement of the animation on the X-axis. This is particularly useful for movements such as jumping and stepping, where the actor might be in a similiar position in first and last frame but shifted on the left or on the right.
Select the first unit and open the "Fusion" section of DaVinci. This tab might feel intimidating if you've never seen it, but we only need a couple of elements. Open the effects section and drag the "Tracker" node on the white line of the Node tree.

![Desktop View](/assets/img/stimuli/13b_trackernode.png){: width="700" height="400" }

A green graphic square will show on the video output, click on the small square on the top-left corner and drag it so that the tracker sits on the center dot of the waist. Before doing this, make sure that you are on the first frame by clicking at the left-most point of the timeline underneath the video output (where all the numbers are). 

Once the tracker is positioned, enlarge it horizontally so that it contains the 3 dots of the waist. You can do that by simply clicking on the vertical lines of the square and dragging them out.
We have now "armed" the tracker, meaning that it will look for that pattern on the entirety of the unit, recording the movement frame by frame. In order to make it work, click on the "Track Forward" button.

![Desktop View](/assets/img/stimuli/13d_tracktoend.png)

The tracker will now go through the whole unit, trying to follow along with the waist. You can check visually while it works, and you have to make sure that it does not go crazy, as it can sometimes happen. If it does, reset it (worst case you can just delete it and re-place the tracker node) and start again changing some parameters, especially the "Search Area" which is represented by the dotted lines.

Once you have a good-enough tracking of the movement, we will need to convert the path to XY coordinates, and delete the Y tracking so that only the horizontal movement is counter-balanced. To do this, right click on the green visualization of the tracker and search for "Tracker1Point1Path1: Polypath". Hover on it and, on the menu that shows up, click on "Convert to XY Path" and confirm with 0 offset.

![Desktop View](/assets/img/stimuli/14_converttoxy.png){: width="700" height="400" }

You will have to open the Spline section now, and you can find it on the top-right angle of the screen.

![Desktop View](/assets/img/stimuli/13e_spline.png){: width="700" height="400" }

On the section that appears, right click on the Y track and press "Delete".

What we've been doing until now has only allowed us to know the exact movement of the waist through the unit. To stabilize it, open the settings of the Tracker node (by double clicking it), go to the "Operation" tab and change the operation to "Match Move". Then, on the "Merge" value, select "BG only".

![Desktop View](/assets/img/stimuli/14_trackernodeoperation.png){: width="700" height="400" }

You can now go back to DaVinci's "Edit" section. Select the unit that has been tracked (you can recognize it by the fact that it has some graphic elements next to the name), duplicate it and evaluate how it looks. It's likely that the "Smooth Cut" transition will still be required to have a smooth transition, but at least the actor will not move around now, allowing for easier smoothing.

If you do add the smooth transition, it can happen that some black vertical "scanlines" will appear on the transition point. 

![Desktop View](/assets/img/stimuli/100_scanlines.png){: width="700" height="400" }

If this happens, it will only happen laterally on the right or left side. To fix it, add a white solid color effect above the animation and use the "Cropping" section contained in the "Settings" part of the solid color to only cover up the part of the screen where the scanlines appear. If it appears in both sides, add two solid colors and use one for the right side and one for the left side.

# Creating the A/V/AV versions
Now that we have the "Core" (defined as the 40s animation made up of looping units), we can export them in the three modality-specific versions. In order to do that, we only need to disable the track we do not want before exporting the file.

![Desktop View](/assets/img/stimuli/25_disablevideo.png)

Disabling the animation track will only leave the white background we set up earlier.

![Desktop View](/assets/img/stimuli/24_disableaudio.png)

Muting the audio track will leave us with a video-only animation.
Of course enabling everything will give us the audio-visual version.


After disabling the track we need to disable, go to DaVinci's "Export" tab, make sure that export is MP4 (or what you need) and framerate is 50. Then add to render queue and start the render process.


# Creating the +/-delay versions
For the creation of the delay versions duplicate the timeline we've created the stimuli in. In this second timeline, make sure the playhead is at the first frame and move forward of 2/4 frames depending on how much delay you need. Select everything in either the video or the audio track and move it so that it starts on the position of the playhead. Then grab the left edge of the first unit (not every repetition of the unit, otherwise each repetition is extended) and drag it back so that the first 2/4 frames are not empty. Go to the end of the timeline and cut the 2/4 frames that exceed the 40s mark.
For the creation of the positive delays (+40/+80ms), the audio track is the one that gets shifted forward. For the creation of the negative delays, the video track is the one that gets shifted forward.

My workflow was to start with the positive delays: 
- Move the audio track 2 frames forward
- Fill in the missing 2 frames
- Delete the 2 frames exceeding 40s
- Export the +40ms core
- Move the audio tracks 2 more frames forward
- Fill in the missing 2 frames
- Delete the 2 frames exceeding 40s
- Export the +80ms core
- Shift the audio track 4 frames backward
- Repeat process with the video track


# Creating the final stimulus
Now that we have a folder with every A/V/AV version and another folder with the +/- 40/80ms versions, it's time to add the acoustic beep at the start of every stimulus. 
Create a new timeline in the main folder and find:
- 3s video clip with a gray background and an acoustic beep at exactly 2s
- 1s video clip with a gray background

These will be provided in the folder of the experiment, but new ones can easily be created.

In the new timeline, place the 3s video clip at the start of the timeline and the 1s clip at 43s. Lock this track (both video and audio) with the lock icon on the left.
Now open the folder with every core, place the first core inside the timeline so that a new track is created above the ones already present. 
Make sure that the core is positioned perfectly at the frame following the first gray clip and one frame before the second gray clip. If some frames are missing (or the core is too long), make sure that the stimulus is exactly 40s. If it isn't, something must have been gone wrong with the creation of it. Go back to the corresponding timeline and fix it before moving on. This is necessary since a core lasting more or less than 40s might indicate a wrong unit loop.

If the core sits nicely, you can export the final stimulus. This needs to be done for every stimulus.

![Desktop View](/assets/img/stimuli/26_capocoda.png){: width="700" height="400" }



# Dance stimuli
For the dance stimuli, the creation of the A/V/AV versions, as well as that of the delay versions, is pretty much the same. For the final stimulus creation, remember that the dance stimuli are 4s longer, and this needs to be accomodated by placing 4 additional seconds between the first and the second gray clip.