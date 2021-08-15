# Hello-world
Cod pentru testare automata construit cu selenium si java
Buna. Mirabela ma numesc si acesta este proiectul meu pentru examenul de tester automat
Inca nu am facut nici o modificare dar daca voi face va aparea aici

import org.junit.Assert;
import org.junit.Test;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.Select;
import org.openqa.selenium.support.ui.WebDriverWait;

import java.util.List;

public class InregistrationTest {
public WebDriver driver;

@Test
    public void InregistrationTest(){
    //descarcam driverul
    //setam driverul de chrome

     System.setProperty("webdriver.chrome.driver", "C:\\Automation\\chromedriver\\chromedriver.exe" );
     driver = new ChromeDriver();
     driver.get("https://www.kitchenshop.ro/register");

     //maximize driver
     driver.manage().window().maximize();

     WebElement ContNouButton = driver.findElement(By.xpath("//span[contains(text(), 'Cont nou')]"));
     ContNouButton.click();

    String ExpectedInregistrationTitle = "Înregistreaza un cont nou";
    String ActualInregistrationTitle = driver.getTitle();
    Assert.assertEquals("Inregistration page whas not displayed",ExpectedInregistrationTitle, ActualInregistrationTitle);

     //declaram elementele de pe pagina
    WebElement EmailElement = driver.findElement(By.id("Email"));


    WebElement ParolaElement = driver.findElement(By.id("Password"));
    ParolaElement.sendKeys("kNDk*s5DZUhh6H#");

    WebElement AdaugaDetaliiPersonale = driver.findElement(By.xpath("//button[@id='toggle-personal-details-button']"));
    AdaugaDetaliiPersonale.click();

    WebElement NumeElement = driver.findElement(By.id("LastName"));
    NumeElement.sendKeys("Almasi");

    WebElement PrenumeElement = driver.findElement(By.id("FirstName"));
    PrenumeElement.sendKeys("Mirabela");

    WebElement SelectDay = driver.findElement(By.xpath("//select[@name='DateOfBirthDay']"));
    Select Day = new Select(SelectDay);
    Day.selectByValue("9");

    WebElement SelectMonth = driver.findElement(By.xpath("//select[@name='DateOfBirthMonth']"));
    Select Month = new Select(SelectMonth);
    Month.selectByVisibleText("iulie");

    WebElement SelectYear = driver.findElement(By.xpath("//select[@name='DateOfBirthYear']"));
    Select Year = new Select(SelectYear);
    Year.selectByValue("1970");

    WebElement SelectGender = driver.findElement(By.id("gender-female"));
    SelectGender.click();

    WebElement SelectCountry = driver.findElement(By.id("CountryId"));
    SelectCountry.click();
    List<WebElement> CountryOption = driver.findElements(By.xpath("//select[@data-val='true']/option"));
    for (int index = 0; index<CountryOption.size(); index++){
    String curentElement = CountryOption.get(index).getText();
    if (curentElement.equals("Romania")){
        CountryOption.get(index).click();
    }
    }

    WebElement SelectJudet = driver.findElement(By.id("StateProvinceId"));
    SelectJudet.click();
    Select Judet = new Select(SelectJudet);
    Judet.selectByVisibleText("Bihor");

    WebElement SelectCity = driver.findElement(By.id("City"));
    SelectCity.sendKeys("Tileagd");

    WebElement SelectPhone = driver.findElement(By.id("Phone"));
    SelectPhone.sendKeys("0745123589");

    WebElement SelectAdress = driver.findElement(By.id("StreetAddress"));
    SelectAdress.sendKeys("Strada Morii Nr.5");

    WebElement SelectCodPostal = driver.findElement(By.id("ZipPostalCode"));
    SelectCodPostal.sendKeys("123654");

    WebElement OkButton = driver.findElement(By.id("eu-cookie-ok"));
    OkButton.click();

    WebElement SelectTermeniSiConditii = driver.findElement(By.id("AcceptTermsOfUsage"));
    SelectTermeniSiConditii.click();

    WebElement SelectPoliticadeConfidentialitate = driver.findElement(By.id("AcceptConfidentialityPolicy"));
    SelectPoliticadeConfidentialitate.click();

    WebElement SelectInregistrareContButton = driver.findElement(By.id("register-button"));
    SelectInregistrareContButton.click();

    driver.close();

}

}

