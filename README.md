#Magento Content Guide

##General Overview
The purpose of this document is to educate on how to update the template pages within the context of the code already written for this project.

To update any given pages in the Content Management System (CMS), head to your base url, followed by /admin, /dmadmin. Once here, enter the appropriate credentials.

##Pages
To create/modify pages go to CMS -> Pages -> Manage Content which is located in the navigation bar..

For either creating or editing pages the following is the same:



**Page Title**: Is the page title which you see in the browser tab

**URL Key**: Here you set the path without the domain prefixed, ex. contact-us would become localhost.com/contact-us

**Store View**: Are used to determine the store you wish for your content to be visible on
- All Store Views: This will show in all stores
- Canada:
	- EN : This will only show in Canada english
	- FR : This will only show in Canada French

```
Note: You may create pages using the same name and have different store views to allow for country/language specific content to be displayed
```

**Status**: Is used to turn the page on / off

**Under Version Control**: Is used to allow all changes to be recorded, every time a change is made. This allows you to go back to older version if needed. 

If you are returning to a page that has already been versioned you will see something like this. Click the link and you will be able to update content again.




**Content Heading**: will be shown on the heading area on the page.

**Content Section**: View Static block section for more details. You may add static blocks to pages using the identifier found within each block; all you need to do is add {{block type="cms/block" block_id="identifier from block goes here"}}



**Keywords**: enter keywords that you wish to have on the page for seo and search engines. ex. books, ebooks, movies, history

**Description**: enter description text that you wish to have on the page for seo and search engines. 

**Inserting Copy/Content**: If the page in question follows a specific design, and is not utilizing static blocks, please follow the instructions indicated in the templates, as they will ensure that the output of the copy/content inserted into the template will be outputted as indicated in the design assets.

As an example, if we have two paragraphs of text that we would like to appear in the browser as: 


	Nullam id dolor id nibh ultricies vehicula ut id elit. Nullam quis risus eget urna mollis ornare vel eu leo. Nullam quis risus eget urna mollis ornare vel eu leo. Duis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Vivamus sagittis lacus vel augue laoreet rutrum faucibus dolor auctor.

	Maecenas faucibus mollis interdum. Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Curabitur blandit tempus porttitor.

Our code in the CMS editor would need to look like:

```
<p>Nullam id dolor id nibh ultricies vehicula ut id elit. Nullam quis risus eget urna mollis ornare vel eu leo. Nullam quis risus eget urna mollis ornare vel eu leo. Duis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Vivamus sagittis lacus vel augue laoreet rutrum faucibus dolor auctor.</p>

<p>Maecenas faucibus mollis interdum. Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Curabitur blandit tempus porttitor.</p>
```

##Static Blocks

To update any given blocks in the Content Management System (CMS), head to your base url (staging = `yoursite.localhost.com`), followed by `/dmadmin`. Once here, enter the appropriate credentials. From here, navigate to CMS (located in the top navigation bar) -> Static blocks.



From here, you will be able to see all the editable static blocks. Select the block that you would like to edit by clicking on it. 

All the code written into the static blocks are written to comply with the designs provided for those individual pages. All copy/content that you wish to insert into the templates **must follow the format indicated in the blocks themselves**. It is a good practice to keep a copy of the code before making any changes as all changes will be directly applied to the site upon saving. In the event something is wrong with your recent update you will have your previous content saved to your computer.



##Editing static block fields

**Block Title**: Is the name of the static block that is used for internal use and will not be seen by any users. The main purpose is to help organize your content.

**Identifier**: Should never be changed as this is for developer use only

**Store View**: Are used to determine the store you wish for your content to be visible on
- All Store Views: This will show in all stores
- Canada:
	- EN : This will only show in Canada english
	- FR : This will only show in Canada French

**Status**: Is used to turn on and off a block

**Content**: This section is one of the more complicated section if you have never used a CMS before. Below are possible content options that you may need



From here, you will be able to see all the editable pages. Select the page that you would like to edit by clicking on it, you will be brought to a new page. You will notice that on the left of this page there is a sidebar with the title “Page Information”. Navigate to the “Content” tab of this sidebar. This will bring you to the “What You See Is What You Get” (WYSIWYG, wiz-ee-wig) editor, which is where all the content you wish to see on the page must be inputted





##Uploading Images
To upload images, first navigate to a section in the template where it is indicated that an image should be place (this has already been accounted for as per the design files). This will be indicated via HTML comments that images should be placed between the lines that read "IMAGE MUST BE BETWEEN THESE TAGS".

Once there, click on the button that reads `Insert Image` in the native editor, which should be just below where you would input the content heading. Now navigate to the file that you would like to appear on your page, either already in the database, or if the file is on your computer click the `Browse Files...` button and navigate to the specific file(s) you would like to upload. Click `Open`, and then `Upload Files`. These files will then be added to the root storage, which means that they are available to be put on the site now.

To actually put them on the site, simply click the image that you would like to see on the page and click the "Insert File" button in the top right corner. This will output something that looks like: `<img src="{{media url="wysiwyg/[imageName]"}}" alt="" />`. Note that image tags are self-closing and therefore do not require a closing tag.

 

Please take a moment to include a brief (3-7 words) of your photo within the quotation marks following the `alt=`. As an example, if you were to upload the Scholastics logo, the tag would look like: `<img src="{{media url="wysiwyg/scholasticsLogo.jpg"}}" alt="Scholastics logo" />`. The alt attribute is very important not only for SEO, but also for those who are visually impaired and require a screen reader.

Where indicated, please include the following attribute to your images: `style=”max-width: 100%;”`. Using the above link as an example, our code will now look like: `<img src="{{media url="wysiwyg/scholasticsLogo.jpg"}}" alt="Scholastics logo" style=”max-width: 100%;” />`.

##Anchors/Links
Should you need to include a link somewhere in your copy, you must follow a very specific format. Similar to paragraphs, all links must be wrapped in an opening (`<a>`), and closing (`</a>`) anchor tag. 

The text in between the opening and closing anchor tags will be what the user sees on the page.

Links, however, absolutely must have an `href` attribute attached to the opening tag. The value for the `href` attribute determines where a given link leads to. 

There are essentially two different formats you should follow for the `href` attribute, depending on where you would like the links to redirect to. These formats will be referred to as “relative” links and “absolute” links. The difference between the two is that relative links direct to somewhere else within the current website (such as the about-us page of the current website), whereas absolute links direct to an address external to the current website (such as Google).


As an example, to get to the contact-us page on yoursite.localhost.com, the correct url would be `yoursite.localhost.com/contact-us`. The problem with simply setting this as the `href` attribute in the CMS editor, is that once the site has gone to production, it will have a different url as the base such as `yoursite.com`.

To circumvent this, we can use a little code for our `href` attribute. Put the code `“{{store url="[PATH TO PAGE]"}}”` as the value of the `href` attribute, replacing `PATH TO PAGE` with the path to the page you want to direct to. Using this (assuming that the base url of our store is yoursite.localhost.com), the following code: `<a href="{{store url="about-us"}}">About Us</a>` will be turned into `<a href=”http://yoursite.localhost.com/about-us”>About Us</a>` before being rendered by browser.

Absolute links, fortunately, are much easier to manage, though they also have a specific format you must follow. Like all links, absolute links require an href attribute to whichever site you wish to redirect to. What’s important for these links is that you include the full url to the website in question. This means that you must include “http://” (which stands for hypertext transfer protocol) before all links, simply setting the href attribute to “google.com” or even “www.google.com” will not suffice, as the browser will simply render it as a string of characters, rather than an address.

Now, for example, if we want to write a link that directs the user to www.google.com, but shows in the browser as “This is a link to Google”, our code will look like <a href=”http://www.google.com>This is a link to Google</a>, and will be rendered in the browser as This is a link to Google.

Similar to images, links can take another attribute that is important both for SEO and for accessibility issues - the “title” attribute. To add this, simply add: title=”[DESCRIPTION]” to your opening anchor tag. Now the code for our link above to Google will look like <a href=”http://www.google.com” title=”Google search engine”>This is a link to Google</a>.

About Us Page
This page follows the pattern of text adjusted to the left on the page, with an image sitting to the right of it. Given that, there are two sections created within the template to accommodate this design. All text should be placed between the tags that indicate “ALL TEXT MUST BE BETWEEN THESE TWO TAGS”. Remember that every individual paragraph within these tags should be between it’s own opening (<p>) and closing (</p>) tags

As per the design, there are some paragraphs (from the design it appears only the first paragraph) that feature text that is both slightly larger and is coloured red. For these particular paragraphs, I have created a specific paragraph tag that has styles applied to it to match the design provided. This particular paragraph tag is indicated within the template, marked beside the opening and closing tags with “opening RED paragraph tag” and “closing RED paragraph tag” commented beside them, respectively.

The image for this page should be inserted between the lines which read “IMAGE MUST BE BETWEEN THESE TAGS”. Once again, please take a moment to fill in the “alt” attribute after you have inserted the image tag.

Contact Us Page
All content inputted in this page template will be rendered before the “Contact Us” header on on the contact-us page.

Any content inputted in the “Content Heading” field in the CMS will be rendered with the same size, colour, and weight as the “Contact Us” header, appearing at the top of the page.

Similarly, any text inputted in the CMS editor will be rendered after the content of the “Content Heading” field (if it is inputted), but before the “Contact Us” header. If there is text to input, please take care to ensure that every paragraph is wrapped in an opening (<p>) and closing (</p>) paragraph tag.

Shipping Policy, Web Privacy Policy, and Terms of Use Pages
These pages follow a simple 1-column layout, and will consist largely (or entirely of text). As with all other pages, the text inputted into the “Content Heading” field in the CMS editor will be outputted as a heading on the page.

As always, any text wish to see in the body of the page must go in the body of the CMS editor, once again, ensuring that each individual paragraph is wrapped in it’s own opening (<p>) and closing (</p>) tag.

Translations

First and foremost, this feature is very powerful and should only be used while in the development stage. This feature is also quite quirky, and for that reason we recommend using Firefox to make these changes. 

As mentioned, this feature should only be used while the site is in development, however, it can be enabled through the admin panel. To do this, log into the admin panel and navigate to System -> Configuration -> Developer (at the bottom of the left-hand menu), and scroll down to the “Translate Inline” tab, and set the “Enabled for Frontend” attribute to yes.

CAUTION: By doing this, you are enabling translations to be change by anyone through the front-end, including people who are simply browsing the site at that time.







To change the text while on the French version of the site, simply navigate to the bottom-left corner of the English site and click on the link that reads “Français”. The page will reload in French.

Developer client restrictions can be used to allow only certain IPs to view the developer options OR your translation text editor options






You will notice that some text areas have a dotted red box surrounding them - these are the areas which you can modify the translation. To modify them, simply hover over the text until a small book icon appears and click on it. 



A modal dialogue box will appear. Simply enter the text you would like to appear in the text field with the label “Custom”.



Press the “Submit” button, and be sure to refresh the page, or you will not see the changes take effect.

As a reminder:

```
Although we absolutely do not recommend doing this while the site is live, if for whatever reason you must change the translation, it can be enabled through the admin panel. To do this, log into the admin panel and navigate to System -> Configuration -> Developer (at the bottom of the left-hand menu), and scroll down to the “Translate Inline” tab, and set the “Enabled for Frontend” attribute to yes.
```

**CAUTION**: By doing this, you are enabling translations to be change by anyone through the front-end, including people who are simply browsing the site at that time.





