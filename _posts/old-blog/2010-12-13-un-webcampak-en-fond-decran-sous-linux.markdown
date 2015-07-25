---
layout: page
subheadline: "Tech"
title: "Setting a webcampak capture as a dynamic wallpaper on Linux"
date: 2010-12-13 08:07:14+00:00
teaser: "You can use a webcampak picture as a wallpaper on Linux, this is not a very common situation as webcam pictures quality tends to be low. But with Webcampak you can enjoy high resolution pictures right on your wallpaper."
header:
    image_fullwidth: "header_typewriter.jpg"
    caption: Image by Florian Klauer
    caption_url: "http://florianklauer.de/"
image:
    thumb:  typewriter_thumb.jpg
    homepage: homepage_typewriter.jpg
categories:
    - tech
comments: false
show_meta: true
---
The script available below has been created for [Gnome](http://fr.wikipedia.org/wiki/GNOME) desktop environement, this is the environment available by default with [Ubuntu](http://fr.wikipedia.org/wiki/Ubuntu).

All necessary actions will be performed using a console, you could also do the same with any graphical interface.

First open a console, with Gnome go to "Applications" > "Accessories" > "Console", then type in the following commands :

    #> mkdir Pictures
    #> cd Pictures
    #> mkdir wallpaper
    #> cd wallpaper


Then check the full path of the directory you are currently into _pwd_ :

    #> pwd
    /home/maison/Images/wallpaper


Write down the result of the above command, you will need it for the script :


    #> gedit script.sh


Copy/paste the following code into the text editor :


    #!/bin/bash
    wget http://mon_url/live/webcam-1280x1024.jpg -O /home/maison/Images/wallpaper/Wallpaper_$(date +%Y%m%d%s).jpg
    gconftool-2 -t str --set /desktop/gnome/background/picture_filename /home/maison/Images/wallpaper/Wallpaper_$(date +%Y%m%d%s).jpg
    gconftool-2 -t str --set /desktop/gnome/background/picture_options scaled


Replace the url with your own picture url  (mon_url/live/webcam-1280x1024.jpg), the change the path by replacing  /home/maison/Images/wallpaper with the result of "pwd" command.

Save your file and quit gedit.

You can test your script with the following command :


    bash script.sh


Your wallpaper should be replaced with a picture from your webcampak.

We then need to add a task within GNU/Linux crontab. Cron will take care of executing the script regularly (i.e. every 10 minutes).


    crontab -e


Add the following line at the end of the script (replace directory to match your environement)


    */10 * * * * bash /home/Utilisateur/Images/wallpaper/script.sh > /home/Utilisateur/Images/wallpaper/wallpaper.log


Save and quit, your system will now automatically refresh your wallpaper.


![](http://wiki.webcampak.com/images/9/9f/Webcampak-wallpaper.jpg)

_This article has been automatically imported from our old blog, there might be formatting or layout issues._
