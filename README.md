# Debug tool using Playwright

This debugging tool allows you to test your web app on various web engines, such as Chrome's V8 and Safari's WebKit. It's particularly useful if you're developing on a Windows machine and need to test your app in the Safari browser without access to an iPhone or Mac computer. Additionally, the tool can be configured to test other browsers like Firefox. Note: This project isn't my original creation—I simply followed this guide: https://joyofcode.xyz/test-your-site-in-every-browser

I'm just setting it up for you.

## For installation after cloning repo

Simply follow these steps:

1. Open with editor.
2. in project root and in terminal run: `npm install`
3. Make sure your web app is already running and you have the url, example: it is running on `http://localhost:3000/`
4. Open the file `test/browser.ts` and change the port number to the port your app is currently running on.
5. Run the project using: `npm run test:safari` or `npm run test:chrome` or `npm run test:firefox`

The tool will open two windows, one where you can see your app running and the second a controller for the tool.
You can also open inspector tool, just like in the web browser.

Happy debugging!

## Steps in the guide

### No need for this if above steps were taken.

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
