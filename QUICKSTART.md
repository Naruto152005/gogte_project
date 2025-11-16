# 🚀 Quick Start Guide - AI Sleep Quality & Productivity Coach

Get up and running in 5 minutes!

## Prerequisites Check

Before starting, ensure you have:
- ✅ Python 3.8 or higher (`python --version`)
- ✅ Node.js 18 or higher (`node --version`)
- ✅ MongoDB installed and running
- ✅ OpenAI API key (optional but recommended)

## Step-by-Step Setup

### 1. Backend Setup (5 minutes)

```bash
# Navigate to backend folder
cd backend

# Create virtual environment
python -m venv venv

# Activate virtual environment
# Windows:
venv\Scripts\activate
# Mac/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Setup environment variables
cp .env.example .env

# Edit .env file with your settings
# Minimum required:
# - SECRET_KEY (use any random string)
# - MONGODB_URI (default works if MongoDB is running locally)
# - OPENAI_API_KEY (optional - fallback responses work without it)

# Start the backend server
python app.py
```

Backend should now be running on `http://localhost:5000`

### 2. Frontend Setup (3 minutes)

Open a new terminal:

```bash
# Navigate to frontend folder
cd frontend

# Install dependencies
npm install

# Start development server
npm run dev
```

Frontend should now be running on `http://localhost:3000`

### 3. First Use

1. Open browser to `http://localhost:3000`
2. Click "Sign up" 
3. Enter your email and name
4. Start using the app!

## Quick Test

### Test Sleep Tracking
1. Go to "Sleep Tracker" page
2. Enter yesterday's sleep:
   - Sleep time: 11:00 PM yesterday
   - Wake time: 7:00 AM today
   - Sleep quality: 4/5
   - Mood: 4/5
3. Click "Log Sleep Data"
4. View your data on the Dashboard

### Test AI Coach
1. Go to "AI Coach" page
2. Ask a question: "How can I improve my sleep quality?"
3. View personalized response

## Optional: n8n Setup

For advanced workflow automation:

```bash
# Install n8n globally
npm install -g n8n

# Start n8n
n8n start
```

Then:
1. Open `http://localhost:5678`
2. Import workflows from `n8n_workflows/` folder
3. Configure webhooks
4. Activate workflows

## Troubleshooting

### Backend Issues

**"ModuleNotFoundError"**
```bash
pip install -r requirements.txt
```

**"MongoDB connection failed"**
- Ensure MongoDB is running: `mongod` or check Windows Services
- Verify MONGODB_URI in .env

**"OpenAI API error"**
- App works without OpenAI (uses fallback responses)
- To use AI features, add valid OPENAI_API_KEY to .env

### Frontend Issues

**"Cannot connect to backend"**
- Ensure backend is running on port 5000
- Check console for CORS errors
- Verify VITE_API_URL in .env (optional)

**"npm install fails"**
```bash
# Clear cache and retry
npm cache clean --force
npm install
```

### Database Issues

**MongoDB not running**
```bash
# Windows
net start MongoDB

# Mac
brew services start mongodb-community

# Linux
sudo systemctl start mongod
```

## Environment Variables Reference

### Backend (.env)
```env
SECRET_KEY=your-secret-key-here
MONGODB_URI=mongodb://localhost:27017/sleep_coach_db
OPENAI_API_KEY=sk-your-key-here (optional)
N8N_WEBHOOK_URL=http://localhost:5678/webhook (optional)
PORT=5000
```

### Frontend (.env)
```env
VITE_API_URL=http://localhost:5000/api
```

## Default Ports

- **Frontend**: http://localhost:3000
- **Backend**: http://localhost:5000  
- **n8n**: http://localhost:5678
- **MongoDB**: localhost:27017

## Testing the Application

### Manual Testing Checklist

- [ ] User registration works
- [ ] User login works
- [ ] Sleep logging saves data
- [ ] Productivity logging saves data
- [ ] Dashboard shows charts
- [ ] AI Coach responds to questions
- [ ] Predictive insights display

### Sample Data

You can create sample data by logging:
- 7 days of sleep data
- 7 days of productivity data
- Then view correlations and insights

## Next Steps

1. **Customize AI Prompts**: Edit `backend/services/ai_service.py`
2. **Add Features**: Extend the API and frontend
3. **Setup n8n Workflows**: Automate notifications and analysis
4. **Deploy**: Use Render/Vercel for production deployment

## Getting Help

- Check the main README.md for detailed documentation
- Review API endpoints in backend/routes/
- Check browser console for errors
- Verify all services are running

## Success Indicators

You'll know everything is working when:
- ✅ Backend shows "Database connected successfully"
- ✅ Frontend loads without errors
- ✅ You can register and login
- ✅ Sleep/productivity data saves and displays
- ✅ Dashboard shows visualizations
- ✅ AI Coach provides responses

---

**Enjoy building healthier sleep habits! 😴💤**
