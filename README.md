<!-- Improved compatibility of back to top link: See: https://github.com/othneildrew/Best-README-Template/pull/73 -->

<a name="readme-top"></a>

<!--
*** Thanks for checking out the Best-README-Template. If you have a suggestion
*** that would make this better, please fork the repo and create a pull request
*** or simply open an issue with the tag "enhancement".
*** Don't forget to give the project a star!
*** Thanks again! Now go create something AMAZING! :D
-->

<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->

[![Deployment][github-deployment-shield]][github-deployment-url]
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/zachreborn/resume_website">
    <img src="./media/images/ts_zachary_bw.jpg" alt="Logo" width="300" height="300">
  </a>

<h3 align="center">resume_website</h3>

  <p align="center">
    An up to date resume which captures my philosphy, career, skills, projects, and accolades in a meaningful way. Allows recruiters, hiring managers, and leadership team's to see who I am at a quick glance or read through.
    <br />
    <a href="https://github.com/zachreborn/resume_website"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/zachreborn/resume_website">View Demo</a>
    ·
    <a href="https://github.com/zachreborn/resume_website/issues">Report Bug</a>
    ·
    <a href="https://github.com/zachreborn/resume_website/issues">Request Feature</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->

## About The Project

[![Product Name Screen Shot][product-screenshot]](https://zacharhill.co)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Built With

- ![HTML]
- ![CSS]
- [![AMAZONAWS][aws.amazon.com]][aws-url]
- [![GitHub][github.com]][github-url]

A static HTML/CSS site hosted on **AWS S3** and served through **AWS CloudFront**
(CDN) with **Route 53** DNS. The AWS environment is provisioned with
**Terraform**, and deployments are automated with **GitHub Actions**.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->

## Getting Started

This is a build-free static site &mdash; there is no bundler, package manager, or
container to run. Open the HTML files directly in a browser.

### Prerequisites

- A modern web browser
- (Optional) [Git](https://git-scm.com/) to clone the repository

### Installation

1. Clone the repository
   ```sh
   git clone https://github.com/zachreborn/resume_website.git
   ```
2. Open the site locally
   ```sh
   open index.html
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- DEPLOYMENT -->

## Deployment

Deployments are handled automatically by GitHub Actions:

- **Dev** (`.github/workflows/dev.yml`): runs on pushes to any branch except
  `main`/`master`/`production`/`prod`; syncs the site to the dev S3 bucket.
- **Prod** (`.github/workflows/main.yml`): runs on pushes to `main`; syncs to the
  prod S3 bucket and invalidates the CloudFront cache.
- **Test** (`.github/workflows/test.yml`): runs Super Linter on pull requests.

### AWS authentication (OIDC)

The deployment workflows authenticate to AWS using **GitHub OIDC** rather than
long-lived access keys. Each job assumes an IAM role via
`aws-actions/configure-aws-credentials@v4` using `role-to-assume`. Configure the
following per-environment GitHub Actions variables:

- `AWS_ROLE_ARN` &mdash; IAM role the workflow assumes (trusts the GitHub OIDC provider)
- `AWS_DEV_REGION` / `AWS_PROD_REGION`
- `AWS_DEV_BUCKET_NAME` / `AWS_PROD_BUCKET_NAME`
- `AWS_PROD_CLOUDFRONT_DISTRIBUTION_ID`

The IAM role and its OIDC trust policy are managed in Terraform (see the
[Terraform repository](https://github.com/zachreborn/octo_prod_resume)). No AWS
access keys are stored as repository secrets.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- USAGE EXAMPLES -->

## Usage

See the live site and the [architecture page](https://zacharyhill.co/architecture.html)
for a topology diagram and deployment overview.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- LICENSE -->

## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->

## Contact

Zachary Hill - [![LinkedIn][linkedin-shield]][linkedin-url] - zhill@zacharyhill.co

Project Link: [https://github.com/zachreborn/resume_website](https://github.com/zachreborn/resume_website)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ACKNOWLEDGMENTS -->

## Acknowledgments

- [Zachary Hill](https://zacharyhill.co)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
<!-- [workflow-build-shield]: https://img.shields.io/github/actions/workflow/status/zachreborn/resume_website/main.yml?style=for-the-badge -->
<!-- [workflow-build-url]: https://github.com/zachreborn/resume_website/actions/workflows/main.yml -->

[github-deployment-shield]: https://img.shields.io/github/deployments/zachreborn/resume_website/prod?style=for-the-badge
[github-deployment-url]: https://github.com/zachreborn/resume_website/deployments/activity_log?environment=prod
[contributors-shield]: https://img.shields.io/github/contributors/zachreborn/resume_website.svg?style=for-the-badge
[contributors-url]: https://github.com/zachreborn/resume_website/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/zachreborn/resume_website.svg?style=for-the-badge
[forks-url]: https://github.com/zachreborn/resume_website/network/members
[stars-shield]: https://img.shields.io/github/stars/zachreborn/resume_website.svg?style=for-the-badge
[stars-url]: https://github.com/zachreborn/resume_website/stargazers
[issues-shield]: https://img.shields.io/github/issues/zachreborn/resume_website.svg?style=for-the-badge
[issues-url]: https://github.com/zachreborn/resume_website/issues
[license-shield]: https://img.shields.io/github/license/zachreborn/resume_website.svg?style=for-the-badge
[license-url]: https://github.com/zachreborn/resume_website/blob/master/LICENSE
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/zachary-hill-5524257a/
[product-screenshot]: ./media/images/screenshot.png
[html]: https://img.shields.io/badge/HTML-E34F26?style=for-the-badge&logo=html5&logoColor=white
[css]: https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white
[aws.amazon.com]: https://img.shields.io/badge/AMAZONAWS-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white
[aws-url]: https://aws.amazon.com
[github.com]: https://img.shields.io/badge/Github-181717?style=for-the-badge&logo=github&logoColor=white
[github-url]: https://github.com
