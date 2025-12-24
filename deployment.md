# Deployment Workflow (GitHub → SiteGround via SFTP)

This document describes how deployments work for this site and how to publish changes going forward.

The site is a static HTML/CSS site deployed automatically to SiteGround using **GitHub Actions + SFTP**.

---

## Step 4: Commit and Push the Deployment Workflow

Once the GitHub Actions workflow file has been created at:

.github/workflows/deploy.yml

commit and push it to the `main` branch.

### Commands

```bash
git add .github/workflows/deploy.yml
git commit -m "Add SiteGround SFTP deploy workflow"
git push origin main

What Happens Next

GitHub detects a push to the main branch

A GitHub Actions workflow is triggered

The workflow:

Checks out the repository

Uploads all files at the repo root to SiteGround via SFTP

Files are deployed to:

/public_html/

How to Verify

Go to the repository on GitHub

Click the Actions tab

Click the most recent workflow run

Confirm all steps complete successfully (green checkmark)

If the workflow completes successfully, the deployment is live.

Go-Forward Workflow (Day-to-Day Use)

After initial setup, no manual FTP uploads are required.

Standard Update Process

Make changes locally (HTML, CSS, images, etc.)

Commit the changes

Push to main

git status
git commit -am "Describe your change"
git push origin main

Result

GitHub automatically deploys the updated site

Changes are live within seconds to a minute

No interaction with SiteGround UI is required

Repository Structure Expectations

The repository root should contain the site files directly:

index.html
styles.css
assets/
  images/

Important Notes

The main branch is the production branch

Any push to main triggers a deployment

SFTP credentials are stored securely as GitHub Secrets

The server directory is already scoped to public_html

Troubleshooting

Deployment fails
→ Check the GitHub Actions logs for authentication or connection errors

Site updates not visible
→ Hard refresh browser cache
→ Confirm files were uploaded in the Actions log

Assets missing
→ Verify relative paths and filename casing (Linux servers are case-sensitive)

Summary

GitHub is the source of truth

GitHub Actions handles deployment

SiteGround only receives built files

Deployment is automatic, repeatable, and auditable
