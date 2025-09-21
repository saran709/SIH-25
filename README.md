# Student-Industry-Faculty Bridge Platform

A comprehensive web platform designed for the Smart India Hackathon that connects students, industry professionals, and faculty members to facilitate internships, mentorship, and collaborative opportunities.

## 🎯 Project Overview

This platform serves as a digital bridge between academia and industry, enabling:
- **Students** to discover internships, jobs, and mentorship opportunities
- **Industry professionals** to recruit talent and share expertise
- **Faculty members** to guide students and collaborate with industry
- **Administrators** to manage the entire ecosystem

## 🚀 Features

### For Students
- **Profile Management**: Create comprehensive profiles with skills, education, and portfolio
- **Opportunity Discovery**: Browse and apply for internships, jobs, and projects
- **Application Tracking**: Monitor application status and receive updates
- **Mentorship Requests**: Connect with industry professionals and faculty
- **Skill Development**: Access learning resources and track progress
- **Networking**: Connect with peers and professionals
- **Certification**: Earn verified certificates for completed programs

### For Industry Professionals
- **Talent Recruitment**: Post opportunities and review applications
- **Application Management**: Efficient hiring process with filtering and sorting
- **Mentorship Programs**: Offer guidance to students
- **Collaboration**: Work with educational institutions
- **Analytics**: Track recruitment metrics and success rates

### For Faculty Members
- **Student Guidance**: Monitor and guide student progress
- **Industry Collaboration**: Facilitate partnerships and projects
- **Curriculum Integration**: Align academic programs with industry needs
- **Research Opportunities**: Connect with industry for research projects
- **Performance Analytics**: Track student outcomes and program effectiveness

### For Administrators
- **Platform Management**: Complete control over users, content, and settings
- **Analytics Dashboard**: Comprehensive insights into platform usage
- **Content Moderation**: Ensure quality and appropriate content
- **System Configuration**: Manage platform settings and features
- **Report Generation**: Generate detailed reports for stakeholders

## 💻 Technology Stack

### Backend
- **PHP 8.0+** with MVC architecture
- **MySQL 8.0+** for database management
- **RESTful API** design pattern
- **JWT Authentication** for secure access
- **File Upload Management** for documents and media
- **Email Integration** with PHPMailer
- **Real-time Notifications** system

### Frontend
- **HTML5** with semantic markup
- **CSS3** with Flexbox, Grid, and animations
- **Vanilla JavaScript** with ES6+ features
- **Chart.js** for data visualization
- **Font Awesome** for icons
- **Responsive Design** for all devices
- **Progressive Web App** features

### Security Features
- **bcrypt** password hashing
- **CSRF Protection** for forms
- **Input Sanitization** and validation
- **Rate Limiting** for API endpoints
- **Session Management** with secure cookies
- **Email Verification** for account security
- **File Upload Security** with MIME validation
- **SQL Injection Protection** with prepared statements

### Advanced Features
- **Advanced Search Engine** with filtering and facets
- **Real-time Notifications** with email integration
- **File Management System** with category organization
- **Analytics Dashboard** with interactive charts
- **Certificate Generation** and verification
- **Mentorship Matching** algorithm
- **Application Workflow** management
- **Multi-role Authentication** system

## 📁 Project Structure

```
student-industry-bridge/
├── backend/
│   ├── config/
│   │   ├── Database.php          # Database connection and configuration
│   │   ├── config.php           # Application settings and constants
│   │   └── email.php            # Email configuration for notifications
│   ├── controllers/
│   │   ├── AuthController.php   # Authentication and session management
│   │   ├── UserController.php   # User management and profiles
│   │   ├── OpportunityController.php # Internship/job postings
│   │   ├── ApplicationController.php # Application processing
│   │   ├── MentorshipController.php  # Mentorship connections
│   │   └── api/                 # API-specific controllers
│   │       ├── NotificationController.php # Real-time notifications
│   │       ├── FileController.php        # File upload/download
│   │       └── SearchController.php      # Advanced search functionality
│   ├── models/
│   │   ├── User.php            # User data model
│   │   ├── Opportunity.php     # Opportunity data model
│   │   ├── Application.php     # Application data model
│   │   ├── Mentorship.php      # Mentorship data model
│   │   ├── Notification.php    # Notification data model
│   │   └── Certificate.php     # Certificate data model
│   ├── utils/
│   │   ├── Auth.php           # Authentication utilities
│   │   ├── Security.php       # Security and validation functions
│   │   ├── FileHandler.php    # File upload and management
│   │   ├── EmailSender.php    # Email sending functionality
│   │   └── Logger.php         # Application logging
│   └── api/
│       └── index.php          # API router and endpoint handler
├── frontend/
│   ├── pages/
│   │   ├── pre-login/         # Landing and authentication pages
│   │   │   ├── index.html     # Homepage
│   │   │   ├── login.html     # Login page
│   │   │   ├── register.html  # Registration page
│   │   │   ├── about.html     # About page
│   │   │   └── contact.html   # Contact page
│   │   ├── student/           # Student role pages
│   │   │   ├── dashboard.html # Student dashboard
│   │   │   ├── opportunities.html # Browse opportunities
│   │   │   ├── applications.html  # Track applications
│   │   │   ├── mentorship.html    # Mentorship connections
│   │   │   └── profile.html       # Student profile management
│   │   ├── faculty/           # Faculty role pages
│   │   │   ├── dashboard.html # Faculty dashboard
│   │   │   ├── students.html  # Manage students
│   │   │   ├── projects.html  # Research projects
│   │   │   └── analytics.html # Student performance analytics
│   │   ├── industry/          # Industry role pages
│   │   │   ├── dashboard.html # Industry dashboard
│   │   │   ├── post-opportunities.html # Create job postings
│   │   │   ├── applications.html      # Review applications
│   │   │   └── talent-pool.html       # Browse candidates
│   │   └── admin/             # Admin role pages
│   │       ├── dashboard.html # Admin dashboard
│   │       ├── user-management.html # Manage all users
│   │       ├── content-moderation.html # Content approval
│   │       └── system-settings.html   # Platform configuration
│   ├── css/
│   │   ├── global.css         # Global styles and variables
│   │   ├── components.css     # Reusable component styles
│   │   ├── dashboard.css      # Dashboard-specific styles
│   │   ├── forms.css          # Form styling and validation
│   │   └── responsive.css     # Mobile responsiveness
│   └── js/
│       ├── utils.js           # Utility functions and helpers
│       ├── api.js             # API communication layer
│       ├── auth.js            # Authentication management
│       ├── notifications.js   # Real-time notification handling
│       ├── file-upload.js     # File upload functionality
│       ├── search-engine.js   # Advanced search features
│       ├── dashboard.js       # Common dashboard functionality
│       ├── student-dashboard.js   # Student-specific features
│       ├── faculty-dashboard.js   # Faculty-specific features
│       ├── industry-dashboard.js  # Industry-specific features
│       └── admin-dashboard.js     # Admin-specific features
├── database/
│   ├── schema.sql             # Complete database schema
│   ├── sample-data.sql        # Sample data for testing
│   └── migrations/            # Database migration scripts
├── assets/
│   ├── uploads/
│   │   ├── resumes/           # Student resume uploads
│   │   ├── portfolios/        # Portfolio files
│   │   ├── certificates/      # Certificate documents
│   │   └── company-logos/     # Company branding
│   └── images/
│       ├── logos/             # Platform branding
│       ├── backgrounds/       # Background images
│       └── icons/             # Custom icons and graphics
├── docs/
│   ├── API_DOCUMENTATION.md  # Complete API reference
│   ├── USER_GUIDE.md         # End-user documentation
│   ├── ADMIN_GUIDE.md        # Administrator manual
│   └── DEVELOPER_GUIDE.md    # Development documentation
├── .htaccess                  # Apache URL rewriting
├── composer.json             # PHP dependencies
├── package.json              # Frontend dependencies
└── README.md                 # This file
```

## 🛠️ Installation & Setup

### Prerequisites
- **PHP 8.0+** with extensions: mysqli, pdo, gd, curl, mbstring
- **MySQL 8.0+** or MariaDB 10.4+
- **Apache 2.4+** or Nginx with URL rewriting
- **Composer** for PHP dependency management
- **Node.js 16+** and npm (for frontend build tools, optional)

### Quick Start

1. **Clone the Repository**
   ```bash
   git clone https://github.com/yourusername/student-industry-bridge.git
   cd student-industry-bridge
   ```

2. **Database Setup**
   ```bash
   # Create database
   mysql -u root -p
   CREATE DATABASE student_bridge;
   exit

   # Import schema
   mysql -u root -p student_bridge < database/schema.sql

   # Import sample data (optional)
   mysql -u root -p student_bridge < database/sample-data.sql
   ```

3. **Backend Configuration**
   ```bash
   # Copy configuration template
   cp backend/config/config.php.example backend/config/config.php
   
   # Edit configuration file
   nano backend/config/config.php
   ```

   Update the configuration with your database credentials:
   ```php
   <?php
   define('DB_HOST', 'localhost');
   define('DB_NAME', 'student_bridge');
   define('DB_USER', 'your_username');
   define('DB_PASS', 'your_password');
   
   define('BASE_URL', 'http://localhost/student-industry-bridge');
   define('UPLOAD_PATH', __DIR__ . '/../assets/uploads/');
   
   // Email configuration
   define('SMTP_HOST', 'smtp.gmail.com');
   define('SMTP_PORT', 587);
   define('SMTP_USER', 'your-email@gmail.com');
   define('SMTP_PASS', 'your-app-password');
   ?>
   ```

4. **Install Dependencies**
   ```bash
   # PHP dependencies
   composer install

   # Frontend dependencies (optional)
   npm install
   ```

5. **Web Server Setup**
   
   **For Apache:**
   - Ensure `.htaccess` is in the root directory
   - Enable `mod_rewrite` module
   - Configure virtual host to point to project directory

   **For Nginx:**
   ```nginx
   server {
       listen 80;
       server_name localhost;
       root /path/to/student-industry-bridge;
       index index.php index.html;

       location / {
           try_files $uri $uri/ /index.php?$query_string;
       }

       location ~ \.php$ {
           fastcgi_pass 127.0.0.1:9000;
           fastcgi_index index.php;
           include fastcgi_params;
           fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
       }
   }
   ```

6. **Set Permissions**
   ```bash
   # Make upload directories writable
   chmod -R 755 assets/uploads/
   chmod -R 755 backend/logs/

   # For production, use more restrictive permissions
   chmod -R 644 assets/uploads/
   chmod -R 600 backend/config/
   ```

### Development Setup

1. **Enable Debug Mode**
   ```php
   // In backend/config/config.php
   define('DEBUG_MODE', true);
   define('LOG_LEVEL', 'DEBUG');
   ```

2. **Database Seeding**
   ```bash
   # Run sample data import
   mysql -u root -p student_bridge < database/sample-data.sql
   ```

3. **Frontend Development**
   ```bash
   # Install development tools
   npm install -g live-server

   # Start development server
   live-server --port=3000 --open=frontend/pages/pre-login/
   ```

## 🚀 Usage Guide

### Default Admin Account
After importing sample data:
- **Email**: admin@studentbridge.com
- **Password**: admin123
- **Role**: Administrator

### Sample User Accounts
- **Student**: student@university.edu / password123
- **Faculty**: faculty@university.edu / password123
- **Industry**: recruiter@techcorp.com / password123

### API Usage

The platform provides a comprehensive REST API for integration:

```javascript
// Authentication
const response = await fetch('/api/auth/login', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
        email: 'user@example.com',
        password: 'password123'
    })
});

// Get opportunities
const opportunities = await fetch('/api/opportunities?type=internship&category=technology');

// Submit application
const application = await fetch('/api/applications', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
        opportunity_id: 1,
        cover_letter: 'Dear hiring manager...',
        resume_url: '/uploads/resume.pdf'
    })
});
```

See [API_DOCUMENTATION.md](docs/API_DOCUMENTATION.md) for complete API reference.

## 🔧 Configuration

### Environment Variables
Create a `.env` file for sensitive configuration:
```bash
# Database
DB_HOST=localhost
DB_NAME=student_bridge
DB_USER=your_username
DB_PASS=your_password

# Email
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your-email@gmail.com
SMTP_PASS=your-app-password

# Security
JWT_SECRET=your-super-secret-key
ENCRYPTION_KEY=32-character-encryption-key

# File Upload
MAX_FILE_SIZE=10485760
ALLOWED_EXTENSIONS=pdf,doc,docx,jpg,png

# API
RATE_LIMIT=1000
API_VERSION=1.0
```

### Feature Toggles
Enable/disable features in `config.php`:
```php
define('ENABLE_EMAIL_VERIFICATION', true);
define('ENABLE_FILE_UPLOADS', true);
define('ENABLE_REAL_TIME_NOTIFICATIONS', true);
define('ENABLE_ANALYTICS', true);
define('ENABLE_CERTIFICATE_GENERATION', true);
```

- **Backend**: PHP with MySQL/MariaDB
- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **Database**: MySQL with relational design
- **Server**: Apache/Nginx
- **Security**: HTTPS, bcrypt, session management

## Quick Start

1. **Setup Database**
   ```sql
   mysql -u root -p < database/schema.sql
   ```

2. **Configure Backend**
   ```php
   // Edit backend/config/database.php
   define('DB_HOST', 'localhost');
   define('DB_USER', 'your_username');
   define('DB_PASS', 'your_password');
   define('DB_NAME', 'student_bridge');
   ```

3. **Start Development Server**
   ```bash
   php -S localhost:8000 -t frontend/
   ```

4. **Access Application**
   - Open browser to `http://localhost:8000`
   - Default admin credentials will be provided in setup

## API Documentation

The application provides REST APIs for:
- User authentication and management
- Opportunity CRUD operations
- Application tracking
- Notification system
- Analytics and reporting

## Contributing

1. Fork the repository
2. Create feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

For support and questions:
- Create an issue in the repository
- Contact the development team
- Check the documentation in `/docs`

---

**Built for Smart India Hackathon 2024** 🇮🇳