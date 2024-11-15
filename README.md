# Mobile App Automation Tests

This project contains automated tests for a mobile application using appium. The tests cover various functionalities such as form fields, drag and drop actions.

## Project Structure
├── pageobjects

│   ├── dragAndDrop.page.js

│   ├── formFields.page.js

│   ├── home.page.js

│   └── ...

├── tests

│   ├── app.form.fields.test.js

│   ├── app.drag.and.drop.test.js

│   ├── app.swipe.test.js

│   └── ...

├── wdio.conf.js

└── README.md

- **pageobjects/**: Contains the Page Object Model (POM) files that encapsulate the elements and actions for different screens of the app.
- **tests/**: Contains the test files that use the page objects to perform various test scenarios.
- **wdio.conf.js**: Configuration file for WebdriverIO.

## Prerequisites

- Node.js (v14 or higher)
- npm (v6 or higher)
- Appium (v1.20 or higher)
- Android SDK

## Installation

1. Clone the repository:

git clone https://github.com/yourusername/mobile-app-automation-tests.git
cd mobile-app-automation-tests

2. Install the dependencies:

npm install

3. Ensure Appium is installed and running:

npm install -g appium

4. Set up the Android environment:

- Install Android Studio and set up the Android SDK.
- Add the Android SDK tools to your PATH.

## Running Tests

To run the tests, use the following command:

npx wdio wdio.conf.js

## Test Scenarios

### Form Fields Tests

Tests the ability to type different types of data into input fields and validate the text.

### Drag and Drop Tests

Tests the drag and drop functionality to complete a picture.



- **pageobjects/**: Contains the Page Object Model (POM) files that encapsulate the elements and actions for different screens of the app.
- **tests/**: Contains the test files that use the page objects to perform various test scenarios.
- **wdio.conf.js**: Configuration file for WebdriverIO.

## Prerequisites

- Node.js (v14 or higher)
- npm (v6 or higher)
- Appium (v1.20 or higher)
- Android SDK

## Installation

1. Clone the repository:

git clone https://github.com/yourusername/mobile-app-automation-tests.git
cd mobile-app-automation-tests

2. Install the dependencies:

npm install

3. Ensure Appium is installed and running:

npm install -g appium

4. Set up the Android environment:

- Install Android Studio and set up the Android SDK.
- Add the Android SDK tools to your PATH.

## Running Tests

To run the tests, use the following command:

npx wdio wdio.conf.js

## Test Scenarios

### Form Fields Tests

Tests the ability to type different types of data into input fields and validate the text.

### Drag and Drop Tests

Tests the drag and drop functionality to complete a picture.

## Page Objects

### FormFieldsPage
Encapsulates the elements and actions related to the form fields functionality.
### Class: FormFieldsPage

This class defines the elements and actions for interacting with form fields on a sample page.

```javascript
class FormFieldsPage {
    get homeButton() { return $('~Home'); }
    get formsButton() { return $('~Forms'); }
    get textInput() { return $('~text-input'); }
    get switchElement() { return $('~switch'); }

    async openForms() {
        await this.homeButton.waitForDisplayed({ timeout: 20000 });
        await this.formsButton.click();
    }

    async setInputValue(value) {
        await this.textInput.setValue(value);
    }

    async getInputValue() {
        return await this.textInput.getText();
    }

    async toggleSwitch() {
        await this.switchElement.click();
    }

    async getSwitchValue() {
        return await this.switchElement.getText();
    }

    async validateInputValue(expectedValue) {
        const expectedText = expectedValue === '' ? 'Type something' : expectedValue;
        const actualText = await this.getInputValue();
        expect(actualText).toBe(expectedText);
    }

    async validateSwitchValue(expectedValue) {
        const actualValue = await this.getSwitchValue();
        expect(actualValue).toBe(expectedValue);
    }
}

module.exports = new FormFieldsPage();
```

## Reporting

This project uses the `@wdio/allure-reporter` to generate test reports. To view the reports:

1. Run the tests to generate the report data:

npx wdio wdio.conf.js

2. Generate the Allure report:

npx allure generate allure-results --clean

3. Open the Allure report:

npx allure open

The Allure report will open in your default web browser, providing a detailed view of the test results.


## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or bug fixes.
