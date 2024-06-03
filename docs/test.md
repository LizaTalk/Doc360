The HTTP app provides modules for communication based on the [Hypertext Transfer Protocol (HTTP)](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol). HTTP is the fundamental component of data transfer for the World Wide Web. As the backbone of information exchange between web servers and clients, HTTP allows you to download web pages, access files, make API calls, and trigger webhooks.

Overview of the HTTP modules
----------------------------

Select a module of the HTTP app based on the authentication requirements of the resource you want to use. To use modules that require authentication, you have to create a connection first.

-   Make a request: universal module, best to use for resources that do not require authentication.

-   Make a basic auth request: for resources that require [basic authentication](https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication#basic_authentication_scheme).

-   [Make an API key Auth request](https://www.make.com/en/help/tools/http.html#make-an-api-key-auth-request-935242 "Make an API key Auth request"): for resources that require [API key authentication](https://swagger.io/docs/specification/authentication/api-keys/).

-   Make an OAuth 2.0 request: for resources that require [OAuth 2.0](https://oauth.net/2/) authorization.

-   Make a client certificate auth request: for resources that require client-side certificate authentication.

-   [Get a file](https://www.make.com/en/help/tools/http.html#get-a-file-935242 "Get a file"): download a file from the URL.

-   [Resolve a target URL](https://www.make.com/en/help/tools/http.html#resolve-a-target-url "Resolve a target URL"): retrieve the target URL from a chain of HTTP redirects.

-   [Retrieve headers](https://www.make.com/en/help/tools/http.html#retrieve-headers "Retrieve Headers"): to get headers from the HTTP request module in separate bundles.

### Note

The module dialog fields that are displayed in bold (in the Makescenario, not in this documentation article) are mandatory!

Make a request
--------------

The Make a request module allows you to create an HTTP request and send it to a server. The output bundle contains the HTTP response.

|

Evaluate all states as errors (except for 2xx and 3xx)

 |

Use the response status to detect errors. Otherwise, the module reports only Make related errors (like mapping errors or missing required values).

 |
|

URL

 |

Enter the request URL.

 |
|

Serialize URL

 |

Encodes the API call URL with the URL encoding (encoding special characters for example).

 |
|

Method

 |

Select the HTTP method you want to use:

-   GET: to retrieve information for an entry.

-   POST: to create a new entry.

-   PUT: to update/replace an existing entry.

-   PATCH: to make a partial entry update.

-   DELETE: to delete an entry.

 |
|

Headers

 |

Enter request [headers](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields). For example, the response content type.

### Caution

The HTTP app requests do not have the [Accept header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Accept). If the HTTP request returns an unexpected response, try adding the `Accept: */*` header.

![HTTP_1.png](https://www.make.com/en/help/image/uuid-bf098487-c35e-7ff8-1b76-eee30dddf64b.png)

 |
|

Query String

 |

Enter the query key-value pairs.

 |
|

Body type

 |

HTTP `body` contains the data transferred in an HTTP request.

|

Raw

 |

The Raw`body` type is suitable for most HTTP requests, even if the app documentation does not specify the data type.

Specify the data format of the `body` content in the Content type field.

![HTTP_2.png](https://www.make.com/en/help/image/uuid-4d692efa-45d2-86e4-ba7d-6c034a3955c6.png)

 |
|

Application/x-www-form-urlencoded

 |

This body type is to `POST` data using `application/x-www-form-urlencoded`.

![HTTP_3.png](https://www.make.com/en/help/image/uuid-839bbe55-cf4b-a708-d010-1fc6febf7ece.png)

For `application/x-www-form-urlencoded`, the body of the HTTP request sent to the server is one query string. The keys and values are encoded in key-value pairs separated by `&` and with a `=` between the key and the value. For binary data, use the `multipart/form-data` body type instead.

Example of the resulting HTTP request format: `field1=value1&field2=value2`

 |
|

Multipart/form-data

 |

Use the `multipart/form-data` content type to send files in the HTTP request.

Add fields to the request. Each field must contain a key-value pair:

Text: Enter the key and value to send in the request body.

File: Enter the key, and specify the source file you want to send in the request body. Map the file you want to upload from the previous module (for example: HTTP > Get a File or Google Drive > Download a File), or enter the file name and file data manually.

 |

 |
|

Parse response

 |

Enable to parse HTTP responses into bundles. With this option, you don't need to add the Parse JSON or Parse XML modules. Otherwise, the HTTP module returns the raw response data.

Before you can use parsed JSON or XML content, run the module once manually so that the module can recognize the response content and allow you to map it in subsequent modules.

![HTTP_4.png](https://www.make.com/en/help/image/uuid-2995ac4c-f305-3332-fd8b-5ce88d28b42b.png)

 |
|

User name

 |

Enter the user name to send the request with the basic auth.

 |
|

Password

 |

Enter the password to send the request with the basic auth.

 |
|

Timeout

 |

Specify the request timeout in seconds (1-300). Default: 40 seconds.

 |
|

Share cookies with other HTTP modules

 |

Enable to share cookies from the server with all HTTP modules in your scenario.

 |
|

Self-signed certificate

 |

Upload your certificate if you want to use TLS using your self-signed certificate.

 |
|

Reject connections that use unverified (self-signed) certificates

 |

Enable to reject connections that use unverified TLS certificates.

 |
|

Follow redirect

 |

Enable to follow URL redirects that return 3xx response statuses.

 |
|

Follow all redirect

 |

Enable to follow URL redirects regardless of response statuses.

 |
|

Disable serialization of multiple same query string keys as arrays

 |

Make handles multiple values for the same URL query string parameter key as arrays (e.g., `www.test.com?foo=bar&amp;foo=baz` will be converted to `www.test.com?foo[0]=bar&amp;foo[1]=baz`). Enable to deactivate this behavior.

 |
|

Request compressed content

 |

Enable to request compression of the response data. Adds the `[Accept-Encoding](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Accept-Encoding)` header.

 |
