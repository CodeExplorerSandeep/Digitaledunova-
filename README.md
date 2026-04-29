# DIGITAL EDUNOVA - Virtual Classroom Management System

A comprehensive web-based application for online teaching, learning, assessment, and academic management.

## Features

### User Roles
- **Admin**: Manage users, courses, batches, view reports, send notifications, system settings, manage feedback
- **Teacher**: Upload study materials, create assignments/tests, mark attendance, evaluate submissions, manage batches
- **Student**: Access materials, submit assignments, attempt tests, view grades, pay fees, enroll in batches
- **Parent**: Monitor student performance, view attendance & fees, enroll children in batches
- **Visitor**: View courses, register account, submit public feedback

### Core Modules
1. **Authentication & User Management**
   - Secure login/signup with bcrypt password hashing
   - Forgot password & reset password functionality
   - Role-based access control (RBAC)
   - Session management with timeout
   - User approval workflow for teachers and students

2. **Course & Batch Management**
   - CRUD operations for courses and batches
   - Link teachers to courses
   - Link students to batches
   - Batch enrollment with payment processing
   - Registration number generation (SE/TR/PM format)

3. **Study Material Module**
   - Teachers can upload PDF, DOCX, JPG, PNG files
   - File validation and unique naming
   - Students can download materials
   - Organized by batch

4. **Assignment & Test Module**
   - Create assignments with due dates and max marks
   - Students can submit files
   - Teachers can grade submissions with feedback
   - Test creation and result tracking
   - MCQ support with question banks

5. **Attendance Module**
   - Mark attendance (Present/Absent/Late)
   - View attendance history
   - Calculate attendance percentage
   - Unique attendance tracking per student per date

6. **Payment & Invoice Module**
   - Multiple payment methods (UPI, Card, Net Banking, Cash, Coupon)
   - Coupon/Gift card system with percentage and fixed value discounts
   - GST calculation (18%)
   - Invoice generation with subtotal, GST amount breakdown
   - Transaction ID tracking
   - Payment validation (requires payment method selection)
   - Receipt generation

7. **Notification System**
   - Send notifications to users
   - Target specific roles or all users
   - Mark as read/unread
   - Real-time notification display

8. **Feedback & Report Module**
   - User feedback with ratings (1-5 stars)
   - Public feedback (visitor feedback without login)
   - Feedback filtering by type (All/User/Public)
   - Comprehensive reporting system:
     - User reports
     - Course reports
     - Batch reports
     - Study material reports
     - Attendance reports
     - Assignment reports
     - Test reports
     - Payment reports
     - Wallet reports
     - Coupon/Gift card reports
     - Public feedback reports
     - User feedback reports
     - Notification reports
   - Export reports to CSV

9. **Coupons & Gift Cards**
   - Create and manage coupons/gift cards
   - Percentage or fixed value discounts
   - Usage limits and expiry dates
   - Track usage count per coupon
   - User wallet integration

10. **Settings Management**
    - Site logo upload
    - Site name configuration
    - Dark/Light mode preference
    - System-wide settings

## Technology Stack

- **Frontend**: HTML5, CSS3 (Flexbox/Grid), JavaScript (Vanilla)
- **Backend**: PHP (Core PHP)
- **Database**: MySQL
- **Server**: Apache (XAMPP)

## Installation

**For detailed installation instructions, see [INSTALLATION.md](INSTALLATION.md)**

### Quick Start (XAMPP)

1. **Extract/Clone the project**
   ```
   Place the project folder in: C:\xampp\htdocs\digitaledunova
   ```

2. **Import Database**
   - Start Apache and MySQL in XAMPP
   - Go to phpMyAdmin (http://localhost/phpmyadmin)
   - Create a new database named `digitaledunova`
   - Import the `database.sql` file located in the project root

3. **Configure Database Connection**
   - Open `config.php` in the project root
   - Update database credentials if needed (default: root, empty password)

4. **Run Migration Scripts**
   ```cmd
   cd C:\xampp\htdocs\digitaledunova
   php add_batch_thumbnail.php
   php add_course_image_column.php
   php add_enrollments_table.php
   php add_parent_enrollment_system.php
   php add_mcq_tables.php
   php add_teacher_batch_table.php
   ```

5. **Access the Application**
   - Open browser and go to: http://localhost/digitaledunova
   - Default Admin Login:
     - Email: admin@digitaledunova.com
     - Password: admin123

**For platform-specific installation (Linux, macOS, Docker), see [INSTALLATION.md](INSTALLATION.md)**

## Hosting / Production Deployment

**For detailed deployment instructions, see [DEPLOYMENT.md](DEPLOYMENT.md)**

### Quick Deployment Checklist

**Before Deployment:**
- [ ] Change database credentials in `config.php`
- [ ] Update `SITE_URL` to your production domain
- [ ] Disable error reporting (set to 0)
- [ ] Import `database.sql` to production database
- [ ] Run migration scripts in order
- [ ] Set proper file permissions for `/uploads` directory
- [ ] Update timezone if needed (currently set to Asia/Kolkata)
- [ ] Test all file upload functionality
- [ ] Change default admin password immediately

**After Deployment:**
- [ ] Test login functionality
- [ ] Test file uploads
- [ ] Test payment processing
- [ ] Test email notifications (if configured)
- [ ] Check SSL/HTTPS configuration
- [ ] Set up database backups
- [ ] Configure cron jobs for any scheduled tasks (if needed)

**For detailed deployment guides (cPanel, VPS, Docker), see [DEPLOYMENT.md](DEPLOYMENT.md)**

## Project Structure

```
/digitaledunova
│── /admin              # Admin dashboard and modules
│   ├── activity-log.php
│   ├── approvals.php
│   ├── assignments.php
│   ├── batches.php
│   ├── coupons.php
│   ├── courses.php
│   ├── dashboard.php
│   ├── enrollment_requests.php
│   ├── feedback.php
│   ├── materials.php
│   ├── notifications.php
│   ├── parents.php
│   ├── payments.php
│   ├── profile.php
│   ├── reports.php
│   ├── settings.php
│   ├── students.php
│   ├── teachers.php
│   └── users.php
│── /teacher            # Teacher dashboard and modules
│   ├── assignments.php
│   ├── attendance.php
│   ├── batches.php
│   ├── dashboard.php
│   ├── feedback.php
│   ├── materials.php
│   ├── notifications.php
│   ├── profile.php
│   ├── submissions.php
│   └── tests.php
│── /student            # Student dashboard and modules
│   ├── assignments.php
│   ├── attendance.php
│   ├── batches.php
│   ├── courses.php
│   ├── dashboard.php
│   ├── enroll.php
│   ├── feedback.php
│   ├── grades.php
│   ├── invoice.php
│   ├── materials.php
│   ├── my-courses.php
│   ├── notifications.php
│   ├── payments.php
│   ├── profile.php
│   ├── receipt.php
│   └── tests.php
│── /parent             # Parent dashboard and modules
│   ├── attendance.php
│   ├── batches.php
│   ├── courses.php
│   ├── dashboard.php
│   ├── enroll.php
│   ├── enrollment_requests.php
│   ├── feedback.php
│   ├── fees.php
│   ├── invoice.php
│   ├── my-courses.php
│   ├── performance.php
│   ├── profile.php
│   └── receipt.php
│── /visitor            # Visitor pages (landing, register)
│   └── courses.php
│── /includes           # Shared components
│   ├── auth.php
│   ├── batch_helper.php
│   ├── db.php
│   ├── footer.php
│   ├── functions.php
│   └── header.php
│── /uploads            # File upload directory
│   ├── batches/
│   ├── courses/
│   ├── materials/
│   └── profile_pictures/
│── config.php          # Configuration file
│── database.sql        # Database schema
│── index.php           # Landing page
│── login.php           # Login page
│── logout.php          # Logout handler
│── search.php          # Search functionality
│── search-results.php  # Search results page
│── forgot-password.php # Password recovery
│── reset-password.php  # Password reset
│── README.md           # This file
│── INSTALLATION.md     # Detailed installation guide
│── DEPLOYMENT.md       # Production deployment guide
└── Migration Scripts  # Database migration scripts
    ├── add_batch_thumbnail.php
    ├── add_course_image_column.php
    ├── add_enrollments_table.php
    ├── add_parent_enrollment_system.php
    ├── add_mcq_tables.php
    └── add_teacher_batch_table.php
```

## Security Features

- Password hashing with bcrypt
- Prepared statements for SQL injection prevention
- Input validation and sanitization
- Session management with timeout
- Role-based access control (RBAC)
- Soft delete system (status field)
- Audit logging
- CSRF protection
- Payment method validation
- File type validation

## UI Features

- **Responsive Design**: Mobile-friendly layout
- **Dark/Light Mode Toggle**: Theme switching
- **Sidebar Navigation**: Collapsible sidebar with icons
- **Toggle Functionality**: 
  - Minimized: Shows only icons and site logo
  - Maximized: Shows icons with text labels
- **Live Search**: AJAX-powered search functionality
- **User Menu**: Avatar-only display in navbar with dropdown
- **Cards UI**: Statistics and data display
- **Search and Filter**: Advanced filtering capabilities
- **Pagination**: Large dataset handling
- **Modal Dialogs**: Form modals for actions
- **Toast Notifications**: Success/error messages
- **Tab System**: For filtering feedback types
- **Export Functionality**: CSV export for reports

## Database Schema

### Core Tables
- **users**: User accounts with roles (admin, teacher, student, parent)
- **teachers**: Teacher profiles linked to users
- **students**: Student profiles linked to users
- **parents**: Parent profiles with student linkage
- **courses**: Course catalog with images
- **batches**: Batch/session management with thumbnails and discounts
- **enrollments**: Student batch enrollments with payment tracking
- **parent_student_requests**: Parent enrollment requests for children
- **parent_student_relationships**: Approved parent-student links

### Academic Tables
- **study_materials**: Course materials
- **assignments**: Assignment management
- **submissions**: Student submissions
- **tests**: Test/exam management
- **mcq_questions**: Multiple choice questions
- **mcq_options**: MCQ answer options
- **mcq_results**: MCQ test results
- **attendance**: Attendance tracking
- **grades**: Grade records

### Financial Tables
- **payments**: Payment records with GST
- **invoices**: Invoice generation with GST breakdown
- **coupons**: Discount coupons and gift cards
- **user_wallet**: User wallet for coupon tracking

### System Tables
- **notifications**: User notifications
- **feedback**: User and public feedback
- **audit_log**: System audit trail
- **settings**: System configuration
- **batch_teachers**: Teacher-batch assignments
- **teacher_batch**: Alternative teacher-batch mapping

## Documentation

### Available Documentation Files

- **[README.md](README.md)** - This file, system overview and quick start guide
- **[INSTALLATION.md](INSTALLATION.md)** - Detailed installation instructions for all platforms
- **[DEPLOYMENT.md](DEPLOYMENT.md)** - Production deployment guide with security and optimization

### Quick Links

- **Installation**: See [INSTALLATION.md](INSTALLATION.md) for detailed setup instructions
- **Deployment**: See [DEPLOYMENT.md](DEPLOYMENT.md) for production deployment
- **Migration Scripts**: Run scripts in order listed in Migration Scripts section

## Recent Updates

### Latest Session Improvements
1. **Parent Enrollment System**:
   - Parents can request enrollment for children in batches
   - Admin approval workflow for enrollment requests
   - Parent-student relationship management
   - Batch purchase functionality for parents
   - Parent monitoring of enrolled students
2. **Batch & Course Thumbnails**:
   - Batch thumbnail upload for teachers and admins
   - Course image upload for admins
   - Image preview functionality
   - File validation (JPG, PNG, GIF, max 2MB)
3. **Admin Enrollment Requests**:
   - Dedicated admin interface for enrollment requests
   - Approve/reject functionality with reason tracking
   - Request history and audit trail
4. **Database Schema Updates**:
   - Added `enrollments` table for batch enrollments
   - Added `parent_student_requests` table for enrollment requests
   - Added `parent_student_relationships` table for approved links
   - Added `thumbnail` column to batches table
   - Added `course_image` column to courses table
5. **Teacher Materials Display**:
   - Fixed materials query to show all uploaded materials
   - Proper JOIN chain for teacher-student relationships
   - Enhanced material management interface
6. **Code Cleanup**:
   - Fixed parse errors in parent dashboard
   - Resolved database column reference issues
   - Improved error handling

## File Upload Rules

- Allowed file types: PDF, DOCX, JPG, PNG
- Max file size: 100MB (configurable)
- Files stored in /uploads folder
- Unique filename generation (timestamp-based)
- File type validation before upload

## Default Credentials

**Admin:**
- Email: admin@digitaledunova.com
- Password: admin123

**To create other users:**
- Admin can create users via the Users management page
- Visitors can register via the registration page (requires admin approval)

## Migration Scripts

The project includes several migration scripts for database updates. Run these in order when setting up or updating the system:

### Core Migrations (Run in Order)
1. `add_batch_thumbnail.php` - Add thumbnail column to batches table
2. `add_course_image_column.php` - Add course_image column to courses table
3. `add_enrollments_table.php` - Create enrollments table for batch enrollments
4. `add_parent_enrollment_system.php` - Create parent enrollment system tables
5. `add_mcq_tables.php` - Create MCQ test system tables
6. `add_teacher_batch_table.php` - Create teacher-batch assignment table

### Feature-Specific Migrations
- `fix_feedback_table.php` - Update feedback table for public feedback
- `add_gst_to_invoices.php` - Add GST columns to invoices
- `add_transaction_id.php` - Add transaction IDs to payments
- `update_payments_schema.php` - Update payments table schema
- `add_registration_number.php` - Add registration number columns
- `add_profile_picture.php` - Add profile picture support
- `add_description_to_batches.php` - Add description field to batches
- `add_batch_discount_validity.php` - Add discount validity to batches

### Utility Scripts
- `ensure_user_codes.php` - Ensure all users have user codes
- `update_user_codes.php` - Update user codes for existing users
- `fix_registration_numbers.php` - Fix registration number format
- `fix_foreign_keys.php` - Fix foreign key constraints

## API Endpoints

- **Live Search**: `/search.php` - AJAX-powered search
- **Search Results**: `/search-results.php` - Display search results

## Browser Compatibility

- Chrome (recommended)
- Firefox
- Safari
- Edge
- Mobile browsers (iOS Safari, Chrome Mobile)

## Performance Optimizations

- Prepared statements for efficient database queries
- Indexed columns for fast lookups
- Lazy loading for large datasets
- Pagination for large result sets
- Optimized CSS with CSS variables for theming

## Support

For issues or questions, please contact the development team.

## License

This project is for educational purposes.

## Version History

### Current Version
- Enhanced public feedback system
- Improved sidebar navigation
- Payment validation fixes
- Database schema updates
- UI/UX improvements

### Previous Versions
- Initial release with core modules
- Payment and invoice system
- Notification system
- Report generation
