# server-date-time
Server Date Time

### serverDate.js
` var xmlHttp;
function srvTime(){
	try {
		//FF, Opera, Safari, Chrome
		xmlHttp = new XMLHttpRequest();
	}
	catch (err1) {
		//IE
		try {
			xmlHttp = new ActiveXObject('Msxml2.XMLHTTP');
		}
		catch (err2) {
			try {
				xmlHttp = new ActiveXObject('Microsoft.XMLHTTP');
			}
			catch (eerr3) {
				//AJAX not supported, use CPU time.
				alert("AJAX not supported");
			}
		}
	}
	xmlHttp.open('HEAD',window.location.href.toString(),false);
	xmlHttp.setRequestHeader("Content-Type", "text/html");
	xmlHttp.send('');
	return xmlHttp.getResponseHeader("Date");
}

var st = srvTime();
var date = new Date(st);`


### index.html
`<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Server date/time</title>
<script language="javascript" src="serverDate.js"></script>
</head>
<script language="javascript">
var localTime = new Date();
document.write("Local machine time is: " + localTime + "<br>");
document.write("Server time is: " + date);
</script>
<body>
</body>
</html>`
