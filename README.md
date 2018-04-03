# faker data

package fakerTestData;

import com.github.javafaker.Faker;

public class FakerTestDataGenerator {

	//public static void main(String[] args) {

	public static void generateFakeData() {
		
		Faker faker = new Faker();
		
		String fullName = faker.name().fullName();
		String firstName = faker.name().firstName();
		String lastName = faker.name().lastName();
		String buildingNumber = faker.address().buildingNumber();
		String streetName = faker.address().streetName();
		String city = faker.address().city();
		String zip = faker.address().zipCode();
		String state = faker.address().stateAbbr();
//		String zipByState = faker.address().zipCodeByState("OR");
		String phoneNumber = faker.phoneNumber().cellPhone();
		String email = faker.internet().emailAddress();
		String ssn = faker.idNumber().ssnValid();
				
		
		System.out.println("SSN: " + ssn);
		  System.out.println("Full Name: " + fullName);
		  System.out.println("First Name: " + firstName);
		  System.out.println("Last Name: " + lastName);
		  System.out.println("Building Number: " + buildingNumber);
		  System.out.println(streetName +" Street");
		  System.out.println("City: " + city);
		  System.out.println("Zip: " + zip);
		  System.out.println("State: " + state);
//		  System.out.println("ZIP: " + zipByState);
		  
		  System.out.println("Phone Number: " + phoneNumber);
		  System.out.println("Email:" + email);
			

   }

}

+++++


generator


++++

package fakerTestData;

public class GenerateData {

	public static void main(String[] args) {
		
		FakerTestDataGenerator data = new FakerTestDataGenerator();


		for (int i = 0; i < 10; i++) {
			data.generateFakeData();
			
			System.out.println();
			System.out.println();
			
			
		}
		
	}
  
  
  +++++
  
  
  Random string generator+++++
  ++++++
  
  package randomGenerator;

import java.util.Random;

public class RandomStringGenerator {

	public static void main(String[] args) {
	
		String characters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"; // caharacters used and there is 26 characters 
		String randomStringResult=""; //use empty string
		

		int length = 5; //Set the length of  your srandom String say 5..

		
		
		Random r = new Random();
		
		     //int length = r.nextInt(9); // or you can create this instead of int length = 5; to generate strings up to 9 characters from 0 to 9
		
		//use a character array in order to get above character all together and put together and acces later, creat an array
		
		char[] text = new char[length]; //length is size of the array is 5 and trandomStringResult is where we will store our randomString
		
		
		//create a for loop to add each individual random character to the array we created, each character will go to an index, each index will have one character.
		
		for(int i = 0; i < length; i++){
			text[i] = characters.charAt(r.nextInt(characters.length())); // instead of characters.length() you can also put 26
			//System.out.println(i); this will print you numbers/indexes --> 0 1 2 3 4   total 5
		} 
		
//turns indexes in to one stream
		
		for(length=0; length < text.length; length++){
			
			randomStringResult += text[length];
		}
		
		System.out.println(randomStringResult);
	}

}

++++++
Random test data generator

++++++

package randomGenerator;
import java.util.Random;

public class RandomTestDataGenerator {

	public static void main(String[] args) {
	
//		Random SSN
		Random r1 = new Random(System.nanoTime() % 100000);
		int ssn = r1.nextInt(1000000000);
		  
//		Random other fields
		Random r = new Random();
		
		String fullName = "fullName"+r.nextInt();
		String firstName = "firstName"+r.nextInt();
		String lastName = "lastName"+r.nextInt();
		
		
		
		String address = "address"+r.nextInt();
		long phoneNumber = (long)(Math.random() * 100000 + 5037000000L);
		String email = "email"+r.nextInt();
		
		
		  System.out.println("SSN: " + ssn);
		  System.out.println("Full Name: " + fullName);
		  System.out.println("First Name: " + firstName);
		  System.out.println("Last Name: " + lastName);
		  System.out.println("Address: " + address);
		  System.out.println("Phone Number: " + phoneNumber);
		  System.out.println("Email:" + email);
		  
		 
	}

}


+++++++
Buffer reader doent work:

+++++

package readWriteExcel;

public static void main(String[] args) throws IOException
{    
    BufferedReader reader1 = new BufferedReader(new FileReader("C:\\file1.txt"));
     
    BufferedReader reader2 = new BufferedReader(new FileReader("C:\\file2.txt"));
     
    String line1 = reader1.readLine();
     
    String line2 = reader2.readLine();
     
    boolean areEqual = true;
     
    int lineNum = 1;
     
    while (line1 != null || line2 != null)
    {
        if(line1 == null || line2 == null)
        {
            areEqual = false;
             
            break;
        }
        else if(! line1.equalsIgnoreCase(line2))
        {
            areEqual = false;
             
            break;
        }
         
        line1 = reader1.readLine();
         
        line2 = reader2.readLine();
         
        lineNum++;
    }
     
    if(areEqual)
    {
        System.out.println("Two files have same content.");
    }
    else
    {
        System.out.println("Two files have different content. They differ at line "+lineNum);
         
        System.out.println("File1 has "+line1+" and File2 has "+line2+" at line "+lineNum);
    }
     
    reader1.close();
     
    reader2.close();
}
	    
}

++++++

read write excel +++ doesnt work

+++++

package readWriteExcel;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;

import org.apache.poi.hssf.usermodel.HSSFCell;
import org.apache.poi.hssf.usermodel.HSSFRow;
import org.apache.poi.hssf.usermodel.HSSFSheet;
import org.apache.poi.hssf.usermodel.HSSFWorkbook;

public class ReadandWriteExcel {

	public static void main(String[] args) throws Exception {
		
		/// .xls older version  
			String excelFilePath = "Users/sk/Desktop.EmpData.xlsx";
			FileInputStream fis = new FileInputStream(excelFilePath);
			
			//Workbook
			HSSFWorkbook wb1 = new HSSFWorkbook(fis); 
			//WorkSheet
			HSSFSheet	sh1 = wb1.getSheet("Sheet1"); 
			HSSFSheet   sh2 = wb1.getSheetAt(0); 
			//Row
			
			HSSFRow   rw = sh1.getRow(1);
			HSSFCell  cell = rw.getCell(1);
			if(cell==null){
				rw.createCell(1);
				cell.setCellValue("my new value");
			}else{
				cell.setCellValue("my new value");
			}
			FileOutputStream fos = new FileOutputStream(excelFilePath);
			wb1.write(fos);
			fos.close();
			
			//Cell 
			//HSSFCell cell = rw.getCell(2);

			
			
	}

} 


++++++
excel utils
+++

package utilities;


import java.io.FileInputStream;
import java.io.FileOutputStream;

import org.apache.poi.xssf.usermodel.XSSFCell;
import org.apache.poi.xssf.usermodel.XSSFRow;
import org.apache.poi.xssf.usermodel.XSSFSheet;
import org.apache.poi.xssf.usermodel.XSSFWorkbook;


public class ExcelUtils {

	private static XSSFSheet excelWSheet;
	private static XSSFWorkbook excelWBook;
	private static XSSFCell cell;
	private static XSSFRow row;
	private static String excelFilePath;

	// This method is to set the File path and to open the Excel file, Pass
	// Excel Path and Sheetname as Arguments to this method
	public static void openExcelFile(String path, String sheetName) {
		excelFilePath = path;
		try {
			// Open the Excel file
			FileInputStream ExcelFile = new FileInputStream(path);
			// Access the required test data sheet
			excelWBook = new XSSFWorkbook(ExcelFile);
			excelWSheet = excelWBook.getSheet(sheetName);

		} catch (Exception e) {
			e.printStackTrace();
		}
	}

	// This method is to read the test data from the Excel cell, in this we are
	// passing parameters as Row num and Col num
	public static String getCellData(int rowNum, int colNum) {
		try {
			cell = excelWSheet.getRow(rowNum).getCell(colNum);
			String cellData = cell.toString();
			return cellData;
		} catch (Exception e) {
			//e.printStackTrace();
			return "";
		}
	}

	// This method is to write in the Excel cell, Row num and Col num are the
	// parameters
	public static void setCellData(String value, int rowNum, int colNum) {
		try {
			row = excelWSheet.getRow(rowNum);
			cell = row.getCell(colNum);

			if (cell == null) {
				cell = row.createCell(colNum);
				cell.setCellValue(value);
			} else {
				cell.setCellValue(value);
			}

			// Constant variables Test Data path and Test Data file name
			FileOutputStream fileOut = new FileOutputStream(excelFilePath);
			excelWBook.write(fileOut);

			fileOut.close();
		} catch (Exception e) {
			e.printStackTrace();
		}
	}

	public static int getUsedRowsCount() {
		try {
			int rowCount = excelWSheet.getPhysicalNumberOfRows();
			return rowCount;
		} catch (Exception e) {
			e.printStackTrace();
			return 0;
		}

	}
}

+++++
use excel utils

+++

package utilities;



public class UseExcelUtils {

	public static void main(String[] args) {

//				getting value from excel
				//ExcelUtils.openExcelFile(Config.getProperty("testDataPath"), "Sheet1");
		
				ExcelUtils.openExcelFile("testDataPath", "Sheet1");
				String value=ExcelUtils.getCellData(6, 1);
				System.out.println(value);
				
//				setting value
				ExcelUtils.setCellData("I believe in you", 1, 3);
//				getting used row count
				int rowCount=ExcelUtils.getUsedRowsCount();
				System.out.println(rowCount);
			}

	}


//WRITE TO EXCEL AND TEXT FILE

@When("^the user selects body type$")
public void the_user_selects_body_type() throws Throwable {
	// this is the way to get dropdown from select tag and loop throu it
	Page.sleep(2000);
	WebElement carBody = hp.bodyType;
	Select enter = new Select(carBody);
	List<WebElement> body = enter.getOptions();
	for (WebElement menu : body) {
		System.out.println(menu.getText());
		String filePath = "./src/test/resources/com/progressive/test-data text/CarBody.txt";
		// String path = "./src/test/resources/com/progressive/test-data
		// excel/CarBody.xlsx";
		String path = "./src/test/resources/com/progressive/test-data excel/Progres.xlsx";
					// text file 
		FSUtils.writeToAFile(filePath, menu.getText());
		// create excel file
		ExcelUtils.createExcelFile(path, "progresive");
		// open excel file
		ExcelUtils.openExcelFile(path, "progresive");
		for (int i = 0; i < body.size(); i++) {
			// ExcelUtils.setCellData(enter.getOptions().get(i).getText(),
			// i, 1);
			// create headers for each dropdown and throw them to excel
			// Setting Headers
			ExcelUtils.setCellData("Body Type", 0, 1);
			ExcelUtils.setCellData(enter.getOptions().get(i).getText(), i, 1);
		}
	}
	enter.selectByIndex(2);
	System.out.println("the size of car Body type: " + body.size());
}



++++++

pom.xml

++++

<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.etl.testing</groupId>
  <artifactId>ETL_Testing</artifactId>
  <version>0.0.1-SNAPSHOT</version>
<properties>
		<maven.compiler.source>1.8</maven.compiler.source>
		<maven.compiler.target>1.8</maven.compiler.target>
		<cucumber.version>1.2.5</cucumber.version>
	</properties>

	<repositories>
		<repository>
			<id>oracle</id>
			<url>http://www.datanucleus.org/downloads/maven2/</url>
		</repository>
	</repositories>

	<dependencies>
		<dependency>
			<groupId>org.apache.poi</groupId>
			<artifactId>poi</artifactId>
			<version>3.17</version>
		</dependency>
		<dependency>
			<groupId>org.apache.poi</groupId>
			<artifactId>poi-ooxml</artifactId>
			<version>3.17</version>
		</dependency>
		<dependency>
			<groupId>junit</groupId>
			<artifactId>junit</artifactId>
			<version>4.12</version>
		</dependency>
		<dependency>
			<groupId>org.seleniumhq.selenium</groupId>
			<artifactId>selenium-java</artifactId>
			<version>3.8.1</version>
		</dependency>

		<dependency>
			<groupId>info.cukes</groupId>
			<artifactId>cucumber-junit</artifactId>
			<version>${cucumber.version}</version>
		</dependency>
		<dependency>
			<groupId>info.cukes</groupId>
			<artifactId>cucumber-java</artifactId>
			<version>${cucumber.version}</version>
		</dependency>
		<dependency>
			<groupId>io.github.bonigarcia</groupId>
			<artifactId>webdrivermanager</artifactId>
			<version>2.0.1</version>
		</dependency>
		<dependency>
			<groupId>org.apache.poi</groupId>
			<artifactId>poi-ooxml</artifactId>
			<version>3.17</version>
			<scope>test</scope>
		</dependency>
		<dependency>
			<groupId>oracle</groupId>
			<artifactId>ojdbc6</artifactId>
			<version>11.2.0.3</version>
		</dependency>

		<dependency>
			<groupId>com.google.api-client</groupId>
			<artifactId>google-api-client</artifactId>
			<version>1.23.0</version>
		</dependency>
		<dependency>
			<groupId>com.google.apis</groupId>
			<artifactId>google-api-services-gmail</artifactId>
			<version>v1-rev76-1.23.0</version>
		</dependency>
		<dependency>
			<groupId>com.google.oauth-client</groupId>
			<artifactId>google-oauth-client-jetty</artifactId>
			<version>1.23.0</version>
		</dependency>
		<dependency>
			<groupId>org.mortbay.jetty</groupId>
			<artifactId>jetty</artifactId>
			<version>6.1.5</version>
		</dependency>
		
	<!--
	Dependency for Faker com.github.javafaker is below
	https://github.com/DiUS/java-faker
	-->
		<dependency>
    <groupId>com.github.javafaker</groupId>
    <artifactId>javafaker</artifactId>
    <version>0.14</version>
</dependency>

	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-compiler-plugin</artifactId>
				<version>3.3</version>
			</plugin>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-surefire-plugin</artifactId>
				<version>2.19.1</version>
				<configuration>
					<testFailureIgnore>true</testFailureIgnore>
					<includes>
						<include>**/*CukesRunner.java</include>
					</includes>
				</configuration>
			</plugin>
		</plugins>
	</build>
</project>

}


