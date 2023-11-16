# YTube_video_trimming
import pytube
from moviepy.video.io.VideoFileClip import VideoFileClip


# create a YouTube object, and add your link
youtube = pytube.YouTube("https://www.youtube.com/watch?v=U9x0WDwMhmA")

# get the video stream with 4K resolution
video_stream = youtube.streams.filter(res="2160p").first()

#store your file
output_file_path = "/content/sample_data/video.mp4"

# download the video stream
# video_stream.download(output_path=".", filename=output_file_path)
video_stream.download(output_path="downloads")      # creates folder


input_path_file = output_file_path

#.subclip(startseconds, endseconds)
trimmedvideo = VideoFileClip(input_path_file).subclip(22,32)

trimmedvideo.write_videofile("/content/sample_data/trimmedvideo.mp4")
