# Sleep analyser
___Analyses screenshots taken on an iPhone 5s, this program is tested with +-2000 pictures from my iCloud___

Although there are a lot of apps available that keep track of sleeping cycles, your bedtime etc. I always liked using the iPhone alarm. The reason is that it is simple to use and that you don't have to sleep till a fixed time, but that you can choose to sleep for a certain amount of hours. An example to demonstrate: it is 01:00 o'clock and I am going to bed. I like to sleep 9 hours and need some time to fall asleep, so I would set a timer for 9 hours and 5 minutes. Afterwards I would lock and unlock my screen and make a screenshot. See for example this image:
<img src="http://i.imgur.com/PFm7JvB.jpg" alt="drawing" width="20%" height="20%"/>

I started making screenshots of my sleeping timer a few years ago (when I couldn't even program yet) with the idea that I would be able to write a program for it some point in my life. Now I did :) This is how it works.
## Recognising screenshots of lock screen - Filter 1
I downloaded screenshots from iCloud, but they were mixed with other random screenshots. I took one example image and used this to 'train' the program (a lot is hardcoded so training is an overstatement). If you would like to use this program yourself, you should take your own example with your own background and searchspaces. So the program loops through all downloaded images and matches a big part of the background from the example lockscreen to the screenshot. The program moves all the matched screenshots to another folder called filter_one.
## Recognising screenshots of lock screen - Filter 2
This can just be screenshots of my lock screen or background and don't have to be a screenshot of the timer itself. Template matching (normalized cross correlation) is used to find a tiny clock on the screen. The tiny clock is always displayed when the timer is set. Template matching is slower than just comparing if part of an image are the same, so that's why this 'filter' is only used now. It moves all the screenshots of lock screen displaying a timer to a folder called filter_two.
## Classification
Just like the last step, template matching is used. This time to find all the numbers displayed in the selected searchspace. The search space is the space where the remaining time of the timer can be displayed on an iPhone 5s. All the good matches with a number (>.92) are assumed to present the remeaning time. Based on the locations of the numbers the remaining time (in hours) is calulated. A picture of each number in the same size must be added to a folder called classification.
## Visualisation
Based on all the remaining times of the timers an average and standard deviation is calculated. This shows how much you sleep and how consitent the amount of sleep is. This is represented in a dotplot and Gausian. See image: <img src="https://imgur.com/f2HiAG7.png" alt="drawing"/>

If you have any questions, you can contact me at mmeester@hotmail.nl
