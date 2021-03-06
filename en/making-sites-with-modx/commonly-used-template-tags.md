---
title: "Commonly Used Template Tags"
_old_id: "60"
_old_uri: "2.x/making-sites-with-modx/commonly-used-template-tags"
---

- [Default Resource Content Field Tags](#CommonlyUsedTemplateTags-DefaultResourceContentFieldTags)
- [Other Common Tags](#CommonlyUsedTemplateTags-OtherCommonTags)
- [All Tags](#CommonlyUsedTemplateTags-AllTags)
- [See Also](#CommonlyUsedTemplateTags-SeeAlso)



 This page lists the most commonly used MODx Revolution tags as an aid to anyone converting HTML/CSS layouts into MODx [Templates](making-sites-with-modx/structuring-your-site/templates "Templates"). These are frequently referred to as "tags" or "placeholders" (and sometimes "template variables"), so we mention those terms here as an aid to searching, although technically speaking they are **not** placeholders or template variables: they are MODx tags. Yes, it can be confusing for the newcomer, so just remember that there are different flavors of these tags, each with its own purpose and name. Placeholders are set in code and are displayed with placeholder tags. [Template Variables](making-sites-with-modx/customizing-content/template-variables "Template Variables") are extra resource content fields created by the user; they can be thought of as custom fields. Neither placeholders, not template variables are pre-set by the MODx core.

##  Default Resource Content Field Tags 

 In MODx Revolution, each page will always have the following content fields that you can use when constructing your templates. Except for the Resource ID and the parent field, they are all supplied by the user when editing the resource and may be empty if the user did not fill them in:

| Tag | Description | Example Usage |
|-----|-------------|---------------|
| **\[\[\*id\]\]** | the Resource ID of the page (set by MODx when the page is created. | Often used in conjunction with the link syntax, e.g. `<a href="[[~[[*id]]]]">Bookmark this page!</a>` |
| **\[\[\*pagetitle\]\]** | the Title of the page. | `<title>[[*pagetitle]]</title>` |
| **\[\[\*longtitle\]\]** | the Long Title of the page | `<h1>[[*longtitle]]</h1>` |
| **\[\[\*alias\]\]** | the page alias. | _Used to construct the URL of the page_ |
| **\[\[\*description\]\]** | the page Description | `<meta name="description" content="[[*description]]"/>` |
| **\[\[\*introtext\]\]** | the Introductory Text field (a.k.a. the summary). | Often used by Snippets to summarize posts, e.g. [Ditto](/extras/evo/ditto "Ditto")`<div id="summary">[[*introtext]]</div>` |
| **\[\[\*parent\]\]** | the ID of the parent page (if any). Set by MODx when the page is created. Can be altered by the user. | Often used in conjunction with the link syntax, e.g. `<a href="[[~[[*parent]]]]">Up to parent page</a>` |
| **\[\[\*menutitle\]\]** | the Title used when the page appears in menus. | _Most frequently used by Snippets such as_ _[Wayfinder](/extras/evo/wayfinder "Wayfinder")_ _when dynamically constructing menus_ |
| **\[\[\*content\]\]** | the content of the page. | `<body>[[*content]]</body>` |

##  Other Common Tags 

 These tags represent system settings, which are editable under the **System** menu -> **System Settings**.

| Tag | Description | Example Usage |
|-----|-------------|---------------|
| **\[\[++site\_url\]\]** | Contains the URL for your site, e.g. <http://www.yoursite.com/> | With many CMS's that rely on Apache rewrites, it's common practice to include a base tag in your HTML head: `<base href="[[++site_url]]" />` |
| **\[\[++site\_name\]\]** | Name of the site | `<title>[[++site_name]] | [[*pagetitle]]</title>` |
| **\[\[++site\_start\]\]** | Contains the ID of the page designated as your "home" page. | Often used in conjunction with the link syntax, e.g. `<a id="logo" href="[[~[[++site_start]]]]">Home</a>` |
| **\[\[$chunk\]\]** | This references a chunk by name. Chunks are any bit of reusable content. | Common chunks might be for _header_ or _footer_ |
| **\[\[~link\]\]** | Use this syntax to build links to pages by referencing their unique id (visible in parentheses next to the page's name in the resource tree). These links will not break if pages are moved or renamed. You can change the generated scheme of the link by passing the &scheme parameter (see [link\_tag\_scheme](administering-your-site/settings/system-settings/link_tag_scheme)) | `<a id="logo" href="[[~1]]">Home</a>` |
| **\[\[%translated\_message\]\]** | Use lexicon tags to localize messages. | \[\[!%setting\_emailsender? &topic=`setting` &namespace=`core` &language=`en`\]\] |

##  All Tags 

 As you increase your understanding of how MODx templates work, you'll want to have at your disposal the complete list of available content fields. Here is the complete list of all tags, gleaned from this [blog post](http://modxcms.com/forums/index.php/topic,63481.0/topicseen.html).

| Tag | Data Type | Description | Example Usage |
|-----|-----------|-------------|---------------|
| **\[\[\*alias\]\]** | text | Alias | Normally, you will use the _id_ to generate the URL, e.g. `<a href="[[~[[*id]]]]">Click Here!</a>`, but this lets you print out the alias parameter. |
| **\[\[\*cacheable\]\]** | int 0/1 | Cacheable |  |
| **\[\[\*class\_key\]\]** | int | Class Key of the Resource, e.g. _modDocument_ |  |
| **\[\[\*content\]\]** | text | Resource Content |  |
| **\[\[\*content\_type\]\]** | int | Content Type |  |
| **\[\[\*createdon\]\]** | date | Created On date, e.g. _2011-04-14 20:40:50_, often used in conjunction with the _strtotime_ output filter | `[[*createdon:strtotime:date=`%a %b %e, %Y`]]` See [Date Formats](making-sites-with-modx/commonly-used-template-tags/date-formats "Date Formats"). |
| **\[\[\*createdby\]\]** | int | Created By User ID Number |  |
| **\[\[\*deleted\]\]** | int 0/1 | Deleted |  |
| **\[\[\*deletedby\]\]** | int | Deleted By User ID Number |  |
| **\[\[\*deletedon\]\]** | date | Date of Deletions | `[[*deletedon:strtotime:date=`%a %b %e, %Y`]]` See [Date Formats](making-sites-with-modx/commonly-used-template-tags/date-formats "Date Formats"). |
| **\[\[\*description\]\]** | text | Description |  |
| **\[\[\*editedon\]\]** | date | Edited On date, e.g. _2011-04-18 09:06:08_ | `[[*editedon:strtotime:date=`%a %b %e, %Y`]]` See [Date Formats](making-sites-with-modx/commonly-used-template-tags/date-formats "Date Formats"). |
| **\[\[\*editedby\]\]** | int | Edited By User ID number |  |
| **\[\[\*hidemenu\]\]** | int 0/1 | Hide From Menus; this attribute is read by many Snippets, e.g. WayFinder |  |
| **\[\[\*id\]\]** | int | Resource ID | Used frequently to generate links to this page. |
| **\[\[\*introtext\]\]** | text | Summary |  |
| **\[\[\*isfolder\]\]** | int 0/1 | Container |  |
| **\[\[\*link\_attributes\]\]** | text | Link attributes; these are inserted automatically when you use the \[\[~123\]\] syntax |  |
| **\[\[\*longtitle\]\]** | text | Long Title |  |
| **\[\[\*menuindex\]\]** | int | Menu Index |  |
| **\[\[\*menutitle\]\]** | text | Menu Title |  |
| **\[\[\*pagetitle\]\]** | text | Page Title |  |
| **\[\[\*parent\]\]** | int | Parent Resource |  |
| **\[\[\*pub\_date\]\]** | date ---Publish Date |  |
| **\[\[\*published\]\]** | int 0/1 | Published |  |
| **\[\[\*publishedby\]\]** | int | Published By User ID Number |  |
| **\[\[\*publishedon\]\]** | date | Published On | `[[*publishedon:strtotime:date=`%a %b %e, %Y`]]` See [Date Formats](making-sites-with-modx/commonly-used-template-tags/date-formats "Date Formats"). |
| **\[\[\*richtext\]\]** | int 0/1 | Rich Text |
| **\[\[\*searchable\]\]** | int 0/1 | Searchable |  |
| **\[\[\*template\]\]** | int | Template ID number |  |
| **\[\[\*unpub\_date\]\]** | date – Unpublish Date | `[[*unpub_date:strtotime:date=`%a %b %e, %Y`]]` See [Date Formats](making-sites-with-modx/commonly-used-template-tags/date-formats "Date Formats"). |
| **\[\[\*uri\_override\]\]** | int 0/1 | Freeze URI |  |
| **\[\[\*uri\]\]** | string | URI |  |

 Just to clarify on pub\_date – it's only set when the user sets a future date for publication in the Publish On field. And when the doc is actually published, it's zeroed out.  The publishedon field always contains the most recent date that the resource changed form unpublished to published (or the date a new doc was saved with Publish checked).



##  See Also 

- [Date Formats](making-sites-with-modx/commonly-used-template-tags/date-formats "Date Formats") : shows how to format date fields.

1. [Resources](making-sites-with-modx/structuring-your-site/resources)
  1. [Content Types](making-sites-with-modx/structuring-your-site/resources/content-types)
  2. [Named Anchor](making-sites-with-modx/structuring-your-site/resources/named-anchor)
  3. [Static Resource](making-sites-with-modx/structuring-your-site/resources/static-resource)
  4. [Symlink](making-sites-with-modx/structuring-your-site/resources/symlink)
      1. [Using Resource Symlinks](making-sites-with-modx/structuring-your-site/resources/symlink/using-resource-symlinks)
  5. [Weblink](making-sites-with-modx/structuring-your-site/resources/weblink)
2. [Templates](making-sites-with-modx/structuring-your-site/templates)
3. [Chunks](making-sites-with-modx/structuring-your-site/chunks)
4. [Using Snippets](making-sites-with-modx/structuring-your-site/using-snippets)