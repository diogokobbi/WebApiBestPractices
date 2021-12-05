# WebApiBestPractices

A ToDo List API following some best practices:

## 1. Design

  1. URI values should correspond to nouns
  2. When referring to collections, URI values should typically be plural
  3. Requests for individual resources should append an identifier
  4. Avoid coupling your Web API directly to your data/domain model
  5. Avoid Deeply Nested URI Structures
  6. Hypermedia as the Engine of Application State (HATEOAS): RFC 5988
  7. Standard Verbs and Behaviors: define API operations in terms of HTTP methods
  8. Do not use the Post-Redirect-Get (PRG) Pattern: not an issue, but works better with MVC
  9. Support Content Negotiation
  10. GET, PUT, DELETE, HEAD, and PATCH actions should be idempotent
  11. Provide live, runtime documentation
  12. Include Response Types Produced on your documentation
  13. Implement Paging, Searching, and Sorting
  14. Implement the API versioning
  15. Follow the HTTP specification when sending a response:
    1. If a query is successful, it should return status code 200 (OK).
    2. If a resource is not found, the operation should return HTTP status code 404 (Not Found).
    3. If the client sends a request that successfully deletes a resource, the status code should be 204 (No Content).
    4. If the client sends a request that creates a new resource, the status code should be 201 (Created).
    5. If the client puts invalid data into the request, the server should return HTTP status code 400 (Bad Request).
    6. If the method updates an existing resource, it returns either 200 (OK) or 204 (No Content).
    7. If the delete operation is successful, the web server should respond with HTTP status code 204 (No Content)
    8. iIt might not be possible to update an existing resource. In that case, consider returning HTTP status code 409 (Conflict).
    9. Send HTTP requests to routes that do not support them, the only valid response should be status code 405 (Not Allowed).
    10. Consider making the operation asynchronous. Return HTTP status code 202 (Accepted) to indicate the request was accepted for processing but is not completed.
  17. Include the appropriate HTTP status code rather than simply returning status code 500 for every situation
  18. Ensure that each request is stateless

## 2. Implementation

  1. Validate Model State using a filter
  2. Use [ApiController]
  3. Thin or minimal controllers
  4. Inherit from ControllerBase, not Controller
  5. Use Proper HTTP Status Codes as Results
  6. Prefer NotFound to NullReferenceException: Use a filter to confirm existence
  7. Don’t ask for an ID in the route and also in the BindingModel
  8. Use DTOs Appropriately: Consider having separate NewResourceDTO and ResourceDTO types  
  9. Keep the ConfigureServices method clean and readable 
  10. Use Environment Based Settings
  11. Use ActionFilters to Remove Duplicated Code
  12. Have a logging mechanism in place
  13. Capture exceptions and return a meaningful response to clients
  14. Consider implementing a global error handling strategy across the entire web API
  15. Use ETags to Support Optimistic Concurrency
  16. Implement a client SDK

## 3. Performance

  1. Do not return full object tree with root-level request  
  2. Use async code
  3. Support client-side caching using the Cache-Control header
  4. Cache the response
  5. Use the ReadFormAsync Method to read the content from the form body
  6. Provide ETags to optimize query processing
  7. Support streaming to enable optimized uploading and downloading: use "Transfer-Encoding: Chunked" in response header
  8. Use HTTP compression
  9. Combine encoded compression with streaming: compress the data first before streaming it, and specify the gzip content encoding and chunked transfer encoding in the message headers
  10. Implement partial responses for clients that do not support asynchronous operations
  11. Provide asynchronous support for long-running requests:  provide a polling or notification mechanism.
  12. Consider creating a façade, running as a separate process and that routes requests to the web API

## 4. Security

  1. Use HTTPS
  2. Use Web tokens for authentication
  3. Always hash or do not store user password
  4. Track clients and implement throttling to reduce the chances of DOS attacks: return a response message with status 503 (Service Unavailable) and include a Retry-After header
  5. All requests must be authenticated and authorized, and the appropriate level of access control must be enforced.
  6. 


## 5. Testing

  1. Test all routes to verify that they invoke the correct operations.
  2. Verify all links and URIs in response messages
  3. 

### References:

1. https://docs.microsoft.com/en-us/azure/architecture/best-practices/api-implementation
2. https://devintxcontent.blob.core.windows.net/showcontent/Speaker%20Presentations%20Spring%202019/Web%20API%20Best%20Practices.pdf
3. https://mathieu.fenniak.net/the-api-checklist/
