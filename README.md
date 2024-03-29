# Supertramp
A worldwide open collection of hiking gpx

## Project introduction
*Society, crazy indeed, hope you're not lonely without me*

The main idea is to gather GPX of hiking tracks from users all around the world. We are of course talking about hike YOU have done, not randomly gathered around the web. In this way this could be a sort of hub where to exchange tracks and informations about them. As you can guess it will be a sort of "write-only" project: there would be no reason in modifying GPX uploaded by other users.

## Why Github
If you use Github 95% of the time you will have a sedentary job. Hiking is a great way to take a breathe out in the wood/on some mountain top and enjoy a different scenery!

## How to contribute
Simply record your hike with any GPS device capable of producing a GPX file and create a pull request where you add that one. At the moment the folder structure is very simple; inside the GPX directory just follow this hierarchy: CountryName -> RegionName and save your file there. __NO FILE OR DIRECTORY NAME WILL HAVE SPACES__. For the folder just use CamelCase (eg. EmiliaRomagna), while for file name follow this format:
1. Decide at least 3 places you passed by during the hike (starting point, one during the hike and ending point). Of course you can have more than 3, and if the starting and ending point are the same is not a problem;
2. All these places will have to be written in CamelCase with no spaces;
3. Delimit the various places with an underscore;
4. The final result should be: StageOne_StageTwo_StageThree.gpx.
  * If you have a hike that goes between Rome, London and New York the filename will be Rome_London_NewYork.gpx;
  * If the hike is a loop, for example going with the route Rome, London and back to Rome, the filename will be Rome_London_Rome.gpx.
5. Again, you don't have to limit to 3 stage. Just write down the one you think are useful to identify the GPX.

## Master the GPX art
To really understand how to write a clean and valid GPX file, readable by EVERY application that follows the standard, I suggest you to check the [official standard specification](https://www.topografix.com/GPX/1/1/). The following paragraph are a bit more in detail on this topic (nothing too technical, but it's good to learn how to write a good GPX)

#### Waypoint
Of course feel free to add any waypoint you want along the hike. The more information you put in your file, the more interesting will be to look at it. Doing a bit of experimentation it seems that Garmin devices, when reading everything you write between the \<wpt>\</wpt> tags, won't show you the waypoint if they have the \<src> tag, so __remember to remove it__. I still don't understand why this happen (it shouldn't, since the \<src> tag is listed in the official specification) and I hope to solve this issue

#### Comment and Description
Creating the track and the waypoints is just the start. It's interesting, if you want, to add also description and comments for the various element you save in the GPX. Personally I use QMapShack to handle all this kind of elements, but at a code-level you would have just to add __\<desc>\</desc>__ tag with the description in and a __\<cmt>\</cmt>__ tag with a comment in it. You can add one or both of them to every waypoint (so inside the \<wpt> tag) and in the track itself (so inside the \<trk> tag)

#### Minimal GPX header
The opening tag, \<gpx>, is usually full of key-values once you exit from the applications that created it. __IF__ you plan to write a GPX with no \<extensions> tag, the minimum required opening tag is the following: 
__\<gpx xmlns="http://www.topografix.com/GPX/1/1" version="1.1" creator="App/URL you used to create the GPX" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.topografix.com/GPX/1/1 http://www.topografix.com/GPX/1/1/gpx.xsd">__

#### Validation
The last step should be the validation against the official schema. [You can check here](https://www.topografix.com/gpx_validation.asp) the official way to validate your GPX.

## Future Development
The first objective is to create a script that, from all the hosted GPX, will create a Database to help searching through them. Also an integration with a service like OSM would be good, but that is something really down the road
