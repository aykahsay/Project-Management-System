
## CAP-Manager Web Application

A Java web application for managing CAP (Capital Allocation Program) applications with admin review functionality.

### Project Structure

```
CAP-Manager/                 <- Root (Maven/NetBeans Web Application)
 ├─ src/main/java/
 │   ├─ com.capmanager.config
 │   │    └─ DBUtil.java          # Database connection utility
 │   ├─ com.capmanager.mail
 │   │    └─ MailUtil.java        # Email notification utility
 │   ├─ com.capmanager.model
 │   │    ├─ Application.java     # Application entity/model
 │   │    └─ Comment.java         # Comment entity/model
 │   ├─ com.capmanager.servlet
 │   │    ├─ ApplyServlet.java           # Handle new applications
 │   │    ├─ AdminLoginServlet.java      # Admin authentication
 │   │    ├─ AdminReviewServlet.java     # Application review process
 │   │    ├─ CommentServlet.java         # Comment management
 │   │    └─ DownloadBudgetServlet.java  # Budget document download
 ├─ src/main/webapp/
 │   ├─ WEB-INF/
 │   │    ├─ web.xml              # Servlet configuration
 │   │    └─ lib/                 # Dependencies (mysql-connector jar)
 │   ├─ apply.jsp                 # Application submission form
 │   ├─ login.jsp                 # Admin login page
 │   ├─ admin.jsp                 # Admin dashboard
 │   ├─ view_application.jsp      # Application details page
 │   └─ fragments/                # Reusable UI components
 │        ├─ header.jsp           # Page header
 │        ├─ footer.jsp           # Page footer
 │        └─ css/                 # Stylesheets
 ├─ pom.xml                       # Maven dependencies and build configuration
 └─ sql/
      └─ cap_schema.sql          # Database schema and initial data
```

## Features

- **Application Submission**: Users can submit CAP applications through web forms
- **Admin Dashboard**: Administrative interface for reviewing applications
- **Comment System**: Admins can add comments to applications during review
- **Budget Download**: Download budget documents associated with applications
- **Email Notifications**: Automated email alerts for application status changes
- **Database Management**: MySQL database with connection pooling

## Technologies Used

- **Backend**: Java Servlets, JSP
- **Frontend**: JSP, HTML, CSS, JavaScript
- **Database**: MySQL with JDBC
- **Build Tool**: Maven
- **Server**: Apache Tomcat
- **Email**: JavaMail API

## Prerequisites

- Java JDK 8 or higher
- Apache Tomcat 9.x
- MySQL Server 5.7 or higher
- Maven 3.6+ (if using Maven)

## Installation & Setup

1. **Database Setup**:
   ```sql
   mysql -u root -p < sql/cap_schema.sql
   ```

2. **Database Configuration**:
   Update `DBUtil.java` with your database credentials:
   ```java
   private static final String URL = "jdbc:mysql://localhost:3306/cap_db";
   private static final String USERNAME = "your_username";
   private static final String PASSWORD = "your_password";
   ```

3. **Email Configuration**:
   Update `MailUtil.java` with your SMTP settings:
   ```java
   properties.put("mail.smtp.host", "your-smtp-host");
   properties.put("mail.smtp.port", "587");
   ```

4. **Build and Deploy**:
   ```bash
   mvn clean package
   # Copy WAR file to Tomcat webapps directory
   ```

## Configuration

### Database Properties
The application uses MySQL with the following default settings:
- Database Name: `cap_db`
- Host: `localhost`
- Port: `3306`

### Email Settings
Configure SMTP settings in `MailUtil.java` for:
- Application submission confirmations
- Status update notifications
- Admin alerts

## Usage

1. **Access Application**: Navigate to `http://localhost:8080/CAP-Manager/`
2. **Submit Application**: Use the apply.jsp form to submit new applications
3. **Admin Login**: Access `/login.jsp` with admin credentials
4. **Review Applications**: Use admin dashboard to review and process applications

## API Endpoints

- `POST /apply` - Submit new application
- `POST /admin-login` - Admin authentication
- `GET /admin-review` - View applications for review
- `POST /comment` - Add comments to applications
- `GET /download-budget` - Download budget documents

## Database Schema

Key tables:
- `applications` - Stores application details
- `comments` - Stores admin comments on applications
- `users` - Admin user accounts

## Development

### Adding New Features
1. Create model classes in `com.capmanager.model`
2. Implement servlets in `com.capmanager.servlet`
3. Create JSP views in `webapp/`
4. Update `web.xml` for new servlet mappings

### Building with Maven
```bash
mvn clean compile    # Compile source code
mvn package          # Create WAR file
mvn tomcat7:deploy   # Deploy to Tomcat (if plugin configured)
```

## Troubleshooting

### Common Issues
1. **Database Connection**: Verify MySQL service is running and credentials are correct
2. **Email Notifications**: Check SMTP settings and network connectivity
3. **File Uploads**: Ensure Tomcat has write permissions to temp directory

### Logs
Check Tomcat logs for detailed error information:
- `catalina.out`
- `localhost.log`


## To create this README.md file:

```powershell
# Create the README.md file
@'
# CAP-Manager Web Application

[The content above...]
'@ | Out-File -FilePath "README.md" -Encoding utf8

# Add it to Git and commit
git add README.md
git commit -m "Add project documentation and README"
```

