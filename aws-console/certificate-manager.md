# AWS Certificate Manager: Console Walkthrough

**Mental model:** ACM issues and renews TLS certificates for supported AWS endpoints. Certificate validation proves you control the domain; it does not automatically attach the certificate to a load balancer or distribution.

Related note: [AWS SSL-TLS.md](../../AWS%20SSL-TLS.md)

## Request a public certificate

1. Confirm the exact domain names and the AWS service that will use the certificate.
2. Open [AWS Certificate Manager](https://console.aws.amazon.com/acm/home), choose the correct Region, then **Request → Request a public certificate**.
3. Enter the primary domain and any needed subject alternative names. Choose **DNS validation** when you can manage the domain's DNS; it supports managed renewal when the validation record remains in place.
4. Add tags if useful, review the names, and request the certificate.
5. Open the pending certificate and publish the ACM-provided CNAME validation record in the authoritative DNS zone (Route 53 may offer a create-record action). Wait until the certificate status is **Issued**.
6. In the consuming service, select the certificate: for example, the HTTPS listener of an ALB or the alternate domain settings of CloudFront. CloudFront viewer certificates must be requested in `us-east-1`; other services typically require the same Region as the endpoint.

## Verify and maintain

Check that every requested name is covered, validation records still exist, the certificate is in the endpoint's required Region, and the endpoint is actually configured to use it. ACM public certificates are generally renewed automatically when eligible and DNS validation remains valid; monitor status and expiry.

**Remember:** **request → prove domain control → attach to endpoint → keep validation**.

**Official references:** [Request a public certificate](https://docs.aws.amazon.com/acm/latest/userguide/gs-acm-request-public.html) · [DNS validation](https://docs.aws.amazon.com/acm/latest/userguide/dns-validation.html)
