# Webflow Git

> A utility to track changes to a Webflow site on GitHub. 

## Introduction

Webflow Git is a simple utility used to track changes to a Webflow site on GitHub. Both style and content changes are tracked, and every modification is stored as a GitHub commit. It's simple to setup, because it doesn't require access to your Webflow account and all configuration can be done via GitHub web interface.

It works by taking a snapshot of the site at regular intervals, formatting the code and comparing it to the previous revision. If it detects any difference, it commits the change to the repository.

## Usage

1. Click "Use this template" button above the code to start generating a new repository based on this one.
<screenshot>

2. Name your new repository the same as your site domain, for example www.example.com. Alternatively you can choose any name you prefer, and specify the domain in the [configuration](#Configuration) file.
<screenshot>

## Configuration
  
You can customize Webflow Git by editing [webflowgit.yml](./webflowgit.yml) configuration file.

### site

### pages
Ignore (since includes cms by default). One example would be to ignore the CMS-generated pages (as they are included by default)

### Snapshot frequency
Every hour
Can be customized by editing the config file (link)
  
## Epilogue
  
This project was created out of frustration to fix regressions on Webflow projects. Although there's a built-in backup functionality, it's time-consuming to find out at which point something has broken down, and then, due to lack of diff functionality, it's very difficult to understand the nature of the modification that caused the issue.

Some parts of this tool are inspired by an excellent [Upptime](https://upptime.js.org/) site monitor., most notably using GitHub Teamplate and configuration management.
