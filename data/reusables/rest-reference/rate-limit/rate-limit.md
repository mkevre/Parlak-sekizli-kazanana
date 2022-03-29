The REST API overview documentation describes the [rate limit rules](/rest/overview/resources-in-the-rest-api#rate-limiting). You can check your current rate limit status at any time using the Rate Limit API described below.

### Understanding your rate limit status

The Search API has a [custom rate limit](/rest/reference/search#rate-limit), separate from the rate limit governing the rest of the REST API. The GraphQL API also has a [custom rate limit]({% ifversion ghec%}/free-pro-team@latest{% endif %}/graphql/overview/resource-limitations#rate-limit) that is separate from and calculated differently than rate limits in the REST API.

For these reasons, the Rate Limit API response categorizes your rate limit. Under `resources`, you'll see four
objects:

* The `core` object provides your rate limit status for all non-search-related resources in the REST API.

* The `search` object provides your rate limit status for the [Search API](/rest/reference/search).

* The `graphql` object provides your rate limit status for the [GraphQL API]({% ifversion ghec%}/free-pro-team@latest{% endif %}/graphql).

* The `integration_manifest` object provides your rate limit status for the [GitHub App Manifest code conversion](/apps/building-github-apps/creating-github-apps-from-a-manifest/#3-you-exchange-the-temporary-code-to-retrieve-the-app-configuration) endpoint.

For more information on the headers and values in the rate limit response, see "[Resources in the REST API](/rest/overview/resources-in-the-rest-api#rate-limit-http-headers)."