# Selenium Hybrid Framework

A comprehensive Selenium WebDriver automation framework for e-commerce application testing, built using Java, Maven, TestNG, and following Page Object Model design pattern.

## 🚀 Features

- **Hybrid Framework**: Combines Data-Driven, Keyword-Driven, and Modular approaches
- **Page Object Model**: Clean separation of test logic and page elements
- **Cross-Browser Testing**: Support for Chrome, Firefox, Safari, and Edge
- **Parallel Execution**: TestNG parallel execution support
- **Data-Driven Testing**: Excel-based test data management
- **Robust Reporting**: Allure and TestNG HTML reports
- **CI/CD Integration**: GitHub Actions workflow included
- **Screenshot Capture**: Automatic screenshot on test failures
- **Retry Mechanism**: Configurable test retry on failures
- **Environment Management**: Support for multiple test environments

## 🛠️ Technology Stack

- **Java 11+**
- **Maven** - Dependency management
- **Selenium WebDriver 4.x** - Web automation
- **TestNG** - Testing framework
- **Allure** - Advanced reporting
- **Apache POI** - Excel file handling
- **Log4j2** - Logging framework
- **WebDriverManager** - Automatic driver management
- **Jackson** - JSON processing
- **MySQL** - Database connectivity

## 📁 Project Structure

```
selenium-hybrid-framework/
├── src/
│   ├── main/java/com/ecommerce/automation/
│   │   ├── base/          # Base classes for tests and driver management
│   │   ├── pages/         # Page Object Model classes
│   │   ├── utils/         # Utility classes (Excel, Config, Wait, etc.)
│   │   ├── constants/     # Application constants
│   │   ├── listeners/     # TestNG listeners
│   │   ├── enums/         # Enumerations
│   │   ├── exceptions/    # Custom exceptions
│   │   └── factories/     # Factory classes
│   └── test/
│       ├── java/com/ecommerce/automation/
│       │   ├── tests/     # Test classes
│       │   └── dataproviders/ # TestNG data providers
│       └── resources/
│           ├── testdata/  # Excel test data files
│           ├── config/    # Configuration files
│           └── testng.xml # TestNG suite configuration
├── .github/workflows/     # CI/CD pipeline
├── pom.xml               # Maven configuration
└── README.md
```

## 🎯 Getting Started

### Prerequisites

- Java 11 or higher
- Maven 3.6+
- IDE (IntelliJ IDEA/Eclipse)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/your-username/selenium-hybrid-framework.git
cd selenium-hybrid-framework
```

2. Install dependencies:
```bash
mvn clean install
```

3. Update configuration:
   - Edit `src/test/resources/config/config.properties`
   - Update environment variables in `.env` file

### Running Tests

#### Run all tests:
```bash
mvn clean test
```

#### Run specific test suite:
```bash
mvn clean test -DsuiteXmlFile=testng.xml
```

#### Run tests by groups:
```bash
# Smoke tests
mvn clean test -Dgroups=smoke

# Regression tests
mvn clean test -Dgroups=regression
```

#### Run with specific browser:
```bash
mvn clean test -Dbrowser=chrome
```

#### Parallel execution:
```bash
mvn clean test -DparallelMode=methods -DthreadCount=3
```

## 📊 Reports

### Allure Reports
```bash
# Generate Allure report
mvn allure:report

# Serve report
mvn allure:serve
```

### TestNG Reports
Reports are generated in `target/surefire-reports/` directory.

## 🔧 Configuration

### Browser Configuration (`config.properties`)
```properties
browser=chrome
headless=false
implicitWait=10
explicitWait=20
pageLoadTimeout=30
```

### Environment Variables (`.env`)
```env
BASE_URL=https://demo.ecommerce.com
DB_URL=jdbc:mysql://localhost:3306/testdb
DB_USERNAME=testuser
DB_PASSWORD=testpass
```

## 🧪 Writing Tests

### Example Test Class
```java
public class LoginTests extends BaseTest {
    
    @Test(groups = {"smoke", "login"})
    public void testValidLogin() {
        HomePage homePage = new HomePage(driver);
        LoginPage loginPage = homePage.navigateToLogin();
        loginPage.login("user@example.com", "password123");
        // Add assertions
    }
}
```

### Page Object Example
```java
public class LoginPage extends BasePage {
    
    @FindBy(id = "email")
    private WebElement emailField;
    
    public LoginPage(WebDriver driver) {
        super(driver);
    }
    
    public void login(String email, String password) {
        sendKeys(emailField, email);
        // Implementation
    }
}
```

## 🏗️ CI/CD Pipeline

The project includes GitHub Actions workflow for continuous integration:

- Automated testing on push/pull requests
- Multi-browser testing
- Report generation and artifact storage
- Notification on failure

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📋 Test Data Management

Test data is managed through Excel files located in `src/test/resources/testdata/`:
- `login_data.xlsx` - Login test scenarios
- `product_data.xlsx` - Product-related test data

## 🐛 Troubleshooting

### Common Issues

1. **WebDriver not found**: WebDriverManager handles driver downloads automatically
2. **Test failures**: Check logs in `logs/` directory
3. **Configuration issues**: Verify `config.properties` and `.env` files

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📞 Support

For support and questions:
- Create an issue in GitHub repository
- Contact: support@example.com

## 🔄 Version History

- **v1.0.0** - Initial release with core framework features
- **v1.1.0** - Added parallel execution and enhanced reporting
- **v1.2.0** - Database integration and improved error handling

---

**Happy Testing! 🎉**