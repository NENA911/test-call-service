# Test Call Service

The Test Call Service implements the test function described in RFC 6881. The functions mimics an entire actual 9-1-1 call path as closely as practical. The test mechanism is completely automatic, with no manual intervention required. To route the same as an actual emergency call, route urns in the “urn:emergency:service” tree are provided for test calls.

An INVITE message with the Service URN (found in the Request-URI) of “urn:service:test.sos” is interpreted as a request to initiate a test call. The PSAP returns a 200 OK response in normal conditions, indicating that it will complete the test function. The PSAP may limit the number of test calls. If that limit is exceeded, the response is 486 Busy Here. PSAPs may accept requests for sub-services such as “urn:service:test.sos.fire.” and complete a test call, or the PSAP may reject the call and return 404 Not Found. PSAP management may disable the test function (using PSAP policy).

If the PSAP accepts the test, it SHOULD return in the 200 OK a body with MIME type text/plain consisting of the following contents:
* The name of the PSAP, terminated by a CR and LF;
* The string “urn:service:test.sos” terminated by a CR and LF;
* The location reported with the call (in the Geolocation header field). If the location was provided by value, the response would be a natural text version of the received location. If the location was provided by reference, the PSAP dereferences the location, using credentials acceptable to the LIS issued specifically for test purposes. Credentials issued by a PCA-rooted CA have the token “test” as the agent name or the first token in the FQDN. The location returned may not be the same as the LIS would issue for an actual emergency call.

## Owner

The owner of this repository approves all changes to the repository. 

This repository is owned by the NENA Core Services Committee, i3 Architecture working group.

#### Rules:

Specification Required. 

#### Contact:

[https://www.nena.org/page/911CoreSvcs](https://www.nena.org/page/911CoreSvcs) 

## Version History

### Test Call Service v 1.0

Version 1 OpenAPI schema for this service was originally defined in NENA-STA-010.3.2021. See https://www.nena.org/page/i3_Stage
