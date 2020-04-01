# Twitter Video API on AWS
video-nadimelhelou created by GitHub Classroom

by Nadim El Helou

# Summary
This API receives as input a twitter username/handle and returns a summary video of the user's tweets in the last 24 hours. Each tweet is converted to an image, then a video/slideshow is created - using FFMPEG - with all the tweets, each appearing for 5 seconds.

It runs on an AWS EC2 instance.

# Running
This API runs on an AWS EC2 instance so you do not need to download or setup anything on your computer. All you need to do is enter in your browser one of the following:
* `INSTANCE_IP/` - API Main Page.
* `INSTANCE_IP/tweets?username=ibm` - Replace "ibm" with any twitter username. Will return a summary video of the username's tweets in the last 24 hours.
* `INSTANCE_IP/tracking` - Allows you to track all API calls. Shows you all past and current calls along with their status ("completed" or "in progress").

NOTE: The AWS instance is not always running so ask me for the "INSTANCE_IP", it changes every time you start the instance

# Multithreading
This API uses multithreading in order to support multiple parallel calls: four independent threads are used to execute requests. Each API call is added to a queue and will be processed when it reaches the top of the queue. Each thread executes the `create_video()` function, in which the thread executes the request at the top of the queue and returns the created video.
