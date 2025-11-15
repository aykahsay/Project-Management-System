### Project-Management-System
CAP-Manager/                 <- root (Maven or NetBeans web app)
 ├─ src/main/java/
 │   ├─ com.capmanager.config
 │   │    └─ DBUtil.java
 │   ├─ com.capmanager.mail
 │   │    └─ MailUtil.java
 │   ├─ com.capmanager.model
 │   │    ├─ Application.java
 │   │    └─ Comment.java
 │   ├─ com.capmanager.servlet
 │   │    ├─ ApplyServlet.java
 │   │    ├─ AdminLoginServlet.java
 │   │    ├─ AdminReviewServlet.java
 │   │    ├─ CommentServlet.java
 │   │    └─ DownloadBudgetServlet.java
 ├─ src/main/webapp/
 │   ├─ WEB-INF/
 │   │    ├─ web.xml
 │   │    └─ lib/ (mysql-connector jar)
 │   ├─ apply.jsp
 │   ├─ login.jsp
 │   ├─ admin.jsp
 │   ├─ view_application.jsp
 │   └─ fragments (header/footer css)
 ├─ pom.xml (if using Maven)
 └─ sql/
      └─ cap_schema.sql

