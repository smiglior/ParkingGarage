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
import PG.Employee;
import org.junit.Test;
import static org.junit.Assert.*;
import java.util.*;

/**
 *
 * @author xomin
 */
public class EmployeeTest {

    @Test
    public void getLicenseTest() {
        Employee e1 = new Employee("cassel", "sam", "Garage Manager", "AKD8374K");
        e1.setLicense("HIJ2574");
        String l = "HIJ2574";
        assertEquals("checking for equality", l, e1.getLicense());
    }

    @Test
    public void setLicenseTest() {
        Employee e1 = new Employee("cassel", "sam", "Garage Manager", "AKD8374K");

        assertTrue("checking for equality", e1.setLicense("HIJ2575"));

    }

    @Test
    public void getLicensePlates() {
        Employee e1 = new Employee("cassel", "sam", "Garage Manager", "AKD8374K");
        e1.setLicense("HIJ2574");
        e1.setLicense("HIJ2575");
        e1.setLicense("HIJ2576");
        e1.setLicense("HIJ2577");
        String[] temp = new String[4];
        temp[0] = "HIJ2574";
        temp[1] = "HIJ2575";
        temp[2] = "HIJ2576";
        temp[3] = "HIJ2577";

        assertArrayEquals("checing for equality", temp, e1.getLicencePlates());
    }

    @Test
    public void printPlatesTest() {
        Employee e1 = new Employee("cassel", "sam", "Garage Manager", "AKD8374K");
        e1.setLicense("HIJ2574");
        e1.setLicense("HIJ2575");
        e1.setLicense("HIJ2576");
        e1.setLicense("HIJ2577");

        List<String> test = Arrays.asList("HIJ2574", "HIJ2575", "HIJ2576", "HIJ2577");

        assertEquals("checking for equality", test, e1.printPlates());
    }

    @Test
    public void getLastNameTest() {
        Employee e1 = new Employee("cassel", "sam", "Garage Manager", "AKD8374K");

        String name = "cassel";
        assertEquals("Check to see equal", name, e1.getLastName());
    }

    @Test
    public void getFirstNameTest() {
        Employee e1 = new Employee("cassel", "sam", "Garage Manager", "AKD8374K");

        String name = "sam";
        assertEquals("Check to see equal", name, e1.getFirstName());
    }

    @Test
    public void getOccupationTest() {
        Employee e1 = new Employee("cassel", "sam", "Garage Manager", "AKD8374K");

        String job = "Garage Manager";
        assertEquals("Check to see equal", job, e1.getOccupation());
    }

    @Test
    public void setHoursTest() {
        Employee e1 = new Employee("cassel", "sam", "Garage Manager", "AKD8374K");
        e1.setHours(20.5);
        double hours = 20.5;

        assertEquals(hours, e1.getHours(), 0);

    }

    @Test
    public void getHoursTest() {
        Employee e1 = new Employee("cassel", "sam", "Garage Manager", "AKD8374K");
        e1.setHours(20.5);
        double hours = 20.5;

        assertEquals(hours, e1.getHours(), 0);

    }

    @Test
    public void getIDTest() {
        Employee e1 = new Employee("cassel", "sam", "Garage Manager", "AKD8374K");
        String temp = "AKD8374K";
        assertEquals("Check for equality", temp, e1.getID());
    }

    @Test
    public void getPaymentTypeTest() {
        Employee e1 = new Employee("cassel", "sam", "Garage Manager", "AKD8374K");

        String temp = "Salary: 72,000.00";

        assertEquals("Check equality", temp, e1.getPaymentType());

        Employee e2 = new Employee("cassel", "sam", "Store Manager", "AKD8374K");

        String temp2 = "Salary: 42,000.00";

        assertEquals("Check equality", temp2, e2.getPaymentType());

        Employee e3 = new Employee("cassel", "sam", "Valet", "AKD8374K");

        String temp3 = "Hourly Rate: 15.00";

        assertEquals("Check equality", temp3, e3.getPaymentType());

        Employee e4 = new Employee("cassel", "sam", "Store Associate", "AKD8374K");

        String temp4 = "Hourly Rate: 12.50";

        assertEquals("Check equality", temp4, e4.getPaymentType());

        Employee e5 = new Employee("cassel", "sam", "Booth Sitter", "AKD8374K");

        String temp5 = "Hourly Rate: 18.00";

        assertEquals("Check equality", temp5, e5.getPaymentType());

    }

    @Test
    public void printPayCheckTest() {
        Employee e1 = new Employee("cassel", "sam", "Garage Manager", "AKD8374K");

        String temp = "PayCheck: 2,769.23";

        assertEquals("Check equality", temp, e1.printPayCheck(72000));

        Employee e2 = new Employee("cassel", "sam", "Store Manager", "AKD8374K");

        String temp2 = "PayCheck: 1,615.38";

        assertEquals("Check equality", temp2, e2.printPayCheck(42000));

        Employee e3 = new Employee("cassel", "sam", "Valet", "AKD8374K");
        e3.setHours(20.5);
        String temp3 = "PayCheck: 307.50";

        assertEquals("Check equality", temp3, e3.printPayCheck(15));

        Employee e4 = new Employee("cassel", "sam", "Store Associate", "AKD8374K");
        e4.setHours(20.5);
        String temp4 = "PayCheck: 256.25";

        assertEquals("Check equality", temp4, e4.printPayCheck(12.50));

        Employee e5 = new Employee("cassel", "sam", "Booth Sitter", "AKD8374K");

        e5.setHours(10);
        String temp5 = "PayCheck: 180.00";

        assertEquals("Check equality", temp5, e5.printPayCheck(18.00));

    }
}
import java.util.*;

public class Customer {

private String lastName, firstName;
private String emailAddress;
private String licensePlate;
private List<String> licensePlates = new ArrayList<>();
private List<String> raffleTickets = new ArrayList<>();

public Customer(String lastN, String firstN, String email, String license) {

lastName = lastN;
firstName = firstN;
emailAddress = email;
licensePlate = license;
licensePlates.add(licensePlate);


}

public  boolean addLicense(String license) {
return licensePlates.add(license);
}

public  boolean removeLicense(String license) {
if (!licensePlates.contains(license)) {
	return false;
} else {
	return licensePlates.remove(license);
}

}

public String getName() {
return lastName + ", " + firstName;
}

public String getFirstName() {

return firstName;
}

public String getLastName() {

return lastName;
}

public String getEmail() {
return emailAddress;
}

public String getLicense() {
return licensePlate;
}

public List<String> printPlates() {

return licensePlates;
}


public String getCustomer() {

return "Last Name: " + lastName + " First Name: " + firstName +
		    "\nEmail Address: " + emailAddress +
	            "\nPlates on File: " + licensePlates.toString();
}

public static void main(String[] args) {
Customer c1 = new Customer("wolf", "lone", "loneWolf@gmail.com", "rxm10937pol");
System.out.println(c1.getName());
System.out.println(c1.getEmail());
System.out.println(c1.getLicense());

c1.addLicense("deck-9op0");
c1.addLicense("call-98yu");
c1.addLicense("mash-45p9");
c1.addLicense("palr-32yt");

System.out.println(c1.getCustomer());
System.out.println(c1.printPlates());
}

}
public class Security {

// id scanner for payment
// leaving gate accessed by certain employees 
// after payment fulfilled gate should open then after 30 seconds gate should close

private Employee empOnDuty;
private String gate;
private boolean isOpen;


public Security(String gateLocation, boolean state){

gate = gateLocation;
isOpen = state;
}

public boolean setState(boolean state){

return isOpen = state;
}

// ternary operator, result = testCondition ? value1 : value2
public String state() {

return isOpen ? "open" : "closed"; 
}

// set employee on duty
public void setEmpOnDuty(Employee duty){

empOnDuty = duty;
}

// get employe on duty
public String getEmpOnDuty() {

return empOnDuty.getEmployeeInfo();
}

public static void main(String[] args){

Security main = new Security("Main Gate", false);
Employee e = new Employee("hanks","Tom","booth sitter");
Customer c1 = new Customer("wolf","lone","loneWolf@gmail.com","rxm786");
main.setEmpOnDuty(e);
System.out.println(main.getEmpOnDuty());
//main.setEmpOnDuty(c1);

}


}
