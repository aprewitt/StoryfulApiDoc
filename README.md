h1. Storyful API Documentation

The Storyful API provides read access to a variety of Storyful data. This documentation is not exhaustive but outlines the main methods and how to use the API.

Contact support@storyful.com with any questions or issues.

h2. Base

@api.storyful.com@

h2. Version

The current, and only, version of the Storyful API is @1@. You may include the version in request URLs e.g.
@http://api.storyful.com/v1/stories@

h2. HTTPS/HTTP

HTTP and HTTPS is supported.

h2. XML and JSON

The default response type is JSON. XML can be returned by appending .xml to your requests e.g.
@http://api.storyful.com/stories.json@

h2. Authentication

Contact support@storyful.com for your 32 character permanent access token. This token must be provided with all requests to private data. Use the @access_token@ parameter e.g.
@https://api.storyful.com/stories?access_token=zt218bq3zw67316b7wj789012l56p012@

(Please note that @zt218bq3zw67316b7wj789012l56p012@ is not a functioning access token and is only used as an example in this documentation.)

h2. Common response concepts

Responses may contain these often used entities.

h3. Paging

pre. per_page: @integer@,

@per_page@ is how many items per page are returned. This can be controlled by using the @per_page@ parameter in your request.

pre. previous: @url@,
next: @url@,

@previous@ and @next@ provide URLs to the next or previous page of results. @null@ if there is no next or previous page.

pre. page: @integer@,
total_pages: @integer@,
total_items: @integer@,

@total_pages@ is the @total_items@ divided by @per_page@.

h3. Request entity

Each response contains a @request@ entity describing your request.

pre. request: {
  url: @url@,

The full URL of your request.

pre.   status: @integer@
}

The @status@ can be one of these HTTP status codes; @200@ (OK), @404@ (Not Found) or @403@ (Forbidden).

h2. Methods

h3. Stories

A list of @story@ items created by authorised users orderded descending by @updated_at@.

e.g. @http://api.storyful.com/stories@

pre. stories: [*list of @story@ items*]

h3. Story

A @story@ item represents a collection of @story_items@ and metadata created by an authorised user.

e.g. @http://api.storyful.com/stories/41414@

pre. story: {
  id: 41414,
  resource_url: "/stories/41414",

The canonical resource URL of the @story@.

pre.   html_resource_url: "http://storyful.com/stories/41414?feature=embedded",

The @html_resource_url@ is the URL you can use to embed the story using an iframe in another HTML document.

pre.   short_url: "http://stryfl.com/10us",

The @short_url@ is the short URL for the @story@.

pre.   story_items_resource_url: "/stories/41414/story_items",

The @story_items_resource_url@ is the URL of the @story_items@ for this @story@.

pre.   title: "Mexicans storm social media over missing blogger ",

The @title@ is the complete title for the @story@ including @title_clean@, @title_slug@, @clearance_text@, @guidance_text@ and @title_date@.

pre.   title_clean: "Mexicans storm social media over missing blogger ",

The @title_clean@ is the clean title as entered by the author of the @story@.

pre.   title_slug: "MEXICO",

The @title_slug@ is the slug of the @story@ e.g. @MEXICO@.

pre.   clearance_text: "The content in this entry is provided (by an NGO/activist/public body) for public dissemination and rebroadcast. It may be used freely with credit.",

The @clearance_text@ is the text as entered by the @author@ on the clearance status of the @story@.

pre.   guidance_text: "Be advised the content is graphic",

The @guidance_text@ is th text as entered by the @author@ on the guidance advise for the @story@.

pre.   rights_text: "A claim was successful.",

The @rights_text@ is the text as entered by the @author@ on the rights status of the @story@.

pre.   redistribution_text: "This content is provided via a media organisation. Please contact them directly to ascertain redistribution rights.",

The @redistribution_text@ is the text as entered by the @author@ on the redistribution status of the @story@.

pre.   title_clearance: "PUBLIC",

The @title_clearance@ is the clearance status of the @story@.

pre.   title_guidance: "GRAPHIC",

The @title_guidance@ is the guidance status of the @story@.

pre.   title_rights: "SUCCESSFUL",

The @title_rights@ is the rights status of the @story@.

pre.   title_redistribution: "NO",

The @title_redistribution@ is the rights status of the @story@.

pre.   title_date: "2012-09-15",

The @title_date@ is the main date as ented by the @author@ of the events portrayed in the @story@.

pre.   summary: "<p>Mexican activists took to Twitter on Friday looking for information about a popular activist blogger who they claim disappeared earlier this month. According to <a href="http://www.el5antuario.org/">his own blog</a>, El 5anto, also known as Ruy Salgado, has not been seen since September 8. In June of this year, he <a href="http://storyful.com/stories/33381M">claimed the Mexican government was coming for him</a> and asked fans to keep his blog El 5antuario going if he disappeared.</p>",

The @summary@ is the text as entered by the @author@ of the @story@ summarising it.

pre.   location: "19.000,99.000",

The @location@ is the text as entered by the @author@ of the @story@ locating the story. Can be any location format but usually a lattitude,longitude pair.

pre.   created_at: "2012-09-15T01:31:57Z",
  updated_at: "2012-09-15T05:27:32Z",

The date the @story@ was created and updated.

pre.   published_at: "2012-09-15T05:27:04Z",

The date the @story@ was last published. A @story@ can be unpublished and republished.

pre.   lead_image: {
    original_filename: null,
    variants: {
      original: "https://storyful.s3.amazonaws.com/production/stories/41414/original.jpg",
      large: "https://storyful.s3.amazonaws.com/production/stories/41414/large.jpg",
      index_main: "https://storyful.s3.amazonaws.com/production/stories/41414/index_main.jpg",
      index: "https://storyful.s3.amazonaws.com/production/stories/41414/index.jpg",
      standard: "https://storyful.s3.amazonaws.com/production/stories/41414/standard.jpg",
      index_small: "https://storyful.s3.amazonaws.com/production/stories/41414/index_small.jpg",
      smallest: "https://storyful.s3.amazonaws.com/production/stories/41414/smallest.jpg"
    }
  },

The @lead_image@ is a set of images from the lead @story_item@ in the @story@. Useful as a thumbnail for the @story@.

pre.   lead_video: {
    type: "ItemYoutube",
    owner_name: "el5antuario",
    owner_link: "https://www.youtube.com/channel/UC3llShwM5OB1GGur_vuJRsA",
    owner_id: "el5antuario",
    resource_id: "Nx6Nb57zcdQ"
  },

The @lead_video@ is the video, YouTube only, taken from the lead @story_item@ in the story.

pre.   primary_tag: {*@tag@ item*},

The @primary_tag@ is the primary @tag@ assigned to the @story@.

pre.   tags: [*list of @tag@ items*],

The @tags@ assigned to the @story@ by an authorised user.

pre.   channels: [*list of @channel@ items*],

The @channels@ the @story@ is assigned too.

pre.   contacts: [*list of @contact@ items*],

The @conacts@ associated with the @story@.

pre.   author: {
    resource_url: "/authors/fionamccann",
    pro2: true,
    updated_at: "2013-01-06T22:37:57Z",
    created_at: "2011-01-24T10:12:38Z",
    name: "Fiona McCann",
    photo: {
      variants: {
      original: "https://storyful.s3.amazonaws.com/production/users/43/fionamccann-original.png",
      medium: "https://storyful.s3.amazonaws.com/production/users/43/fionamccann-medium.png",
      small: "https://storyful.s3.amazonaws.com/production/users/43/fionamccann-small.png",
      standard: "https://storyful.s3.amazonaws.com/production/users/43/fionamccann-standard.png"
      }
    },
    username: "fionamccann"
  },

The @author@ of the @story@. 

pre.   story_items: [*list of @story_item@ items*]
}

A list of @story_items@ for the @story@.

h3. Story Items

A list of @story_item@ items ordered descending by @updated_at@.

e.g. @http://api.storyful.com/story_items/@

pre. story_items: [*list of @story_item@ items*]

h3. Story Item

A @story_item@ represents some content added to a @story@ by an authorised user.

The @story_item@ comes in many types with a variety of optional properties. Documented are the common properties.

e.g. @http://api.storyful.com/story_items/1988753@

pre. story_item: {
  id: 1988753,
  resource_url: "/story_items/1988753",

The canonical resource URL of the @story_item@.

pre.   story_resource_url: "/stories/41414",

The resource URL of the @story@ this @story_item@ belongs to.

pre.   embed_code: null,

If the @story_item@ is a generic embed provided by the @author@ of the @story@ then the entered embed text goes here.

pre.   owner_name: "el5antuario",
  owner_link: "http://www.youtube.com/user/el5antuario",

The @owner_name@ and @owner_link@ of the @story_item@ as provided by the source network.

pre.   resource_type: "",

The @resource_id@ of the @story_item@ if provided.

pre.   resource_id: "TJgCb2YE3gU",

The ID of the @story_item@ from the source network.

pre.   body: null,

The @body@ text of the @story_item@ provided by the @author@ of the @story@.

pre.   location: "",

The @location@ of the @story_item@ as provided by the @author@ of the @story@. Can be different to the @story@ @location@. Usually lattitude,longitude pair.

pre.   type: "ItemYoutube",

The @story_item@ @type@.

pre.   created_at: "2012-09-15T01:50:28Z",
  updated_at: "2012-09-15T05:20:53Z",

The date the @story_item@ was created and updated.

pre.   editorial_before: true,

The @editorial_before@ specifies whether the @editorial_content@ should be shown before or after the @story_item@.

pre.   editorial_content: "El 5anto rose to prominence in the run up to the country's July elections, as a voice highly critical both of the way the elections were run and of the eventual victor and incoming president Enrique Peña Nieto. He created the blog "El 5antuario":http://www.el5antuario.org/ as a group project that would "locate all the valuable information we find and analyze it based on data that the government and self-censored media organizations religiously continue to hide." He also amassed "over 48,000 Twitter followers":https://twitter.com/el5anto, and published videos and interviews in which he always wore a mask to disguise his identity. In a video put out by his fellow bloggers at El 5antuario on Friday, it was announced that on "September 8 at around 11.02 pm, with one hour still to go to finish transmission, we lost contact with our friend Ruy Salgado." The video goes on to say that Salgado was expected to attend a rally called by left-wing opposition leader Andres Manuel Lopez Obrador in Mexico's Zocalo square the next day, but failed to show up:",
}

The @editorial_content@ text as entered by the @story@ @author@.

h3. Channels

A list of @channel@ items. @stories@, @lists@, @contacts@ and @tags@ can be accesed by @channel@.

Calling this method with an @access_token@ will list @channels@ available to the user.

e.g. @http://api.storyful.com/channels@

pre. channels: [*list of @channel@ items*]

h3. Channel

A @channel@ respresents a grouping of various items. Authorised users manually assign items to @channels@.

e.g. @http://api.storyful.com/channels/1@

pre. channel: {
  id: 1,
  resource_url: "/channels/1",

The canonical resource URL of the @channel@.

pre.  title: "Standard",

The @title@ for display for the @channel@.

pre. subscription: "standard"
  }
The @subscription@ type for the @channel@. Can be @standard@, @pro@ or @system@.

h4. Channel/Stories

@channels/stories@ returns @stories@ assigned to the @channel@.

e.g. @http://api.storyful.com/channels/1/stories@

pre. stories: [*list of @story@ items*]

h4. Channel/Contacts

@channels/contacts@ returns @contacts@ assigned to the @channel@.

e.g. @http://api.storyful.com/channels/1/contacts@

pre. contacts: [*list of @contact@ items*]

h4. Channel/Lists

@channels/lists@ returns @lists@ assigned to the @channel@.

e.g. @http://api.storyful.com/channels/1/lists@

pre. lists: [*list of @list@ items*]

h4. Channels/Tags

@channels/tags@ returns @tags@ assigned to any @stories@, @lists@ or @contacts@ assigned to the @channel@.

e.g. @http://api.storyful.com/channels/1/tags@

pre. tags: [*list of @tag@ items*]

h3. Authors

A list of @author@ items ordered by @updated_at@ in descending order.

e.g. @http://api.storyful.com/authors@

pre. authors: [*list of @author@ items*]

h3. Author

The @author@ represents a user in the system. A @story@ always has an @author@.

e.g. @http://api.storyful.com/authors/855@

pre. author: {
  resource_url: "/authors/paulmwatson",

The canonical resource URL of the @author@.

pre.   updated_at: "2013-02-18T15:47:10Z",
  created_at: "2011-05-03T15:53:42Z",

The date the @author@ was updated and created.

pre.   name: "Paul M. Watson",
  bio: "CTO of Storyful in Dublin, Ireland. Loves cricket, rugby & braai food, born and bred in South Africa.",

The self-provided @name@ and @bio@ of the @author@

pre.   photo: {
    variants: {
      original: "https://storyful.s3.amazonaws.com/production/users/855/PaulAv-original.jpg",
      medium: "https://storyful.s3.amazonaws.com/production/users/855/PaulAv-medium.jpg",
      small: "https://storyful.s3.amazonaws.com/production/users/855/PaulAv-small.jpg",
      standard: "https://storyful.s3.amazonaws.com/production/users/855/PaulAv-standard.jpg"
    }
  },

The various sizes of the self-provided @photo@ of the @author@

pre.   username: "paulmwatson",

The @username@ of the author used by the system.

pre.   social_links: {
    google: "https://profiles.google.com/paulmiwatson/",
    twitter: "paulmwatson",
    facebook: "http://facebook.com/paulmwatson",
    youtube: "http://www.youtube.com/paulmwatson",
    flickr: "http://www.flickr.com/photos/paulwatson/",
    blogger: "http://blogger.com/paulmiwatson"
  }
}

The self-provided @social_links@ for the @author@.

h4. Author/Stories

@authors/stories@ returns @stories@ owned by the @author@. Ownership can change in the life of a @story@ but is not surfaced by the API.

e.g. @http://api.storyful.com/authors/855/stories@

pre. author: {
  ...
  stories: [*list of @story@ items*]
}

h3. Lists

A list of @list@ items ordered by @updated_at@ in descending order.

e.g. @http://api.storyful.com/lists@

pre. lists: [*list of @list@ items*]

h3. List

A @list@ represents a collection of Twitter users. The @list@ can be imported from Twitter and may remain synchronised but can also be a combination of Twitter lists or not have a Twitter list at all. There is no 500 Twitter user limit for Storyful @lists@.

e.g. @http://api.storyful.com/lists/736@

pre. list: {
  id: 736,
  resource_url: "/lists/736",

The canonical resource URL of the @list@.

pre.   title: "Celebrities",

The @title@ provided by the creator of the list.

pre.   has_analysis: true,

Whether or not the @list@ has analysis information available. Can be @false@ or @true@.

pre.   description: "Celebrity News",

The @description@ provided by the creatoror of the list. Often a reference to the list on Twitter.

pre.   channels: [
    {
      id: 84,
      resource_url: "/channels/84",
      title: "Storyful Favourites",
      subscription: "standard"
    }
  ],

The @channels@ the @list@ has been assigned too.

pre.   tags: [
    {
      id: "culture",
      resource_url: "/tags/culture",
      label: "Culture",
      description: null,
      last_used_at: "2013-02-01T12:23:18Z",
      parent: null
    }
  ],

The @tags@ that have been assigned to the @list@.

pre.   primary_tag: {
    id: "culture",
    resource_url: "/tags/culture",
    label: "Culture",
    description: null,
    last_used_at: "2013-02-01T12:23:18Z",
    parent: null
  },

The @primary_tag@ assigned to the @list@.

pre.   created_at: "2012-03-28T14:46:00Z",
  updated_at: "2013-02-19T09:17:41Z"
}

The date the @list@ was updated and created.

h4. List/Members

@lists/members@ returns the Twitter users assigned to the @list@.

e.g. @http://api.storyful.com/lists/736/members@

pre. members: [*list of @member@ items*]

h4. List/Analysis

@lists/analysis@ returns a variety of content mentioned by @members@ on Twitter in the @list@.

It takes two, required parameters.

@metric@ can be one of @video@, @links@, @photo@, @active@, @mentioned@, @keywords@, @product@, @company@, @country@ and @city@.

@interval@ can be one of @hourly@ (60 minutes), @daily@ (24 hours), @weekly@ (7 days).

The @interval@ is a rolling time period. So @hourly@ would be from the point you make the request back 60 minutes. Not on the hour.

Using a combination of @metric@ and @interval@ you can return a range of content extracted from a list. The results are ordered by most mentioned from the core list of @members@ in the @list@ as well as a set of 2nd degree users in the network.

The response is flexible in the structure depending on the @metric@ used and the source of the content.

Also included in the response is:
pre. start: 201302191417,
end: 201302191318,

@start@ and @end@ denote the time period of the requested analysis, controlled by @interval@.

e.g. @http://api.storyful.com/lists/736/analysis?metric=video&interval=hourly@

pre. video: [
  {
    _id: "51228ed000648b48a200242d",
    content_type: "video",
    created: 1361219280,
    description: "Share your videos with friends, family, and the world",
    domain: "youtube.com",
    embed: [
      {
        provider_url: "http://www.youtube.com/",
        title: "Elizabeth Warren EMBARRASSES Bank Regulators At First Hearing",
        type: "video",
        html: "<iframe width="460" height="259" src="http://www.youtube.com/embed/2F6YkBa_Tig?feature=oembed" frameborder="0" allowfullscreen></iframe>",
        author_name: "Les Grossman",
        height: 259,
        width: 460,
        version: "1.0",
        thumbnail_width: 480,
        thumbnail_height: 360,
        fixed: false,
        thumbnail_url: "http://i3.ytimg.com/vi/2F6YkBa_Tig/hqdefault.jpg",
        provider_name: "YouTube",
        provider_domain: "youtube.com",
        author_url: "http://www.youtube.com/user/LesGr0ssman"
      },
      {
        provider_url: "http://www.youtube.com/",
        handler: "embedly",
        description: "warren bank hearing | Warren questioned top regulators from the alphabet soup that is the nation's financial regulatory structure: the FDIC, SEC, OCC, CFPB, CFTC, Fed and Treasury. Elizabeth Warren is the truth!!!! show your support http://www.warren.senate.gov/ The Democratic senator from Massachusetts had a straightforward question for them: When was the last time you took a Wall Street bank to trial?",
        title: "Elizabeth Warren EMBARRASSES Bank Regulators At First Hearing",
        url: "http://www.youtube.com/watch?v=2F6YkBa_Tig",
        type: "video",
        author_name: "Les Grossman",
        height: 117,
        width: 208,
        html: "<iframe width="208" height="117" src="http://www.youtube.com/embed/2F6YkBa_Tig?feature=oembed" frameborder="0" allowfullscreen></iframe>",
        thumbnail_width: 480,
        version: "1.0",
        provider_name: "YouTube",
        thumbnail_url: "http://i3.ytimg.com/vi/2F6YkBa_Tig/hqdefault.jpg",
        thumbnail_height: 360,
        provider_domain: "youtube.com",
        author_url: "http://www.youtube.com/user/LesGr0ssman"
      }
    ],
    fixed: false,
    title: "Elizabeth Warren EMBARRASSES Bank Regulators At First Hearing",
    uri: "http://www.youtube.com/watch?feature=player_embedded&v=2F6YkBa_Tig"
  }
]

h3. Contacts

A list of @contact@ items ordered by @updated_at@ in descending order.

e.g. @http://api.storyful.com/contacts@

pre. contacts: [*list of @contact@ items*]

h3. Contact

A @contact@ represents a collection of information curated by authorised users.

e.g. @http://api.storyful.com/contacts/48798@

pre. contact: {
  id: 48798,
  resource_url: "/contacts/48798",

The canonical resource URL of the @contact@.

pre.   name: "Paul Watson",
  email: "paul.watson@storyful.com",
  youtube_name: "paulmwatson",
  twitter_name: "paulmwatson",
  skype: "paulmwatson",
  facebook_url: "http://facebook.com/paulmwatson",
  facebook_name: "Paul Michael Watson",
  google_plus_link: "https://plus.google.com/116567234848098671929/",
  google_plus_name: "Paul Watson",
  organization: "Storyful",
  title: "Mr.",
  website_url: "http://paulmwatson.com",
  links: "",
  phone_number: "+353 86 896 8944",
  location: "Dublin, Ireland",
  notes: "Web developer and CTO at Storyful",
  language: "English, Afrikaans",

Information for the @contact@ provided by an authorised user.

pre.   stories_count: 4,

The number of @stories@ the @contact@ has been assigned to by an authorised user.

pre.   is_active: true,

@is_active@ is equivalent to the concept of "published".

pre.   photo: {
    variants: {
      original: "https://storyful.s3.amazonaws.com/production/contacts/48798/photo-original.jpg",
      medium: "https://storyful.s3.amazonaws.com/production/contacts/48798/photo-medium.jpg",
      small: "https://storyful.s3.amazonaws.com/production/contacts/48798/photo-small.jpg",
      standard: "https://storyful.s3.amazonaws.com/production/contacts/48798/photo-standard.jpg"
    }
  },

The various sizes of the provided @photo@ of the @contact@.

pre.   tags: [
    {
      id: "ireland",
      resource_url: "/tags/ireland",
      label: "Ireland",
      description: null,
      last_used_at: "2013-02-13T19:11:50Z",
      parent: {
        id: "europe",
        resource_url: "/tags/europe",
        label: "Europe",
        description: null,
        last_used_at: "2013-02-06T16:51:11Z"
      }
    }
  ],

The @tags@ assigned to the @contact@ by an authorised user.

pre.   primary_tag: {
    id: "ireland",
    resource_url: "/tags/ireland",
    label: "Ireland",
    description: null,
    last_used_at: "2013-02-13T19:11:50Z",
    parent: {
      id: "europe",
      resource_url: "/tags/europe",
      label: "Europe",
      description: null,
      last_used_at: "2013-02-06T16:51:11Z"
    }
  },

The @primary_tag@ assigned to the @contact@.

pre.   created_at: "2013-01-10T15:48:53Z",
  updated_at: "2013-02-18T15:07:00Z"
}

The date the @contact@ was created and updated.

h4. Contact/Stories

@contacts/stories@ returns a list of @story@ items that the @contact@ has been assigned too.

e.g. @http://api.storyful.com/contacts/48798/stories@

pre. contact: {
  ...
  stories: [*list of @story@ items*],

h3. Tags

A list of @tags@ in descending @last_used_at@ order. @last_used_at@ represents the last time the @tag@ was assigned to a @story@, @contact@ or @list@.

e.g. @http://api.storyful.com/tags@

pre. tags: [*list of @tag@ items*]

h3. Tag

A @tag@ represents a collection of items such as @story@, @list@ or @contact@. A @tag@ can have a parent @tag@ but has no other categorisation and lives outside of @channel@ filtering. Based on the @tag@ @parent@ a @children@ structure is provided but is an aggregation and not a directly set property.

e.g. @http://api.storyful.com/tags/tanzania@

pre. tag: {
  id: "tanzania",
  resource_url: "/tags/tanzania",

The canonical resource URL of the @tag@.

pre.   label: "Tanzania",
  description: null,

The authorised user provided @label@ and @description@ of the @tag@.

pre.   stories_count: 7,
  lists_count: 1,
  contacts_count: 0,

The number of @stories@, @lists@ and @contacts@ the @tag@ has been assigned too.

pre.   image: {
    owner_name: "@Tanganyikan",
    owner_link: "http://twitter.com/#!/Tanganyikan/status/112455981123895297/photo/1",
    variants: {
      original: "https://storyful.s3.amazonaws.com/production/stories/7360/original.png",
      large: "https://storyful.s3.amazonaws.com/production/stories/7360/large.png",
      index_main: "https://storyful.s3.amazonaws.com/production/stories/7360/index_main.png",
      index: "https://storyful.s3.amazonaws.com/production/stories/7360/index.png",
      standard: "https://storyful.s3.amazonaws.com/production/stories/7360/standard.png",
      index_small: "https://storyful.s3.amazonaws.com/production/stories/7360/index_small.png",
      smallest: "https://storyful.s3.amazonaws.com/production/stories/7360/smallest.png"
    }
  },

An @image@ automatically pulled from the first @story@ the @tag@ has been assigned too.

pre.   last_used_at: "2012-10-19T19:08:04Z",

The time the @tag@ was last assigned to a @story@, @contact@ or @list@.

pre.   parent: {
    id: "africa",
    resource_url: "/tags/africa",
    label: "Africa",
    description: null,
    stories_count: 5,
    lists_count: 0,
    contacts_count: 0,
    image: null,
    last_used_at: "2012-11-19T22:38:49Z"
  },

The parent @tag@ of this @tag@.

pre.   children: [
    {
      id: "zanzibar",
      resource_url: "/tags/zanzibar",
      label: "Zanzibar",
      description: null,
      stories_count: 4,
      lists_count: 0,
      contacts_count: 0,
      image: {
        owner_name: "@Tanganyikan",
        owner_link: "http://twitter.com/#!/Tanganyikan/status/112455981123895297/photo/1",
        variants: {
          original: "https://storyful.s3.amazonaws.com/production/stories/7360/original.png",
          large: "https://storyful.s3.amazonaws.com/production/stories/7360/large.png",
          index_main: "https://storyful.s3.amazonaws.com/production/stories/7360/index_main.png",
          index: "https://storyful.s3.amazonaws.com/production/stories/7360/index.png",
          standard: "https://storyful.s3.amazonaws.com/production/stories/7360/standard.png",
          index_small: "https://storyful.s3.amazonaws.com/production/stories/7360/index_small.png",
          smallest: "https://storyful.s3.amazonaws.com/production/stories/7360/smallest.png"
        }
      },
      last_used_at: "2012-10-17T13:14:50Z",
      parent: {*a @tag@*}
    }
  ]
}

Automatic aggregation of any @tags@ which have this @tag@ set as @parent@.

h4. Tag/Stories

@tags/stories@ returns a list of @story@ items assigned with this tag.

e.g. @http://api.storyful.com/tags/tanzania/stories@

pre. tag: {
  ...
  stories: [*list of @story@ items*],

h4. Tag/Contacts

@tags/contacts@ returns a list of @contact@ items assigned with this tag.

e.g. @http://api.storyful.com/tags/tanzania/contacts@

pre. tag: {
  ...
  contacts: [*list of @contact@ items*],

h4. Tag/Lists

@tags/lists@ returns a list of @list@ items assigned with this tag.

e.g. @http://api.storyful.com/tags/tanzania/lists@

pre. tag: {
  ...
  lists: [*list of @list@ items*],

h3. Members

A list of @member@ items

e.g. @http://api.storyful.com/members@

pre. members: [*list of @member@ items*]

h3. Member

A @member@ represents an entity assigned to a @list@. Currently only Twitter user entitites are supported.

e.g. @http://api.storyful.com/members/2866@

pre. member: {
  resource_url: "/members/2866",
  id: 2866,

The canonical resource URL for the @member@.

pre.   username: "paulmwatson",

The @username@ of the @member@. This is equiavlent to the Twitter screen name.

pre.   fullname: "Paul Watson",

The @fullname@ of the @member@.

pre.   avatar_url: "http://a0.twimg.com/profile_images/3214897973/36ccc39241084b3b27deea447391cede_normal.jpeg",

The @avatar_url@ of the member.

pre.   source_network_id: 11214,

The @source_network_id@ is the ID of the @member@ from the source network, in this case Twitter.

pre.   bio: "South African web-developer working for @Storyful in Ireland. paul@paulmwatson.com or +353 86 896 8944.",

The @bio@ of the @member@.

pre.   user_location: "Dublin, Ireland",

The @user_location@ of the @member@ as provided by the user on the source network.

pre.   source_network_join_date: "2006-10-31T21:05:36Z",

The @source_network_join_date@ of the @member@ is when the user joined the source network.

pre.   network_type: "twitter",

The @network_type@ of the @member@ represents where the @member@ information came from. Can only be @twitter@.

pre.   source_network_profile_blob: {}

The @source_network_profile_blob@ is the original JSON response from the source network.

h3. Profile

Returns an @author@ corresponding to the @access_token@ used. Useful for ensuring you are using the right @access_token@.

e.g. @http://api.storyful.com/profile?access_token=zt218bq3zw67316b7wj789012l56p012@

pre. profile: {*@author@ item*}
