# Instructions

To run the project locally, navigate to the project directory and run:

```
bundle install
``` 

To start the Jekyll local development server.

```
bundle exec jekyll serve
bundle exec jekyll serve --livereload
``` 

To build static content

```
jekyll build
```

Clean up your jekyll build and cache

```
bundle exec jekyll clean
```


I had that error when I run bundle exec jekyll serve --livereload --trace on Jekyll.4.2.1-Ruby.3.0.3p137(mingw)-Windows. I ran gem install eventmachine --platform=ruby and it compiled at C:\Ruby30-x64\lib\ruby\gems\3.0.0\gems\eventmachine-1.2.7 but when you run bundle install it creates also C:\Ruby30-x64\lib\ruby\gems\3.0.0\gems\eventmachine-1.2.7-x64-mingw32 🤔. The command bundle info eventmachine gives me C:/Ruby30-x64/lib/ruby/gems/3.0.0/gems/eventmachine-1.2.7-x64-mingw32 and that's confimed in the Gemfile.lock with the line eventmachine (1.2.7-x64-mingw32). So I changed that line for eventmachine (1.2.7) and then the output of bundle info eventmachine gives me C:/Ruby30-x64/lib/ruby/gems/3.0.0/gems/eventmachine-1.2.7 and finally the command bundle exec jekyll serve --livereload --trace worked ✔️
