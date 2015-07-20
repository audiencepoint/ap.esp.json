## Synopsis

The ap.esp.json project is a json-based file that uses Regular Expressions to identify the sending range of a given ESP. The range values can be ascertained from the whois database (http://www.whois.com/whois/74.112.65.204). 

Each ESP has its own block of sending IP addresses and each IP Address can be collected from the headers of an email message and can be translated into a regular expression which can Identify the ESP associated with the IP Address.

The Regex for the IP Range can be identified through online tools like this:

[http://www.analyticsmarket.com/freetools/ipregex](http://www.analyticsmarket.com/freetools/ipregex)

## Code Example

The ap.esp.json file can be used to identify the sending ESP with the following snippets of code:

### Javascript
```
$.getJSON("http://<yourserver>.com/ap.esp.min.json", function(data){

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

### PHP

```
//get the contents of the IP regex file	
$jsonData= file_get_contents("http://<yourserver>/ap.esp.min.json");
$phpArray = json_decode($jsonData, true);

$matches = array();

$ip = "123.123.123.123";
			
foreach ($phpArray as $ESPName => $ESPObject) //loop through records of array ( JSON )
{ 
	if (preg_match( "/".$ESPObject["re"]."/", $ip, $matches ) == $SUCCESS )
	{
		return $ESPName;
	}   
}
```

## Motivation

AudiencePoint, as a marketing AND a technology company wants to reinvest in the industry by sharing building blocks that creates greater industry value. 


## Adding a node to this project

Additional nodes can be added alphabetically to ap.esp.json by adding this node:

```
	"MailItAnyway": 
		{"re": "^216\\.27\\.([0-9]|[1-8][0-9]|9[0-5])\\.([0-9]|[1-9][0-9]|1([0-9][0-9])|2([0-4][0-9]|5[0-5]))$", 
		"names": "Mail It Anyway",
		"image": "myMail.png"},	
```

Please remember to add the image of the ESP to the images directory of GitHub and to minify and validate the changes to the file
before you commit to the GitHub Repository. 

[http://www.cleancss.com/json-minify/](http://www.cleancss.com/json-minify/)

The image size should be 128px to 512px.

*NOTE:* The regular expressions are being stored as a string, so backslashes (\\) will need to be escaped (\\\\) .
```
"^216\\.27\\.([0-9]|[1-8][0-9]|9[0-5])\\.([0-9]|[1-9][0-9]|1([0-9][0-9])|2([0-4][0-9]|5[0-5]))$"
```

## Contributors

* Kurt Weisheit 
* Gbemi Ojo

## License

ap.esp.json is licensed under the [MIT License](http://opensource.org/licenses/MIT)
