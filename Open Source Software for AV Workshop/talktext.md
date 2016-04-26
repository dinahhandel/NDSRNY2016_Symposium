
##Intro
Hi everyone, and welcome to the final workshop of the day! I’d like to thank my fellow NDSR cohort members for all their hard work today, and our fellow presenters for their wise words on the topics of grant funding, bag-it, and web archiving. I’m going to try to keep things light and upbeat, and try to only talk for about 25-30 minutes, which will leave time for questions and a little wrap up at the end of the day before we begin our cocktail hour.

When I initially planned this workshop, I thought I might do something that was more hands on, and involved some basic scripting skills using the open source tool [ffmpeg](https://ffmpeg.org/). However, when we learned about the number of people that had registered, I felt that a workshop of that type would be really difficult. The range of skillsets and knowledge would be all over the place, and it would be hard to offer help or assistance to all of you in the event that you encountered technical difficulties, in addition to providing instruction. Furthermore, not everyone attending is versed in audiovisual lingo, or necessarily deals with audiovisual collections. So, instead, what I’d like to do is talk a little bit about video and the components that make up a digital video file, introduce some open source software for working with audiovisual materials, and demo and explain a bash script to create a simple archival information package. 

My approach for the workshop is to talk about both tools and frameworks to use when approaching audiovisual materials, and I’m hoping to present information in an accessible way, in particular for those that may not have prior or in depth knowledge of audiovisual materials, and I encourage questions at the end or later on if you go on to try these tools at your institution, although I can't promise that I will know the answer, and other experts in the audience are encouraged to pipe up and share their own thoughts! For me, when I started to work with audiovisual resources, there was so much that was confusing or unclear about how materials and workflows were described, and while audiovisual material certainly has its challenges, it is possible to learn and gain comfort with the format. What I hope you gain from this presentation is a sense that processing and preserving audiovisual materials is possible, even with very little means. You don’t need an expensive media or digital asset management system to begin organizing, describing, and preserving your audiovisual files. I take a lot of inspiration from the [Digital POWRR folks](http://digitalpowrr.niu.edu/), and believe that taking any step, no matter how small, towards digital preservation is meaningful. 

The structure of this is going to follow something like this: I’m going to talk a little bit about microservices and NDSA levels of digital preservation, and then I'll discuss formats, containers, and codecs, and the differences between analog video that has been digitized, born digital video, and how to think about preservation masters and derivative copies. Then I’m going to show you a little script that I wrote which will create a really simple archival information package (I’ll also introduce that concept) that contains the original file, an access copy, descriptive and technical metadata, and a checksum document. The script will be available on github, so you can download it and modify it yourself if you’d like. I’ll break down each part of the script, in the hopes of making it clear what it is doing, in non-technical terms. Finally, I'll end with talking about some of the options for storage for audiovisual materials, which are typically very large in size. 

###OAIS, microservices, NDSA Levels of Digital Preservation
At CUNY Television, we use a microservices approach to our workflow. What this means is that instead of implementing a monolithic software or software suite that conducts all of our archiving and preservation through a graphical user interface, we have a series of scripts run from the command line that perform discrete archiving and preservation tasks, which can then be combined to automate the transcoding, delivery, metadata creation, and packaging of audiovisual files. This allows for us to build and modify our workflow as needed, and doesn't cost anything other than the time it takes to write scripts, which is certainly time-intensive, especially for beginners. However, what is most useful about this approach is that it allows for institutions to begin taking small steps towards digital preservation, similar to what is suggested by the folks with Digital POWRR. Using the NDSA Levels of Digital Preservation is also a helpful guide, in that it breaks down digital preservation into more manageable pieces, suggesting that any movement towards greater control over materials and how they are described and stored is productive and important. This is especially important in the context of OAIS, or the Reference Model for an Open Archival Information System. I won't get too deep into OAIS except to say that it is a standard for archiving and preservation, that uses the concept of the AIP or Archival Information Package, for long term storage. In lay-person's terms, an Archival Information Package contains the digital object that you want to preserve, and the associated metadata that is needed for the rendering and preservation of the item. I think it is fair to take a broad or even loose interpretation of OAIS standards, especially for under-resourced institutions, because the standard can be overwhelming if you are attempting to adhere to it perfectly. In the spirit of combining OAIS and the ethos of Digital POWRR, I'm going to propose that learning about what types of media formats you have, creating minimal metadata, and organizing your digital files is a great first step in digital preservation. 

[NDSA Levels of Digital Preservation](http://www.digitalpreservation.gov/documents/NDSA_Levels_Archiving_2013.pdf)
[Reference Model for an Open Archival Information System](http://public.ccsds.org/publications/archive/650x0m2.pdf)
[Some Assembly Required - Micro-services and Digital Preservation](http://drewvandecreek.blogspot.com/2016/03/some-assembly-required-micro-services.html)

###Formats, Containers/Wrappers, and Codecs
Video is created in a variety of ways, and there are many components to an audiovisual file. I should say that my examples aren’t exhaustive, as there isn’t enough time, nor do I have the knowledge to talk about the multitude of types of audiovisual materials.

####Analog media/video carriers:
One way that video is created is through the recording of a video signal onto a carrier, such as a tape. This is a significantly less common way of creating video now, but if you have any media in your collection that isn't digital, it is probably on some sort of tape. There are lots of different types of tapes, you might be most familiar with VHS, but there are a wide variety of formats that you could encounter based on the archival setting you’re in- at CUNY TV where my residency is, we have UMatic, Betacam SP and SX primarily. Depending on how old your collection is, or what types of contents were being created, you may encounter open reel tapes in different sizes (early side of video), or cassettes such as Umatic, Betacam, VHS, video8 or hi8, DVCAM, and even audiovisual content stored on optical media such as DVDs. If you have analog media, changes are you’re going to want to migrate the contents on the carrier to a digital file. This can be done through using a playback machine, or deck, a device that captures the signal from the deck and software that converts that signal to a digital file. There are some open source solutions to the software side of things, but unfortunately decks and the devices that capture signals are expensive and sometimes hard to find. Some institutions build their own in-house digitization set-ups, and others receive grants or institutional funds to work with vendors for digitization. A commonly cited figure is that most analog media formats will be unplayable in about 20 years, due to the lack of available hardware to playback media. Analog media is also susceptible to degredation due to storage in undesirable conditions. 

Here's some resources for identifying, assessing, and inventorying analog media:  
[UCLA Special Collections Materials](https://www.flickr.com/photos/124076687@N04/with/14292400264/)  
[Bay Area Video Coalition Audio Visual Compass Identification](http://avcompass.bavc.org/identify)  
[AVCC](https://www.avpreserve.com/tools/avcc/)  
[Columbia University Audio/Video Survey](http://library.columbia.edu/services/preservation/audiosurvey.html)  
[Texas Commission on the Arts Videotape Identification and Assessment Guide](http://www.arts.texas.gov/wp-content/uploads/2012/04/video.pdf)  
[California Audiovisual Preservation Project Guide to Identification of Audiovisual Formats](http://calpreservation.org/wp-content/uploads/2013/10/2013-Audiovisual-Formats_draft_webversion-2013oct15.pdf)  
[Preservation Self-Assessment Program](https://psap.library.illinois.edu/format-id-guide)  
[Inspection templates and forms for analog media](https://github.com/amiaopensource/analog-inspection)  

####Digital Video:
Most video currently is created and stored digitally. From the short videos we create with our mobile devices, to higher quality production video, there are numerous ways to create born digital video. This also means that you can receive video in many different formats. Digital video files contain video data and a wrapper or container, which is metadata about the video file. [maybe open video file in hex editor to show video data?]  

#####Containers
A container (sometimes referred to as a wrapper) is important, as it communicates with the video player on your operating system. Containers can be expressed through file extensions, but this isn't a perfect indicator as different file formats can share the same extension.  

[show output of container metadata?]  

Some common containers are .avi, which stands for audio video interleave, and is associated with the windows operating system, .mov (which is part of QuickTime) and is associated with the Mac operating system. There’s also .mkv (matroska) and .mxf (material exchange format) which are both playable on both Mac and Windows operating systems.  
There are benefits to choosing some containers over others, including whether or not the container is still actively developed or if it is an open specification, what operating system you use, and whether the codec is widely in use by others. There are plenty of other containers that you could come across with digital video files, and I encourage you to look at the Wikipedia links listed below. 

[Digital Container Format](https://en.wikipedia.org/wiki/Digital_container_format)  
[Comparison of Video Container Formats](https://en.wikipedia.org/wiki/Comparison_of_video_container_formats)  


#####Codecs
In addition to containers, there’s also the video’s codec. This is one of those video terms when I first started working with video where I was like.. what does this even mean?! I’m no longer ashamed to say I confused codec with container all the time at first… and honestly, it is confusing, because is some instances, like DV, it is both. A video codec is a program that encodes a data stream or signal for transmission, storage or encryption, or decodes the datastream for playback or editing. 

[fix this section, add visual from Dave, clarify difference more between codec and encoding]

#####Encoding
There are many different encodings, and one way you might hear them referred to is lossy or lossless. This description has to do with the amount of video data that is kept or lost through compression of the file. An uncompressed codec means that none of the video data is compressed, and it is considered the standard for preservation master files. however, this also means that the file size of the video is quite large, and this isn’t typically a sustainable solution for many archives, as larger video sizes mean the need for more storage, which is ultimately more expensive. If you aren’t able to handle using an uncompressed codec, there is another option. A codec that has lossless compression is smaller in size than an uncompressed codec, and lossless means that although the data is compressed, the file will decide to the same data as the original encoding. Some well-known lossless encoding specifications are FFV1 version 3, lossless JPEG2000, and lossless h264. Similar to wrappers or containers, there are some benefits to choosing one codec over another, including openness, wide use, and whether or not the particular codec is known to produce artifacts from the compression process that result in playback errors of the video files. 

[List of codecs](https://en.wikipedia.org/wiki/List_of_codecs)  
[List of Open Source Codecs](https://en.wikipedia.org/wiki/List_of_open-source_codecs)  
[Wikipedia page for codec](https://en.wikipedia.org/wiki/Codec)  
  
#####Bit Depth
Finally, something else to consider about digital video files is their bit depth. Bit depth is the resolution quality of the video. there’s 10 bit, which is the highest quality (and contributes to a larger file size), and 8 bit, which is slightly smaller but also of a slightly lower quality. 

So, when you’re working with video files, these are all factors to consider. Typically, when you’re digitizing (or having a vendor digitize), or working with a production unit that is exporting video from an editing software, you can specify which container, codec, and bit depth you’d like to use, although these are limited by one another, for example many codecs support limited values of bit depths. 

###ffmpeg 
ffmpeg is an open source software that is used to decode and encode audiovisual files. You can use ffmpeg to transcode from one format to another. ffmpeg can be used from the command line, but if you prefer using a graphical user interface to transcode files, I recommend the open source software [handbrake](https://handbrake.fr/).  

ffmpeg can be complicated to begin using because of the multitude of options within an ffmpeg command. I’d like to refer everyone to an amazing resource called [ffmprovisr](http://amiaopensource.github.io/ffmprovisr/), which is a site that has sample ffmpeg commands, with explanations of what each component does. the basic structure of an ffmpeg command goes something like this:  

ffmpeg (calling the software)  
-i (signifying that the input video file will follow the -i)  
input (your video file)  
flags (options that dictate what the software is going to do to the file input)  
output (the resulting file and its location)  

We’re going to use ffmpeg in our script to create our access copy, and here’s the command that we’ll use:  

ffmpeg -i input_file -c:v libx264 -pix_fmt yuv420p -preset veryslow -crf 18 -c:a copy output_file  

[ffmpeg wiki geared towards archivsts](https://github.com/amiaopensource/ffmpeg/wiki)  
[ffmpeg bug tracker and wiki](https://trac.ffmpeg.org/wiki)  

The other pieces of open source software we’re going to use in our packaging script are metadata-related. We’ll use [mediainfo](https://mediaarea.net/en/MediaInfo) to acquire technical metadata about our files, and md5deep as a way to generate fixity information. 

ok, that was a lot of information. As I’ve mentioned, I’ve tried to compile as many resources as I could on our symposium’s github page, along with the text of this presentation, so that you can refer back to it and learn more at your own pace.  

###Packaging Script Demo
So the script that I’m going to demonstrate is written in a language called bash, which works in Mac and Linux environments, and will be part of Windows 10. I don't know how to use Bash in a Windows environment though, so the demo will be in a Mac operating system.

###Storage of Audiovisual Materials
As I've mentioned before, depending upon the size of your audiovisual files, setting up storage infrastructure can be very expensive. Rather than go into different options, I'm just going to offer some aspects to consider: 

1. cost of the storage
2. how easy or difficult is it to retrieve your materials from storage?
3. what is the environmental impact of the storage you'll be using? 
4. the amount of materials you want to store, and your projected growth of storage over time

###General Resources
[New England Archivists AV 101 Workshop: Resources](https://docs.google.com/document/d/1CzJ3B4m_V6pXmMacdRuw_MJpy22p5FqlLC8nPq0JLOY/edit)
