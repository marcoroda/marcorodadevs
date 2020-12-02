# Jekyll Static website based on [jekyll-theme-console](https://github.com/b2a3e8/jekyll-theme-console)
This is the repo for my [marcoroda.com](https://marcoroda.com). 

# Build and Serve using a Docker Image
$ sudo docker run --rm -it   --volume="$PWD:/srv/jekyll"   --volume="$PWD/vendor/bundle:/usr/local/bundle"   -p 4000:4000 jekyll/jekyll:3.8   jekyll serve


