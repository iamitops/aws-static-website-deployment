# CloudLaunch — AWS Static Website

A responsive static frontend built with HTML, CSS and vanilla JavaScript. It is designed as a hands-on AWS deployment project.

## Project features

- Responsive desktop, tablet and mobile layout
- Mobile navigation menu
- Cloud/DevOps landing page sections
- No framework or package installation required
- AWS CodeBuild `buildspec.yml` included

## Project structure

```text
aws-static-website/
├── index.html
├── styles.css
├── script.js
├── buildspec.yml
├── .gitignore
└── README.md
```

## Run locally

Open `index.html` in a browser. For a local web server, run:

```bash
python -m http.server 8000
```

Then visit `http://localhost:8000`.

## Push to Git

Create an empty repository in your Git provider, then run these commands from this folder:

```bash
git init
git add .
git commit -m "Initial commit: CloudLaunch static website"
git branch -M main
git remote add origin YOUR_REPOSITORY_URL
git push -u origin main
```

Replace `YOUR_REPOSITORY_URL` with the HTTPS or SSH URL of your own repository.

## AWS deployment — manual S3 hosting

1. Create an S3 bucket with a globally unique name.
2. Upload `index.html`, `styles.css` and `script.js` to the bucket.
3. Enable static website hosting and set `index.html` as the index document.
4. Configure access using an appropriate public-read bucket policy only if using the S3 website endpoint directly. Do not enable public access casually.
5. For a production-style setup, keep the bucket private and use CloudFront with Origin Access Control (OAC), then configure the default root object as `index.html`.
6. Open the CloudFront distribution domain to verify the website.

## AWS CI/CD architecture

```text
Git repository
     |
     v
AWS CodePipeline
     |
     v
AWS CodeBuild (buildspec.yml)
     |
     v
S3 deployment bucket
     |
     v
Amazon CloudFront
     |
     v
Website visitors
```

For a production pipeline, configure a source connection supported by your Git provider, a CodeBuild build stage, and an S3 deploy stage. Add a CloudFront cache invalidation step after deployment if required. Keep AWS permissions least-privilege and never commit credentials or access keys to Git.

## Suggested role description

**Role:** Frontend development and AWS deployment practice.

**Responsibilities:** Created a responsive static website using HTML, CSS and JavaScript; organized the source code in Git; prepared an AWS CodeBuild build specification; and documented the S3 and CloudFront deployment workflow.

## Important

This repository contains the website source and deployment configuration. It does not contain AWS credentials, a live AWS deployment, or a Git remote. Configure those in your own AWS account and Git repository.
