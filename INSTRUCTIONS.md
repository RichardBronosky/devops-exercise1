# Instructions
- Please don't fork this repository
    - It makes it too easy for other visitors to find your work
- Clone the repository to your local workspace
- Make commits early and often
    - Commit messages are a form of [documentation][documentation]
- Send the completed exercise as a [git bundle][gitbundle]
    - This cuts down on plagiarism

# Introduction
The goal of this exercise is to completely terraform a static site hosted in s3 with terraform. This should be doable using *mostly* [AWS Free Tier Resources][free]. (See the [Notes](#notes) section for details.) Here are the resources you will need:

# Resources
## S3 Bucket
- Bucket should contain static objects from [StaticSite][staticsite]
- Bucket must be private
- Only Cloudfront is allowed access to bucket
## CloudFront
- Uses S3 bucket as origin
- Uses Lambda@Edge to route viewer requests to index.html in s3 bucket
- Routing should work for subdirectories as well
## Lambda@Edge
- Routes viewer requests to index.html

# Requirements
1. Terraform module for deploying all [Resources](#resources).
2. Ideally the entire static site can be deployed with a single command.
3. Put complete (but not "wordy") usage instructions in the [README.md][readme] file.
    - The README should be measured by "if I needed to deploy this in an emergency, would I be satisfied by this documentation".

# Notes
- Lambda@Edge has no Free Tier offering.
- S3 and CloudFront are in the "AWS Free Tier (12 Month Introductory Period)" category.
- All AWS accounts are "production ready" and require a credit card (that has not been used on any other account) to open.
  - There is no such thing as a "Free Tier account".
  - You do not get charged if you do not use services outside the Free Tier.
- If you have an account that is no longer in the "12 Month Introductory Period" of the Free Tier, you may choose to use it anyway and should not incur significant charges.
  - The StaticSite files are 1.2MB
  - Lambda@Edge is [$0.0000006 per request and $0.00005001 per GB-second of memory used][lambda]
  - S3 is [$0.026 (or less) per GB][s3]
  - CloudFront is [$0.085 (or less) per GB served][cloudfront].

[free]: https://aws.amazon.com/free/
[lambda]: https://aws.amazon.com/lambda/pricing/#Lambda.40Edge_pricing_details
[s3]: https://aws.amazon.com/s3/pricing/#Lambda.40Edge_pricing_details
[cloudfront]: https://aws.amazon.com/cloudfront/pricing/#On-demand_Pricing
[staticsite]: ./StaticSite
[readme]: ./README.md
[documentation]: https://www.azquotes.com/quote/1463174
[gitbundle]: https://git-scm.com/book/en/v2/Git-Tools-Bundling
