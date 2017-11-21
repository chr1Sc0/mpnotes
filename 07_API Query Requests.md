# Query API
The mPulse Query API is a unified REST API that allows mPulse customers to fetch aggregate data and receive a JSON response with mPulse data.

Comprehensive documentation about this API can be found here: http://docs.soasta.com/query-api/.

### Login
Due to the SSO integration with Luna, logging with username as password is not possible in general. Hence authenticating through an apiToken is needed to use the API through the following steps:

1.  Generate the API token for the user belonging to the Tenant in "Settings -> My Settings"
2.  Authenticate with the API token and get the session token:
    ```
    # curl -k -X PUT -H "Content-type: application/json" \
    --data-binary '{"apiToken":"7d7352b2-29ac-481e-b401-5e617e7a804a"}' \
    "https://mpulse.soasta.com/concerto/services/rest/RepositoryService/v1/Tokens"
    {"token":"82833ca8-352-133-478f-b83e-4babaa3e5f00"}
    ```

3.  Once the session token is received, submit the requests. It's important to provide the session token as authentication header and also provide the correct Tenant ID in the URL For example:
    ```
    # curl -v -H "Authentication: d1293c87-54e-13b-4fca-a727-6d76059d366b0" \
    "https://mpulse.soasta.com/concerto/mpulse/api/v2/SKH8G-XA4XU-7CEVY-J48GX-VBMJ4/summary?date=2017-10-10"
    ```

For more info read [here](https://community.akamai.com/docs/DOC-9096-mpulse-api-login-changes).

### Examples
There are example calls made through the mPulse API:

```
# curl -H "Authentication: 2d9b2b03-aa4-139-4ad1-8bb9-d572084a73ec" \
"https://mpulse.soasta.com/concerto/mpulse/api/v2/SKH8G-XA4XU-7CEVY-J48GX-VBMJ4/summary?date-comparator=Last3Hours&timer=PageLoad"
{"median":"2939","moe":"422.1183940980747","n":"16","p95":"4199","p98":"4415"}

# curl -H "Authentication: 2d9b2b03-aa4-139-4ad1-8bb9-d572084a73ec" \
"https://mpulse.soasta.com/concerto/mpulse/api/v2/SKH8G-XA4XU-7CEVY-J48GX-VBMJ4/summary?date-comparator=Last3Hours&timer=DNS"
{"median":"241","moe":"0.0","n":"1","p95":"241","p98":"241"}

# curl -H "Authentication: 2d9b2b03-aa4-139-4ad1-8bb9-d572084a73ec" \
"https://mpulse.soasta.com/concerto/mpulse/api/v2/SKH8G-XA4XU-7CEVY-J48GX-VBMJ4/summary?date-comparator=Last3Hours&timer=DNS&timer=DomLoad"
{"median":"2939","moe":"422.1183940980747","n":"16","p95":"4199","p98":"4415"}

# curl -H "Authentication: 2d9b2b03-aa4-139-4ad1-8bb9-d572084a73ec" \
"https://mpulse.soasta.com/concerto/mpulse/api/v2/SKH8G-XA4XU-7CEVY-J48GX-VBMJ4/summary?date-comparator=Last3Hours&timezone=Europe/Madrid"
{"median":"2939","moe":"422.1183940980747","n":"16","p95":"4199","p98":"4415"}

# curl -H "Authentication: 2d9b2b03-aa4-139-4ad1-8bb9-d572084a73ec" \
"https://mpulse.soasta.com/concerto/mpulse/api/v2/SKH8G-XA4XU-7CEVY-J48GX-VBMJ4/histogram?date-comparator=Last3Hours&timezone=Europe/Madrid"
{"chartTitle":"Number of Samples","chartTitleSuffix":null,"datasetName":"RumHistogram","reportType":"RumHistogram","resultName":null,"series":"{series: [{name: \"Number of Samples\", aPoints: [{s:1200,e:1350,c:2},{s:1350,e:1500,c:1},{s:2550,e:2700,c:1},{s:2700,e:2850,c:1},{s:2850,e:3000,c:5},{s:3150,e:3300,c:2},{s:3300,e:3450,c:1},{s:3450,e:3600,c:1},{s:3950,e:4200,c:1},{s:4200,e:4500,c:1}], kValue: 150, median: 2939, percentile_name: \"Median\", p95: 4199, p98: 4415, buckets: 134}]}"}

# curl -H "Authentication: 2d9b2b03-aa4-139-4ad1-8bb9-d572084a73ec" \
"https://mpulse.soasta.com/concerto/mpulse/api/v2/SKH8G-XA4XU-7CEVY-J48GX-VBMJ4/histogram?date-comparator=Last3Hours&timezone=Europe/Madrid&series-format=json&format=json"
{"chartTitle":"Number of Samples","chartTitleSuffix":"null","datasetName":"RumHistogram","reportType":"RumHistogram","resultName":"null","series":{series: [{name: "Number of Samples", aPoints: [{s:1200,e:1350,c:2},{s:1350,e:1500,c:1},{s:2550,e:2700,c:1},{s:2700,e:2850,c:1},{s:2850,e:3000,c:6},{s:3150,e:3300,c:2},{s:3300,e:3450,c:1},{s:3450,e:3600,c:1},{s:3950,e:4200,c:1},{s:4200,e:4500,c:1}], kValue: 150, median: 2949, percentile_name: "Median", p95: 4199, p98: 4415, buckets: 134}
```
