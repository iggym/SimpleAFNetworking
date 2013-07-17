SimpleAFNetworking example
=====================
A Simple AFNetworking example
 
Overview
--------
- version: 0.1.0
 
 
Description
-----------
Uses iTunes search to retrieve a list of movies that Bruce Willis has appeared in.
see the [link](https://gist.github.com/iggym/6023041 "iTunes feeds") for more info.



####The View Controller

![alt screenshot](https://raw.github.com/iggym/SimpleAFNetworking/master/SimpleAFNetworking/ScreenShot.png)

 
###Interesting Code Snippets

#####Set up the URL and Request
```objectivec
NSURL *url = [[NSURL alloc] initWithString:@"https://itunes.apple.com/search?term=bruce+willis&entity=movie"];
NSURLRequest *request = [[NSURLRequest alloc] initWithURL:url];
```

#####Fetch and parse JSON data in the background
```objectivec
AFJSONRequestOperation *operation = [AFJSONRequestOperation JSONRequestOperationWithRequest:request
       success:^(NSURLRequest *request, NSHTTPURLResponse *response, id JSON) {
        self.results = [JSON objectForKey:@"results"];
        [self.activityIndicatorView stopAnimating];
        [self.tableView setHidden:NO];
        [self.tableView reloadData];
        
    } failure:^(NSURLRequest *request, NSHTTPURLResponse *response, NSError *error, id JSON) {
        NSLog(@"Request Failed with Error: %@, %@", error, error.userInfo);
    }];
    
    [operation start];
```


Requirements
------------
- Xcode 5
 
Compatibility
-------------
- Xcode 5
 
Installation Instructions
-------------------------
Download, unzip, open in Xcode
 
Uninstallation
--------------
delete the directory
 
Support
-------
No Support.
 
Contribution
------------
Any contribution is highly appreciated. The best way to contribute code is to open a [pull request on GitHub](https://help.github.com/articles/using-pull-requests).
 
Developer
---------
@iggym
 
License
-------
[OSL - Open Software Licence 3.0](http://opensource.org/licenses/osl-3.0.php)
 
Copyright
---------
(c) 2013 iggym
