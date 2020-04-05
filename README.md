# Australian Government Media Releases
> The purpose of this repository is to track different sources of Australian Government media releases.

RSS is a web feed that can allow agencies and departments to keep the Australian people up to date on what they are doing. RSS feeds for Australian Government media releases are tracked in a CSV file within this repository. OPML files are a common standard for importing and reading RSS feeds.This CSV file can be converted to an OPML file, which can then be imported into the feed reader of your choice. The OPML file is automatically generated by the csv2opml.py converter can be imported into feed readers such as [Feedly](https://feedly.com/) or [Microsoft Outlook](https://support.office.com/en-us/article/import-a-collection-of-rss-feeds-56c8c59d-e6af-4442-a09c-22a7e594a08e).

## Usage

### View recent media releases

The OPML file is frequently updated, however if you wish to ensure you have the latest version of the RSS feeds, you can run the converter. Navigate to the converters folder and run the csv2opml.py script using the below command.
```python
python csv2opml.py ../rss_feeds.csv
```

The newly created file will be available and ready to import into your chosen feed reader.

In Feedly you can upload using [feedly.com/i/cortex](https://feedly.com/i/cortex)

![Feedly upload: Choose OPML file or drag OPML file here](/docs/images/feedly01.PNG)
--------------------
![Feedly upload: New sources successfully added to Feedly from media-release-rss.opml](/docs/images/feedly02.PNG)
--------------------
![Feedly upload: All personal feeds showing newly added media releases](/docs/images/feedly03.PNG)
--------------------
Note: You can view which Australian Government websites the media releases are coming from in the media-release-rss.csv file.

### Update the sources

While we frequently check for feeds that are broken or invalid, things change quickly. If you notice a link that is broken, we encourage you to submit a pull request and the team can confirm and approve your update. If you know of a feed that is available that we don't have, open a pull request and let us know! The `rss_feeds.csv` file can be updated to include any missing or broken Australian Government RSS feeds that contain media releases.

When updating:
1. All fields should be encapsulated in double quotes (") and seperated by a comma (,)
2. Each line should have 3 fields:
    - Portfolio<br />The name of the government portfolio that the feed belongs to.
    - Feed name<br />The name of the individual feed.
    - Feed URL<br />The address of the RSS feed containing the media releases.

The `parsers/rssparser.py` file will read a CSV file containing RSS feeds with all necessary fields, fetch all of the items from each of the feeds and output some of the key details from each item.
```python
python rssparser.py csv_filename
```

## Potential Future development

1. Updates to `rss_feeds.csv` will trigger `csv2opml.py` to be run against it and the resulting OPML file will be updated in the repository.
2. Continuous check developed to validate RSS feeds and alert DTA staff on those feeds that are no longer functional. 
3. OPML file integrated into current Australian Government Media Release service.
4. Subscription service for media releases. Prototype designs can be viewed in the "ui" folder.

![User interface design for subscribing to Australian Government media releases as seen in ui/subscribe.html](/docs/images/ui.PNG)

## Guidance for agencies and departments publishing media releases

Optimising your media releases by including metadata helps to make it more discoverable. This metadata can be used in future developments.

### Benefits of including metadata with your media releases

- Your audience can find your media releases more easily through search engines.
- Third-party aggregators can help their audiences to find your media releases by:
    - delivering content based on their needs
    - providing a summary of the media release
    - providing detailed filtering options
    - highlighting important information

### What metadata to include

- title of media release
- description of content
- key topics addressed 
- publication date
- revised date
- authorised by
- location
- contact details for enquiries

### How to include metadata

Use standard terms to include metadata with each media release. Best practice standards are shown here, using extension values for the HTML meta tag from [the Web Hypertext Application Technology Working Group (WHATWG)](https://wiki.whatwg.org/wiki/MetaExtensions).

Include metadata in the head of the HTML page using these meta tag names:

```html
<!-- title of media release -->
<meta name="dc.title" content="Title of this media release">
<!-- description of content -->
<meta name="description" content="This is a description of the content in the media release.">
<!-- key topics addressed  -->
<meta name="keywords" content="keyword1, keyword2, keyword3, keyword4">
<!-- publication date -->
<meta name="dc.created" content="Tuesday, October 15th, 2019, 9:22 am">
<!-- revised date -->
<meta name="dc.modified" content="Thursday, October 17th, 2019, 11:15 am">
<!-- authorised by -->
<meta name="dc.creator" content="Name of Minister">
<!-- location -->
<meta name="dcterms.coverage" content="Location covered by media release">
<!-- contact details for enquiries -->
<meta name="contact" content="Government agency, email@agency.gov.au">
```

Best practice is to include this data in an RSS feed of your media releases.

## Disclaimer

Guidance provided in this repository is not official policy of the Australian Government or the Digital Transformation Agency. Feeds are not guaranteed to be up to date and any embargoed content available on the feeds is the responsibility of the issuing agency or department.

## Authors

- [Gordon Grace](https://github.com/gordongrace)
- [Toby Harper](https://github.com/tobyfu)
- [Anthony McKerron](https://github.com/anthonymckerron)
- [Igor Nedeski](https://github.com/nedeskiigor)
- [Kate Newbown](https://github.com/kNewbown)
