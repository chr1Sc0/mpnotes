# Troubleshooting Scenarios

### User Cannot Login
As mPulse portal has been integrated with Luna SSO, previous customers can experieng login problems. In particular, for "POCs", the SSO integration is not enabled but mPulse portal will always redirect to Luna portal.

The customer should instead login directly to mPulse with the URL: https://mpulse.soasta.com/concerto/login

### No Beacons Are Received
1. Check the boomerang object is loaded in the customer webpage:
    		a. Go to Developer Tools
    		b. Open the Console
    		c. Type: BOOMR or BOOMR.version. Example:

          09:05:25.908  BOOMR
          09:05:25.908 {version: "1.500.0", window: Window, boomerang_frame: Window, plugins: {…}, t_start: 1508223921903, …}

          or

          09:05:25.908 BOOMR.version
          09:05:25.908 "1.500.0"

2. Check the application ID is correct in config.js call (Developer Tools -> Network Tab) and matches the one in configured in mPulse.


TODO: Add more scenarios and troubleshooting tools/tips.
