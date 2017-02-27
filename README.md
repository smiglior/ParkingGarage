# ParkingGarage
380 assignment
import java.util.*;
import java.text.DecimalFormat;

public class Employee {

    DecimalFormat f = new DecimalFormat("#,###.00");
    private String lastName, firstName;
    private String jobTitle;
    private String license;
    private List<String> licensePlates = new ArrayList<>();
    private double salary, hourlyWage, hours;
    private String id;

    public Employee(String lName, String fName, String job, String id) {

        lastName = lName;
        firstName = fName;
        jobTitle = job;
        this.id = id;

    }

    public String getEmployeeInfo() {

        return "Name: " + lastName + ", " + firstName + "\nOccupation: " + jobTitle + id;
    }

    public String getID() {
        return id;
    }

    public boolean setLicense(String lPlate) {

        license = lPlate;
      return licensePlates.add(license);
    }

    public String getLicense() {

        return license;
    }

    public String[] getLicencePlates() {

        String[] temp;
        temp = new String[licensePlates.size()];
        licensePlates.toArray(temp);
        return temp;
    }

    public List<String> printPlates() {

        return licensePlates;
    }

    public String getPaymentType() {

        if (jobTitle.equalsIgnoreCase("Valet")) {
            hourlyWage = 15.00;
            return "Hourly Rate: " + f.format(hourlyWage);
        } else if (jobTitle.equalsIgnoreCase("Store Associate")) {
            hourlyWage = 12.50;
            return "Hourly Rate: " + f.format(hourlyWage);
        } else if (jobTitle.equalsIgnoreCase("Booth Sitter")) {
            hourlyWage = 18.00;
            return "Hourly Rate: " + f.format(hourlyWage);
        } else if (jobTitle.equalsIgnoreCase("Store Manager")) {
            salary = 42000;
            return "Salary: " + f.format(salary);
        } else if (jobTitle.equalsIgnoreCase("Garage Manager")) {
            salary = 72000;
            return "Salary: " + f.format(salary);
        } else {
            return "The job description you are looking for is no longer available "
                    + "here at Chip&Dales Garage. Sorry for the inconvenience.";

        }
    }

    public void setHours(double h) {

        hours = h;
    }

    public double getHours() {

        return hours;
    }

    public String printPayCheck(double wage) {
                hourlyWage = wage;
                salary = wage;
        if (jobTitle.equalsIgnoreCase("Valet")) {
            return "PayCheck: " + f.format(hourlyWage * hours);
        } else if (jobTitle.equalsIgnoreCase("Store Associate")) {
            return "PayCheck: " + f.format(hourlyWage * hours);
        } else if (jobTitle.equalsIgnoreCase("Booth Sitter")) {
            return "PayCheck: " + f.format(hourlyWage * hours);
        } else if (jobTitle.equalsIgnoreCase("Store Manager")) {
            return "PayCheck: " + f.format(salary / 26);
        } else if (jobTitle.equalsIgnoreCase("Garage Manager")) {
            return "PayCheck: " + f.format(salary / 26);
        } else {
            return "No paycheck to be calculated";
        }

    }

    public String getLastName() {

        return lastName;
    }

    public String getFirstName() {

        return firstName;
    }

    public String getOccupation() {

        return jobTitle;
    }
}
