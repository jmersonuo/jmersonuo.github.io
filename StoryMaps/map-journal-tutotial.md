
# Story Map Journal Tutorial #
Adapted from [arcgis.com](https://storymaps-classic.arcgis.com/en/app-list/map-journal/tutorial/) for Geog 410/510 Stroies and Maps, Feb 13, 2020

Joanna Merson and Marcel Brousseau

---
The stepts for creating your story map are to:

<ol type="I">
  <li>State the "story" goal </li>
  <li>Pick a format (“App”) see handout </li>
  <li>Add a title and your first section </li>
  <li>Add text and an image </li>
  <li>Customize the map</li>
  <li>
    <ol type="i"> 
      <li>Change the basemap</li>
      <li>Add data manually (add points from the novel)  </li> 
      <li>Search for data (something relevant to the novel) </li> 
    </ol>
  </li>
  <li>Define "story actions" </li>
  <li>Configure and share your map/li> 
</ol>

## I. State the story goal ##
What is the goal of your "story"? Do you want to provide photos or recordings for different locations? Do you want to convey distance? Do you want to creat an experienctial version of a journey?

## II. Pick a format ##

There are several Esri StoryMaps "Classic" formats that you can follow. Here is a flowchart to help you decide which is best for your story.  *For this demo, we will use **Story Map Journal**.*

**Getting started**

In this tutorial you'll use an interactive Story Map Journal℠ Builder to author your journal entries, which we call sections. For each section you'll specify the web map, image, video or other web content that you want your Map Journal to display when your users reach that section, and how you want that content to be displayed.

For example, you might choose to display the same web map throughout your Map Journal, and have each section automatically zoom to a different area on that map. Or you may author your Map Journal so that it takes your users through multiple web maps, and associated images and videos, as they read through the sections. Lots of different combinations are possible.

You can use any ArcGIS Online web maps in your Map Journal: you can create new web maps, use your existing web maps, or use web maps that have been created and shared publicly by other users or organizations.

If you'll be creating one or more new web maps for use in your Map Journal, you can either create them in [ArcGIS Online](http://www.arcgis.com/home/)  before you start building your Map Journal, or you can create them on-the-go within the Map Journal Builder. From within the Builder, you can also edit web maps that you own. After you have created your Map Journal, you can continue to work on your maps to refine their content, symbology, and popups.


### 1 ###
Start the [Story Map Journal Builder](https://uo-online.maps.arcgis.com/apps/MapJournal/index.html?fromScratch). You can use a free, non-commercial ArcGIS public account or an ArcGIS subscription account.

Alternatively, you can start in the ArcGIS Online website, open the web map you want to use in your Map Journal, or any one of the web maps if you intend to use several, share it as a web application, and then choose Story Map Journal from the application gallery. The Map Journal Builder will launch so you can configure the application.   

### 2 ###
In the dialog that appears when the Map Journal Builder starts, choose the layout you would like to use and press Start. In this tutorial we'll use the default Side Panel layout but the steps are the same for the Floating Panel layout. <img src="https://storymaps-classic.arcgis.com/en/app-list/map-journal/img/step2.png" width ="334px"> 

## III. Add a title and your first section ##
### 1. Title ###
Enter a title for your Map Journal. You can also take an optional quick tour of the Builder at this point.  
<img src="https://storymaps-classic.arcgis.com/en/app-list/map-journal/img/step3.png" width ="334px">

Our title is:
> A journey within The Devil's Highway

### 2. Home section ###
The dialog will appear that lets you add the first entry, the "home section", into your Map Journal. The home section is the first section your users will see when they open your Map Journal, so it serves as the introduction.

In this dialog, you are first prompted for the content you want this section to show in the "main stage": the main area of the display to the right of the side panel. Choose between a Map, Image, Video or Web page.

We are going to use a web map, which is the default option, click the Map dropdown and choose the option to **create a new map**. When you create a new map, the map editor window will appear. Zoom to the areas you plan to use, then save and close your new map. We'll come back and edit it later. 

You will then be given the options, shown in the screenshot **below**, to customize how the map is displayed. You can choose to display a particular area of the map, turn layers on or off, display a particular feature's popup, or any combination of those. For example if you choose a custom location, the Builder will prompt you to interactively zoom to the area you want to use, and then you'll press a button to capture that extent. We will come back and edit this later.  
  
Press Next to add your first content.  
  
<img src="https://storymaps-classic.arcgis.com/en/app-list/map-journal/img/step4.png" width ="334px">

### 1. Opening text ###
The Add Home Section dialog will now prompt you to enter and format the content that will appear in the side panel for the home section. You can type directly into the built-in rich text editor. You can also paste text into the editor from word processing programs in which case the formatting is carried over into the editor. You can also embed graphics, images and videos in with the text. You can also define "story actions" in the section's text so that, for example, clicking a word automatically zooms the main stage's map to a particular location. (We'll show you how to set up these actions in step **8** below).

We will use the following text:
>In May 2001, a group of men attempted to cross the Mexican border into the desert of southern Arizona, through the deadliest region of the continent, the "Devil's Highway." Three years later, Luis Alberto Urrea wrote about what happened to them. 
> Scroll down to follow their journey.

Press Add. Your completed home section will now appear in your Map Journal.  

<img src="https://storymaps-classic.arcgis.com/en/app-list/map-journal/img/step5.png" width ="334px">

To save your work so far, press the Save button in the top right hand corner of the Builder.  

## IV. Add another section: text and an image ##

### 1. Add a section ###
Use the Add Section button at the bottom of the side panel to add additional sections into your Map Journal. The same dialog will appear each time you add a section allowing you to specify the content for the main stage and the side panel.

To make edits or other changes to a section you've added, click the blue edit button at the top of the side panel.

You can use the Organize button to reorder and delete sections.

<img src="https://storymaps-classic.arcgis.com/en/app-list/map-journal/img/step7.png" width ="334px">

Title:
> Cabeza Prieta Wilderness 

Set the custom location to the Cabeza Prieta Wilderness and the press next.

I am going to add a short peice of text:
> We begin in the Cabeza Prieta Wilderness. A beautiful piece of land along the US/Mexico border.

### 2. Add an image ###

Click camera icon to insert an image. You could use images stored on a fliker account or add an image from a link using an iframe. To do this you can insert the URL of an image into the code block below.

Link:
`<iframe src="https://winapps.umt.edu/winapps/media2/wilderness/images/NWPS/lib/thumbID250/4246.jpg"></iframe> `

Alternitive text: 
> Photo of the Cabeza Prieta Wilderness

Add a caption under the photo - size 9, dark grey: 
> Cabeza Prieta Wilderness (Credit: NPS)


## V. Customize the map ##

Now that we know how to add sections, let's look at editing the map.
Go back to the top (Main Stage) and click the pencil to edit the section. Now click "edit" besode the map title.

In the map editor you can customize the maps that used in your story.
### 1. Change the basemap ###

As a novice cartographer, select one of the 12 provided basemaps. For this demo, we are going to choose "terrain", to emphasise the topography, while maintaining a neutral background that our data points will stand out on.

In the furutre, you can learn how to [customize](https://www.esri.com/arcgis-blog/products/developers/mapping/design-custom-basemaps-with-the-new-arcgis-vector-tile-style-editor/) basemaps.

<img src="https://www.esri.com/arcgis-blog/wp-content/uploads/2018/05/vse-1920x1080.png" height ="300px">

### 2. Add data manually (add points from the novel) ###

1. Click "Add" > "Add Map Notes". You can change the name of they layer. I am not going to. The templates will give you different map symbols to choose from. I am going to leave it with the default, "Map Notes".  
2. Click on a template from the Add Feature's menu. Notice that you can create features that are point, line, and area types. We are going to use a point feature using "Stickpin".   
3. Pan and zoom to the desired location and click on the map to add a pin.  
4. Set the pin's title and desscription. You can even add an image here. The map is interactive, so you are adding information that will exist in a popup on the pin.  
5. Optionally change the symbol. Notice there are *dozens* of options to choose from.  
6. Save the map.   

### 3. Search for data (something relevant to the novel) ###

1. Click "Add" > "Browse Living Atlas Layers". ArcGIS Living Atlas of the World is a collection of global geographic information. Curated by Esri with contributions from its partner and user communities, Living Atlas contains valuable maps, data layers, tools, services, and apps for geographic analysis.  
2. Search for "township and range".  
3. Click the + to add the PLSS data to the map.
4. Save and close the map. Press Save again.

Notice that your edits to the map persist when you scroll up and down the map/


## VI. Define "story actions" ##

As we mentioned above, you can optionally define "story actions" in the side panel content for a section to provide users with another level of interaction when they read your Map Journal. For example in this [Map Journal example](http://links.esri.com/storymaps/map_journal_example_main_stage_action_popups) story actions have been added to the sections that turn different layers on in the map.

To define a story action in a section, edit the section's side panel text by clicking the blue edit button at the top of the side panel and in the Edit Section dialog's Side Panel tab, select the text that you want to turn into an action. Now click the first button in the Story Actions toolbar. A dialog will appear allowing you to specify what the action will do. Your action can zoom to a location on the web map the section is displaying, turn one or more of its layers on or off, display a popup for one of its features, or a combination of these. You can also switch to a different web map or load an image, video or web page, or navigate to a different section in your Map Journal. Press Apply and then Save when you are done.

Story actions are easy to define but give you great flexibility for engaging users and directing their attention to specific locations on your maps, etc.

<img src="https://storymaps-classic.arcgis.com/en/app-list/map-journal/img/step8.png" width ="334px">

## VII. Configure and share your map ##

Now you've defined all the sections, you can refine your Map Journal's appearance by clicking the Settings button at the top of the Builder.

The Settings dialog lets you change some layout options, choose a different color scheme (theme), and customize the logo that appears at the top of your story. Using your own logo is important because it adds authority to your story and shows people who created it. Your organization's logo and color scheme may already be reflected in your story if they have been set as defaults by your ArcGIS account administrator (this option is only available if you are using an ArcGIS subscription account). Be sure to specify a URL that your readers will be taken to when they click your logo, so they can find out more about your organization.

<img src="https://storymaps-classic.arcgis.com/en/app-list/map-journal/img/step9.png" width ="334px">

Once you are happy with the look of your Map Journal, you are ready to share it.

First press the Save button in the top right hand corner of the Builder to ensure that all your work is saved. Now press the Share button at the top of the Builder. In the dialog that appears, you can share your Map Journal publicly, or, if you're using an ArcGIS subscription account, you'll also see the option to share your Map Journal so it is accessible only within your organization. The dialog will warn you about any issues in your story content that would prevent it from working correctly for your audience. For example it will warn you if any of the data in a publicly shared story map isn't publicly accessible.

Congratulations, your Story Map Journal is now operational!

To make further changes to your Map Journal, you can launch it and click the Edit button you'll see in its header. (That button is only present when you are signed in to ArcGIS Online with your account: other people won't see it).

To manage your Map Journal go to My Stories. My Stories lists all the story map apps you have created that are hosted in ArcGIS Online. It lets you edit your stories, review their content, check them for issues, upload thumbnails for them, etc. For example you can launch and edit the web maps used in your Map Journal from My Stories to make modifications to them.

<img src="https://storymaps-classic.arcgis.com/en/app-list/map-journal/img/step10.png" width ="334px">
