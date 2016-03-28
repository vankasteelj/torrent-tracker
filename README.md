## torrent-tracker

### What is it?
torrent-tracker is an implementation of both the [UDP](http://www.bittorrent.org/beps/bep_0015.html) and [HTTP](http://www.bittorrent.org/beps/bep_0003.html) tracker protocol's that the BitTorrent protocol use to exchange information on peers. The library supports [compact peer lists](http://www.bittorrent.org/beps/bep_0023.html) as well as some [UDP tracker extensions](http://www.bittorrent.org/beps/bep_0041.html).

This library was originally written by [jduncanator](https://github.com/jduncanator) for his swarm-tracker library.

### Is this a fork of node-tracker?
Yes. [XeonCore](https://github.com/xeoncore) is nowhere to be found and node-tracker is no longer maintained.

### How to use it?

A really simple example:

    var Tracker = require('torrent-tracker')
    var test1 = new Tracker('udp://tracker.openbittorrent.com:80/announce')
    var test2 = new Tracker('udp://open.demonii.com:1337/announce')
    var test3 = new Tracker('udp://tracker.istole.it:80/announce')
    var test4 = new Tracker('http://tracker.ex.ua/announce')
    test1.scrape(['5ead8155bb9ced9d36f3196b120e897c61b2af49','8a943f9c60ca01698cb213faf6e489e469246121'], function(err, msg) { console.log(msg); })
    test2.scrape(['5ead8155bb9ced9d36f3196b120e897c61b2af49','8a943f9c60ca01698cb213faf6e489e469246121'], function(err, msg) { console.log(msg); })
    test3.scrape(['5ead8155bb9ced9d36f3196b120e897c61b2af49','8a943f9c60ca01698cb213faf6e489e469246121'], function(err, msg) { console.log(msg); })
    test4.scrape(['5ead8155bb9ced9d36f3196b120e897c61b2af49','8a943f9c60ca01698cb213faf6e489e469246121'], function(err, msg) { console.log(msg); })
