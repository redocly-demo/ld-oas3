# API OVERVIEW

# Authentication

All REST API resources are authenticated with [personal access tokens](https://docs.launchdarkly.com/v2.0/docs/api-access-tokens) or session cookies. Other authentication mechanisms are not supported. You can manage personal access tokens on your [Account settings](https://app.launchdarkly.com/settings/tokens) page.

LaunchDarkly also has SDK keys, mobile keys, and client-side IDs that are used by our server-side SDKs, mobile SDKs, and client-side JavaScript SDKs, respectively. **These keys cannot be used to access our REST API**. These keys are environment-specific, and can only perform read-only operations (fetching feature flag settings).

| Auth mechanism                                                                      | Allowed resources                                                                                     | Use cases                                          |
| :---------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------- | :------------------------------------------------- |
| [Personal access tokens](https://docs.launchdarkly.com/v2.0/docs/api-access-tokens) | Can be customized on a per-token basis                                                                | Building scripts, custom integrations, data export |
| SDK keys                                                                            | Can only access read-only SDK-specific resources and the firehose, restricted to a single environment | Server-side SDKs, Firehose API                     |

## Via request header

The preferred way to authenticate with the API is by adding an `Authorization` header containing your access token to your requests. The value of the `Authorization` header must be your access token.

Manage personal access tokens from the [Account Settings](https://app.launchdarkly.com/settings/tokens) page.

## Via session cookie

For testing purposes, you can make API calls directly from your web browser. If you're logged in to the application, the API will use your existing session to authenticate calls.

If you have a [role](http://docs.launchdarkly.com/v2.0/docs/teams) other than Admin, or have a [custom role](http://docs.launchdarkly.com/v2.0/docs/custom-roles) defined, you may not have permission to perform some API calls. You'll receive a `401` response code in that case.
<SecurityDefinitions />

# Representations

All resources expect and return JSON response bodies. Error responses will also send a JSON body-- see Errors for a more detailed description of the error format used by the API.

In practice this means that you'll always get a response with a Content-Type header set to application/json.

In addition, request bodies for PUT, POST, REPORT and PATCH requests must be encoded as JSON with a Content-Type header set to application/json.

# Updates

Resources that accept partial updates use the PATCH verb, and support the JSON Patch format. Some resources also support the JSON Merge Patch format. In addition, some resources support optional comments that can be submitted with updates. Comments appear in outgoing webhooks, the audit log, and other integrations.

# Errors

The API always returns errors in a common format. Here's an example:

JSON

```JSON{
"code":"invalid_request",
"message":"A feature with that key already exists",
"id":"30ce6058-87da-11e4-b116-123b93f75cba"
}
```

# CORS

Other info

# Rate limiting

Don't go too fast.

# Open API (Swagger)

Stuff

# Method overriding

# Beta resources

# Versioning
