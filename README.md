Feature:    As a customer in Amazon.com
  I can able to search book
  So I can see the book in book section
@SearchBook
  Scenario: Search Book in Amazon
Given I am in Amazon.com
When I search Book in Departments
When I search "Selenium Web driver" in Book
Then I can see and select the Book
  @AddCart
Scenario:Add the book into Cart
  Given I am in Amazon.com
    When I search Book in Departments
    When I search "Selenium Web driver" in Book
    Then I can see and select the Book
    And I can Add the Book into Cart and proceed to checkout
    
    Step Definitions:
    
    
    package First;

import cucumber.api.PendingException;
import cucumber.api.java.en.And;
import cucumber.api.java.en.Given;
import cucumber.api.java.en.Then;
import cucumber.api.java.en.When;
import org.junit.Assert;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.openqa.selenium.interactions.Actions;

/**
 * Created by kavitha on 27/06/2015.
 */

public class MyStepdefs {
    @When("^I search Book in Departments$")
    public void I_search_Book_in_Departments(){
        WebDriver driver = new FirefoxDriver();

    WebElement element = driver.findElement(By.id("id=\"searchDropdownBox\""));


    driver.findElement(By.cssSelector("[value=\"search-alias=stripbooks\"]")).click();







    }

    @Given("^I am in Amazon.com$")
    public void I_am_in_Amazon_com()  {
        // Express the Regexp above with the code you wish you had
        WebDriver driver = new FirefoxDriver();
        driver.get("https://www.amazon.co.uk/");
        System.out.println("I am on Amazon Page");
        Assert.assertEquals(true, driver.findElement(By.id("nav-your-amazon")).getText());
    }

    @When("^I search \"([^\"]*)\" in Book$")
    public void I_search_in_Book(String arg1)  {
        WebDriver driver = new FirefoxDriver();
        driver.findElement(By.xpath(".//*[@id='twotabsearchtextbox']")).sendKeys("Selenium Webdriver");



    }








    @Then("^I can see and select the Book$")
    public void I_can_see_the_Book() {
        WebDriver driver = new FirefoxDriver();
        driver.findElement(By.id("twotabsearchtextbox")).click();
    }




    }

    @And("^I can Add the Book into Cart and proceed to checkout$")
    public void I_can_Add_the_Book_into_Cart_and_proceed_to_checkout()  {
        WebDriver driver = new FirefoxDriver();
        driver.findElement(By.linkText("Selenium WebDriver Practical Guide")).click();
        driver.findElement(By.id("add-to-cart-button")).click();
        driver.findElement(By.xpath(".//*[@id='hlb-ptc-btn-native']")).click();


    }
}


Runner file:

package First;

/**
 * Created by kavitha on 27/06/2015.
 */

import cucumber.api.junit.Cucumber;
import org.junit.runner.RunWith;
@RunWith(Cucumber.class)
@Cucumber.Options (features="Account",
        format = {"html:target/cucumber"},
    tags = "@SearchBook")

public class RunTest {
}


  
