[![Bourbon Neat](http://neat.bourbon.io/images/logotype.svg)](http://neat.bourbon.io/)

**Neat** is an open source fluid grid framework built on top of [Bourbon](http://bourbon.io) with the aim of being easy enough to use out of the box and flexible enough to customize down the road.


##Requirements
- SASS 3.2+
- Bourbon 2.1+

##Installation
Install [SASS](http://sass-lang.com/) and [Bourbon](https://github.com/CoRD-Dev/libbourbon).

Navigate to your projects local repository and run:

```bash
git submodule add https://github.com/CoRD-Dev/libneat.git sass/neat
```
(`sass/neat` should be the directory your sass/scss files are kept +/neat.)

Import Neat after Bourbon in your stylesheet. 
All additional imports should be below Neat:

```scss
@import "bourbon/bourbon";
@import "neat/neat";

// All other imports
```

(Optional) Install [Bitters](https://github.com/CoRD-Dev/libbitters).


##Credits
![thoughtbot](http://thoughtbot.com/images/tm/logo.png)

Bourbon Neat is maintained and funded by [thoughtbot, inc](http://thoughtbot.com/). Follow [@thoughtbot](http://twitter.com/thoughtbot) on Twitter.

libneat is maintained by [CoRD](http://cord-dev.github.io/) and [The_Catman](http://catmanix.github.io/).

##License
Bourbon Neat is Copyright © 2012-2013 thoughtbot. It is free software, and may be redistributed under the terms specified in the LICENSE file.
