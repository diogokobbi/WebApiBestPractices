# WebApiBestPractices

A ToDo List API following some best practices:

## 1. Design

  1. URI values should correspond to nouns
  2. When referring to collections, URI values should typically be plural
  3. Requests for individual resources should append an identifier:
  4. Avoid coupling your Web API directly to your data/domain model
  5. Avoid Deeply Nested URI Structures
  6. Hypermedia as the Engine of Application State (HATEOAS): RFC 5988
  7. Standard Verbs and Behaviors
  8. Do not use the Post-Redirect-Get (PRG) Pattern: not an issue, but works better with MVC
  9. Support Content Negotiation
  10. Provide live, runtime documentation
  11. Include Response Types Produced on your documentation

## 2. Architecture

  1. Validate Model State using a filter
  2. Use [ApiController]
  3. Thin or minimal controllers
  4. Inherit from ControllerBase, not Controller
  5. Use Proper HTTP Status Codes as Results
  6. Prefer NotFound to NullReferenceException: Use a filter to confirm existence
  7. Don’t ask for an ID in the route and also in the BindingModel
  8. Use DTOs Appropriately: Consider having separate NewResourceDTO and ResourceDTO types  9. 

## 3. Performance

  1. Do not return full object tree with root-level request  2. 

## 4. Security

  1. Use HTTPS
  2. Use Web tokens for authentication

## 5. Testing

