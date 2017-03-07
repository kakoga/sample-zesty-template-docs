note somewhere that images loaded through the plate do not go through image processing so that you will need to load images the exact dimensions that you desire, and/or else plan on replacing the the images on load. In order for the design that you've created to present exactly as you intend, treating the photos in the plate is the ideal way to go.
**open issue for images loaded through plate not being processed by zesty**

# XML Templating in Zesty.io

## Intro
In this section we'll cover how to create a unique blueprints in Zesty.io. Here I am using blueprint synonymously with design. This article will teach you how to write a blueprint from scratch, focusing on the structure of the Plate.XML file, which creates the basic structure of the site. Secondarily, we'll touch on the Plate-Variables.XML file which creates some of the standard styling for your the site.  

One of the main purposes of building your own template is to create a unique blueprint from which you can quickly build a personal site or multiple sites. Blueprints are composed of a set of files in a repo on GitHub. It must be a repo on GitHub, a repo on BitBucket, or other versioning-ware, will not be compatible.

Templates can be used for everything from a single personal site to quickly build multiple sites quickly, such as franchise sites, retail chains, or independent reseller sites.

## Languages

The plate and plate-variable files are written in XML.

Each view's file extension is .tpl, and is written in HTML and [Parsley](https://developer.zesty.io/parsley-templating/).

The style sheet languages are written in CSS, LESS, and/or SCSS.

Client-side Javascript can also be used.

## Process
To begin writing a blueprint, you'll start with the Plate.xml (or Plate). The Plate will build the skeleton of your site. It creates all fields, pages, datasets, and pagesets. After you finish creating a Plate you can load it into Zesty.io by following these [directions](https://developer.zesty.io/docs/templating/building-a-template-with-github/). The actual process of writing a Plate will be addressed in further detail [below](link here).

After writing the Plate, you'll want to write the Plate-Variables.xml file. This file allows you to create uniform styling for your site, for example, a color scheme, uniform font-size for <p>, <H1>, etc. tags, uniform padding or spacing, and more. We'll cover this in more detail [below](link here).

Once you load your Plate in to Zesty.io, you'll be able to see if there are any errors in your XML. If there are errors, Zesty.io will tell you which lines the error(s) are on. Once you correct them your Plate will load successfully.

From there, you can write CSS/LESS/SCSS rules, Javascript, and fill out all the views  for your site.

## What do you need to get started?

All you need is a [GitHub account](https://github.com/) and a [Zesty.io developer account](https://accounts.zesty.io/)

# Overview of a Template

Each template consists of a set of files. These files consist of a Readme, plate.xml, plate-variables.xml, shield.png (optional), a views folder - which contains all of your views, a js folder - which has all of your javascript libraries, a styles folder - which has all of your CSS, Less, and Scss, and a media folder - which has all of your media. The file structure is as shown below:

**[insert diagram of file structure here]**

# The anatomy of Plate.xml
The Plate.xml file contains the code that creates the structure of your site. When the file is loaded into Zesty.io, it creates all of your pages, fields, datasets, and pagesets.
**[insert photo of how plate's fields relate to what the user sees in config]

## Head
The head of your document contains almost everything that a <head> contains in a typical website. The difference is that with Zesty.io only EXTERNAL links go here. You do not need to link to any internal files. So if you're using external scripts, CDNs, Google Fonts, etc. those links would go here. However, links to files in your Styles and JS folder do not need to be included - they will be compiled when the template loads into Zesty.io.
**[include screen shot of Head with notes]**
## Clippings
Note that this section of the plate is the ONLY section that uses inline CDATA tags. All other sections break out fields into <fields> tag and <items> tag sections.
**[include screen shot of Clippings with notes]**
## Ingredients

## Pages, Datasets, Pagesets
### Pages
**[include screen shot of Pages with notes]**
### Datasets
**[include screen shot of Datasets with notes]**
### Pagesets
**[include screen shot of Pagesets with notes]**

# Standard Structure of a Plate.XML
Plates have a standard structure and with standard language. They must conform to the following structure:
```
<?xml version="1.0"?>
  <plate>
    <head>
      <doctype>html5</doctype>
    </head>
    <clippings>
    </clippings>
    <ingredients>
    </ingredients>
  </plate>
  ```

This is a very simple, high-level overview of the structure of a Plate. In the next section we'll take a deep-dive into nitty-gritty of a Plate.


## Standard Structure of a Plate.XML Deep Dive
```
<plate>
  <head>
    <doctype>html5</doctype>
  </head>
  <clippings>
    ...all fields from Clippings dataset go here. They generally follow this form:
    <field-name name="name_of_field" name_friendly="name_friendly_name"><![CDATA[field text goes here.]]></closing-tag>
    <text name="below_logo_text" name_friendly="Below Logo Text"><![CDATA[]]></text>
  </clippings>
  <ingredients>
    <templateset name="homepage" name_friendly="Homepage" view="homepage" parent_item="some_parent_page">
      <fields>
          <text name="page_title" name_friendly="Page Title" required="1"/>
          <images name="main_image" name_friendly="Main Image" limit="1" />
          <wysiwyg_advanced name="body_text" name_friendly="Body Text" />
      </fields>
      <items>
        <item>

        </item>
      </items>
    </templateset>
      <dataset name="homepage_slides" name_friendly="Homepage Slides" parent_item="zesty_home">
      <fields>
        <text name="custom_field_name" name_friendly="Custom Form Name" required="1" list="1"/>
        <yes_no name="field_type_toggle" name_friendly="Field Type (text: 150 character limit; textarea: unlimited)" options="0:Text;1:Textarea;"  list="1"/>
        <sort name="sort_order" name_friendly="Sort Order" list="1" />
      </fields>
      <items>
        <item>


        </item>
      </items>
    </dataset>
    <pageset name="vet_services" name_friendly="Vet Services" view="vet_services" parent_item="services">
    <fields>
      <text name="page_title" name_friendly="Page Title" required="1" />
      <images name="main_image" name_friendly="Main Image" limit="1" />
      <textarea name="body_text" name_friendly="Body Text" />
      <textarea name="download_form_note" name_friendly="Downloadable Forms Note" />
      <textarea name="embedded_form_instrux" name_friendly="Form Instructions" />
      <dropdown name="default_fields" name_friendly="Default Form Fields" options="no_form:No Form;patient_basic:Patient          Basic;patient_address:Patient Address;patient_address_and_pet_info:Patient address and Pet Info;" />
      <one_to_many name="additional_fields" name_friendly="Additional Form Fields (add additional fields that you've created in the Custom Form   dataset)" relationship="custom_form_fields" relationship_field="custom_field_name" />
      <text name="send_form_to" name_friendly="Send Form To (email address)" required="1" />
    </fields>
    <items>
      <item>

      </item>
    </items>
    </pageset>
  </ingredients>
</plate>
```

parameters are included after `name_friendly="name_friendly_name"`. These include:
`limit="some_number"` - limits the number entries for that field.
`required="1"` - This makes the field required in Zesty.io. The user will be unable to leave this field blank. **[screenshot]** Only add this field to required fields.

## Clippings
Clippings are where you put fields or items that you want available site-wide, for example logos, or contact information.
**[insert a photo of clippings here]**

  ***do I break up the basic structure of the document? maybe do a detailed breakdown of the structure?? so have a larger standard overview and then a more detailed 'deep dive' that covers Templatesets, Pagesets, Fields, Items/Item, Required, Limit, Yes_No, dropdown, etc.?
