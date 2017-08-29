# primo-explore-custom-no-search-results

## Description

Create a custom no results templates.

## Installation

1. Assuming you've installed and are using [primo-explore-devenv](https://github.com/ExLibrisGroup/primo-explore-devenv).

2. Navigate to your template/central package root directory. For example:
  ```
  cd primo-explore/custom/MY_VIEW_ID
  ```
3. If you do not already have a package.json file in this directory, create one:
  ```
  npm init -y
  ```
4. Install this package:
  ```
  npm install primo-explore-custom-no-search-results --save-dev
  ```

## Usage

Once installed, inject `customNoSearchResults` as a dependency:

```
let app = angular.module('viewCustom', ['customNoSearchResults'])
```

**Note:** If you're using the --browserify build option, you will need to first import the module with:

```
import 'primo-explore-custom-no-search-results';
```

You'll need to set a `customNoSearchResultsTemplateUrl` value in your `main.js` to point to your custom no search results template:

```
app.value('customNoSearchResultsTemplateUrl', 'custom/MY_VIEW_ID/html/noSearchResult.html);
```

## Example

```
// main.js

import 'primo-explore-custom-no-search-results';

let app = angular.module('viewCustom', ['customNoSearchResults']);

app.value('customNoSearchResultsTemplateUrl', 'custom/MY_VIEW_ID/html/noSearchResult.html);

// html/customNoSearchResults.html

<md-card class="default-card zero-margin _md md-primoExplore-theme">
  <md-card-title>
    <md-card-title-text>
      <span translate="" class="md-headline">No records found</span>
    </md-card-title-text>
  </md-card-title>
  <md-card-content>
    <p>
      <span>Your search returned 0 results. Try one of the options below:</span>
    </p>
    <ul>
      <li><a ng-href="https://ezborrow.url?query={{ $ctrl.parentCtrl.term }}">Request a book from E-ZBorrow (NYU only)</a></li>
      <li><a ng-href="http://www.worldcat.org/search?qt=worldcat_org_all&q={{ $ctrl.parentCtrl.term }}">Search WorldCat for items in nearby libraries</a></li>
      <li><a href="http://library.institution.edu">Ask a Librarian</a></li>
    </ul>
  </md-card-content>
</md-card>
```