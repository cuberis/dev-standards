##Overview

The following guide will cover several practices that the Cuberis team uses for effectively managing projects. Our goals with these practices are to promote open and transparent communication, control project expectations, and provide a clear and unambiguous development trajectory to ensure client needs are met.

###Functional Spec Documents

*n.b. the following was written with WordPress in mind, and while the ideas should be applicable to other platforms, the terminology or execution might be different*

Before development takes place on a project, a functional spec should be put together. The functional spec document should cover every piece of content within a site, with no exceptions.

####Purpose of a functional spec

There are a few reasons for putting together a functional spec: the biggest is to manage client expectations. Clients should have a firm understanding of both what they are capable of editing themselves and how the rest of the site operations. By having a client sign off on a functional spec, they are agreeing to our ideas of how the site works. This eliminates ambiguity in the tail end of a project's development cycle.

The second purpose of a functional spec is to ensure that a project's developer(s) has a clear vision of how the more programmatic aspects of the site will function before any development actually takes place. This leads to more efficient, destination-driven programming, as well as avoiding "I don't know how to do this" moments in the development stage of the project -- compare writing a functional spec with rubber duck programming.

####Content categories

For a typical WordPress site, all pieces of content should be grouped into one of four categories:

* Static content (that is, hardcoded)
* Dynamic content that can be client-edited on a site-wide basis
* Dynamic content that can be client-edited on a page-by-page basis
* Dynamic content that is handled programmatically

Static content should (in practice) be the least prominent type -- it might include things like icons or section headers. Site-wide dynamic content might include something like a logo or contact information (as a total aside, site-wide dynamic content should be handled with WordPress' Customizer), whereas page-by-page dynamic content might include something like a page title.

(One helpful method for identifying content function is to print out wireframes, section off individual pieces of content, and highlight each piece of content with a color pertaining to its function. Do not stop until literally everything on the page is highlighted).

####The spec itself

Once content type has been determined, the developer should go to work writing the functional spec itself. The document should be split into three primary sections: Custom Post Types, Integrations, and Page-Specific functionality.

#####Custom post types
The Custom Post Type should contain a list of all CPTs that will be used by a site, and any metadata fields that will be associated with each.

There are a few goal of highlighting CPTs in the functional spec document: The first is to force the developer to think about site content in terms of being a collection of data points. By matching these data points with elements of the site's front-end, we can ensure that the site has a logical data structure.

The second (and perhaps larger goal) is to ensure that clients know exactly how much information they'll need to be able to provide for their site to operate.

The third goal is for developers to also consider metadata that **isn't** necessary for a content object. By eliminating extraneous dashboard fields (whether vanilla WP or otherwise) we can create a clean, easy-to-use UI that ensures clients can maintain their site as easily as possible.

#####Integrations

*(n.b. that this section won't be necessary for all projects, just those that integrate heavily with a third-party resource)*

The integrations section should make explicit the purpose of integrating with a third-party resource and what the intended functionality is.

This section should also make speific note of any limitations (e.g. data transfer caps, authentication) that pertain to third-party resources.


#####Page-specific functionality

The goal of this section is to identify each discrete piece of content on a page-by-page basis as well as its category (see **supra**). Each piece of content should be given its own subhead, with a brief description of how the content will be created (e.g. from a custom field, a WordPress query, pulled from a third-party, etc.) This allows clients to have a better understanding of how the site works, which leads to more effictive communication. This also ensures clients are aware of their own editing capabilities.

This section should begin with a brief note explaining that any piece of content not specifically covered in the spec can be assumed to be static. This eliminates any misunderstandings with clients.