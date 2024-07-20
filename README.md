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


code:

import java.util.Random;
import java.util.Scanner;
interface Colorcode
{
	static String bgred="\u001B[41m";
 	static String bgblue="\u001B[44m";
    static String bgmegenta="\u001B[45";
    static String bggreen="\u001B[42m";
  	static String bgyellow="\u001B[43m";
    static String SET_BOLD_TEXT = "\033[0;1m";
	static String REDBRI= "\033[1;91m";
	static String increaseFontSize = "\033[1;31m";
	static String resetFormatting = "\033[0m";
	static String BOLD="\u001B[1m";
	static String BLINK ="\u001B[5m";
	static String whitebg="\u001B[47m";
	static String black ="\u001B[30m";
	String skblue = "\u001B[36m";
	static String magent = "\u001B[95m";
	static final String ital = "\u001B[3m";
	static String ul = "\u001B[4m";
	static String RESET = "\u001B[0m";
    static String RED = "\u001B[31m";
    static String GREEN = "\u001B[32m";
    static String YELLOW = "\u001B[33m";
	static String BLUE="\u001B[34m";
	static String PURPLE="\u001B[35m";
	static String WHITE="\u001B[37m";
	static String CYAN="\u001B[36m";
	static String ANSI_RED_BACKGROUND = "\u001B[41m";
	//PURPLE	\u001B[35m	
	static String PURPLE_BACKGROUND	= "\u001B[45m";

}


class MobileOTPVerification implements Colorcode {
    static Scanner scanner = new Scanner(System.in);

    static boolean isValidMobileNumber(String MobileNum) {
        return MobileNum.matches("[6789]\\d{9}");
    }

    static int sendOTP(String MobileNum) {
        Random random = new Random();
        int otp = 1000 + random.nextInt(9000);
        System.out.println("OTP sent to " + MobileNum + " " + otp);
        return otp;
    }

    static void otpVerification(String MobileNum) {
	String category = "";
        int otp = sendOTP(MobileNum);
        int userOTP = scanner.nextInt();
        if (userOTP == otp) {
            System.out.println(skblue+"Login Successful"+RESET);
            isSpecifications();
        } else {
            System.out.println(RED+"Incorrect OTP. Login Failed"+RESET);
            System.out.println(RED+"Please Enter The new OTP"+RESET);
            otpVerification(MobileNum);
        }
    }

    static void login() {
	String category = "";
        System.out.println(GREEN+"Enter Mobile Number"+RESET);
        String MobileNum = scanner.nextLine();
        if (isValidMobileNumber(MobileNum)) {
            System.out.println(skblue+"Enter the OTP sent to your Mobile Number"+RESET);
            otpVerification(MobileNum);
        } else {
            System.out.println(BLUE+"Invalid Input. Please enter a 10-digit mobile number starting with 6, 8, 9, or 7"+RESET);
            System.out.println(RED+"Enter valid Mobile Number"+RESET);
            login();
        }
    }

    public static void main(String[] args) // main Method
    {
	String category = "";
        System.out.println(BLINK+skblue+"*** Welcome to Health Care Assist ***"+RESET);
	System.out.println();
        System.out.println(YELLOW+"Please login or exit"+RESET);
	System.out.println();
        System.out.println(BLUE+"1. Login"+RESET);
        System.out.println(BLUE+"2. Exit"+RESET);
        char choice = scanner.next().charAt(0);
        switch (choice) {
            case '1':
		scanner.nextLine();
                login();
                break;
            case '2':
                System.out.println("Exit");
                System.exit(0);
                break;
            default:
                System.out.println("Invalid choice. Please try again.");
                main(args);
                break;
        }
    }

    static void isSpecifications() {
	String category = "";
	System.out.println(PURPLE+"********************************"+RESET);
	System.out.println();
        System.out.println(RED+"1. Body Mass Index of Men"+RESET);
        System.out.println(RED+"2. Body Mass Index of Women"+RESET);
        System.out.println(RED+"3. Health Details"+RESET);
        System.out.println(RED+"4. Basic Medicines"+RESET);
        System.out.println(RED+"5. Exit"+RESET);
        System.out.println(RED+"Enter Your Specification"+RESET);
	System.out.println();
	System.out.println(PURPLE+"********************************"+RESET);
        char specification = scanner.next().charAt(0);
        switch (specification) {
            case '1':
                BodyMassIndex(1);
                break;
            case '2':
                BodyMassIndex(2);
                break;
            case '3':
                healthDetails();
                break;
            case '4':
                BasicMedicines.diseases(scanner);
                break;
            case '5':
                System.out.println("Exit");
                System.exit(0);
                break;
            default:
                System.out.println("Enter your correct specification");
                isSpecifications();
        }
    }

    static void BodyMassIndex(int parameter) {
        System.out.println("Continue 1 Back 2");
        char c = scanner.next().charAt(0);

        if (c == '1') {
            String category = "";
            // Prompt user to input height in meters
	    System.out.println(BLUE+"********************************"+RESET);
	    System.out.println();
            System.out.print(skblue+"Enter your height in meters: "+RESET);
            double height = scanner.nextDouble();
            // Prompt user to input weight in kilograms
	    System.out.println(BLUE+"********************************"+RESET);
	    System.out.println();
            System.out.print(skblue+"Enter your weight in kilograms: "+RESET);
            double weight = scanner.nextDouble();
            // Calculate BMI
            double bmi = calculateBMI(height, weight);
            // Determine BMI category
            if (parameter == 1)
                category = maleDetermineBMICategory(bmi);
            else if (parameter == 2)
                category = femaleDetermineBMICategory(bmi);
            // Output the BMI and category
            System.out.printf("Your BMI is: %.2f%n", bmi);
            System.out.println("BMI Category: " + category);
            System.out.println("Home 1 Stop 2");
            char ch = scanner.next().charAt(0);

            if (ch == '1') {
                isSpecifications();
            } else if(ch == '2'){
                return;
            }
        } else if (c == '2') {
            isSpecifications();
        } else {
            System.out.println("Enter correct option");
            BodyMassIndex(parameter);
        }
    }

    static double calculateBMI(double height, double weight) {
        return weight / (height * height);
    }

    public static String maleDetermineBMICategory(double bmi) {
        if (bmi <= 0.00) {
            System.out.println("You entered the wrong inputs. Please try again");
            return " ";
        } else if (bmi < 18.5) {
            System.out.println("Underweight");
            System.out.println("Due to underweight, you may experience symptoms like Digestion, Respiratory & Low Immunity.");
            return "Please contact Dr. Preethi (Ph-7788556633)";
        } else if (bmi >= 18.5 && bmi < 24.9) {
            System.out.println("Normal Weight");
            System.out.println("You are in High Energy level");
            return "Normally maintain regular diet";
        } else if (bmi >= 25 && bmi < 29.9) {
            System.out.println("Overweight");
            System.out.println("Due to overweight, you may experience symptoms like Diabetes & Depression");
            return "Please contact Dr. Arjun Reddy (Ph-9911334466)";
        } else if (bmi >= 30 && bmi < 34.9) {
            System.out.println("Over Obese");
            System.out.println("Due to Over Obese you may experience symptoms like Heart stroke, Blood pressure, cancer & lung swollen");
            return "Please contact Dr. Ragaranjan Murthy";
        } else {
            return "Overweight due to obesity";
        }
    }

    static String femaleDetermineBMICategory(double bmi) {
        if (bmi <= 0.00) {
            System.out.println("You entered the wrong inputs. Please try again");
            return " ";
        } else if (bmi < 17.5) {
            System.out.println("Underweight");
            System.out.println("Due to underweight, you may experience symptoms like Digestion, Respiratory & Low Immunity.");
            return "Please contact Dr. Preethi (Ph-7788556633)";
        } else if (bmi >= 17.5 && bmi < 23.9) {
            System.out.println("Normal Weight");
            System.out.println("You are in High Energy level");
            return "Normally maintain regular diet";
        } else if (bmi >= 24 && bmi < 28.9) {
            System.out.println("Overweight");
            System.out.println("Due to overweight, you may experience symptoms like Diabetes & Depression");
            return "Please contact Dr. Arjun Reddy (Ph-9911334466)";
        } else if (bmi >= 29 && bmi < 33.9) {
            System.out.println("Over Obese");
            System.out.println("Due to Over Obese you may experience symptoms like Heart stroke, Blood pressure, cancer & lung swollen");
            return "Please contact Dr. Ragaranjan Murthy";
        } else {
            return "Overweight due to obesity";
        }
    }

    static void healthDetails() {
        while (true) {
	    String category = "";
	    System.out.println(CYAN+"********************************"+RESET);
	    System.out.println();
            System.out.println(PURPLE+"Enter your choice:"+RESET);
            System.out.println(PURPLE+"A. Orthopedic Doctor"+RESET);
            System.out.println(PURPLE+"B. Eye Doctor"+RESET);
            System.out.println(PURPLE+"C. Heart Doctor"+RESET);
            System.out.println(PURPLE+"D. Lung Doctor"+RESET);
            System.out.println(PURPLE+"E. Dermatologist"+RESET);
            System.out.println(PURPLE+"F. Neurologist"+RESET);
            System.out.println(PURPLE+"G. Gynecologist"+RESET);
            System.out.println(PURPLE+"H. Psychiatrist"+RESET);
            System.out.println(PURPLE+"I. Back"+RESET);
	    System.out.println();
	    System.out.println(CYAN+"********************************"+RESET);

            char choice = scanner.next().charAt(0);
            switch (choice) {
                case 'A':
                    OrthopedicDoctor orthoDoctor = new OrthopedicDoctor("Dr. Murthy Rao");
                    orthoDoctor.displayDetails();
                    break;
                case 'B':
                    EyeDoctor eyeDoctor = new EyeDoctor("Dr. L.V. Prasad");
                    eyeDoctor.displayDetails();
                    break;
                case 'C':
                    HeartDoctor heartDoctor = new HeartDoctor("Dr. Supriya Reddy");
                    heartDoctor.displayDetails();
                    break;
                case 'D':
                    LungDoctor lungDoctor = new LungDoctor("Dr. Ravi Krishna");
                    lungDoctor.displayDetails();
                    break;
                case 'E':
                    DermatologistDoctor dermatologistDoctor = new DermatologistDoctor("Dr. Priya Sharma");
                    dermatologistDoctor.displayDetails();
                    break;
                case 'F':
                    NeurologistDoctor neurologistDoctor = new NeurologistDoctor("Dr. Rahul Gupta");
                    neurologistDoctor.displayDetails();
                    break;
                case 'G':
                    GynecologistDoctor gynecologistDoctor = new GynecologistDoctor("Dr. Ananya Singh");
                    gynecologistDoctor.displayDetails();
                    break;
                case 'H':
                    PsychiatristDoctor psychiatristDoctor = new PsychiatristDoctor("Dr. Sameer Kapoor");
                    psychiatristDoctor.displayDetails();
                    break;
                case 'I':
                    isSpecifications(); // Go back to the specifications menu
                    break;
                default:
                    System.out.println("Please Enter correct choice!");
                    break;
            }
        }
    }
}

class BasicMedicines implements Colorcode {
    static void cold() {
	System.out.println();
	System.out.println(RED);
        System.out.println("symptoms");
        System.out.println("- runny nose");
        System.out.println("- Sneezing");
        System.out.println("- low grade fever");
        System.out.println("- stuffy");
        System.out.println("if you have like this symptons perfer (Cetirizine-10mg):before sleep");
	System.out.println(RESET);
    }

    static void fever() {
	System.out.println();
	System.out.println(RED);
        System.out.println("symptoms");
        System.out.println("- Vomiting");
        System.out.println("- Headache");
        System.out.println("- Low output if urine or dark urine");
        System.out.println("- Flushed face");
        System.out.println("if you have like this symptons perfer (Paracetamol 650 MG Tablet):before taking a tablet plece had food.");
	System.out.println(RESET);
    }


    static void stomachpain() {
	System.out.println();
	System.out.println(RED);
        System.out.println("Symptoms associated with abdominal pain");
        System.out.println("- Changes in bowel habits");
        System.out.println("- Difficulty swallowing");
        System.out.println("- Bloating or swelling that lasts more than a few days");
        System.out.println("- Unexpected weight loss");
        System.out.println("if you have like this symptons perfer (acetaminophen (Aspirin Free Anacin, Liquiprin, Panadol, Tylenol)): taking a tablet with normal water.");
	System.out.println(RESET);
    }

    static void bodypain() {
	System.out.println();
	System.out.println(RED);
        System.out.println("Symptoms associated with some forms of whole-body pain can include");
        System.out.println("-Joint aches and pains, or aches all over the body.");
        System.out.println("- Numbness and tingling in the upper or lower limbs.");
        System.out.println("- Muscle pain and widespread muscle aches.");
        System.out.println("- Aching with or without fever.");
        System.out.println("if you have like this symptons perfer (ibuprofen and diclofenac):be carefull and don't use reguraly");
	System.out.println(RESET);
    }

    static void toothpain() {
	System.out.println();
	System.out.println(RED);
        System.out.println("Symptoms relate to toothache and swelling");
        System.out.println("- swelling around your tooth and inside your mouth.");
        System.out.println("- swelling of your jaw and face.");
        System.out.println("- pain when chewing.");
        System.out.println("- bleeding from your tooth or gums.");
        System.out.println("if you have like this symptons perfer (Advil, Motrin IB, and generic):before sleep");
	System.out.println(RESET);
    }

    static void Earinfection() {
	System.out.println();
	System.out.println(RED);
        System.out.println("Symptoms of an Earinfection");
        System.out.println("- pain inside the ear.");
        System.out.println("- a high temperature.");
        System.out.println("- difficulty hearing.");
        System.out.println("- itching and irritation in and around the ear.");
        System.out.println("if you have like this symptons perfer drops (Aluminum acetate);shake well before use");
	System.out.println(RESET);
    }

    static void Eyeinfection() {
	System.out.println();
	System.out.println(RED);
        System.out.println("Symptoms of an Eyeinfection");
        System.out.println("- Pain or discomfort.");
        System.out.println("- Itchy eyes.");
        System.out.println("- Feeling that something's on or in your eye.");
        System.out.println("- Burning in your eyes.");
        System.out.println("if you have like this symptons perfer drops (Viscotears liquid gel eye drops (10g));shake well before use");
	System.out.println(RESET);
    }

    static void Allergies() {
	System.out.println();
	System.out.println(RED);
        System.out.println("Symptoms of an allergic reaction include");
        System.out.println("-Rashes.");
        System.out.println("-Hives (a rash with raised red patches) ");
        System.out.println("- Itchy, watery eyes.");
        System.out.println("- Stomach cramps");
        System.out.println("if you have like this symptons perfer drops (Aluminum acetate);shake well before use");
	System.out.println(RESET);
    }

    static void Gastritis() {
	System.out.println(RED);
	System.out.println();
        System.out.println("Stomach upset or pain.");
        System.out.println("- Belching and hiccups.");
        System.out.println("- Nausea and vomiting.");
        System.out.println("- Feeling of fullness or burning in your stomach.");
        System.out.println("- Loss of appetite.");
        System.out.println("if you have like this symptons perfer tablet (Pantazole 10mg);early morning before food.");
	System.out.println(RESET);
    }

    static void diseases(Scanner scanner) {
        char op;
        while(true) {
	    
	    System.out.println(CYAN+"**********************************"+RESET);
	    System.out.println();
	    
            System.out.println(CYAN+"enter the option: "+RESET);
            System.out.println(CYAN+"enter a for cold ");
            System.out.println("enter b for fever ");
            System.out.println("enter c for stomach pain");
            System.out.println("enter d for body pain");
            System.out.println("enter e for tooth pain");
            System.out.println("enter f for Earinfection");
            System.out.println("enter g for Eyeinfection");
            System.out.println("enter h for Allergies");
	    System.out.println("enter i for Gastristis");
            System.out.println("enter z to go back to main home"+RESET);
	    System.out.println();
	    System.out.println(CYAN+"**********************************"+RESET);
		
            op = scanner.next().charAt(0);
            switch (op) {
                case 'a':
                  cold();
                  break;

                case 'b':
                    fever();
                    break;

                case 'c':
                    stomachpain();
                    break;

                case 'd':
                   bodypain();
                    break;

                case 'e':
                   toothpain();
                   break;

                case 'f':
                  Earinfection();
                    break;

                case 'g':
                   Eyeinfection();
                    break;
		
		case 'h':
                Allergies();
                    break;

                case 'i':
                  Gastritis();
                    break;
		
		case 'z':
		MobileOTPVerification.isSpecifications();
		break;

                default: {
                    System.out.println("invalid input. enter correct option");
                    break;
                }
            }
      }  
    }
}

abstract class Doctor {
    String name;
    String specialty;

    Doctor(String name, String specialty) {
        this.name = name;
        this.specialty = specialty;
    }

    abstract void displayDetails();
}

// Concrete class for OrthopedicDoctor
class OrthopedicDoctor extends Doctor implements Colorcode{
    OrthopedicDoctor(String name) {
        super(name, "Orthopedic");
    }

    @Override
    void displayDetails() {
	String category = "";
	System.out.println(GREEN);
        System.out.println("Name: " + name);
        System.out.println("Specialty: " + specialty);
        System.out.println("Available for: Legs and Hand injuries");
        System.out.println("Hospital Name: CARE HOSPITAL");
        System.out.println("Available time: 10:00 AM - 5:00 PM");
        System.out.println("Experience: 12 years");
	System.out.println(RESET);
	
        System.out.println();
    }
}

// Concrete class for EyeDoctor
class EyeDoctor extends Doctor implements Colorcode{
    EyeDoctor(String name) {
        super(name, "Ophthalmologist");
    }

    @Override
    void displayDetails() {
	String category = "";
	System.out.println(CYAN);
        System.out.println("Name:" + name);
        System.out.println("Specialty:  " + specialty);
        System.out.println("Available for: Eye related issues");
        System.out.println("Hospital Name: L.V PRASAD EYE HOSPITAL");
        System.out.println("Available time: 11:00 AM - 7:00 PM");
        System.out.println("Experience: 20 years");
	System.out.println(RESET);
        System.out.println();
    }
}

// Concrete class for HeartDoctor
class HeartDoctor extends Doctor implements Colorcode {
    HeartDoctor(String name) {
        super(name, "Cardiologist");
    }

    @Override
    void displayDetails() {
	String category = "";
	System.out.println(CYAN);
        System.out.println("Name:  " + name);
        System.out.println("Specialty: " + specialty);
        System.out.println("Available for: Heart related issues");
        System.out.println("Hospital Name: APOLLO HOSPITAL");
        System.out.println("Available time: 10:30 AM - 6:00 PM");
        System.out.println("Experience: 10 years");
        System.out.println(RESET);
	System.out.println();
    }
}

// Concrete class for LungDoctor
class LungDoctor extends Doctor implements Colorcode{
    LungDoctor(String name) {
        super(name, "Pulmonologist");
    }

    @Override
    void displayDetails() {
	String category = "";
	System.out.println(GREEN);
        System.out.println("Name: " + name);
        System.out.println("Specialty:  " + specialty);
        System.out.println("Available for: Lung related issues");
        System.out.println("Hospital Name: YASHODA HOSPITAL");
        System.out.println("Available time: 12:00 AM - 8:00 PM");
        System.out.println("Experience: 8 years");
	System.out.println(RESET);
        System.out.println();
    }
}

class DermatologistDoctor extends Doctor implements Colorcode{
    DermatologistDoctor(String name) {
        super(name, "Dermatologist");
    }

    @Override
    void displayDetails() {
	String category="";
	System.out.println(GREEN);
        System.out.println("Name: " + name);
        System.out.println("Specialty: " + specialty);
        System.out.println("Available for: Skin-related issues");
        System.out.println("Hospital Name: SKIN CARE HOSPITAL");
        System.out.println("Available time: 9:00 AM - 4:00 PM");
        System.out.println("Experience: 15 years");
	System.out.println(RESET);
        System.out.println();
    }
}

class NeurologistDoctor extends Doctor implements Colorcode {
    NeurologistDoctor(String name) {
        super(name, "Neurologist");
    }

    @Override
    void displayDetails() {
	String category = "";
	System.out.println(CYAN);
        System.out.println("Name: " + name);
        System.out.println("Specialty: " + specialty);
        System.out.println("Available for: Deals with disorders of the nervous system");
        System.out.println("Hospital Name: NEUROLOGY CENTER");
        System.out.println("Available time: 10:00 AM - 6:00 PM");
        System.out.println("Experience: 18 years");
	System.out.println(RESET);
	System.out.println();
    }
}

class GynecologistDoctor extends Doctor implements Colorcode{
    GynecologistDoctor(String name) {
        super(name, "Gynecologist");
    }

    @Override
    void displayDetails() {
	String category = "";
	System.out.println(GREEN);
        System.out.println("Name: " + name);
        System.out.println("Specialty: " + specialty);
        System.out.println("Available for: Focuses on women's reproductive health");
        System.out.println("Hospital Name: WOMEN'S HEALTH CLINIC");
        System.out.println("Available time: 8:00 AM - 6:00 PM");
        System.out.println("Experience: 12 years");
	System.out.println(RESET);
        System.out.println();
    }
}

class PsychiatristDoctor extends Doctor implements Colorcode{
    PsychiatristDoctor(String name) {
        super(name, "Psychiatrist");
    }

    @Override
    void displayDetails() {
	String category = "";
	System.out.println(CYAN);
        System.out.println("Name: " + name);
        System.out.println("Specialty: " + specialty);
        System.out.println("Available for: Deals with mental health and disorders");
        System.out.println("Hospital Name: MIND CARE HOSPITAL");
        System.out.println("Available time: 10:00 AM - 6:00 PM");
        System.out.println("Experience: 20 years");
	System.out.println(RESET);
        System.out.println();
    }
}
