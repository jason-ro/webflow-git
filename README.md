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

### site

### pages
Ignore (since includes cms by default). One example would be to ignore the CMS-generated pages (as they are included by default)

### Snapshot frequency
Every hour
Can be customized by editing the config file (link)
