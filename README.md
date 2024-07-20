# Java-command-output
Doctor Recommendation System command based oops project

Mobile OTP Verification System:

Overview:

This project is a Java-based application that provides a mobile OTP verification system. The system allows users to verify their mobile numbers using OTP (One-Time Password) and offers health-related information based on user input.

Features:

Mobile Number Validation: Checks if the mobile number is valid.
OTP Generation and Verification: Sends a randomly generated OTP to the user's mobile number and verifies it.
Health Specifications: Provides options to view health details and basic medicines based on symptoms.
Doctor Information: Displays details of various doctors based on their specialty.
Technologies Used:

-Java
-Scanner (for user input)
-Random (for OTP generation)
-Project Structure
-Colorcode Interface: Contains ANSI color codes used for formatting text output.
-MobileOTPVerification Class: Handles OTP verification, user login, and displays health specifications.
-BasicMedicines Class: Provides information on basic medicines for common ailments.
-Doctor Abstract Class: Base class for different types of doctors.
-Concrete Doctor Classes: OrthopedicDoctor, EyeDoctor, HeartDoctor, LungDoctor, DermatologistDoctor, NeurologistDoctor, GynecologistDoctor, and 
 PsychiatristDoctor extend Doctor and implement specific details.
 Usage
-Run the Application: Execute the MobileOTPVerification class to start the application.
-Login: Enter a valid mobile number to receive an OTP. Input the OTP to log in.
-Select Options: After logging in, choose from various health specifications and doctor details.
