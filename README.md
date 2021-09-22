# Webflow Git

> A utility to track changes to a Webflow site on GitHub. 

## Introduction

Webflow Git is a simple utility used to monitor changes to a Webflow site on GitHub. Both style and content changes are tracked, and every change is stored as a GitHub commit. 

The utility is simple to set up because it doesn't require access to your Webflow account and all customization can be done via GitHub web interface.

## Usage

0. Log-in or create a GitHub account.

1. Click "Use this template" button above the code to start generating a new repository based on this one.

![Use this template]()

2. Name your new repository the same as your site domain (e.g. www.example.com). Alternatively, you can choose any name you like and specify the domain in the [configuration](#configuration).

![Repository name]()

## Configuration
  
You can customize Webflow Git by editing [webflowgit.yml](./webflowgit.yml) configuration file. To do that, open the file contents and click on the Pen icon.

![Edit configuration]()
  
Make sure to test your changes by [triggering the check manually](#manual-trigger).

### site

Specify the site to be 

### pages
Ignore (since includes CMS by default). One example would be to ignore the CMS-generated pages (as they are included by default)

## How it works

The utility works by visiting your site at regular intervals, downloading, formatting and comparing the code to the previous revision. If any difference is detected, a new revision is committed to the repository.

### Check frequency

Your site is checked for updates every hour. 

> Advanced: this can be customized by updating the cron schedule in [workflow configuration file](./.github/workflows/main.yml).

### Manual trigger

You can launch the check manually by clicking on actions on the menu below your project name, then select `webflow-git` workflow and finally click on Run workflow.

![Trigger manually]
  
## Epilogue
  
This project was created out of frustration with random regressions in Webflow projects. Although there's a built-in backup functionality, it's time-consuming to find out at which moment something has broken down, and then, due to lack of diff functionality, it's very difficult to understand the nature of the modification that caused the regression. The problem becomes even more severe if more than one person develops the same project.

Some parts of this tool are inspired by an excellent [Upptime](https://upptime.js.org/) site monitor, most notably using GitHub Template and configuration management.
