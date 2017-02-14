### <a name="region">Region</a>
The region is not usually required to generate a quote, as we can in general infer the energetic region from the provided postcode.
However there are a small number of postcodes for which we cannot infer the region - e.g. new builds.
If we cannot determine the region for a given postcode and the region parameter has not been provided, the response to this endpoint will be `428 - Precondition Required`.

In this circumstance the request needs to be resent with the region parameter provided.