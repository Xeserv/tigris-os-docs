# Pricing

Tigris pricing is based on the following components:

- Data Storage: the amount of data stored in your buckets.
- Requests: the number of requests made to your buckets and objects. The request
  costs are based on the type of request and are calculated based on the
  quantity of requests.
- Data Transfer: the amount of data transferred out of your buckets.

## Pricing table

| Component                                     | Price                 |
| --------------------------------------------- | --------------------- |
| Data Transfer                                 | Free                  |
| Data Storage                                  | $0.02/GB/month        |
| Class A Requests: PUT, COPY, POST, LIST       | $0.005/1000 requests  |
| Class B Requests: GET, SELECT, and all others | $0.0005/1000 requests |

## Free allowances

We offer a free allowance as follows:

- 5GB of data storage per month
- 10,000 PUT, COPY, POST, LIST requests per month
- 100,000 GET, SELECT, and all other requests per month

## Enterprise pricing

For larger workloads we offer the ability to customize the pricing and service
contract to best fit your needs. Please reach out to us at
[sales@tigrisdata.com](mailto:sales@tigrisdata.com) to discuss your
requirements.

## Example pricing

### Example 1

Let's say you have a bucket with 10GB of data with an average size of 1MB per
object, and you make 100,000 GET requests to the objects in the bucket. You will
be charged as follows:

- Data Storage: 5GB x $0/GB/month (free allowance) + 5GB x $0.02/GB/month =
  $0.10
- PUT Requests: 10,000 x $0/1000 requests (free allowance) = $0
- GET Requests: 100,000 x $0/1000 requests (free allowance) = $0
- Data Transfer: $0

### Example 2

Let's say you have a bucket with 100GB of data with an average size of 1MB per
object, and you make 1,000,000 GET requests to the objects in the bucket. You
will be charged as follows:

- Data Storage: 5GB x $0/GB/month (free allowance) + 95GB x $0.02/GB/month =
  $1.90
- PUT Requests: 10,000 x $0/1000 requests (free allowance) + 90,000 x
  $0.005/1000 requests = $0.45
- GET Requests: 100,000 x $0/1000 requests + 900,000 x $0.0005/1000 requests =
  $0.45
- Data Transfer: $0

## Frequently asked questions

<details>
<summary>What happens if I receive unexpected traffic?</summary>

We are happy to discuss a refund if you experience unexpected traffic due to an
attack that results in a surprisingly large bill. Please reach out to us at
[help@tigrisdata.com](mailto:help@tigrisdata.com).

</details>

<details>
<summary>Do you charge for unauthorized access?</summary>

We do not charge for unauthorized requests to your buckets and objects. You will
not be charged for the following error responses: 301 Moved Permanently, 307
Temporary Redirect, 400 Bad Request, 403 Forbidden, 404 Not Found, 405 Method
Not Allowed, 409 Conflict, 411 Length Required, 412 Precondition Failed, 416
Requested Range Not Satisfiable, 304 Not Modified, 500 Internal Server Error,
and 501 Not Implemented.

</details>

<details>
<summary>What constitutes Class A and Class B requests?</summary>

The following requests are classified as Class A and Class B requests:

#### Class A Requests

CreateBucket, CreateMultipartUpload, CopyObject, ListObjects, ListObjectsV2,
ListMultipartUploads, ListBuckets, ListParts, PutBucketCors,
PutBucketLifecycleConfiguration, PutObjectTagging, PutObjectAcl,
PutObjectRetention, PutObjectLegalHold, PutObjectLockConfiguration,
PutBucketAcl, PutBucketPolicy, PutBucketTagging,
PutBucketAccelerateConfiguration, PutBucketOwnershipControls, PutObject

#### Class B Requests

GetBucketAccelerateConfiguration, GetBucketAcl, GetBucketCors,
GetBucketLifecycleConfiguration, GetBucketLocation, GetBucketOwnershipControls,
GetBucketPolicy, GetBucketPolicyStatus, GetBucketRequestPayment,
GetBucketTagging, GetBucketVersioning, GetObject, GetObjectAcl,
GetObjectTagging, HeadBucket, HeadObject

#### Free Requests

All DELETE and CANCEL requests are free

</details>

<details>
<summary>Do you charge for data transfer?</summary>

While other cloud providers tax you for each GB of data transferred, we don't.
At Tigris, we don't charge for regional data transfer, region-to-region data
transfer, or data transfer out to the internet (egress) in the majority of use
cases. However, if your bandwidth requirements are extraordinary, please reach
out to us at [sales@tigrisdata.com](mailto:sales@tigrisdata.com) to discuss your
requirements.

</details>

<details>
<summary>How is data storage calculated over a period of a month?</summary>

Tigris measures storage in binary gigabytes (GB), where 1 GB equals 2^30 bytes .
This unit, also called a gibibyte (GiB), is defined by the International
Electrotechnical Commission (IEC). In the same way, 1 TB is equivalent to 2^40
bytes, or 1024 GB.

Storage costs are calulated using **GB/month**. A **GB/month** is determined by
averaging the daily peak storage over a billing period (1 month). Example:

- Storing 1 GB (1,073,741,824 bytes) constantly for whole month will be charged
  as 1 GB/month
- Storing 10 GB for 12 days in June, and then 20 GB for the rest 18 days will be
  charged as 16 GB/month
  - 10 GB x 12/30 + 20 GB x 18/30 = 16 GB/month

</details>

<details>
<summary>Do you charge for storing multiple copies of data?</summary>

Tigris, by default, manages the data distribution for you, ensuring data is
stored close to the users to ensure low latency and high availability. However,
as mentioned in the [Object Regions](/docs/objects/object_regions.md) section,
you may choose to control the data distribution and store multiple copies of
your data in different regions. In such cases, the storage cost is calculated
based on the number of copies stored. For example, if you elect to store two
copies of your data in two different regions, you will be charged twice for the
storage.

</details>
