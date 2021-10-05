# Webflow Git

> A utility to track changes to a Webflow site on GitHub. 

## Introduction

Webflow Git is a simple utility used to monitor and track changes to a Webflow site on GitHub. Both style and content changes are detected and every change is stored as a GitHub commit. 

The utility is simple to set up because it doesn't require access to your Webflow account and all customization can be done via the GitHub web interface.

## Installation

1. Log-in or create a GitHub account.

2. Click the "Use this template" button above the code to generate a new repository based on this template repository:

![Use this template](https://user-images.githubusercontent.com/2506014/134331253-501c4947-e66a-4066-b939-9a48ff001d60.png)

3. Name your new repository the same as your Webflow site domain (e.g. www.example.com). Alternatively, you can choose any repository name and specify the site domain in the [configuration file](#configuration):

![Repository name](https://user-images.githubusercontent.com/2506014/134332104-ee3c654d-6481-465f-b791-56a7dd2c50ca.png)

## Configuration
  
You can customize Webflow Git by editing the [webflowgit.yml](./webflowgit.yml) configuration file. To achieve this, open the file contents and click on the Pen icon:

![Edit configuration](https://user-images.githubusercontent.com/2506014/134331242-fd3da739-705c-4e18-9f37-b6db6398c6ef.png)
  
Make sure to test your changes by [triggering the check manually](#manual-trigger).

### site

Specify URL of the site to be monitored, including the protocol, e.g.:

```
site: https://www.example.com
```

Disable tracking completely:

```
site: false
```

By default, the site domain is the same as your repository name.

### pages

Do not track changes in pages content (track style changes only):

```
pages: false
```

Ignore changes in some pages (for example CMS-generated pages, like blog posts or product pages). This setting uses [glob syntax](https://github.com/micromatch/picomatch#globbing-features):

```
pages:
  ignore:
  - /posts/**
```

By default, all pages are tracked.

## How it works

The utility works by visiting your site at regular intervals and downloading, formatting and comparing the code to the previous revision. If any difference is detected, a new revision is committed to the repository.

### Check frequency

Your site is checked for updates every hour. 

> Advanced: this can be customized by updating the cron schedule in the [workflow configuration file](./.github/workflows/main.yml).

### Manual trigger

You can launch the check manually. To achieve this, click the Actions link on the menu below your project name, then select `webflow-git` workflow and finally click on the "Run workflow" button:

![Trigger manually](https://user-images.githubusercontent.com/2506014/134331249-c2e64b87-3d8d-4dbd-b1d9-46352fd5d3bd.png)
  
## Epilogue
  
This project was created out of frustration with random regressions in Webflow projects. Although there's a built-in backup functionality, it's time-consuming to find out at which point something has broken down, and then, due to the lack of diff functionality, it's very difficult to understand the nature of the modification that caused the regression. The problem becomes even more severe if multiple people develop the same project.

Some parts of this tool are inspired by an excellent [Upptime](https://upptime.js.org/) site monitor, most notably using the GitHub Template and configuration management.

<sub>webflowgitbyloomchild</sub>
