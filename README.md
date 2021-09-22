# Webflow Git

> A utility to track changes to a Webflow site on GitHub. 

## Introduction

Webflow Git is a simple utility used to monitor and track changes to a Webflow site on GitHub. Both style and content changes are detected, and every change is stored as a GitHub commit. 

The utility is simple to set up because it doesn't require access to your Webflow account and all customization can be done via GitHub web interface.

## Installation

0. Log-in or create a GitHub account.

1. Click "Use this template" button above the code to generate a new repository based on this template repository.

![Use this template]()

2. Name your new repository the same as your Webflow site domain (e.g. www.example.com). Alternatively, you can choose any repository name and specify the site domain in the [configuration file](#configuration).

![Repository name]()

## Configuration
  
You can customize Webflow Git by editing [webflowgit.yml](./webflowgit.yml) configuration file. To do that, open the file contents and click on the Pen icon.

![Edit configuration]()
  
Make sure to test your changes by [triggering the check manually](#manual-trigger).

### site

Specify the site to be monitored, e.g.:

```
site: www.example.com
```

By default the site domain is the same as your repository name.

### pages

Do not track changes in pages content (track only style changes):

```
pages: false
```

Ignore changes in some pages (for example CMS-generated pages, like blog posts or product pages). This setting uses [glob syntax](https://github.com/micromatch/picomatch#globbing-features):

```
pages:
  ignore:
  - /posts/**
```

By default all pages are tracked.

## How it works

The utility works by visiting your site at regular intervals, downloading, formatting and comparing the code to the previous revision. If any difference is detected, a new revision is committed to the repository.

### Check frequency

Your site is checked for updates every hour. 

> Advanced: this can be customized by updating the cron schedule in [workflow configuration file](./.github/workflows/main.yml).

### Manual trigger

You can launch the check manually. To do that click Actions link on the menu below your project name, then select `webflow-git` workflow and finally click on Run workflow.

![Trigger manually]()
  
## Epilogue
  
This project was created out of frustration with random regressions in Webflow projects. Although there's a built-in backup functionality, it's time-consuming to find out at which moment something has broken down, and then, due to lack of diff functionality, it's very difficult to understand the nature of the modification that caused the regression. The problem becomes even more severe if more than one person develops the same project.

Some parts of this tool are inspired by an excellent [Upptime](https://upptime.js.org/) site monitor, most notably using GitHub Template and configuration management.
