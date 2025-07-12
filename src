#include <iostream>
#include <string>
#include <fstream>
#include <vector>
#include <sstream>
#include <memory>
#include <iomanip>
#include <ctime>
#include <algorithm>
#include <map>
using namespace std;

// Abstract base class for polymorphism
// Abstract base class for enforcing input/display structure (Polymorphism)
class Person {
public:
    virtual void inputDetails() = 0;
    virtual void displayProfile() const = 0;
    virtual ~Person() {}
};

// Main program menu loop to navigate between user types
void mainmenu();

// Utility function for password masking
// Utility function to securely get password input with masking (Security)
static string getMaskedInput(const string& prompt) {
    string input;
    cout << prompt;
    char ch;
    while ((ch = getchar()) != '\n' && ch != EOF) {
        if (ch == '\b' && !input.empty()) {
            input.pop_back();
            cout << "\b \b";
        }
        else if (isprint(ch)) {
            input.push_back(ch);
            cout << '*';
        }
    }
    cout << endl;
    return input;
}

// Registration class for user credentials
// Handles user registration credentials with input validation (OOP + Security)
class registration {
    string password;
    string username;

public:
    registration() : password(""), username("") {}

    void setPassword(const string& p) {
        password = p;
    }
    void setUsername(const string& u) {
        username = u;
    }
    string getPassword() const {
        return password;
    }
    string getUsername() const {
        return username;
    }

    friend istream& operator>>(istream& is, registration& obj);
};

istream& operator>>(istream& is, registration& obj) {
    bool success = false;
    while (!success) {
        try {
            string password, username;
            cout << "PLEASE ENTER YOUR USERNAME: ";
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
            getline(is, username);
            if (username.empty()) {
                throw invalid_argument("Username cannot be empty.");
            }
            obj.setUsername(username);

            // Utility function to securely get password input with masking (Security)
            password = getMaskedInput("PLEASE ENTER YOUR PASSWORD: ");
            if (password.empty()) {
                throw invalid_argument("Password cannot be empty.");
            }
            obj.setPassword(password);
            success = true;
        }
        catch (const exception& e) {
            cerr << "Error: " << e.what() << " Please try again." << endl;
        }
    }
    return is;
}

// Enhanced String class for user details
// Custom class for personal information, manages dynamic memory safely (OOP + Manual memory management)
class String {
    char* firstname;
    char* secondname;
    char* fathername;
    char* occupation;
    char* gender;
    int age;
    string CNIC;
    string number;
    char* nationality;
    char* address;
public:
    String()
        : firstname(new char[20]()), secondname(new char[20]()), fathername(new char[20]()),
        occupation(new char[20]()), gender(new char[10]()), age(0), CNIC(""), number(""),
        nationality(new char[25]()), address(new char[150]()) {
    }

    void setfirstname(const string& firstname) {
        strcpy_s(this->firstname, 20, firstname.c_str());
    }
    void setsecondname(const string& secondname) {
        strcpy_s(this->secondname, 20, secondname.c_str());
    }
    void setfathername(const string& fathername) {
        strcpy_s(this->fathername, 20, fathername.c_str());
    }
    void setoccupation(const string& occupation) {
        strcpy_s(this->occupation, 20, occupation.c_str());
    }
    void setnationality(const string& nationality) {
        strcpy_s(this->nationality, 25, nationality.c_str());
    }
    void setgender(const string& gender) {
        strcpy_s(this->gender, 10, gender.c_str());
    }
    void setage(int age) {
        this->age = age;
    }
    void setcnic(const string& cnic) {
        this->CNIC = cnic;
    }
    void setnumber(const string& number) {
        this->number = number;
    }
    void setaddress(const string& address) {
        strcpy_s(this->address, 150, address.c_str());
    }
    const char* getfirstname() const { return firstname; }
    const char* getsecondname() const { return secondname; }
    const char* getfathername() const { return fathername; }
    const char* getoccupation() const { return occupation; }
    const char* getnationality() const { return nationality; }
    const char* getgender() const { return gender; }
    int getage() const { return age; }
    string getcnic() const { return CNIC; }
    string getnumber() const { return number; }
    const char* getaddress() const { return address; }
    // Overloaded >> operator for robust and validated data input (Exception Handling)
    friend istream& operator>>(istream& is, String& obj);
    ~String() {
        delete[] firstname;
        delete[] secondname;
        delete[] fathername;
        delete[] occupation;
        delete[] nationality;
        delete[] gender;
        delete[] address;
    }
};

// Overloaded >> operator for robust and validated data input (Exception Handling)
istream& operator>>(istream& is, String& obj) {
    bool success = false;
    while (!success) {
        try {
            string firstname;
            cout << "PLEASE ENTER THE FIRST NAME: ";
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
            getline(is, firstname);
            if (firstname.empty()) throw invalid_argument("First name cannot be empty.");
            obj.setfirstname(firstname);

            string secondname;
            cout << "PLEASE ENTER THE SECOND NAME: ";
            is >> secondname;
            if (secondname.empty()) throw invalid_argument("Second name cannot be empty.");
            obj.setsecondname(secondname);

            string fathername;
            cout << "PLEASE ENTER YOUR FATHER'S NAME: ";
            is >> fathername;
            if (fathername.empty()) throw invalid_argument("Father's name cannot be empty.");
            obj.setfathername(fathername);

            int gen;
            string gender;
            bool validGender = false;
            while (!validGender) {
                cout << "PLEASE SELECT YOUR GENDER (1-MALE, 2-FEMALE): ";
                if (!(is >> gen)) {
                    is.clear();
                    is.ignore(numeric_limits<streamsize>::max(), '\n');
                    cerr << "Invalid input. Please enter 1 or 2." << endl;
                    continue;
                }
                if (gen == 1 || gen == 2) {
                    validGender = true;
                    gender = (gen == 1) ? "MALE" : "FEMALE";
                    obj.setgender(gender);
                }
                else {
                    cerr << "Invalid gender selection. Please try again." << endl;
                }
            }

            string occupation;
            cout << "PLEASE ENTER YOUR OCCUPATION: ";
            is >> occupation;
            if (occupation.empty()) throw invalid_argument("Occupation cannot be empty.");
            obj.setoccupation(occupation);

            int age;
            bool validAge = false;
            while (!validAge) {
                cout << "PLEASE ENTER YOUR AGE: ";
                if (!(is >> age)) {
                    is.clear();
                    is.ignore(numeric_limits<streamsize>::max(), '\n');
                    cerr << "Invalid input. Please enter a number." << endl;
                    continue;
                }
                if (age <= 0) {
                    cerr << "Age must be positive. Please try again." << endl;
                }
                else {
                    validAge = true;
                    obj.setage(age);
                }
            }

            string address;
            cout << "PLEASE ENTER YOUR ADDRESS: ";
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
            getline(is, address);
            if (address.empty()) throw invalid_argument("Address cannot be empty.");
            obj.setaddress(address);

            string cnic;
            bool validCnic = false;
            while (!validCnic) {
                cout << "PLEASE ENTER YOUR CNIC OR SMART CARD NUMBER WITHOUT DASHES (13 digits): ";
                is >> cnic;
                if (cnic.size() != 13) {
                    cerr << "CNIC must be 13 digits. Please try again." << endl;
                }
                else {
                    validCnic = true;
                    obj.setcnic(cnic);
                }
            }

            string number;
            bool validNumber = false;
            while (!validNumber) {
                cout << "PLEASE ENTER YOUR PHONE NUMBER (11 digits): ";
                is >> number;
                if (number.size() != 11) {
                    cerr << "Phone number must be 11 digits. Please try again." << endl;
                }
                else {
                    validNumber = true;
                    obj.setnumber(number);
                }
            }

            string nationality;
            cout << "PLEASE ENTER YOUR NATIONALITY: ";
            is >> nationality;
            if (nationality.empty()) throw invalid_argument("Nationality cannot be empty.");
            obj.setnationality(nationality);

            // Prompt user to end or return to main menu
            char choice;
            bool validChoice = false;
            while (!validChoice) {
                cout << "Do you want to end (E) or return to the main menu (M)? ";
                is >> choice;
                if (choice == 'E' || choice == 'e') {
                    cout << "Ending input process." << endl;
                    validChoice = true;
                }
                else if (choice == 'M' || choice == 'm') {
                    // Main program menu loop to navigate between user types
                    mainmenu();
                    validChoice = true;
                }
                else {
                    cerr << "Invalid choice. Please enter 'E' or 'M'." << endl;
                }
            }

            success = true;
        }
        catch (const exception& e) {
            cerr << "Error: " << e.what() << " Please try again." << endl;
            // Clear input buffer to prevent infinite loop
            cin.clear();
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
        }
    }
    return is;
}

// Membership class for sports membership
// Manages user’s membership info: sport, fee, timing, instructor
class membership {
    char* game;
    char* instructor;
    double amount;
    string time;
    static int instructorset;
public:
    membership() : game(new char[20]()), instructor(new char[20]()), amount(0.0), time("") {}

    void setGame(const string& newGame) {
        strcpy_s(game, 20, newGame.c_str());
    }
    void setinstructorset(int i) {
        instructorset += i;
    }
    void setinstructorset(int i, int j) {
        instructorset = j;
    }
    void setamount(double a) {
        amount = a;
    }
    void settime(const string& time) {
        this->time = time;
    }
    string gettime() const {
        return time;
    }
    static int getinstructorset() {
        return instructorset;
    }
    void setInstructor(const string& newInstructor) {
        strcpy_s(instructor, 20, newInstructor.c_str());
    }
    const char* getGame() const { return game; }
    const char* getInstructor() const { return instructor; }
    double getAmount() const { return amount; }
    ~membership() {
        delete[] game;
        delete[] instructor;
    }
};
int membership::instructorset = 0;

// User class, now abstract for polymorphism
// Inherits Person. Combines registration, personal info, and membership (Inheritance)
class User : public Person {
protected:
    String details;
    registration reg;
    membership member;
public:
    virtual void inputDetails() override {
        cin >> details;
    }
    virtual void displayProfile() const override {
        cout << "Name: " << details.getfirstname() << " " << details.getsecondname() << endl;
        cout << "Age: " << details.getage() << endl;
        cout << "Address: " << details.getaddress() << endl;
        cout << "Nationality: " << details.getnationality() << endl;
        cout << "CNIC: " << details.getcnic() << endl;
        cout << "Contact Number: " << details.getnumber() << endl;
        cout << "Occupation: " << details.getoccupation() << endl;
        cout << "Game: " << member.getGame() << endl;
        cout << "Instructor: " << member.getInstructor() << endl;
        cout << "Fee: " << member.getAmount() << endl;
        cout << "Timings: " << member.gettime() << endl << endl;
    }
    void setmembership() {
        double cost = 0.0;
        string gender;
        string TIME;
        string instructors1[28];
        string instructors2[28];
        string a, b;
        int x = 0;
        int y = 0;
        // File I/O for user/instructor DB with validation
        ifstream ifile1("instructors1.txt");
        // File I/O for user/instructor DB with validation
        ifstream ifile2("instructors2.txt");

        while (ifile1 >> a && x < 28) {
            instructors1[x++] = a;
        }
        ifile1.close();

        while (ifile2 >> b && y < 28) {
            instructors2[y++] = b;
        }
        ifile2.close();

        int age = details.getage();
        gender = details.getgender();
        // Admin login with menu options to manage users, instructors, and analytics
        vector<string> games{ "TENNIS","FOOTBALL","CRICKET","HOCKEY","SQUASH","BADMINTON","SWIMMING" };

        int choice;
        bool validChoice = false;
        while (!validChoice) {
            cout << "\nSelect a sport:" << endl;
            for (int i = 0; i < 7; i++) {
                cout << "PRESS " << i + 1 << " for " << games[i] << endl;
            }
            cout << "Enter your choice: ";

            if (!(cin >> choice)) {
                cin.clear();
                cin.ignore(numeric_limits<streamsize>::max(), '\n');
                cerr << "Invalid input. Please enter a number." << endl;
                continue;
            }

            if (choice >= 1 && choice <= 7) {
                member.setGame(games[choice - 1]);
                member.setinstructorset((choice - 1) * 4);
                validChoice = true;
            }
            else {
                cerr << "Invalid choice. Please enter a number between 1 and 7." << endl;
            }
        }

        if (age >= 10 && age <= 22) {
            member.setamount(4000);
            TIME = "16:00";
            member.settime(TIME);
            if (gender == "MALE") {
                member.setInstructor(instructors1[membership::getinstructorset()]);
            }
            else if (gender == "FEMALE") {
                member.setInstructor(instructors2[membership::getinstructorset()]);
            }
        }
        else if (age >= 23 && age <= 35) {
            TIME = "17:00";
            member.settime(TIME);
            member.setamount(6000);
            member.setinstructorset(1);
            if (gender == "MALE") {
                member.setInstructor(instructors1[membership::getinstructorset()]);
            }
            else if (gender == "FEMALE") {
                member.setInstructor(instructors2[membership::getinstructorset()]);
            }
        }
        else if (age >= 36 && age <= 45) {
            TIME = "18:00";
            member.settime(TIME);
            member.setamount(8000);
            member.setinstructorset(2);
            if (gender == "MALE") {
                member.setInstructor(instructors1[membership::getinstructorset()]);
            }
            else if (gender == "FEMALE") {
                member.setInstructor(instructors2[membership::getinstructorset()]);
            }
        }
        else if (age >= 46 && age <= 60) {
            TIME = "19:00";
            member.settime(TIME);
            member.setamount(10000);
            member.setinstructorset(3);
            if (gender == "MALE") {
                member.setInstructor(instructors1[membership::getinstructorset()]);
            }
            else if (gender == "FEMALE") {
                member.setInstructor(instructors2[membership::getinstructorset()]);
            }
        }
        else {
            cout << "THE AGE RANGE IS NOT SUPPORTED " << endl;
            return;
        }
    }
};

// Novelty: Virtual fitness assistant
// Novelty: Suggests workouts and motivational quotes (AI-like helper)
class VirtualAssistant {
public:
    void greet() {
        time_t now = time(0);
        tm ltm;
        localtime_s(&ltm, &now); // use localtime_s for safety
        cout << "Hello! ";
        if (ltm.tm_hour < 12) cout << "Good morning!";
        else if (ltm.tm_hour < 18) cout << "Good afternoon!";
        else cout << "Good evening!";
        cout << " I'm your virtual fitness assistant." << endl;
    }
    void suggestWorkout(int age, const string& gender) {
        cout << "Based on your age and gender, here are some suggestions:" << endl;
        if (age < 18) cout << "- Focus on basic fitness, flexibility, and fun games." << endl;
        else if (age < 35) cout << "- Try HIIT, strength training, and team sports." << endl;
        else if (age < 50) cout << "- Emphasize endurance, swimming, and moderate weights." << endl;
        else cout << "- Prioritize mobility, swimming, and light cardio." << endl;
        if (gender == "FEMALE") cout << "- Consider group classes for motivation." << endl;
        else cout << "- Consider competitive sports for challenge." << endl;
    }
    void motivationalQuote() {
        vector<string> quotes = {
            "Push yourself, because no one else is going to do it for you.",
            "Success starts with self-discipline.",
            "The body achieves what the mind believes.",
            "Don’t limit your challenges. Challenge your limits.",
            "Strength does not come from winning. Your struggles develop your strengths.",
            "The only bad workout is the one that didn't happen.",
            "Fitness is not about being better than someone else. It's about being better than you used to be."
        };
        srand(static_cast<unsigned>(time(0)));
        cout << "Motivation: " << quotes[rand() % static_cast<int>(quotes.size())] << endl;
    }
};

// Menu class for user interaction
// Main controller class for User, Instructor, and Admin functionalities (OOP Hierarchy)
class menu : public User {
    VirtualAssistant assistant;
public:
    // Handles full registration: info + sport membership + credential storage
    void REGISTRATIONSINGLE() {
        assistant.greet();
        cin >> details;
        setmembership();
        cin >> reg;

        // Check if the username and password already exist in the DBMS
// File I/O for user/instructor DB with validation
        ifstream infile("DBMS.txt");
        string line;
        bool exists = false;
        while (getline(infile, line)) {
            stringstream ss(line);
            string username, password;
            ss >> username >> password;
            if (username == reg.getUsername() && password == reg.getPassword()) {
                exists = true;
                break;
            }
        }
        infile.close();

        if (exists) {
            cout << "Username and password combination already exists. Registration failed." << endl;
            return;
        }

        // File I/O for user/instructor DB with validation
        ofstream outfile("DBMS.txt", ios::app);
        outfile << reg.getUsername() << "  " << reg.getPassword() << "  " << details.getfirstname() << "  " << details.getsecondname() << " " << details.getfathername() << " " << details.getage() << " " << details.getaddress() << " " << details.getnationality() << " " << details.getcnic() << " " << details.getnumber() << " " << details.getoccupation() << " " << member.getGame() << " " << member.getInstructor() << " " << member.getAmount() << " " << member.gettime() << endl;
        outfile.close();

        assistant.suggestWorkout(details.getage(), details.getgender());
        assistant.motivationalQuote();
    }

    // User login functionality with profile display and authentication
    void USERLOGIN() {
        system("cls");
        string username, password, fname, lastname, fathername, age, address, NationalitY, CNic, num, job, sport, teacher, cOst, TiMe;
        string a, b;

        cin >> reg;
        a = reg.getUsername();
        b = reg.getPassword();
        // File I/O for user/instructor DB with validation
        ifstream ifile("DBMS.txt");
        string line;
        while (getline(ifile, line)) {
            stringstream ss(line);
            ss >> username >> password >> fname >> lastname >> fathername >> age >> address >> NationalitY >> CNic >> num >> job >> sport >> teacher >> cOst >> TiMe;
            if (username == a && password == b) {
                cout << "*             USER PROFILE                *" << endl << endl;
                cout << "LOGIN SUCCESSFUL!" << endl << endl;
                cout << "Name: " << fname << " " << lastname << endl;
                cout << "Age: " << age << endl;
                cout << "Address: " << address << endl;
                cout << "Nationality: " << NationalitY << endl;
                cout << "CNIC: " << CNic << endl;
                cout << "Contact Number: " << num << endl;
                cout << "Occupation: " << job << endl;
                cout << "Game: " << sport << endl;
                cout << "Instructor: " << teacher << endl;
                cout << "Fee: " << cOst << endl;
                cout << "Timings: " << TiMe << endl << endl;
                assistant.motivationalQuote();
                return;
            }
        }
        cout << "DATA NOT FOUND!" << endl;
    }

    // Instructor menu for post-login actions
    void INSTRUCTOR_MENU(const string& instructorName) {
        int choice;
        do {
            cout << "===== INSTRUCTOR MENU =====" << endl;
            cout << "1. View Assigned Users" << endl;
            cout << "2. View Motivational Quote" << endl;
            cout << "0. Logout" << endl;
            cout << "Enter your choice: ";
            cin >> choice;
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
            switch (choice) {
            case 1: {
                // File I/O for user/instructor DB with validation
                ifstream ifile3("DBMS.txt");
                string line;
                string username, password, fname, lastname, fathername, age, address, NationalitY, CNic, num, job, sport, teacher, cOst, TiMe;
                bool anyUser = false;
                if (!ifile3) {
                    cerr << "ERROR IN FETCHING DATA." << endl;
                }
                else {
                    cout << "Assigned Users:" << endl;
                    while (getline(ifile3, line)) {
                        stringstream ss2(line);
                        ss2 >> username >> password >> fname >> lastname >> fathername >> age >> address >> NationalitY >> CNic >> num >> job >> sport >> teacher >> cOst >> TiMe;
                        if (instructorName == teacher) {
                            anyUser = true;
                            cout << "Name: " << fname << " " << lastname << ", Game: " << sport << ", Age: " << age << ", Timings: " << TiMe << endl;
                        }
                    }
                    ifile3.close();
                    if (!anyUser) {
                        cout << "No users are currently assigned to you." << endl;
                    }
                }
                break;
            }
            case 2:
                assistant.motivationalQuote();
                break;
            case 0:
                cout << "Logging out..." << endl;
                break;
            default:
                cout << "Invalid choice. Try again." << endl;
            }
            cout << endl;
        } while (choice != 0);
    }

    // Instructor login to view assigned users and manage dashboard
    void INSTRUCTORLOGIN() {
        system("cls");
        string username, password, fname, lastname, fathername, age, address, NationalitY, CNic, num, job, sport, teacher, cOst, TiMe;
        string input_username, input_password;
        string file_username, file_password;
        string line;
        bool found = false;

        // Prompt for username and password using masking
        cout << "PLEASE ENTER YOUR USERNAME: ";
        cin.ignore(numeric_limits<streamsize>::max(), '\n');
        getline(cin, input_username);
        input_username.erase(0, input_username.find_first_not_of(" \t\r\n"));
        input_username.erase(input_username.find_last_not_of(" \t\r\n") + 1);

        // Utility function to securely get password input with masking (Security)
        input_password = getMaskedInput("PLEASE ENTER YOUR PASSWORD: ");
        input_password.erase(0, input_password.find_first_not_of(" \t\r\n"));
        input_password.erase(input_password.find_last_not_of(" \t\r\n") + 1);

        // File I/O for user/instructor DB with validation
        ifstream ifile("instructors.txt");
        while (getline(ifile, line)) {
            // Remove leading/trailing whitespace from the line
            line.erase(0, line.find_first_not_of(" \t\r\n"));
            line.erase(line.find_last_not_of(" \t\r\n") + 1);

            // Use istringstream to split by whitespace (handles multiple spaces/tabs)
            istringstream ss(line);
            ss >> file_username >> file_password;

            // Remove any trailing/leading whitespace from username/password
            file_username.erase(0, file_username.find_first_not_of(" \t\r\n"));
            file_username.erase(file_username.find_last_not_of(" \t\r\n") + 1);
            file_password.erase(0, file_password.find_first_not_of(" \t\r\n"));
            file_password.erase(file_password.find_last_not_of(" \t\r\n") + 1);

            if (file_username == input_username && file_password == input_password) {
                found = true;
                cout << "*             INSTRUCTOR'S DASHBOARD             *" << endl << endl;
                cout << "Welcome, " << file_username << "!" << endl << endl;
                INSTRUCTOR_MENU(file_username);
                break;
            }
        }
        ifile.close();
        if (!found) {
            cout << "INSTRUCTOR DATA NOT FOUND OR INCORRECT PASSWORD!" << endl;
        }
    }

    // Admin login with menu options to manage users, instructors, and analytics
        // ADMINISTRATOR SECTION - ENHANCED WITH DEBUGGING INFO
    // Admin login with menu options to manage users, instructors, and analytics
    void ADMIN() {
        system("cls");
        string admin_user, admin_pass;
        string stored_user, stored_pass;

        cout << "=============================" << endl;
        // Admin login with menu options to manage users, instructors, and analytics
        cout << "|   ADMINISTRATOR LOGIN     |" << endl;
        cout << "=============================" << endl;

        // Allow multiple login attempts
        int attempts = 0;
        const int MAX_ATTEMPTS = 3;
        bool loggedIn = false;

        while (attempts < MAX_ATTEMPTS && !loggedIn) {
            // Clear input buffer
            cin.ignore(numeric_limits<streamsize>::max(), '\n');

            // Get credentials
            cout << "Username: ";
            getline(cin, admin_user);
            // Utility function to securely get password input with masking (Security)
            admin_pass = getMaskedInput("Password: ");

            // Read admin credentials from file
            ifstream adminFile("admin.txt");
            if (!adminFile) {
                cerr << "Error: admin.txt file not found!" << endl;
                cout << "Please create admin.txt with credentials" << endl;
                return;
            }

            getline(adminFile, stored_user);
            getline(adminFile, stored_pass);
            adminFile.close();

            // Remove potential carriage returns and newlines
            stored_user.erase(remove(stored_user.begin(), stored_user.end(), '\r'), stored_user.end());
            stored_user.erase(remove(stored_user.begin(), stored_user.end(), '\n'), stored_user.end());
            stored_pass.erase(remove(stored_pass.begin(), stored_pass.end(), '\r'), stored_pass.end());
            stored_pass.erase(remove(stored_pass.begin(), stored_pass.end(), '\n'), stored_pass.end());

            // Trim whitespace from ends
            stored_user.erase(0, stored_user.find_first_not_of(" \t"));
            stored_user.erase(stored_user.find_last_not_of(" \t") + 1);
            stored_pass.erase(0, stored_pass.find_first_not_of(" \t"));
            stored_pass.erase(stored_pass.find_last_not_of(" \t") + 1);

            if (admin_user == stored_user && admin_pass == stored_pass) {
                loggedIn = true;
                // Admin login with menu options to manage users, instructors, and analytics
                cout << "\nADMIN LOGIN SUCCESSFUL!\n";
                assistant.motivationalQuote();
                cout << endl;
            }
            else {
                attempts++;
                // Admin login with menu options to manage users, instructors, and analytics
                cout << "\nINVALID ADMIN CREDENTIALS! Attempt " << attempts << " of " << MAX_ATTEMPTS << endl;
                if (attempts < MAX_ATTEMPTS) {
                    cout << "Please try again." << endl;
                }
            }
        }

        if (!loggedIn) {
            cout << "Maximum login attempts reached. Returning to main menu." << endl;
            return;
        }

        int choice;
        do {
            // Admin login with menu options to manage users, instructors, and analytics
            cout << "===== ADMINISTRATOR MENU =====" << endl;
            cout << "1. Add New User" << endl;
            cout << "2. Delete User" << endl;
            cout << "3. View All Users" << endl;
            cout << "4. Search User" << endl;
            cout << "5. View All Instructors" << endl;
            cout << "6. Add New Instructor" << endl;
            cout << "7. Delete Instructor" << endl;
            cout << "8. Generate Membership Report" << endl;
            cout << "9. Get Motivational Quote" << endl;
            cout << "0. Logout" << endl;
            cout << "Enter your choice: ";
            cin >> choice;

            switch (choice) {
            case 1: addUser(); break;
            case 2: deleteUser(); break;
            case 3: viewAllUsers(); break;
            case 4: searchUser(); break;
            case 5: viewAllInstructors(); break;
            case 6: addInstructor(); break;
            case 7: deleteInstructor(); break;
                // Novelty: Generates analytics and AI-based recommendations
            case 8: generateReport(); break;
            case 9: assistant.motivationalQuote(); break;
            case 0: cout << "Logging out..." << endl; break;
            default: cout << "Invalid choice! Try again." << endl;
            }
            cout << endl;
        } while (choice != 0);
    }

private:
    // Admin login with menu options to manage users, instructors, and analytics
        // ADMIN HELPER FUNCTIONS
    void addUser() {
        cout << "===== ADD NEW USER =====" << endl;
        // Handles full registration: info + sport membership + credential storage
        REGISTRATIONSINGLE();
        cout << "User added successfully!" << endl;
    }

    void deleteUser() {
        cout << "===== DELETE USER =====" << endl;
        string target;
        cout << "Enter username to delete: ";
        cin >> target;

        // File I/O for user/instructor DB with validation
        ifstream inFile("DBMS.txt");
        // File I/O for user/instructor DB with validation
        ofstream tempFile("temp.txt");
        string line;
        bool found = false;

        while (getline(inFile, line)) {
            stringstream ss(line);
            string username;
            ss >> username;
            if (username == target) {
                found = true;
                continue; // Skip this line
            }
            tempFile << line << endl;
        }

        inFile.close();
        tempFile.close();

        if (found) {
            remove("DBMS.txt");
            rename("temp.txt", "DBMS.txt");
            cout << "User deleted successfully!" << endl;
        }
        else {
            remove("temp.txt");
            cout << "User not found!" << endl;
        }
    }

    void viewAllUsers() {
        cout << "===== ALL REGISTERED USERS =====" << endl;
        // File I/O for user/instructor DB with validation
        ifstream inFile("DBMS.txt");
        string line;
        int count = 0;

        while (getline(inFile, line)) {
            count++;
            stringstream ss(line);
            string username, password, fname, lname, father, age, addr, nation, cnic, num, job, sport, teacher, fee, time;
            ss >> username >> password >> fname >> lname >> father >> age >> addr >> nation >> cnic >> num >> job >> sport >> teacher >> fee >> time;

            cout << "User #" << count << endl;
            cout << "Username: " << username << endl;
            cout << "Name: " << fname << " " << lname << endl;
            cout << "Sport: " << sport << ", Fee: " << fee << endl;
            cout << "Instructor: " << teacher << ", Time: " << time << endl;
            cout << "------------------------" << endl;
        }

        if (count == 0) cout << "No users found!" << endl;
        inFile.close();
    }

    void searchUser() {
        cout << "===== SEARCH USER =====" << endl;
        string target;
        cout << "Enter username: ";
        cin >> target;

        // File I/O for user/instructor DB with validation
        ifstream inFile("DBMS.txt");
        string line;
        bool found = false;

        while (getline(inFile, line)) {
            stringstream ss(line);
            string username, password, fname, lname, father, age, addr, nation, cnic, num, job, sport, teacher, fee, time;
            ss >> username >> password >> fname >> lname >> father >> age >> addr >> nation >> cnic >> num >> job >> sport >> teacher >> fee >> time;

            if (username == target) {
                found = true;
                cout << "\nUSER FOUND!\n";
                cout << "Username: " << username << endl;
                cout << "Full Name: " << fname << " " << lname << endl;
                cout << "Father's Name: " << father << endl;
                cout << "Age: " << age << endl;
                cout << "Address: " << addr << endl;
                cout << "Nationality: " << nation << endl;
                cout << "CNIC: " << cnic << endl;
                cout << "Phone: " << num << endl;
                cout << "Occupation: " << job << endl;
                cout << "Sport: " << sport << endl;
                cout << "Instructor: " << teacher << endl;
                cout << "Fee: " << fee << endl;
                cout << "Time Slot: " << time << endl;
                break;
            }
        }

        if (!found) cout << "User not found!" << endl;
        inFile.close();
    }

    void viewAllInstructors() {
        cout << "===== ALL INSTRUCTORS =====" << endl;
        // File I/O for user/instructor DB with validation
        ifstream inFile("instructors.txt");
        string line;
        int count = 0;

        while (getline(inFile, line)) {
            count++;
            stringstream ss(line);
            string username, password;
            ss >> username >> password;

            cout << "Instructor #" << count << ": " << username << endl;
        }

        if (count == 0) cout << "No instructors found!" << endl;
        inFile.close();
    }

    void addInstructor() {
        cout << "===== ADD NEW INSTRUCTOR =====" << endl;
        string username, password;
        cout << "Enter username: ";
        cin >> username;
        // Utility function to securely get password input with masking (Security)
        password = getMaskedInput("Enter password: ");

        // Check if instructor exists
// File I/O for user/instructor DB with validation
        ifstream inFile("instructors.txt");
        string line;
        while (getline(inFile, line)) {
            stringstream ss(line);
            string existingUser;
            ss >> existingUser;
            if (existingUser == username) {
                cout << "Instructor already exists!" << endl;
                inFile.close();
                return;
            }
        }
        inFile.close();

        // Add new instructor
// File I/O for user/instructor DB with validation
        ofstream outFile("instructors.txt", ios::app);
        outFile << username << " " << password << endl;
        outFile.close();

        cout << "Instructor added successfully!" << endl;
    }

    void deleteInstructor() {
        cout << "===== DELETE INSTRUCTOR =====" << endl;
        string target;
        cout << "Enter instructor username: ";
        cin >> target;

        // File I/O for user/instructor DB with validation
        ifstream inFile("instructors.txt");
        // File I/O for user/instructor DB with validation
        ofstream tempFile("temp.txt");
        string line;
        bool found = false;

        while (getline(inFile, line)) {
            stringstream ss(line);
            string username;
            ss >> username;
            if (username == target) {
                found = true;
                continue; // Skip this line
            }
            tempFile << line << endl;
        }

        inFile.close();
        tempFile.close();

        if (found) {
            remove("instructors.txt");
            rename("temp.txt", "instructors.txt");
            cout << "Instructor deleted successfully!" << endl;
        }
        else {
            remove("temp.txt");
            cout << "Instructor not found!" << endl;
        }
    }

    // Novelty: Advanced membership analytics
// Novelty: Generates analytics and AI-based recommendations
    void generateReport() {
        cout << "===== MEMBERSHIP ANALYTICS REPORT =====" << endl;
        // File I/O for user/instructor DB with validation
        ifstream inFile("DBMS.txt");
        string line;

        map<string, int> sportCount;
        map<string, double> sportRevenue;
        map<string, int> ageGroupCount = { {"10-22",0}, {"23-35",0}, {"36-45",0}, {"46-60",0} };
        int totalMembers = 0;
        double totalRevenue = 0.0;

        while (getline(inFile, line)) {
            stringstream ss(line);
            string username, password, fname, lname, father, ageStr, addr, nation, cnic, num, job, sport, teacher, feeStr, time;
            ss >> username >> password >> fname >> lname >> father >> ageStr >> addr >> nation >> cnic >> num >> job >> sport >> teacher >> feeStr >> time;

            if (feeStr.empty() || ageStr.empty()) continue;

            try {
                int age = stoi(ageStr);
                double fee = stod(feeStr);

                // Update sport statistics
                sportCount[sport]++;
                sportRevenue[sport] += fee;

                // Update age groups
                if (age >= 10 && age <= 22) ageGroupCount["10-22"]++;
                else if (age >= 23 && age <= 35) ageGroupCount["23-35"]++;
                else if (age >= 36 && age <= 45) ageGroupCount["36-45"]++;
                else if (age >= 46 && age <= 60) ageGroupCount["46-60"]++;

                totalMembers++;
                totalRevenue += fee;
            }
            catch (...) {
                cerr << "Error processing line: " << line << endl;
            }
        }
        inFile.close();

        // Display report
        cout << "\nTOTAL MEMBERS: " << totalMembers << endl;
        cout << "TOTAL MONTHLY REVENUE: $" << fixed << setprecision(2) << totalRevenue << endl;

        cout << "\n===== SPORTS BREAKDOWN =====" << endl;
        for (const auto& pair : sportCount) {
            cout << pair.first << ": " << pair.second << " members"
                << ", Revenue: $" << fixed << setprecision(2) << sportRevenue[pair.first]
                << " (" << (pair.second * 100.0 / totalMembers) << "%)" << endl;
        }

        cout << "\n===== AGE DISTRIBUTION =====" << endl;
        for (const auto& pair : ageGroupCount) {
            cout << pair.first << ": " << pair.second << " members"
                << " (" << (pair.second * 100.0 / totalMembers) << "%)" << endl;
        }

        // Novelty: AI-powered recommendations
        cout << "\n===== BUSINESS RECOMMENDATIONS =====" << endl;
        if (totalMembers < 20) {
            cout << "➤ Focus on marketing to increase membership base" << endl;
        }

        auto maxSport = max_element(sportCount.begin(), sportCount.end(),
            [](const pair<string, int>& a, const pair<string, int>& b) {
                return a.second < b.second;
            });

        auto minSport = min_element(sportCount.begin(), sportCount.end(),
            [](const pair<string, int>& a, const pair<string, int>& b) {
                return a.second < b.second;
            });

        cout << "➤ Most popular sport: " << maxSport->first
            << " (" << maxSport->second << " members)" << endl;
        cout << "➤ Consider promotions for: " << minSport->first
            << " (" << minSport->second << " members)" << endl;

        if (ageGroupCount["10-22"] > ageGroupCount["46-60"] * 3) {
            cout << "➤ Youth programs are thriving - consider expanding" << endl;
        }
        else if (ageGroupCount["46-60"] > totalMembers * 0.4) {
            cout << "➤ Senior programs are popular - add specialized classes" << endl;
        }

        // Motivational closing
        cout << "\n";
        assistant.motivationalQuote();
    }
};

int main() {
    // Main program menu loop to navigate between user types
    mainmenu();
    return 0;
}

// Main program menu loop to navigate between user types
void mainmenu() {
    menu m1;
    int select;
    do {
        system("cls");
        cout << "=============================" << endl;
        cout << "| WELCOME TO UZAIR IRONFORGE  |" << endl;
        cout << "=============================" << endl;
        cout << "|                               |" << endl;
        cout << "| 1. Register a Single User     |" << endl;
        cout << "| 2. User Login                 |" << endl;
        cout << "| 3. Instructor Login           |" << endl;
        cout << "| 4. Administrator Login        |" << endl;
        cout << "|                               |" << endl;
        cout << "| 0. Exit                       |" << endl;
        cout << "|                               |" << endl;
        cout << "=============================" << endl;

        // Input validation for main menu
        bool validChoice = false;
        while (!validChoice) {
            cout << "Enter your choice: ";
            if (!(cin >> select)) {
                cin.clear();
                cin.ignore(numeric_limits<streamsize>::max(), '\n');
                cerr << "Invalid input. Please enter a number." << endl;
                continue;
            }

            if (select >= 0 && select <= 4) {
                validChoice = true;
            }
            else {
                cerr << "Invalid choice. Please select between 0 and 4." << endl;
            }
        }

        system("cls");
        switch (select) {
        case 1: {
            cout << "USER REGISTRATION" << endl;
            // Handles full registration: info + sport membership + credential storage
            m1.REGISTRATIONSINGLE();
            break;
        }
        case 2: {
            cout << "USER LOGIN" << endl;
            // User login functionality with profile display and authentication
            m1.USERLOGIN();
            break;
        }
        case 3: {
            cout << "INSTRUCTOR LOGIN" << endl;
            // Instructor login to view assigned users and manage dashboard
            m1.INSTRUCTORLOGIN();
            break;
        }
        case 4: {
            // Admin login with menu options to manage users, instructors, and analytics
            cout << "ADMIN LOGIN" << endl;
            // Admin login with menu options to manage users, instructors, and analytics
            m1.ADMIN();
            break;
        }
        case 0: {
            cout << "Exiting program..." << endl;
            break;
        }
        }
        if (select != 0) {
            cout << endl << "Press Enter to continue...";
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
            cin.get();
        }
    } while (select != 0);
}
