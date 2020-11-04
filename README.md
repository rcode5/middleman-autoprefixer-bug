## prove middleman-autoprefixer bug with ai/autoprefixer-rails v10.0.x

To repro the issue (https://github.com/ai/autoprefixer-rails/issues/194):

```bash
% bundle install
% bundle exec middleman serve
```

You should get something like:
```
...
TypeError: fileURL.replace is not a function
bundler: failed to load command: middleman (/Users/jon/.rbenv/versions/2.6.5/bin/middleman)
ExecJS::ProgramError: TypeError: fileURL.replace is not a function
  fileURLToPath ((execjs):4407:70)
  Input.origin ((execjs):9802:23)
  Input.error ((execjs):9747:25)
  Declaration.error ((execjs):760:34)
  Warning.toString ((execjs):7894:26)
  (execjs):22761:18
  Array.map (<anonymous>)
  process ((execjs):22759:38)
  eval (eval at <anonymous> ((execjs):22778:8), <anonymous>:1:23)
  (execjs):22778:8
  /Users/jon/.rbenv/versions/2.6.5/lib/ruby/gems/2.6.0/gems/execjs-2.7.0/lib/execjs/external_runtime.rb:39:in `exec'
  /Users/jon/.rbenv/versions/2.6.5/lib/ruby/gems/2.6.0/gems/execjs-2.7.0/lib/execjs/external_runtime.rb:21:in `eval'
  ```
  
It appears that it comes down to this css file 
https://github.com/rcode5/middleman-autoprefixer-bug/blob/main/source/stylesheets/site.css.scss

It had lots of stuff in there before and I just kept commenting things out until I got down to the smallest amount that would cause the failure.

