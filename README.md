# Debug tool using Playwright

This is a debugging tool for testing your web app on different web engines, such as chromes V8 and safaris Webkit.
This comes in handy if you, for example, are developing in a Windows machine and want to test on Safari browser but don't have access to an Iphone or Mac computer.
This tool can also be set up to test on other browsers aswell, like firefox.
The project is not mine, i actually just followed this guide: https://joyofcode.xyz/test-your-site-in-every-browser

I'm just setting it up for you.

## For installation after cloning repo.

Simply follow these steps:

1. in project root, run: `npm install`
2. Make sure your web app is already running and you have the url, example: it is running on `http://localhost:3000/`
3. Open the file `test/browser.ts` and change the port number to the port your app is running on.
4. Run the project using: `npm run test:safari`

## Here are the steps in the guide, for setting up from scratch:

1. Initialize a new project inside an empty folder:
   `npm init -y`

2. Install @playwright/test as a development dependency:
   `npm i -D @playwright/test`

3. Install the default browsers:
   `npx playwright install`

4. Update package.json

```
   {
     "scripts": {
     "test:chrome": "npx playwright test --headed --browser=chromium",
     "test:firefox": "npx playwright test --headed --browser=firefox",
     "test:safari": "npx playwright test --headed --browser=webkit"
     },
     "devDependencies": {
     "@playwright/test": "^1.22.1" //This is not important, only above changes
     }
   }
```

5. Add a test for Playwright
   Create the file: `tests/browser.test.ts`
   and add the following code:

```
import { test } from '@playwright/test'

test('test browser', async ({ page }) => {
// point this to wherever you want
await page.goto('http://localhost:3000/') // NOTE your app must be running before the test runs, also, port number here must be same as your apps

// keep browser open
await page.pause()
})
```

6. Run the test using one of the scripts.
   `npm run test:safari`
   `npm run test:chrome`
   `npm run test:firefox`

Done. Happy debugging!
