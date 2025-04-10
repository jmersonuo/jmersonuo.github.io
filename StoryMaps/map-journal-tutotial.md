
# Story Map Journal Tutorial #
<small> Adapted from [arcgis.com](https://storymaps-classic.arcgis.com/en/app-list/map-journal/tutorial/) for Geog 410/510 Stroies and Maps, Feb 13, 2020 </small>
Joanna Merson and Marcel Brousseau

---
The steps for creating your story map are to:

<ol type="I">
  <li>State the "story" goal </li>
  <li>Pick a format (“App”) </li>
  <li>Add a title and your first section </li>
  <li>Add text and an image </li>
  <li>Add a map
    <ol type="i"> 
      <li>Add a map</li>
      <li>Change the basemap</li>
      <li>Add data manually (add points from the novel)  </li> 
      <li>Search for data (something relevant to the novel) </li> 
    </ol>
  </li>
  <li>Configure and share your map</li> 
  <li>Advanced: Set up "story actions" </li>
</ol>

## I. State the story goal ##
What is the goal of your "story"? Do you want to provide photos or recordings for different locations? Do you want to convey long distance of a journey? Do you want to show the density of events at one location? Do you want to create an experiential version of a journey? Set your goal so that you can use it for the basis of your design and content decisions.

## II. Pick a format ##

There are several Esri StoryMaps "Classic" formats that you can follow. Here is a [flowchart](https://jmersonuo.github.io/StoryMaps/Pick%20a%20storymap%20flowchart.pdf) to help you decide which is best for your story. *For this demo, we will use **Story Map Journal**.*

### 1. Background ###

In this tutorial you'll use an interactive Story Map Journal℠ Builder to author your journal entries, which we call sections. For each section you'll specify the web map, image, video or other web content that you want your Map Journal to display when your users reach that section, and how you want that content to be displayed.

For example, you might choose to display the same web map throughout your Map Journal, and have each section automatically zoom to a different area on that map. Or you may author your Map Journal so that it takes your users through multiple web maps, and associated images and videos, as they read through the sections. Lots of different combinations are possible.

If you'll be creating one or more new web maps for use in your Map Journal, you can either create them in [ArcGIS Online](http://www.arcgis.com/home/)  before you start building your Map Journal, or you can create them on-the-go within the Map Journal Builder. From within the Builder, you can also edit web maps that you own. After you have created your Map Journal, you can continue to work on your maps to refine their content, symbology, and popups.


### 2. Getting started ###
Start the [Story Map Journal Builder](https://uo-online.maps.arcgis.com/apps/MapJournal/index.html?fromScratch). You can use a free, non-commercial ArcGIS public account or an ArcGIS subscription account.

Alternatively, you can start in the ArcGIS Online website, open the web map you want to use in your Map Journal, or any one of the web maps if you intend to use several, share it as a web application, and then choose Story Map Journal from the application gallery. The Map Journal Builder will launch so you can configure the application.   

In the dialog that appears when the Map Journal Builder starts, choose the layout you would like to use and press Start.   

*In this tutorial we'll use the default Side Panel layout but the steps are the same for the Floating Panel layout.  *
<img src="https://storymaps-classic.arcgis.com/en/app-list/map-journal/img/step2.png" width ="334px"> 

## III. Add a title and your first section ##
### 1. Title ###
Enter a title for your Map Journal. You can also take an optional quick tour of the Builder at this point.  
<img src="https://storymaps-classic.arcgis.com/en/app-list/map-journal/img/step3.png" width ="334px">

Our title is:
> The Devil's Highway: Helicopters

### 2. Home section ###
### 2.1. Configure the opening section ###
The dialog will appear that lets you add the first entry, the "home section", into your Map Journal. The home section is the first section your users will see when they open your Map Journal, so it serves as the introduction.

In this dialog, you are first prompted for the content you want this section to show in the "main stage": the main area of the display to the right of the side panel. Choose between a Map, Image, Video or Web page.

We are going to use an image. I am going to **upload** an image. Set it's position to **fill** and give it the following alternitive text:
>Desert landscape on the Cabeza prieta national wildlife refuge.

<img src="https://jmersonuo.github.io/StoryMaps/img/imageUpload.JPG" width ="334px"> <img src="https://jmersonuo.github.io/StoryMaps/img/imageSettings.JPG" width ="334px">

Press **Next**.  

### 2.2. Add opening text ###
The Add Home Section dialog will now prompt you to enter and format the content that will appear in the side panel for the home section. You can type directly into the built-in rich text editor. You can also paste text into the editor from word processing programs in which case the formatting is carried over into the editor. You can also embed graphics, images and videos in with the text. You can also define "story actions" in the section's text so that, for example, clicking a word automatically zooms the main stage's map to a particular location. (We'll show you how to set up these actions in **Section VII. Set up “story actions”** below).

We will use the following text:
>Luis Alberto Urrea's 2004 chronicle The Devil's Highway: A True Story describes the deaths of fourteen Mexican men in the Sonoran desert of southern Arizona, as well as the rescue of twelve other men by the U.S. Border Patrol. The men were migrating to the U.S. for economic opportunities. The fourteenth chapter of the book, "Helicopters," describes numerous deaths and rescues in detail, and geolocates the deceased in the harsh desert landscape. 
>  
> Scroll down to follow their journey.

<img src="https://jmersonuo.github.io/StoryMaps/img/EditTitle.JPG" width ="334px">

Press **Add**. Your completed home section will now appear in the Map Journal.  
To save your work so far, press the **Save** button in the top right hand corner of the Builder.  

## IV. Add another section: text, and image, and a map ##

### 1. Add a section ###
Use the Add Section button at the bottom of the side panel to add additional sections into your Map Journal. The same dialog will appear each time you add a section allowing you to specify the content for the main stage and the side panel.

To make edits or other changes to a section you've added, click the blue edit button at the top of the side panel. <img src="https://jmersonuo.github.io/StoryMaps/img/editButton.JPG" height="25px">  

You can use the Organize button to reorder and delete sections. <img src="https://jmersonuo.github.io/StoryMaps/img/organizeButton.JPG" height="45px"> 

Title:
> Federal Wilderness Areas 

### 2. Add a map ###
Set the main stage content to **Map**. Then click the Map dropdown and choose the option to **create a new map**. When you create a new map, the map editor window will appear. Zoom to the area you plan to use, then save and close your new map. We'll come back and edit it later. 

You will then be given the options, shown in the screenshot **below**, to customize how the map is displayed. You can choose to display a particular area of the map, turn layers on or off, display a particular feature's popup, or any combination of those. For example if you choose a custom location, the Builder will prompt you to interactively zoom to the area you want to use, and then you'll press a button to capture that extent. We will come back and edit the map later. 

Set the custom location to the Cabeza Prieta Wilderness and the press next.

We are going to add a short piece of text:
> The landscape of Desolation is technically protected land under the aegis of the U.S. government. Two federally protected land areas sits side by side in this roughly 2,000-square-mile landscape: Cabeza Prieta National Wildlife Refuge to the west, and Organ Pipe Cactus National Monument to the east. 

<img src="https://jmersonuo.github.io/StoryMaps/img/newSection.JPG" width ="334px">

### 2. Add an image ###

Click the camera icon to insert an image. <img src="https://jmersonuo.github.io/StoryMaps/img/editButton.JPG" height="25px">  
You could use images stored on a fliker account or add an image from the web. To do this you can insert the URL of any image, just be sure to **credit the source**.

Link:
> https://winapps.umt.edu/winapps/media2/wilderness/images/NWPS/lib/thumbID250/4246.jpg

Caption:
> Cabeza Prieta Wilderness (Credit: NPS)

Alternitive text: 
> Photo of saguaro cactuses and a mountain the Cabeza Prieta Wilderness

After adding the image we have this:  
<img src="https://jmersonuo.github.io/StoryMaps/img/afterImage.JPG" width ="334px">

**Save** the changes to your map.

## V. Edit the map ##

Now that we know how to add sections, let's look at adding a map.  
   
<img src="https://storymaps-classic.arcgis.com/en/app-list/map-journal/img/step4.png" width ="334px">  
Go back to the top (Main Stage) and click the pencil to edit the section, click on the "main stage" tab. Now click "edit" beside the map title.

In the map editor, you can customize the maps that used in your story.  

### 2. Change the basemap ###

As a novice cartographer, select one of the 12 provided basemaps. For this demo, we are going to choose "Imagery", to emphasize the landscape.  

<img src="https://jmersonuo.github.io/StoryMaps/img/Basemaps.JPG" width ="334px">

In the future, you could learn how to [customize](https://www.esri.com/arcgis-blog/products/developers/mapping/design-custom-basemaps-with-the-new-arcgis-vector-tile-style-editor/) basemaps.

<img src="https://www.esri.com/arcgis-blog/wp-content/uploads/2018/05/vse-1920x1080.png" height ="250px">

### 3. Add data manually (add points from the novel) ###

1. Click **Add** > **Add Map Notes**. You can change the name of the layer. We are just going to leave it for now. The templates will give you different map symbols to choose from. We are going to leave it with the default, "Map Notes".  
2. Notice that you can create features that are point, line, and area types. We are going to use a point feature using "Stickpin".   
3. Pan and zoom to the desired location and click on the map to add a pin.  
4. Set the pin's title and description. You can even add an image here. The map is interactive, so you are adding information that will exist in a popup on the pin.  
5. Optionally change the symbol. Notice there are *dozens* of options to choose from.  
6. **Save** the map. 

<img src="https://jmersonuo.github.io/StoryMaps/img/POI.JPG" width ="334px">

### 4. Search for data (something relevant to the novel) ###

1. Click "Add" > "Browse Living Atlas Layers". ArcGIS Living Atlas of the World is a collection of global geographic information. Curated by Esri with contributions from its partner and user communities, Living Atlas contains valuable maps, data layers, tools, services, and apps for geographic analysis.  
3. Click the small dropdown and click "ArcGIS Online". This allows you to search any content that other arcGIS users have published publically. These will not be as stable as the Living Atlas, but you can usually trust government sources. 
4. Search for "Cabeza Prieta". 
5. There is one layer found. Click the + to add the Wilderness Areas data to the map.
6. **Save** the map. 

<img src="https://jmersonuo.github.io/StoryMaps/img/WildernessAreas.JPG" width ="334px">  

7. Click on the **Details** tab
8. Hover over the layer and press the symbol button (square, rectangle, and circle) 
8. Click options to change to the symbology for all the features in the layer. I'm making it green, with no outline and, 50% transparent.

<img src="https://jmersonuo.github.io/StoryMaps/img/wildernessSymbol.JPG" width ="334px">  

8. Press **Save** again. Close the Map.
9. **Save** the changes to your map.

<img src="https://jmersonuo.github.io/StoryMaps/img/WildSection.JPG" width ="334px">  

## VI. Configure and share your map ##

### 1. Configure ###

Now you've defined all the sections, you can refine your Map Journal's appearance by clicking the **Settings** button at the top of the Builder.

The **Settings** dialog lets you change some layout options, choose a different color scheme (theme), and customize the logo that appears at the top of your story. 

<img src="https://storymaps-classic.arcgis.com/en/app-list/map-journal/img/step9.png" width ="334px">

### 2. Share ###
Once you are happy with the look of your Map Journal, you are ready to share it.

First press the **Save** button in the top right hand corner of the Builder to ensure that all your work is saved. Now press the **Share** button at the top of the Builder. In the dialog that appears, you can share your Map Journal publicly. The dialog will warn you about any issues in your story content that would prevent it from working correctly for your audience. For example it will warn you if any of the data in a publicly shared story map isn't publicly accessible.

Congratulations, your Story Map Journal is now operational!

To make further changes to your Map Journal, you can launch it and click the **Edit** button you'll see in its header. (That button is only present when you are signed in to ArcGIS Online with your account: other people won't see it).

To manage your Map Journal go to [My Stories](https://storymaps-classic.arcgis.com/en/my-stories/). My Stories lists all the story map apps you have created that are hosted in ArcGIS Online. It lets you edit your stories, review their content, check them for issues, upload thumbnails for them, etc. For example you can launch and edit the web maps used in your Map Journal from My Stories to make modifications to them.

<img src="https://storymaps-classic.arcgis.com/en/app-list/map-journal/img/step10.png" width ="334px">


## VII. Advanced set up "story actions" ##

As we mentioned above, you can optionally define "story actions" in the side panel content for a section to provide users with another level of interaction when they read your Map Journal. For example in this [Map Journal example](http://links.esri.com/storymaps/map_journal_example_main_stage_action_popups) story actions have been added to the sections that turn different layers on in the map.

To define a story action in a section, edit the section's side panel text by clicking the blue edit button at the top of the side panel and in the **Edit Section** dialog's **Side Panel** tab, select the text that you want to turn into an action. Now click the first button in the **Story Actions** toolbar. A dialog will appear allowing you to specify what the action will do. Your action can zoom to a location on the web map the section is displaying, turn one or more of its layers on or off, display a popup for one of its features, or a combination of these. You can also switch to a different web map or load an image, video or web page, or navigate to a different section in your Map Journal. Press Apply and then Save when you are done.

Story actions are easy to define but give you great flexibility for engaging users and directing their attention to specific locations on your maps, etc.

<img src="https://storymaps-classic.arcgis.com/en/app-list/map-journal/img/step8.png" width ="334px">
