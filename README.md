# cypress_cucumber_testing
Welcome to the cypress_cucumber_testing repository! This project is dedicated to implementing test techniques, ensuring quality, and practicing the use of JavaScript, Cypress, and Cucumber.
## Purpose
The main objectives of this repository are:
- Implementing test techniques: Explore and apply various testing methodologies to ensure the reliability and stability of software applications.
- Assuring quality: Implement testing strategies to identify and address defects early in the development process, ultimately improving the overall quality of the software.
- Practicing JavaScript, Cypress, and Cucumber: Gain hands-on experience with JavaScript as the primary programming language, Cypress as the end-to-end testing framework, and Cucumber for behavior-driven development (BDD).
## Install dependencies 
 1. npm init -y
 2. npm install cypress --save-dev
 3. npm install @badeball/cypress-cucumber-preprocessor --save-dev
 4. npm install @bahmutov/cypress-esbuild-preprocessor --save-dev
## Configuration  
 1. Update cypress config
cypress.config.js :
####   
    const { defineConfig } = require("cypress");
    const createBundler = require("@bahmutov/cypress-esbuild-preprocessor");
    const preprocessor = require("@badeball/cypress-cucumber-preprocessor");
    const createEsbuildPlugin = require("@badeball/cypress-cucumber-preprocessor/esbuild");
    module.exports = defineConfig({
    e2e: {
    setupNodeEvents(on, config) {
      on("file:preprocessor",
      createBundler({
        plugins: [createEsbuildPlugin.default(config)],
      }));
      preprocessor.addCucumberPreprocessorPlugin(on, config);
      return config;
    },
 	specPattern: "**/*.feature",
    },
    }) 

2. Update "cypress-cucumber-preprocessor" config 
####  
    "cypress-cucumber-preprocessor": {
    "step_definitions": "cypress/support/step_definitions/",
    "nonGlobalStepDefinitions": false}


