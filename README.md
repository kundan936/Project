package Stepdefinition;

import java.time.Duration;

import org.openqa.selenium.By;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;

import io.cucumber.java.en.Given;
import io.cucumber.java.en.Then;
import io.cucumber.java.en.When;

public class HomestaysandVilla {
	WebDriver driver;
	public void Program() {
	driver = new ChromeDriver();
	}
	public void Quit() {
		driver.quit();
	}
	@Given("I am on Home page")
	public void i_am_on_home_page() throws InterruptedException {
	    // Write code here that turns the phrase above into concrete actions
	    //throw new io.cucumber.java.PendingException();
		driver.get("https://www.makemytrip.com");
		driver.manage().window().maximize();
		Thread.sleep(3000);
	    WebElement frame = driver.findElement(By.xpath( "//*[@id='webklipper-publisher-widget-container-notification-frame']"));
		driver.switchTo().frame(frame); 
		WebElement clsBtn =driver.findElement(By.xpath("//a[@id='webklipper-publisher-widget-container-notification-close-div']"));
	    clsBtn.click();
		String parentWindowHandle=driver.getWindowHandle();
	    driver.switchTo().window(parentWindowHandle);
	}

	@When("I click on Homestays & Villas")
	public void i_click_on_homestays_villas() {
	    // Write code here that turns the phrase above into concrete actions
	   // throw new io.cucumber.java.PendingException();
		driver.findElement(By.xpath("//span[@class='chNavIcon appendBottom2 chSprite chHomestays']")).click();
	}

	@When("I select city as {string}")
	public void i_select_city_as(String string) {
	    // Write code here that turns the phrase above into concrete actions
	    //throw new io.cucumber.java.PendingException();
		WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
		WebElement a = wait.until(ExpectedConditions.visibilityOfElementLocated(By.id("city")));
		a.click();
		WebDriverWait wait1 = new WebDriverWait(driver, Duration.ofSeconds(10));
		WebElement wait2 = wait1.until(ExpectedConditions.visibilityOfElementLocated(By.xpath("//input[@placeholder='Where do you want to stay?']")));
		wait2.sendKeys("Goa");
		Actions actions = new Actions(driver);
		actions.pause(Duration.ofSeconds(2)).sendKeys(Keys.ARROW_DOWN)
		.sendKeys(Keys.ENTER).build().perform();
	}

	@When("I select Check-In as {string}")
	public void i_select_check_in_as(String string) {
	    // Write code here that turns the phrase above into concrete actions
	    //throw new io.cucumber.java.PendingException();
		WebElement checkin = driver.findElement(By.xpath("//div[@class='DayPicker-Day' and @tabindex='-1' and @aria-label='Thu Apr 04 2024']"));
        JavascriptExecutor executor = (JavascriptExecutor) driver;
        executor.executeScript("arguments[0].click();", checkin);
	}

	@When("I select Check-Out as {string}")
	public void i_select_check_out_as(String string) {
	    // Write code here that turns the phrase above into concrete actions
	    //throw new io.cucumber.java.PendingException();
		WebElement element = driver.findElement(By.xpath("/html/body/div[1]/div/div[2]/div/div/div/div/div[1]/div[2]/div[1]/div/div/div/div[2]/div/div[2]/div[2]/div[3]/div[2]/div[1]"));
        element.click();
	}

	@When("I select Guests as {string}")
	public void i_select_guests_as(String string) {
	    // Write code here that turns the phrase above into concrete actions
	    //throw new io.cucumber.java.PendingException();
		WebElement apply = driver.findElement(By.xpath("//button[@data-cy='RoomsGuestsNew_327' and @type='button']"));
        apply.click();
	}

	@When("I select the price as {string}")
	public void i_select_the_price_as(String string) {
	    // Write code here that turns the phrase above into concrete actions
	    //throw new io.cucumber.java.PendingException();
		driver.findElement(By.xpath("//span[@data-cy=\"travelForText\"]")).click();
        driver.findElement(By.xpath("//li[text()='₹2500-₹5000']")).click();
	}

	@Then("I will be able to view selected price")
	public void i_will_be_able_to_view_selected_price() {
	    // Write code here that turns the phrase above into concrete actions
	    //throw new io.cucumber.java.PendingException();
	}

	@When("I Click on Search")
	public void i_click_on_search() {
	    // Write code here that turns the phrase above into concrete actions
	    //throw new io.cucumber.java.PendingException();
	    driver.findElement(By.xpath("//button[@id=\'hsw_search_button\']")).click();
	}

	@Then("I will be able to view list of villas")
	public void i_will_be_able_to_view_list_of_villas() {
	    // Write code here that turns the phrase above into concrete actions
	    //throw new io.cucumber.java.PendingException();
	}

	@When("I select Property type as {string}")
	public void i_select_property_type_as(String string) {
	    // Write code here that turns the phrase above into concrete actions
	    //throw new io.cucumber.java.PendingException();
		driver.findElement(By.xpath("//span[text()='Tree house']")).click();
	}

	@Then("I will be able to view the Tree house")
	public void i_will_be_able_to_view_the_tree_house() {
	    // Write code here that turns the phrase above into concrete actions
	    //throw new io.cucumber.java.PendingException();
	}

	@When("I click on the Tree house")
	public void i_click_on_the_tree_house() {
	    // Write code here that turns the phrase above into concrete actions
	   // throw new io.cucumber.java.PendingException();
		WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
		WebElement treehouse = wait.until(ExpectedConditions.visibilityOfElementLocated(By.xpath("//span[text()='Nirvana Hill Resort']")));;
	    treehouse.click();
	}

	@Then("I can view the details of Tree house")
	public void i_can_view_the_details_of_tree_house() {
	    // Write code here that turns the phrase above into concrete actions
	    //throw new io.cucumber.java.PendingException();
	}

}

