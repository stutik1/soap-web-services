# soap-web-services


**Command which run this application to fetch the data**

curl [command-line-options] | xmllint --format -

curl --header "content-type: text/xml" -d @src/main/resources/req.xml http://localhost:8080/ws | xmllint --format -