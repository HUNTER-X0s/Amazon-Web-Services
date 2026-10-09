# Amazon CloudFront: Console Walkthrough

**Mental model:** CloudFront is the edge layer. A viewer connects to a distribution; its cache behavior decides whether to serve a cached response or contact an origin such as S3 or an application load balancer.

Related note: [AWS CloudFront CDN.md](../../AWS%20CloudFront%20CDN.md)

## Create a distribution for a private S3 origin

1. Create an S3 bucket and upload a harmless test object. Keep S3 Block Public Access enabled.
2. Open [CloudFront](https://console.aws.amazon.com/cloudfront/v4/home) and choose **Distributions → Create distribution**.
3. Choose a single website/app and select the S3 bucket as the origin. Use the recommended S3 origin settings and enable Origin Access Control (OAC) so CloudFront, rather than the public internet, can read the bucket.
4. Review default cache behavior, viewer protocol policy (redirect HTTP to HTTPS for a website), allowed methods, compression, and security protections. Keep only required methods and avoid caching user-specific/private responses.
5. Add a custom domain only if you control it. Attach a valid ACM certificate; for CloudFront viewer certificates the certificate must be in **US East (N. Virginia), us-east-1**. Otherwise use the CloudFront-provided domain for the practice exercise.
6. Review and create the distribution. If prompted, allow CloudFront to update the S3 bucket policy for OAC. Wait until status is **Deployed**.
7. Open the distribution domain name and request the test object's path. Verify it loads over HTTPS and that the S3 object is still not directly public.

## Verify and clean up

Check origin, OAC, bucket policy, cache behavior, certificate, and distribution status. Deployments and invalidations take time. To clean up, disable and delete the distribution (which can take several minutes), remove its OAC only when unused, and then remove the test bucket/object if desired. Distributions and data transfer can incur charges.

**Remember:** **viewer → edge cache → private origin**. Do not make a bucket public just to make CloudFront work.

**Official references:** [Create a distribution](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/distribution-web-creating-console.html) · [S3 origin with OAC](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html) · [ACM certificate Region requirement](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/cnames-and-https-requirements.html)
