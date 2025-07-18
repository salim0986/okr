# OKR Management System v1.0

A comprehensive full-stack **Objectives and Key Results (OKR) Management System** built with modern technologies to help organizations set, track, and manage their goals across different organizational levels.

## 🚀 Features

### Core Functionality
- **Multi-tenant Architecture**: Support for multiple organizations with isolated data
- **Hierarchical Structure**: Organization → Department → Team → User
- **Role-based Access Control**: Different permissions for different user roles
- **Real-time Progress Tracking**: Track key result progress with updates
- **Comprehensive Dashboard**: Visual representation of OKR progress
- **Responsive Design**: Mobile-friendly interface

### User Roles & Permissions
- **Admin**: System-wide access to all organizations and data
- **Organization Admin**: Access to their organization's data only
- **Department Manager**: Access to their department's data only
- **Team Lead**: Access to their team's data only
- **Employee**: Access to their own data and team objectives

### Key Features
- User authentication and authorization (JWT-based)
- Organization, Department, and Team management
- Objective creation and management
- Key Result tracking with progress updates
- Role-based data filtering and CRUD operations
- Secure API endpoints with proper validation

## 🛠 Technology Stack

### Backend (NestJS)
- **Framework**: NestJS (Node.js)
- **Database**: PostgreSQL with TypeORM
- **Authentication**: JWT (JSON Web Tokens)
- **Security**: bcrypt for password hashing, CORS enabled
- **Architecture**: Modular design with separate modules for each entity

### Frontend (Next.js)
- **Framework**: Next.js 13+ with App Router
- **Language**: TypeScript
- **Styling**: Tailwind CSS
- **UI Components**: shadcn/ui component library
- **Forms**: React Hook Form with validation
- **State Management**: React hooks and context

## 📁 Project Structure

```
├── backend/                 # NestJS Backend
│   ├── src/
│   │   ├── auth/           # Authentication module
│   │   ├── user/           # User management
│   │   ├── organization/   # Organization management
│   │   ├── department/     # Department management
│   │   ├── team/           # Team management
│   │   ├── okr/            # Objectives management
│   │   ├── keyresult/      # Key Results management
│   │   ├── progress/       # Progress tracking
│   │   └── utils/          # Utility functions
│   └── test/               # E2E tests
│
├── frontend/               # Next.js Frontend
│   ├── app/                # App Router pages
│   │   ├── auth/           # Authentication pages
│   │   ├── dashboard/      # Dashboard and management pages
│   │   └── api/            # API routes
│   ├── components/         # React components
│   │   ├── ui/             # shadcn/ui components
│   │   ├── auth/           # Authentication components
│   │   ├── dashboard/      # Dashboard components
│   │   └── layout/         # Layout components
│   ├── lib/                # Utility libraries
│   └── hooks/              # Custom React hooks
│
└── README.md
```

## 🚀 Getting Started

### Prerequisites
- Node.js (v18 or higher)
- PostgreSQL database
- npm or yarn package manager

### Backend Setup

1. **Navigate to backend directory**:
   ```bash
   cd backend
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Set up environment variables**:
   Create a `.env` file in the backend directory:
   ```env
   DB_HOST=localhost
   DB_PORT=5432
   DB_USERNAME=your_db_username
   DB_PASSWORD=your_db_password
   DB_NAME=okr_management
   JWT_SECRET=your_jwt_secret_key
   PORT=3001
   ENVIRONMENT=development
   ADMIN_PASSWORD=your_admin_password
   ```

4. **Run database migrations** (if applicable):
   ```bash
   npm run migration:run
   ```

5. **Start the backend server**:
   ```bash
   npm run start:dev
   ```

### Frontend Setup

1. **Navigate to frontend directory**:
   ```bash
   cd frontend
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Set up environment variables**:
   Create a `.env.local` file in the frontend directory:
   ```env
   BACKEND_URL=http://localhost:3001
   NEXT_PUBLIC_APP_URL=http://localhost:3000
   ```

4. **Start the frontend development server**:
   ```bash
   npm run dev
   ```

5. **Access the application**:
   Open [http://localhost:3000](http://localhost:3000) in your browser

## 🔐 API Endpoints

### Authentication
- `POST /api/v1/user/login` - User login
- `POST /api/v1/user/register` - User registration

### Organizations
- `GET /api/v1/organization` - Get organizations (role-based)
- `POST /api/v1/organization` - Create organization (admin only)
- `GET /api/v1/organization/:id` - Get organization by ID
- `PUT /api/v1/organization/:id` - Update organization

### Departments
- `GET /api/v1/department` - Get departments (role-based)
- `POST /api/v1/department` - Create department
- `GET /api/v1/department/organization/:orgId` - Get departments by organization

### Teams
- `GET /api/v1/team` - Get teams (role-based)
- `POST /api/v1/team` - Create team
- `GET /api/v1/team/department/:deptId` - Get teams by department

### Objectives (OKRs)
- `GET /api/v1/okr` - Get objectives (role-based)
- `POST /api/v1/okr` - Create objective
- `GET /api/v1/okr/:id` - Get objective by ID
- `PUT /api/v1/okr/:id` - Update objective

### Key Results
- `GET /api/v1/keyresult` - Get key results (role-based)
- `POST /api/v1/keyresult` - Create key result
- `GET /api/v1/keyresult/objective/:id` - Get key results by objective

### Progress Tracking
- `GET /api/v1/progress` - Get progress updates
- `POST /api/v1/progress` - Create progress update

## 🔒 Security Features

- **JWT Authentication**: Secure token-based authentication
- **Role-based Access Control**: Hierarchical permissions system
- **Data Isolation**: Users can only access data within their organizational scope
- **Password Security**: bcrypt hashing for password storage
- **CORS Protection**: Configured for secure cross-origin requests
- **Input Validation**: Comprehensive validation on all endpoints

## 🎨 UI Components

The frontend uses a comprehensive set of UI components including:
- Forms and inputs with validation
- Data tables with sorting and filtering
- Modal dialogs for CRUD operations
- Dashboard widgets and charts
- Navigation and layout components
- Responsive design components

## 📊 Role-based Data Access

### Admin
- Can see and manage all organizations, departments, teams, and users
- System-wide access to all OKRs and progress data
- Can create organizations and assign organization admins

### Organization Admin
- Can see and manage only their organization's data
- Can create departments and assign department managers
- Can view all OKRs within their organization

### Department Manager
- Can see and manage only their department's data
- Can create teams and assign team leads
- Can view OKRs within their department

### Team Lead
- Can see and manage only their team's data
- Can create and manage team OKRs
- Can track team progress

### Employee
- Can view their own profile and team information
- Can view team OKRs and contribute to progress updates
- Limited access to organizational data

## 🚀 Deployment

### Frontend (Vercel - Recommended)
1. Push your code to GitHub
2. Connect your repository to Vercel
3. Set environment variables in Vercel dashboard
4. Deploy with one click

### Backend (Railway/Render)
1. Connect your GitHub repository
2. Set up environment variables
3. Configure database connection
4. Deploy the backend service

### Docker Deployment
Use the provided Docker configuration for containerized deployment:
```bash
docker-compose up -d
```

## 🔮 Version 1.0 - Current Features

This is **Version 1.0** of the OKR Management System. Current features include:

✅ **Completed Features**:
- User authentication and role-based access control
- Organization, Department, and Team management
- Objective and Key Result creation and tracking
- Progress updates and monitoring
- Responsive web interface
- Role-based data filtering
- Secure API endpoints

## 🛣 Future Development (v2.0+)

The system will be further developed with additional features:

🔄 **Planned Features**:
- **Real-time Notifications**: Email and push notifications for deadlines and updates
- **Advanced Analytics**: Comprehensive reporting and data visualization
- **Mobile Application**: React Native mobile app for iOS and Android
- **Integration APIs**: Third-party integrations (Slack, Microsoft Teams, etc.)
- **Advanced Reporting**: Export capabilities and custom report generation
- **Audit Logging**: Comprehensive audit trails for all actions
- **Performance Metrics**: Advanced KPI tracking and benchmarking
- **Collaboration Tools**: Comments, mentions, and team collaboration features
- **Calendar Integration**: Deadline tracking and calendar synchronization
- **Advanced Permissions**: Fine-grained permission system
- **Multi-language Support**: Internationalization and localization
- **Dark Mode**: Theme customization options
- **Bulk Operations**: Mass import/export and bulk editing capabilities
- **API Rate Limiting**: Enhanced security and performance controls
- **Caching Layer**: Redis integration for improved performance

## 🤝 Contributing

This project is currently in active development. Contributions, issues, and feature requests are welcome!

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 📞 Support

For support and questions, please create an issue in the GitHub repository.

---

**Note**: This is Version 1.0 of the OKR Management System. The system will continue to evolve with additional features and improvements in future versions.
