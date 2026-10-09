AWS CloudFront CDN



AWS CloudFront is a content delivery network (CDN) that speeds up the delivery of web content to users by caching it at the servers (edge locations) close to them, improving load times and performance globally.





AWS CloudFront primarily caches static content like images, CSS, JavaScript, and videos. It can also cache dynamic content, for example, HTML or API responses, if configured with caching policies and headers



By default sensitive or user-specific data and backend logic are not cached. Cache behavior is controlled via TTLs, cache behaviors, and origin headers.







Amazon CloudFront has three types of infrastructure to securely deliver content with high performance to end users:

* CloudFront Regional Edge Caches (RECs) are situated within AWS Regions, between your applications' web server and CloudFront Points of Presence (POPs) and embedded Points of Presence. CloudFront has 13 RECs globally.
* CloudFront Points of Presence are situated within the AWS network and peer with internet service provider (ISP) networks. CloudFront has 600+ POPs in 100+ cities across 50+ countries.
* CloudFront embedded Points of Presence are situated within internet service provider (ISP) networks, closest to end viewers. In addition to CloudFront POPs, there are 600+ embedded POPs across 200+ cities in North America, Europe, and Asia.





Browsers act like a mini-CDN by caching website files (like images, CSS, and JavaScript) locally on a user's device, which speeds up loading for repeat visits.

Only helps individual users.







Included in Always Free Tier

* 1 TB of data transfer out to the internet per month
* 10,000,000 HTTP or HTTPS Requests per month
* 2,000,000 CloudFront Function invocations per month
* 2,000,000 CloudFront KeyValueStore reads per month
* Free SSL certificates
* No limitations, all features available







+-----------------------+------------------------------------------+------------------------------------------+

## Remember CloudFront as a cache in front of an origin

The viewer requests a URL; a cache behavior decides which settings apply; CloudFront either returns a valid cached response or asks the origin for it. The cache key determines which requests share a cached response. If it includes too little, user-specific content could leak; if it includes too much, the cache becomes less useful.

For S3, keep the bucket private and use Origin Access Control so only the intended distribution can read it. Use a short or disabled cache for frequently changing/private responses and longer caching for versioned static assets. An invalidation clears cached copies but does not alter the object at the origin.

**Recall check:** A page shows old content after deployment. Is the source file necessarily wrong? No—check origin object/version, cache policy, and whether the distribution has finished deploying.

AWS Shield Standard is baseline protection that does not require manual enablement. Shield Advanced is a separate subscription and resource-protection process; confirm its operational readiness and current cost before opting in.

**Console practice:** [CloudFront walkthrough](guides/aws-console/cloudfront.md) · [AWS Shield overview](guides/aws-console/shield.md)



| Feature               | CloudFront                               | Multi-Location Hosting                   |

+-----------------------+------------------------------------------+------------------------------------------+



| Performance           | Optimized for static content \& caching.  | Optimized for dynamic content near users.|

| Cost                  | Pay-per-use, often cheaper.              | Higher costs for server \& database setup.|

| Ease of Use           | Easy to set up, minimal management.      | Requires managing multi-server instances.|

| Scalability           | Auto-scales globally.                    | Requires manual scaling per location.    |

| Content Freshness     | Cached content may require invalidation. | Dynamic content is always current.       |

| Compliance            | Less control over data residency.        | Full control over where data is hosted.  |

| Security              | Built-in access control \& signed URLs.   | Requires individual firewall setups.     |

| SSL/TLS Configuration | Automated AWS Certificate integration.   | Requires manual renewal on each server.  |

| DDoS Protection       | Native, free mitigation via AWS Shield.  | Requires third-party tools/scrubbing.    |

+-----------------------+------------------------------------------+------------------------------------------+

