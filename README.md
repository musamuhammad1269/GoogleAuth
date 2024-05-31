
Here's the text with proper formatting:

Spring Boot Google OAuth2 Authentication
Introduction
This is a Spring Boot application that demonstrates how to implement sign-in, sign-up, and authentication using Google OAuth2. The application is configured to authenticate users with their Google accounts and provides a simple web interface using Thymeleaf.

Features
Google OAuth2 authentication
Customizable login and home pages
Secure endpoints that require authentication
Easy setup and configuration
Prerequisites
Java 11 or higher
Maven
Google Cloud account
Setup and Configuration
Step 1: Clone the Repository
bash
Copy code
git clone https://github.com/your-username/spring-boot-google-oauth2.git
cd spring-boot-google-oauth2
Step 2: Configure Google API
Go to the Google Cloud Console.
Create a new project.
Enable the Google+ API for your project.
Set up OAuth 2.0 credentials:
Navigate to APIs & Services > Credentials.
Click on Create Credentials > OAuth Client ID.
Configure the consent screen with necessary details.
Choose Web Application and configure the authorized redirect URIs (e.g., http://localhost:8080/login/oauth2/code/google).
Note down the Client ID and Client Secret.
Step 3: Configure Application Properties
Update the src/main/resources/application.yml file with your Google Client ID and Client Secret:

yaml
Copy code
spring:
  security:
    oauth2:
      client:
        registration:
          google:
            client-id: YOUR_GOOGLE_CLIENT_ID
            client-secret: YOUR_GOOGLE_CLIENT_SECRET
            scope: profile, email
            redirect-uri: "{baseUrl}/login/oauth2/code/{registrationId}"
            client-name: Google
        provider:
          google:
            authorization-uri: https://accounts.google.com/o/oauth2/auth
            token-uri: https://oauth2.googleapis.com/token
            user-info-uri: https://www.googleapis.com/oauth2/v3/userinfo
            user-name-attribute: sub
Step 4: Build and Run the Application
Build the application:

bash
Copy code
mvn clean install
Run the application:

bash
Copy code
mvn spring-boot:run

