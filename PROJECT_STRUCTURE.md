# Project Structure

```
gogte_project/
│
├── backend/                          # Python Flask Backend
│   ├── database/
│   │   ├── __init__.py
│   │   └── db_connection.py         # MongoDB connection & setup
│   │
│   ├── models/
│   │   ├── __init__.py
│   │   └── models.py                # Data models (User, SleepLog, etc.)
│   │
│   ├── routes/
│   │   ├── __init__.py
│   │   ├── auth_routes.py           # Authentication endpoints
│   │   ├── sleep_routes.py          # Sleep tracking endpoints
│   │   ├── productivity_routes.py   # Productivity tracking endpoints
│   │   └── ai_coach_routes.py       # AI coaching endpoints
│   │
│   ├── services/
│   │   ├── __init__.py
│   │   └── ai_service.py            # OpenAI integration & AI logic
│   │
│   ├── app.py                       # Main Flask application
│   ├── requirements.txt             # Python dependencies
│   ├── .env.example                 # Environment variables template
│   └── .gitignore                   # Git ignore rules
│
├── frontend/                         # React Frontend
│   ├── src/
│   │   ├── components/
│   │   │   └── Layout.jsx           # Main layout component
│   │   │
│   │   ├── pages/
│   │   │   ├── Login.jsx            # Login/Register page
│   │   │   ├── Dashboard.jsx        # Main dashboard
│   │   │   ├── SleepTracker.jsx     # Sleep logging page
│   │   │   ├── ProductivityTracker.jsx  # Productivity logging page
│   │   │   └── AICoach.jsx          # AI coach interface
│   │   │
│   │   ├── services/
│   │   │   └── api.js               # API service layer
│   │   │
│   │   ├── App.jsx                  # Main App component
│   │   ├── App.css                  # App styles
│   │   ├── main.jsx                 # Entry point
│   │   └── index.css                # Global styles
│   │
│   ├── public/                      # Static assets
│   ├── index.html                   # HTML template
│   ├── package.json                 # Node dependencies
│   ├── vite.config.js              # Vite configuration
│   ├── tailwind.config.js          # Tailwind CSS config
│   ├── postcss.config.js           # PostCSS config
│   ├── .env.example                # Environment variables template
│   └── .gitignore                  # Git ignore rules
│
├── n8n_workflows/                   # n8n Automation Workflows
│   ├── sleep_analysis_workflow.json     # Sleep data analysis workflow
│   └── daily_recommendations_workflow.json  # Daily AI recommendations
│
├── README.md                        # Main documentation
├── QUICKSTART.md                   # Quick start guide
└── .dist/                          # Build output directory

```

## Component Descriptions

### Backend Components

#### **app.py**
- Main Flask application entry point
- Registers all route blueprints
- Initializes database connection
- Configures CORS and middleware

#### **database/db_connection.py**
- MongoDB connection management
- Database initialization
- Index creation for performance
- Connection pooling

#### **models/models.py**
- `User`: User account model
- `SleepLog`: Sleep tracking data model
- `ProductivityLog`: Productivity data model
- `AIRecommendation`: AI-generated recommendations model

#### **routes/**
- **auth_routes.py**: Registration, login, Google OAuth
- **sleep_routes.py**: Sleep logging, analytics, trends
- **productivity_routes.py**: Productivity logging, correlation analysis
- **ai_coach_routes.py**: AI recommendations, chat, insights

#### **services/ai_service.py**
- OpenAI API integration
- Prompt engineering
- Fallback responses when API unavailable
- Predictive analytics

### Frontend Components

#### **App.jsx**
- Main application component
- Authentication state management
- Route configuration
- User session handling

#### **components/Layout.jsx**
- Navigation bar
- Page layout wrapper
- User menu
- Responsive design

#### **pages/**
- **Login.jsx**: Authentication interface
- **Dashboard.jsx**: Overview with charts and insights
- **SleepTracker.jsx**: Sleep data entry form
- **ProductivityTracker.jsx**: Productivity data entry form
- **AICoach.jsx**: Chat interface and predictive insights

#### **services/api.js**
- Axios instance configuration
- API endpoint definitions
- Request interceptors
- Error handling

### n8n Workflows

#### **sleep_analysis_workflow.json**
- Triggered when sleep data is logged
- Analyzes sleep quality
- Generates AI recommendations
- Saves insights to database

#### **daily_recommendations_workflow.json**
- Scheduled daily at 7 AM
- Fetches user sleep patterns
- Generates personalized morning messages
- Sends notifications (if configured)

## Data Flow

### Sleep Logging Flow
```
User Input (Frontend)
    ↓
SleepTracker Component
    ↓
API Call (sleepAPI.createLog)
    ↓
Backend Route (/api/sleep/log)
    ↓
Database (MongoDB sleep_logs collection)
    ↓
n8n Workflow Trigger (optional)
    ↓
AI Analysis & Recommendations
    ↓
Save to database
```

### Dashboard Data Flow
```
Dashboard Component Mounts
    ↓
Parallel API Calls:
  - sleepAPI.getAnalytics()
  - sleepAPI.getLogs()
  - coachAPI.getRecommendation()
    ↓
Backend Processes Requests
    ↓
MongoDB Queries
    ↓
Data Aggregation & Processing
    ↓
JSON Response to Frontend
    ↓
Chart.js Visualization
```

### AI Coaching Flow
```
User Question (Frontend)
    ↓
coachAPI.chat()
    ↓
Backend Route (/api/coach/chat)
    ↓
AIService.chat_response()
    ↓
OpenAI API Call (or Fallback)
    ↓
Response Processing
    ↓
Return to User
```

## API Endpoints Reference

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - User login
- `POST /api/auth/google-auth` - Google OAuth

### Sleep Tracking
- `POST /api/sleep/log` - Log sleep data
- `GET /api/sleep/logs/:userId?days=30` - Get sleep logs
- `GET /api/sleep/analytics/:userId?days=30` - Get analytics

### Productivity
- `POST /api/productivity/log` - Log productivity data
- `GET /api/productivity/logs/:userId?days=30` - Get logs
- `GET /api/productivity/correlation/:userId` - Get sleep-productivity correlation

### AI Coach
- `GET /api/coach/recommendation/:userId` - Get daily recommendation
- `POST /api/coach/chat` - Chat with AI assistant
- `GET /api/coach/insights/:userId` - Get predictive insights
- `GET /api/coach/recommendations/:userId?days=7` - Get all recommendations

## Database Collections

### users
```javascript
{
  _id: ObjectId,
  email: String,
  name: String,
  google_id: String (optional),
  created_at: DateTime,
  preferences: {
    target_sleep_hours: Number,
    target_bedtime: String,
    target_wake_time: String,
    notifications_enabled: Boolean
  },
  profile: {
    age: Number,
    occupation: String,
    accessibility_needs: Array
  }
}
```

### sleep_logs
```javascript
{
  _id: ObjectId,
  user_id: String,
  date: String (ISO),
  sleep_time: DateTime,
  wake_time: DateTime,
  duration_hours: Number,
  mood: Number (1-5),
  sleep_quality: Number (1-5),
  notes: String,
  created_at: DateTime,
  updated_at: DateTime
}
```

### productivity_logs
```javascript
{
  _id: ObjectId,
  user_id: String,
  date: String (ISO),
  productivity_score: Number (1-10),
  focus_level: Number (1-5),
  tasks_completed: Number,
  energy_level: Number (1-5),
  notes: String,
  created_at: DateTime,
  updated_at: DateTime
}
```

### ai_recommendations
```javascript
{
  _id: ObjectId,
  user_id: String,
  type: String, // 'sleep', 'productivity', 'daily'
  content: String,
  priority: String, // 'low', 'medium', 'high'
  read: Boolean,
  created_at: DateTime,
  expires_at: DateTime (optional)
}
```

## Technology Stack Details

### Frontend
- **React 18**: Latest React features
- **Vite**: Fast build tool
- **TailwindCSS**: Utility-first CSS
- **Chart.js**: Data visualization
- **Axios**: HTTP client
- **React Router**: Navigation

### Backend
- **Flask**: Lightweight Python web framework
- **PyMongo**: MongoDB driver
- **OpenAI**: AI API integration
- **Flask-CORS**: CORS handling
- **PyJWT**: JWT authentication
- **python-dotenv**: Environment management

### Database
- **MongoDB**: NoSQL document database
- Indexes on user_id and date fields
- Flexible schema for evolving requirements

### Automation
- **n8n**: Workflow automation
- Visual workflow builder
- OpenAI integration
- Webhook triggers
- Scheduled tasks
