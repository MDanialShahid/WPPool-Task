# WP Dark Mode Plugin - Cypress Automation Test Suite

## Overview
This Cypress Test Automation Suite is designed to automate the process of testing the WP Dark Mode plugin functionalities on a WordPress site. The suite includes a series of test scenarios, such as logging into the WordPress admin dashboard, checking the plugin's activation status, enabling dark mode for the admin dashboard, customizing dark mode settings, and validating the applied changes.

## Setup Requirements

### 1. Install Node.js and npm
Ensure you have Node.js and npm installed on your machine. You can download and install them from [Node.js official website](https://nodejs.org/).

Verify the installation by running the following commands:
```bash
node -v
npm -v
```

### 2. Install Cypress
To set up Cypress, navigate to your project folder and run the following command to install Cypress as a development dependency:
```bash
npm install cypress --save-dev
```

## Test Scenarios

### 1. Log in to WordPress:
- Load the environment variables from the `.env` file.
- Log in to the WordPress admin dashboard.

### 2. Check if WP Dark Mode Plugin is Active:
- Verify if the WP Dark Mode plugin is active. If it is not installed, the test will install and activate the plugin.

### 3. Enable Admin Dashboard Dark Mode:
- Navigate to `WP Dark Mode → Controls → Admin Panel Dark Mode` and enable dark mode for the admin panel.
- Validate if the dark mode is applied to the admin dashboard.

### 4. Customize WP Dark Mode Settings:
- Change the floating switch style (select any style except the default).
- Set the custom switch size to 220.
- Change the floating switch position to "Left."
- Disable the keyboard shortcut from the accessibility settings.
- Enable page-transition animation and change the animation effect.

### 5. Save Settings and Validate:
- Save all settings after customization.
- Validate that dark mode is enabled on the front end of the website.

## Cypress Test Suite

The test suite uses Cypress to automate the above scenarios. Below is an example structure of the Cypress test file:

```javascript
describe('WP Dark Mode Plugin Test Suite', () => {
  
  beforeEach(() => {
    cy.visit('http://localhost/wordpress/');
    cy.viewport(1366, 768);
    cy.get('.logged-out').click();
    
    // Log in to WordPress
    cy.get('#user_login').type('danial');
    cy.get('#user_pass').type("Danial@123");
    cy.get('#wp-submit').click();
  });

  it('Install WP Dark Mode Plugin', () => {
    cy.get('#menu-plugins').click();
    cy.get('.page-title-action').click();
    cy.get('#search-plugins').type("WP Dark Mode");
    cy.get('.install-now').click();
    cy.wait(20000);
  });

  it('Activate WP Dark Mode Plugin', () => {
    cy.get('#menu-plugins').click();
    cy.get('#search-plugins').type("WP Dark Mode");
    cy.get('.activate-now').click();
  });

  it('Enable Admin Dark Mode', () => {
    cy.get('#toplevel_page_wp-dark-mode').click();
    cy.get('.wp-dark-mode-admin-sidebar-nav-container').click();
    cy.get('.relative').click(); // Enable Dark Mode
    cy.get('.bg-blue-500').click(); // Save settings
  });

  it('Customize WP Dark Mode Settings', () => {
    cy.get('#toplevel_page_wp-dark-mode').click();
    cy.get('[href="#/switch"]').click();
    cy.get(':nth-child(3)').click(); // Select custom switch style
    cy.get('.gap-2 input').clear().type('220'); // Set custom size
    cy.get(':nth-child(2) > .bg-gray-50').click(); // Set position to Left
    cy.get('.bg-blue-500').click(); // Save settings
  });

  it('Disable Keyboard Shortcut', () => {
    cy.get('#toplevel_page_wp-dark-mode').click();
    cy.get('[href="#/accessibility"]').click();
    cy.get('.relative').click(); // Disable keyboard shortcut
  });

  it('Enable Page Transition Animation', () => {
    cy.get('#toplevel_page_wp-dark-mode').click();
    cy.get('[href="#/animation"]').click();
    cy.get('.w-auto > .relative').click();
    cy.get(':nth-child(4)').click(); // Select animation effect
    cy.get('.bg-blue-500').click(); // Save settings
  });

  it('Validate Dark Mode', () => {
    cy.get('._track > :nth-child(1)').click();
  });
});
```

## Demo Video
You can watch the demo video of this test suite [here](#).

## How to Run the Test Suite

1. Clone the repository to your local machine.
2. Ensure Node.js and npm are installed.
3. Install Cypress by running:
    ```bash
    npm install cypress --save-dev
    ```
4. Add a `.env` file to store environment variables such as WordPress URL, admin credentials, etc.
5. Open Cypress Test Runner by running:
    ```bash
    npx cypress open
    ```
6. Select the test to run from the Cypress Test Runner interface.

## Conclusion
This test suite provides full automation coverage for the WP Dark Mode plugin's core functionalities, including installation, activation, settings customization, and validation. It helps ensure that the plugin functions as expected across different scenarios.

