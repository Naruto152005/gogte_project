# AI Sleep Quality & Productivity Coach

A comprehensive wellness application that helps users optimize their sleep patterns and productivity through AI-powered insights and recommendations.

## 🌟 Features

- **Smart Sleep Tracker**: Log sleep time, wake time, quality ratings, and mood
- **Productivity Dashboard**: Track daily productivity, focus levels, and task completion
- **AI-Powered Coach**: Get personalized recommendations based on your data
- **Quick-Tip Chat Assistant**: Ask questions about sleep hygiene and productivity
- **Predictive Insights**: Receive warnings about potential low-focus days
- **Data Visualization**: Interactive charts showing sleep and productivity trends
- **n8n Workflow Automation**: Automated data processing and AI triggers

## 🛠️ Technology Stack

### Frontend
- React 18 with Vite
- TailwindCSS for styling
- Chart.js for data visualization
- React Router for navigation
- Axios for API calls

### Backend
- Python Flask
- MongoDB for data storage
- OpenAI API for AI recommendations
- JWT for authentication

### Automation
- n8n for workflow orchestration

## 📋 Prerequisites

- Node.js (v18 or higher)
- Python 3.8+
- MongoDB (local or MongoDB Atlas)
- n8n (optional, for workflow automation)
- OpenAI API key (for AI features)

## 🚀 Installation

### Backend Setup

1. Navigate to the backend directory:
```bash
cd backend
```

2. Create a virtual environment:
```bash
python -m venv venv

# Windows
venv\Scripts\activate

# Linux/Mac
source venv/bin/activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Create `.env` file:
```bash
cp .env.example .env
```

5. Edit `.env` and add your configuration:
```env
SECRET_KEY=your-secret-key-here
MONGODB_URI=mongodb://localhost:27017/sleep_coach_db
OPENAI_API_KEY=your-openai-api-key
N8N_WEBHOOK_URL=http://localhost:5678/webhook
PORT=5000
```

6. Start the backend server:
```bash
python app.py
```

The backend will run on `http://localhost:5000`

### Frontend Setup

1. Navigate to the frontend directory:
```bash
cd frontend
```

2. Install dependencies:
```bash
npm install
```

3. Create `.env` file (optional):
```bash
VITE_API_URL=http://localhost:5000/api
```

4. Start the development server:
```bash
npm run dev
```

The frontend will run on `http://localhost:3000`

## 📊 Database Setup

### MongoDB Local

1. Install MongoDB Community Edition
2. Start MongoDB service:
```bash
# Windows
net start MongoDB

# Linux
sudo systemctl start mongod

# Mac
brew services start mongodb-community
```

### MongoDB Atlas (Cloud)

1. Create account at [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a cluster
3. Get connection string
4. Update `MONGODB_URI` in `.env`

## 🤖 n8n Workflow Setup (Optional)

n8n provides powerful automation for:
- Processing sleep data when logged
- Triggering AI analysis
- Sending daily recommendations
- Monitoring for concerning patterns

### Install n8n

```bash
npm install -g n8n
```

### Start n8n

```bash
n8n start
```

Access n8n at `http://localhost:5678`

### Import Workflows

1. Open n8n interface
2. Import the workflow files from `n8n_workflows/` directory
3. Configure webhook URLs
4. Update `.env` with n8n webhook URL

## 🎯 Usage

### First Time Setup

1. Open `http://localhost:3000` in your browser
2. Click "Sign up" to create an account
3. Enter your email and name
4. Start tracking your sleep and productivity!

### Daily Workflow

1. **Morning**: Log your sleep data
   - Sleep time and wake time
   - Sleep quality rating
   - Morning mood

2. **Evening**: Log your productivity
   - Productivity score
   - Focus level
   - Tasks completed
   - Energy level

3. **Anytime**: 
   - View your dashboard for insights
   - Chat with AI coach for tips
   - Check predictive insights

## 🔒 Security

- JWT-based authentication
- Secure password handling
- CORS protection
- Environment variable configuration

## ♿ Accessibility Features

- ARIA labels for screen readers
- Keyboard navigation support
- High contrast mode support
- Focus indicators
- Reduced motion support

## 🌐 API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - User login
- `POST /api/auth/google-auth` - Google OAuth

### Sleep Tracking
- `POST /api/sleep/log` - Create sleep log
- `GET /api/sleep/logs/:userId` - Get sleep logs
- `GET /api/sleep/analytics/:userId` - Get sleep analytics

### Productivity
- `POST /api/productivity/log` - Create productivity log
- `GET /api/productivity/logs/:userId` - Get productivity logs
- `GET /api/productivity/correlation/:userId` - Get sleep-productivity correlation

### AI Coach
- `GET /api/coach/recommendation/:userId` - Get daily recommendation
- `POST /api/coach/chat` - Chat with AI assistant
- `GET /api/coach/insights/:userId` - Get predictive insights

## 📈 Future Enhancements

- Voice assistant integration
- Wearable device data sync (Fitbit, Apple Watch)
- Academic performance correlation
- Social features (anonymous community)
- Mobile app (React Native)
- Advanced ML models for better predictions
- Meditation and breathing exercise timers

## 🤝 Contributing

This is an academic project for the n8n hackathon. Contributions and suggestions are welcome!

## 📝 License

MIT License

## 👥 Team

Developed for the n8n Hackathon focusing on HealthTech and Accessibility

## 🆘 Troubleshooting

### Backend won't start
- Ensure MongoDB is running
- Check Python version (3.8+)
- Verify all environment variables are set

### Frontend shows connection errors
- Verify backend is running on port 5000
- Check CORS settings
- Ensure API URL is correct

### AI features not working
- Verify OpenAI API key is valid
- Check API key has sufficient credits
- Fallback responses will work without API key

## 📧 Support

For issues or questions, please open an issue on GitHub.

---

Built with ❤️ for better sleep and productivity
