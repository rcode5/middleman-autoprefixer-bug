prove middleman-autoprefixer bug with ai/autoprefixer-rails v10.0.x

It appears that it comes down to this css file 
https://github.com/rcode5/middleman-autoprefixer-bug/blob/main/source/stylesheets/site.css.scss

It had lots of stuff in there before and I just kept commenting things out until I got down to the smallest amount that would cause the failure.

