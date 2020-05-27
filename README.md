# das-technical-guidance

[This documentation can be found here](https://skillsfundingagency.github.io/das-technical-guidance/)

How we build and operate products at the Apprenticeship Service. This repo
is inspired by (and steals shamelessly from) the [DfE Digital technical guidance](https://dfe-digital.github.io/technology-guidance/#dfe-digital-technical-guidance), [GDS Way](https://gds-way.cloudapps.digital) and the 
[Ministry of Justice Technical Guidance](https://ministryofjustice.github.io/technical-guidance/#moj-technical-guidance)
.

It's built using [Jekyll][], and hosted using [GitHub Pages][]. It
incorporates HTML, SCSS, JavaScript, and images from [GDS's Tech Docs
Template][tech-docs-template], and reworks them to work with Jekyll
instead of [Middleman][].

[gds-way]: https://github.com/alphagov/gds-way
[Jekyll]: https://jekyllrb.com
[GitHub Pages]: https://pages.github.com
[tech-docs-template]: https://github.com/alphagov/tech-docs-template
[Middleman]: https://middlemanapp.com

## Getting started

To build the site locally using Jekyll we can use the following Docker Command from the root git directory:

```sudo docker run --rm --volume="$PWD:/srv/jekyll" -it jekyll/jekyll:3.8 jekyll build```

to run the site locally from the root git directory we can use:

```sudo docker run --rm --volume="$PWD:/srv/jekyll" -p 4000:4000 -it jekyll/jekyll:3.8 jekyll serve```

To navigate to the built website enter the following in your browser:

```http://0.0.0.0:4000/```


## Making changes

To make changes, edit the appropriate Markdown files in this project.
Jekyll (and therefore this site) uses [kramdown][] for its Markdown
processing.

Make sure to make any changes in a branch, and to create a pull request for review.

[kramdown]: https://kramdown.gettalong.org/syntax.html

## Publishing changes

Because we're using GitHub Pages, any changes merged into the `master`
branch will be published automatically. Every change should be reviewed
in a pull request, no matter how minor, and we've enabled [branch
protection][] to enforce this.
