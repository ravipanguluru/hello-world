
import org.openqa.selenium.By;  
import org.openqa.selenium.WebDriver;  
import org.openqa.selenium.chrome.ChromeDriver; 
import org.openqa.selenium.WebElement;
   
public class MadridCraiglist {  
public static void main(String[] args) {  
        
  // declaration and instantiation of objects/variables  
   System.setProperty("webdriver.chrome.driver","D:\\ChromeDriver\\chromedriver.exe");  
   
   WebDriver driver=new ChromeDriver();  
   driver.manage().window().maximize();
      
 //  Launch craiglist website  
    driver.get("https://madrid.craiglist.org/");  
    
//  Navigate and click on the English language below dropdown on right 
    driver.findElement(By.xpath ("//a[@href="?lang=en&setlang=1"]")).click();
          
//  Navigate to Housing Page under Craiglist  
    driver.findElement(By.xpath("//a[@href="/d/housing/search/hhh?lang=en&cc=gb"]//span[contains(@class,"txt")]")).click();  

// functionality to verify 
// Navigate and click on dropdown menu (sorting) next to top right below save search

 driver.findElement(By.xpath("//a[@href="/d/housing/search/hhh?sort=date&lang=en&cc=gb"]//span[contains(@class,"toggle-arrow")]")).click();

//By default, such sorting possibilities are available (price ⬆, price ⬇, newest)

WebElement price ⬆ = driver.findElement(By.xpath("//a[@href="/d/housing/search/hhh?sort=priceasc&lang=en&cc=gb"]"));
WebElement price ⬇ = driver.findElement(By.xpath("//a[@href="/d/housing/search/hhh?sort=pricedsc&lang=en&cc=gb"]"));
WebElement newest = driver.findElement(By.xpath("//a[@href="/d/housing/search/hhh?sort=date&lang=en&cc=gb"]"));

 Assert.assertEquals(true, price ⬆.isDisplayed());
 Assert.assertEquals(true, price ⬇.isDisplayed());
 Assert.assertEquals(true, newest.isDisplayed());

// Sort by price ⬆
driver.findElement(By.xpath("//a[@href="/d/housing/search/hhh?sort=priceasc&lang=en&cc=gb"]")).click();

// sort by price ⬇ 
driver.findElement(By.xpath("//a[@href="/d/housing/search/hhh?sort=pricedsc&lang=en&cc=gb"]")).click();

// After using search such sorting possibilities are available (price ⬆, price ⬇, newest, upcoming, relevant)

WebElement Searchhousing = driver.findElement(By.xpath("//div[contains(@class,"querybox")]//input[@placeholder="search housing"]"));
Searchhousing.sendkeys("1200");

WebElement Searchbutton = 
driver.findElement(By.xpath("//span[contains(@class,"icon icon-search")]")]));
Searchbutton.click();	

// Navigate and click on drop down menu on right next to price
driver.findElement(By.xpath("//a[contains(@title, "sort by price, highest to lowest")]//span[contains(@class,"toggle-arrow")]")).click();

WebElement relevant = driver.findElement(By.xpath("//a[@href="//a[contains(@title, "show most relevant matches first")]"));
Assert.assertEquals(true, relevant.isDisplayed());

driver.close();

  }  
  }



