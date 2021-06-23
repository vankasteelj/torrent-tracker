## torrent-tracker

### What is it?
torrent-tracker is an implementation of both the [UDP](http://www.bittorrent.org/beps/bep_0015.html) and [HTTP](http://www.bittorrent.org/beps/bep_0003.html) tracker protocol's that the BitTorrent protocol use to exchange information on peers. The library supports [compact peer lists](http://www.bittorrent.org/beps/bep_0023.html) as well as some [UDP tracker extensions](http://www.bittorrent.org/beps/bep_0041.html).

This library was originally written by [jduncanator](https://github.com/jduncanator) for his swarm-tracker library.

### Is this a fork of node-tracker?
Yes. [XeonCore](https://github.com/xeoncore) is nowhere to be found and node-tracker is no longer maintained.

### How to use it?

A really simple example:

```javascript
var test1 = new Tracker('udp://tracker.openbittorrent.com:80/announce')
var test2 = new Tracker('udp://tracker.opentrackr.org:1337/announce')
var test3 = new Tracker('udp://tracker.torrent.eu.org:451/announce')
var test4 = new Tracker('http://nyaa.tracker.wf:7777/announce')
var infohashes = [
    '5ead8155bb9ced9d36f3196b120e897c61b2af49',
    '8a943f9c60ca01698cb213faf6e489e469246121',
    '812b250c42c42a6cbaf40e69290694f55115d524',
];
test1.scrape(infohashes, function(err, msg) { console.log(msg); })
test2.scrape(infohashes, function(err, msg) { console.log(msg); })
test3.scrape(infohashes, function(err, msg) { console.log(msg); })
test4.scrape(infohashes, function(err, msg) { console.log(msg); })
```

Output:
```bash
{
  '5ead8155bb9ced9d36f3196b120e897c61b2af49': { seeders: 0, completed: 10, leechers: 1 },
  '8a943f9c60ca01698cb213faf6e489e469246121': { seeders: 126, completed: 10, leechers: 8 },
  '812b250c42c42a6cbaf40e69290694f55115d524': { seeders: 1, completed: 3, leechers: 16 }
}
{
  '5ead8155bb9ced9d36f3196b120e897c61b2af49': { seeders: 0, completed: 0, leechers: 0 },
  '8a943f9c60ca01698cb213faf6e489e469246121': { seeders: 101, completed: 2882, leechers: 13 },
  '812b250c42c42a6cbaf40e69290694f55115d524': { seeders: 67, completed: 1163, leechers: 47 }
}
{
  '5ead8155bb9ced9d36f3196b120e897c61b2af49': { seeders: 0, completed: 0, leechers: 0 },
  '8a943f9c60ca01698cb213faf6e489e469246121': { seeders: 0, completed: 661, leechers: 7 },
  '812b250c42c42a6cbaf40e69290694f55115d524': { seeders: 43, completed: 1952, leechers: 40 }
}
{
  '812b250c42c42a6cbaf40e69290694f55115d524': { seeders: 105, completed: 6986, leechers: 21 }
}
```
