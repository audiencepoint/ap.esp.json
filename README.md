## Synopsis

ap.esp.json is a javascript source file that uses Regular Expressions to identify the sending range of a given ESP. The range values can be ascertained from the whois database (http://www.whois.com/whois/74.112.65.204). Each ESP has 
its own block of sending IP addresses and each IP Address can be collected from the headers of an email message.

The Regex for the IP Range can be identified through online tools like this:

[http://www.analyticsmarket.com/freetools/ipregex](http://www.analyticsmarket.com/freetools/ipregex)

## Code Example

The ap.esp.json file can be used to identify the sending ESP with the following snippet of Javascript code:

```
$.getJSON("http://<yourserver>.com/ap.esp.json", function(data){

    for( var ipMatch in data )
    {   
        reg = new RegExp(data[ipMatch].re);
        if(reg.test(ipAddress))
        {
        	console.log( data[ipMatch].Name );
        }
    }
}
```

## Motivation

AudiencePoint, as both a marketing & technology company wants to reinvest in the industry by sharing building blocks that creates industry value. 


## Adding a node

Additional nodes can be added alphabetically to ap.esp.json by adding this node:

```
	"MailItAnyway": 
		{"re": "^216\\.27\\.([0-9]|[1-8][0-9]|9[0-5])\\.([0-9]|[1-9][0-9]|1([0-9][0-9])|2([0-4][0-9]|5[0-5]))$", 
		"names": "Mail It Anyway",
		"image": "myMail.png"},	
```

Please remember to add the image of the ESP to the images directory of GitHub.


## Contributors

* Kurt Weisheit 
* Gbemi Ojo

## License

ap.esp.json is licensed under the [MIT License](http://opensource.org/licenses/MIT)