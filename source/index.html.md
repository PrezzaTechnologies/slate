---
title: Checkbox 7 API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:

includes:
  - authentication
  - roles
  - contacts
  - contact-list-security
  - current-contact
  - contact-groups
  - contact-groups-access
  - survey-list
  - survey-folders
  - surveys
  - survey-settings
  - survey-access
  - survey-pages
  - survey-items
  - survey-language-settings
  - files
  - system-settings
  - license-limits
  - single-sign-on
  - errors
  

search: true
---

# Getting Started

<aside class="warning">This documentation is for Checkbox 7 which has not been released yet. For current API documentation please visit <a href="https://www.checkbox.com/developer-center/">https://www.checkbox.com/developer-center/</a></aside>


The Checkbox API is a REST-based JSON API that utilizes OAuth 2.0. The documentation on this page is organized by API Endpoint and code examples are provided in shell. 

To use our API you will need a active Checkbox 7 account. The API documentation provided is valid for both On-Premise and Checkbox Online customers. 

Checkbox Online customers will use their account name where instructed while server customers can leave the parameter blank. 

On-premise customers have no limits on API usage, but the API is only available for Checkbox Online customers with a professional plan or higher. There are no "hard-limits" on the amount of API requests you can make, however mis-use of the API can cause the API to be disabled. 

`API URL: https://api.checkbox.com/v1/{ACCOUNT_NAME}`

<aside class="notice">
You must replace <code>{ACCOUNT_NAME}</code> with your account name.
</aside>



