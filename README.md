# WP Dark Mode Plugin-Test Automation Suite

## Overview

This repository contains a Cypress test automation suite designed for testing the WP Dark Mode plugin for WordPress. The test suite automates the process of installing, activating, configuring, and validating the WP Dark Mode plugin. It also ensures that the plugin's settings are properly applied and visible in the WordPress admin dashboard.

## Setup Requirements

1. **Node.js and npm:** 
   - Ensure that Node.js and npm are installed on your system. You can download and install them from [Node.js official website](https://nodejs.org/).

2. **Cypress Installation:**
   - Install Cypress as a development dependency in your project:
     ```bash
     npm install cypress --save-dev
     ```

## Test Scenarios

The test suite includes the following scenarios:

1. **Log in to WordPress:**
   - Log in to the WordPress admin dashboard.

2. **Install and Activate WP Dark Mode Plugin:**
   - From admin dashboard -> plugins -> add plugins -> search WP Dark Mode and install and activate it.

3. **Enable and Validate Admin Dashboard Dark Mode:**
   - Navigate to WP Dark Mode → Controls → Admin Panel Dark Mode and enable it.
   - Validate if the dark mode is applied.

4. **Customize WP Dark Mode Settings:**
   - Change Floating Switch Style (select any style except the default).
   - Set Custom Switch Size to 220.
   - Change Floating Switch Position to Left.
   - Disable Keyboard Shortcut from Accessibility Settings.
   - Enable Page-Transition Animation and change the Animation Effect.

5. **Save Settings and Validate:**
   - Save all settings after customization and validate if the dark mode is enabled on the front end.

## How to Use the Test Suite

1. **Clone the Repository:**
   - Clone the repository to your local machine:
     ```bash
     git clone <https://github.com/MDanialShahid/WPPool-Task.git>
     cd <repository-directory>
     ```

2. **Install Dependencies:**
   - Install the necessary dependencies:
     ```bash
     npm install
     ```

3. **Set Up Environment Variables:**
   - Create a `.env` file in the root of the project and add your WordPress credentials and any other required configuration:
     ```
     WP_USERNAME=your-username
     WP_PASSWORD=your-password
     ```

4. **Run Cypress Test Suite:**
   - Open Cypress Test Runner and run the test suite:
     ```bash
     npx cypress open
     ```
   - Alternatively, you can run the tests in headless mode:
     ```bash
     npx cypress run
     ```

5. **View Results:**
   - Results will be displayed in the Cypress Test Runner or terminal output if running in headless mode.

## Demo Video

A demo video showcasing the working of the test suite is available here: [Automation Test Suite_Demo Video](<demo-video-link>).
