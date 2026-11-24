# StudyTrack

A student task tracker built with HTML, CSS and JavaScript, hosted on **Amazon S3** and delivered through **Amazon CloudFront**.

**Live site:** https://d3uinhdz6kb4cg.cloudfront.net

![StudyTrack dashboard](screenshots/02-app-live.png)

## Features

- Summary cards: total, pending, completed and overdue tasks
- Task list with search, status filter and priority filter
- Add, edit and delete tasks
- Views for Overview, Due today, Upcoming and Completed
- "Coming up" panel for the next deadlines

## Architecture

```
Visitor  ->  CloudFront  ->  S3 bucket (private, static files)
```

## Project Structure

```
index.html
css/
js/
```

## Setup

1. Create an S3 bucket (this project uses `studytrack-24-11-26` in `eu-north-1`) and keep it private.
2. Upload `index.html`, `css/` and `js/`, keeping the folder structure.
3. Create a CloudFront distribution with the bucket as its origin and origin access control enabled.
4. Set the default root object to `index.html`.
5. Add the bucket policy provided by CloudFront so the distribution can read the files.

![CloudFront origin](screenshots/03-cloudfront-origin.png)

## Verification

1. Wait until the distribution status is **Enabled**.
2. Open the CloudFront domain name in a browser.
3. Confirm the dashboard loads with styling, then add a task and check the summary cards update.

## Updating the App

Upload the changed files to the bucket, then create a CloudFront invalidation (e.g. `/*`) so the update shows immediately.

## Documentation

See [StudyTrack_S3_CloudFront_Documentation.docx](StudyTrack_S3_CloudFront_Documentation.docx) for the full step-by-step guide.
