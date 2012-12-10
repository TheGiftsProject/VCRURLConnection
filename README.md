# VCRURLConnection
VCRURLConnection is an API to record and replay HTTP interactions, inspired by [VCR](https://github.com/myronmarston/vcr)

> _This is still in early stages of development, All bug reports, feature requests, or general feedback are be greatly appreciated!_

## Example
``` objective-c
// load up a cassette
NSString *cassettePath = [[NSBundle mainBundle] pathForResource:@"cassette" ofType:@"json"];
[VCR setCassetteURL:[NSURL fileURLWithPath:cassettePath]];
[VCR start];

NSURL *url = [NSURL URLWithString:@"http://example.com/example"];
[NSURLRequest requestWithURL:url];

// record the request
[NSURLConnection connectionWithRequest:request delegate:self]; // records real HTTP response
[VCR save]; // persist recording to cassette.json

// replay the request
[NSURLConnection connectionWithRequest:request delegate:self]; // replay recorded HTTP response

[VCR stop];
```

## How to get started
- [Download VCRURLConnection](https://github.com/dstnbrkr/VCRURLConnection/zipball/master) and try out the included example app
- Include the files in the VCRURLConnection folder in your test target
- Run your tests once to record all HTTP interactions
- Subsequent test runs will use the recorded HTTP interactions instead of the network
- You can edit the recorded HTTP interactions by hand, the recordings are all stored in a simple JSON file format





