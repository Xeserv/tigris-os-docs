# Overview

Tigris is a globally distributed S3-compatible object storage service that
allows you to store and access any amount of data for a wide range of use cases.
Tigris automatically and intelligently distributes your data close to the users,
and removes the need for you to worry about the complexities of data
replication, and caching. Besides that, Tigris supports the S3 API, which means
you can use the wide range of available S3 tools, libraries, and extensions.

You can use Tigris for a wide range of use cases, such as:

- Storage for real-time applications
- Web content and media (images, videos, etc.)
- Storage for IoT applications
- Data analytics, big data and batch processing
- Storage for machine learning models and datasets
- Backups and archives

## Features of Tigris

### Single Global Endpoint

In Tigris, buckets are inherently global entities. This means that the objects
within your bucket are stored in the region where the initial requests are made.
To optimize performance and reduce latency, these objects are intelligently
distributed to other regions based on the access patterns observed over time.

This means that you can access your bucket from any region by using a single
global endpoint:

![Global Endpoint](/img/tigris-os-global-endpoint.png)

The global endpoint provides a unified entry point for accessing your Tigris
buckets globally, while the dynamic distribution of objects based on access
patterns, results in optimized latency, providing faster access to your data.

### Store Data Near Users

Tigris automatically stores the data close to the users and distributes it to
regions based on the request pattern. There is no configuration required to
enable this feature.

What this means is, if a request comes from a user in Frankfurt, Germany, the
data is stored in the closest region in EU. If a request comes from a user in
New York, US, the data is stored in the closest US region.

![Data Storage](/img/tigris-os-arch-block-store.png)

Furthermore, if the user now starts accessing the data from a region where the
data is not stored, Tigris transparently fetches the data from the region where
the data is stored and caches it in the region where the user is accessing it.
Eventually the data gets moved to the region where the user is accessing it.

### S3-compatible API

Tigris provides an S3-compatible API which allows you to access the wide range
of available S3 tools, libraries, and extensions. See the
[S3 API Compatibility](/docs/api/s3/) section for more details. We also have
[language specific guides](/docs/sdks/s3/) on how to use the AWS S3 SDKs with
Tigris.

### Fast Small Object Retrieval

Tigris provides significantly lower latency for small objects as compared to S3.
This allows you to use the same data storage for both small and large objects.

Small objects storage is optimized by using a combination of inlining and
coalescing techniques. Access to small objects is further optimized by caching
frequently accessed objects in a LSM-based on-disk cache.

You don't need to do anything special to take advantage of this feature. It is
enabled by default for all buckets.
