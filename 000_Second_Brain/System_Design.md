15/08/2024 2145

Status #idea

Tags:

# System Design

Scale
Reliable
Efficiency
a good approach is to think about everything from Infrastructure, Hardware, Software and data, how its stored and secured.
Ultimate goal is to fore-fill user needs, be efficient, be scalable, low maintenance and cost effective
Business only thinks and sees the front end, where as tech team have to look at all the things behind (the back end)
The Process to think about
1. Requirement, functional (what is should do and show), non functional, behind the scenes stuff (back end), how things work
2. Architecture design how things flow together
3. Component
4. Data
5. Interface, interaction between different parts of the system
6. Security 

Considerations
1. Scalability – able to scale without compromising performance no matter how many users increase/decrease
2. Reliability
3. Performance
4. Maintainability
5. Cost
**Always ask what features are required and what the clients focus is on**
**Cant have a solution when you don't know what the problem is!**

![[youtube design.png]]
 The example above is for uploading a video onto YouTube, but must think logically about the system you are designing. Look at the process things need to happen. In YouTube need to upload the data, store the data before video processing can happen etc. The video processing part could be a [[server]] or [[Server-Less Architecture]], [[Micro Services Architecture]]

After video processing and analysis is done it will be put into another object storage ([[S3]]) using [[Lambda Function]] or [[AWS Step Functions]]

The finally (in this YouTube example) they use a CDN ([[Content Delivery Networks Cache]]) to reduce the loading times for the user giving them the best experience possible, but the first instance will be loaded from the final [[S3]] and after that anyone else watching for the same geographic area, it will be loaded from the [[Content Delivery Networks Cache]]

From an [[AWS]] perspective
![[AWS system design.png]]

**System Design YouTube example and someone watching a video**
 First, user goes to homepage and is presented with a static [[Front End]] page, this can be stored in an [[Object Storage]] like AWS [[S3]]. Most landing pages are static because they can load super fast which is exactly what we want to give the user the best experience.
 So when user searches for something, the search will go straight to the [[Content Delivery Networks Cache]] and if the result is in the cache it will be sent back instantly and that request will end there. If its not in the cache the the request will go to the [[API Gateway]] then onto the [[Lambda Function]] that gets triggered to search the database for the [[metadata]] related to the search query, then it gets sent back to the user with the list of videos related to their query. This will not be the actual video, just the data being displayed.
 Playing the video, when selected, if the video is in the cache in our [[Content Delivery Networks Cache]] it will play immediately, but if not the [[Content Delivery Networks Cache]] will get the video from the [[Object Storage]]([[S3]]) which in turn will put the video in the cache for the user and someone else in the same geographical area
# References
