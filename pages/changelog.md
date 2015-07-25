---
layout: page
title: "Webcampak Changelog"
header:
   image_fullwidth: "blog/2015/07/webcampak-code.png"
permalink: "/changelog/"
---
# Changelog (v3.x):
Coming soon

# Changelog (v2.x):
__v2.0-b94__

* Picture rotation
* Other minor improvements


__v2.0-b93__

* Easier way to configure internal sources processing
* Raw files support when used in conjunction with internal sources processing (get) and variable capture rate
* Few other U/I improvements


__v2.0-b91__

* Completely revamped Webcampak Mobile web interface

__v2.0-b83__

* Small improvement in the way configuration settings were loaded/saved for high latency links


__v2.0-b82__

* Display link to both AVI and MP4 in the videos window
* Various other improvements


__v2.0-b70__

* Added DSLR RAW pictures support
* Send stats by email daily
* Some web interfaces modifications (mobile and desktop)
* Critical bug corrections (compared to b61)


__v2.0-b61__ (experimental release)

* New web interface based upon Sencha Extjs Framework (Javascript / Ajax)
* Gather and display stats.
* Better permissions and user rights management.
* Audio & watermark moved to source + global level (instead of global only), this makes those files private.
* FTP Servers configuration moved to source level (instead of global level).
* ...

# Changelog (v1.x):
__v1.7-b04-20120618__

* Removal of some php notice in the viewer/admin panel, code cleaning.


__v1.7-b03-20120613__

* viewer/photos.php photos.tpl: improved interface when viewing small pictures (width below 1024).
* wpakWebcam.py: Updated webcam capture module to assign a physical USB port to a specific source, therefore if multiple webcams are use they cannot move between sources.


__v1.7-a02-20120611__

* Updated the USB webcam capture module.
 _This is an alpha intermediate release._


__v1.7-a01-20120607__

* Corrected a few bugs and started to work on a deflicker feature.
 _This is an alpha intermediate release._


__v1.6-b03-20120525__

* New: Extract date from exif metadata for "ipcam" source (any files uploaded to /tmp/ directory get renamed like this YYYYMMDDHHMMSS.jpg)


__v1.6-b02-20120525__

* wpakVideo.py: Correction of a bug in transition feature, caused by new "minimum time" feature


__v1.6-b01-20120524__

* New: 	- Set a minimum time between two pictures when generating a custom video or post-prod batch


__v1.5-b06-20120516__

* wpakVideo.py: Modification in the way phidget sensors can be inserted into picture
* wpakCaptureManagement.py: Modification in the way phidget sensors can be inserted into picture


__v1.5-b05-20120515__

* Few updates in a lot of files (mostly translation and look & feel).


__v1.5-b04-20120511__

* Few updates in a lot of files.


__v1.5-b03-20120506__

* wpakVideo.py: Correction of a bug.


__v1.5-b02-20120504__

* New: Calendar to select days of the week and timeslots to capture
* New: Stats module, to collect details about running webcampak
* Other modifications include:
* Removal of source planner, planning integrated within source configuration
* viewer/photos: corrected a bug when moving between months


__v1.5-b01-20120425__

* New version, multiple modifications
* Sensors are now considered a source
* FTP servers are configured from a single page, ease things when multiple sources must send pictures to same FTP server
* FTP section has been removed (replaced by FTP servers)
* code update and various other modifications


__v1.4-b04-20120402__

* Updated: Updated to latest version of jqzoom.


__v1.4-b03-20120330__

* New: Added setting not to generate error hotlink pictures if capture failed (keep the last captured picture as hotlink).


__v1.4-b02-20120323__

* wpakRRDGraph.py: Correction of a bug when sending sensors measurements to a remote host
* wpakIPCam.py: Correction of a few bugs
* wpakCaptureManagement.py: Few improvements and corrections
* config-photos.php: Correction of a bug when disabling pictures storage.
* config-avance.php (locale): Change to make things more understandable.


__v1.4-b01-20120314__

* wpakErrorManagement.py: Improved email alerts, the system can send a reminder when a source is offline, frequency of the reminder to be chosen during configuration
* admin/index: Added a dashboard to overview sources (time since last capture, disk usage, ...)


__v1.3-b07-20120312__

* wpakIPCam.py (and others): Define if there is an error based upon the time spent since last picture saved within pictures directory
* Added time since last successful capture within error email subject


__v1.3-b06-20120301__

* New: Added means to skip similar pictures when creating videos (to remove portions with no activity)


__v1.3-b05-20120224__

* New: Capability to insert a thumbnail within a picture in post-production (i.e. a focus on a specific area)


__v1.3-b04-20120221__

* wpakRRDGraph.py: Correction of a bug in RRD graph creations


__v1.3-b0x-201xxxxx__

* Intermediate versions


__v1.3-a01-20111107__

_This is an alpha release, likely to contain bugs._
* New: Added a section to prepare shots for post-production. Including effects (camera tracking, zooming, ...)
* New: Ability to move shots between sources
Those new modifications are mostly targetting central servers with large storage space, CPU and memory.


__v1.2-b05-20111030__

* wpakFTPClass.py: There was a missing try/except
* wpakRRDGraph.py: Wrong maniuplation caused the whole capture to fail


__v1.2-b04-20111016__

* New: wpakVideo.py , config-videocustom.: Added an option to create custom videos unsing only some of the pictures (i.e.: from 8:00am to 4:00pm)
* viewer/../skeleton.tpl: Small modification of the viewer panel, an "empty" source was displayed in some occasions
* viewer/photos.php: Next/Previous was moving by +5 instead of +1, corrected.


__v1.2-b03-20111010__

* slideshow: Added a slideshow using jquery supersized. Can be used to display fullscreen pictures.
* fullscreen: Added fullscreen capabilities using jquery supersized.


__v1.2-b02-20111004__

* wpakVideo.py: Correction of a typo bug for 2 pass video encoding.


__v1.2-b01-20110911__

* RRDTool: Added RRDTool to graph sensors values instead of a custom build functions. Much more reliable.


__v1.1-b11-20110829__

* viewer/photos.php photos.tpl: added 6 thumbnails below pictures (3 previous/following pictures)


__v1.1-b10-20110823__

* admin/*.php *.tpl: added hidden form to ensure nothing gets submitted when restoring tabs from web browsers


__v1.1-b09-20110820__

* wpakCapture.py, config-source.cfg, config-source.php, config-source.tpl: New option for IP Camera (FTP), no actions to be taken if no new pictures available


__v1.1-b08-20110818__

* config-videocustom.php: Email parameter was not properly taken into consideration
* wpakVideo.py: Correction of a bug when generating a MP4 file.


__v1.1-b07-20110817__

* wpakCapture.py: Corrected a bug with FTP upload of images in case capture failed.


__v1.1-b06-20110809__

* viewer/photos.php: Display an error message when there is an empty pictures directory for the current source
* Multi-sensor configuration for video creation (regular and custom) (config-video.php/tpl, config-videocustom.php/tpl, locales, wpakVideo.py)


__v1.1-b05-20110803__

* wpakImageMagick.py: Inserted a missing parameter in color-in function


__v1.1-b04-20110731__

* viewer/videos.php: Using filename and not filedate to determine video creation date (was causing inconsitency if video file was transfered at a later stage)
* wpakDateFormat.py: Added a space in front of the date when adding a legend
* viewer/videos.php/.tpl: Modification of the way video link are displayed (made it easier to understand)


__v1.1-b03-20110724__

* wpakIPCam.py: Taking seconds in consideration in the filename
* webcampak.py: Adding a constraint to get capture delay parameter only for captures (and not videos or sample)


__v1.1-b02-20110722__

* config-photos.tpl/.php: Removed deprecated portions of code
* wpakIPCam.py: Implementing email alerting if no pictures have been uploaded via FTP to the Webcampak.
* config-source.tpl/.php (locales): Added more precise instructions
* New: Check if file has been properly uploaded and allow multiple retry (files: wpakFTPClass.py, config-sourceX.cfg, ...)
* New: Send phidget measurements via FTP to main FTP server (still in progress)


__v1.1-b01-20110705 (major release)__

* /viewer/: Correction of a security issue in the viewer panel allowing authenticated viewers to see pictures from other sources by guessing filenames.
* wpakGraph.py: Removed hard coding, can support up to 4 different sensor per source.
* New: Support for various phidget sensors


__v1.0-b34-20110630__

* wpakDateFormat.py: Added possibility not to insert a date with a legend during video creation
* wpakVideo.py: Added possibility not to insert a date with a legend during video creation
* wpakIPCam.py: If source is a Webcampak, added a check to ensure temporary directories are not processed (only process directory starting with 20)
* New: Added upload archives to an additional FTP server (for example to save pictures to a NAS and send pictures to a Webcampak for remote processing)


__v1.0-b33-20110629__

* admin/../config-videocustom.tpl: Typo mistake creating issues with pre-processing.
* admin/../config-video.tpl: Typo mistake creating issues with pre-processing.
* wpakVideo.py: Changed timestamp calculation method for inserting time & date within videos in pre-processing.


__v1.0-b32-20110628__

* wpakPhidget.py: Addition phidget activation check.


__v1.0-b31-20110624__

* wpakWebFile.py: Added a 10s timeout to webfile download function.
* Changed default capture minimum size, from 300B to 3KB.