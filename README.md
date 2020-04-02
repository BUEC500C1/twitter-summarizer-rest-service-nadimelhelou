# Twitter Video API
video-nadimelhelou created by GitHub Classroom

by Nadim El Helou

## Summary
This API receives as input a twitter username/handle and returns a summary video of the user's tweets in the last 24 hours. Each tweet is converted to an image, then a video/slideshow is created - using FFMPEG - with all the tweets, each appearing for 5 seconds.

## Running
### On your machine
First, **insert your twitter keys and access tokens in the `keys` file.**

In the terminal, run `python api.py` and you should see, in the output, a line similar to: `Running on http://127.0.0.1:5000/`.

Enter the displayed url into your browser and you will be taken to the API home page. In order to input a twitter username, add the following path to the url `/tweets`, then the username code as such:
* `http://127.0.0.1:5000/tweets?username=ibm`.

You can enter any of the following in your browser:
* `http://127.0.0.1:5000/` - API Main Page.
* `http://127.0.0.1:5000/tweets?username=ibm` - Replace "ibm" with any twitter username. Will return a summary video of the username's tweets in the last 24 hours.
* `http://127.0.0.1:5000/tracking` - Allows you to track all API calls. Shows you all past and current calls along with their status ("completed" or "in progress").

### Through AWS
This API also runs on an AWS EC2 instance so you do not need to download or setup anything on your computer. All you need to do is enter in your browser one of the following:
* `INSTANCE_IP/` - API Main Page.
* `INSTANCE_IP/tweets?username=ibm` - Replace "ibm" with any twitter username. Will return a summary video of the username's tweets in the last 24 hours.
* `INSTANCE_IP/tracking` - Allows you to track all API calls. Shows you all past and current calls along with their status ("completed" or "in progress").

NOTE: The AWS instance is not always running so ask me for the "INSTANCE_IP", it changes every time you start the instance.

## Multithreading
This API uses multithreading in order to support multiple parallel calls: four independent threads are used to execute requests. Each API call is added to a queue and will be processed when it reaches the top of the queue. Each thread executes the `create_video()` function, in which the thread executes the request at the top of the queue and returns the created video.
