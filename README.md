# Repository-13
Many programs written with inheritance could be written with composition instead, and vice versa. Rewrite class BasePlusCommissionEmployee (Fig. 9.11) of the CommissionEmployee– BasePlusCommissionEmployee hierarchy to use composition rather than inheritance.
//BasePlusCommission Employee Class
public class BasePlusCommissionEmployee
{
   private CommissionEmployee CE;
   private double baseSalary; // base salary per week

   // six-argument constructor
   public BasePlusCommissionEmployee(String firstName, String lastName, 
      String socialSecurityNumber, double grossSales, 
      double commissionRate, double baseSalary)
   {
      CE=new CommissionEmployee(firstName,lastName, 
      socialSecurityNumber,grossSales,commissionRate);
      
      // if baseSalary is invalid throw exception
      if (baseSalary < 0.0)                   
          throw new IllegalArgumentException(
             "Base salary must be >= 0.0");  

       this.baseSalary = baseSalary;
   }
   
   //set first name
   public void setFirstName(String firstName)
   {
      CE.setFirstName(firstName);
   }
   //get first name
   public String getFirstName()
   {
	   return CE.getFirstName();
   }
   
   //set Last name
   public void setLastName(String lastName)
   {
      CE.setLastName(lastName);
   }
   //get last name
   public String getLastName()
   {
	   return CE.getLastName();
   }
   
   //set social security number
   public void setSocialSecurityNumber(String socialSecurityNumber)
   {
      CE.setSocialSecurityNumber(socialSecurityNumber);
   }
   // get social security number
   public String getSocialSecurityNumber()
   {
	   return CE.getSocialSecurityNumber();
   }
   
   //set Gross salary
   public void setGrossSales(double grossSales)
   {
	   if (grossSales < 0.0) 
	         throw new IllegalArgumentException(
	            "Gross sales must be >= 0.0");

	      CE.setGrossSales(grossSales);
   }
   //get Gross salary
   public double getGrossSales()
   {
	   return CE.getGrossSales();
   }
   // set commission rate
   public void setCommissionRate(double commissionRate)
   {
      if (commissionRate <= 0.0 || commissionRate >= 1.0)
         throw new IllegalArgumentException(
            "Commission rate must be > 0.0 and < 1.0");

      CE.setCommissionRate(commissionRate);
   } 

   // return commission rate
   public double getCommissionRate()
   {
      return CE.getCommissionRate();
   }

   
   // set base salary
   public void setBaseSalary(double baseSalary)
   {
      if (baseSalary < 0.0)                   
         throw new IllegalArgumentException(
            "Base salary must be >= 0.0");  

      this.baseSalary = baseSalary;                
   } 

   // return base salary
   public double getBaseSalary()
   {
      return baseSalary;
   } 

   // calculate earnings
   public double earnings()
   {
      return getBaseSalary() + CE.earnings();
   }

   // return String representation of BasePlusCommissionEmployee
   @Override
   public String toString()
   {
      return String.format("%s %s%n%s: %.2f", "base-salaried",
         CE.toString(), "base salary", getBaseSalary());   
   } 
} // end class BasePlusCommissionEmployee

//// BasePlusCommissionEmployeeTest.java
// Testing class BasePlusCommissionEmployee.

public class BasePlusCommissionEmployeeTest
{
   public static void main(String[] args) 
   {
      // instantiate BasePlusCommissionEmployee object
      BasePlusCommissionEmployee employee = 
         new BasePlusCommissionEmployee(
            "Bob", "Lewis", "333-33-3333", 5000, .04, 300);
      
      // get base-salaried commission employee data
      System.out.println(
         "Employee information obtained by get methods:");
      System.out.printf("%n%s %s%n", "First name is",
         employee.getFirstName());
      System.out.printf("%s %s%n", "Last name is", 
         employee.getLastName());
      System.out.printf("%s %s%n", "Social security number is", 
         employee.getSocialSecurityNumber());
      System.out.printf("%s %.2f%n", "Gross sales is", 
         employee.getGrossSales());
      System.out.printf("%s %.2f%n", "Commission rate is",
         employee.getCommissionRate());
      System.out.printf("%s %.2f%n", "Base salary is",
         employee.getBaseSalary());

      employee.setBaseSalary(1000); 
      
      System.out.printf("%n%s:%n%n%s%n", 
         "Updated employee information obtained by toString", 
         employee.toString());
   } // end main
} // end class BasePlusCommissionEmployeeTest

//public class CommissionEmployee
{
   private String firstName;                              
   private String lastName;                               
   private String socialSecurityNumber;                   
   private double grossSales; // gross weekly sales       
   private double commissionRate; // commission percentage

   // five-argument constructor
   public CommissionEmployee(String firstName, String lastName, 
      String socialSecurityNumber, double grossSales, 
      double commissionRate)
   {
      // implicit call to Object constructor occurs here

      // if grossSales is invalid throw exception
	   if (grossSales < 0.0) 
	         throw new IllegalArgumentException(
	            "Gross sales must be >= 0.0");

	      // if commissionRate is invalid throw exception
	      if (commissionRate <= 0.0 || commissionRate >= 1.0)
	         throw new IllegalArgumentException(
	            "Commission rate must be > 0.0 and < 1.0");

      this.firstName = firstName;                                    
      this.lastName = lastName;                                    
      this.socialSecurityNumber = socialSecurityNumber;         
      this.grossSales = grossSales;
      this.commissionRate = commissionRate;
   } // end constructor 
   
   
   //set first name
   public void setFirstName(String firstName)
   {
      this.firstName = firstName; 
   }

   // return first name
   public String getFirstName()
   {
      return firstName;
   }
   
   //set last name
   public void setLastName(String lastName)
   {
      this.lastName = lastName; 
   }

   // return last name
   public String getLastName()
   {
      return lastName;
   }
   
   //set social security number
   public void setSocialSecurityNumber(String socialSecurityNumber)
   {
      this.socialSecurityNumber = socialSecurityNumber;
   }

   // return social security number
   public String getSocialSecurityNumber()
   {
      return socialSecurityNumber;
   } 

   // set gross sales amount
   public void setGrossSales(double grossSales)
   {
      if (grossSales < 0.0) 
         throw new IllegalArgumentException(
            "Gross sales must be >= 0.0");

      this.grossSales = grossSales;
   } 

   // return gross sales amount
   public double getGrossSales()
   {
      return grossSales;
   } 

   // set commission rate
   public void setCommissionRate(double commissionRate)
   {
      if (commissionRate <= 0.0 || commissionRate >= 1.0)
         throw new IllegalArgumentException(
            "Commission rate must be > 0.0 and < 1.0");

      this.commissionRate = commissionRate;
   } 

   // return commission rate
   public double getCommissionRate()
   {
      return commissionRate;
   }

   // calculate earnings
   public double earnings()
   {
      return getCommissionRate() * getGrossSales();
   } 

   // return String representation of CommissionEmployee object
   @Override 
   public String toString()
   {
      return String.format("%s: %s %s%n%s: %s%n%s: %.2f%n%s: %.2f", 
         "commission employee", getFirstName(), getLastName(), 
         "social security number", getSocialSecurityNumber(), 
         "gross sales", getGrossSales(), 
         "commission rate", getCommissionRate());
   } 
} // end class CommissionEmployee
