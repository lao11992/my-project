# OSRSTracker

Welcome to OSRSTracker! This is a web application for tracking and analyzing Old School RuneScape player data.

Thank you for checking out this early project build! New features are coming soon, and improvements to existing functionality will continue!

## 🚀 Quick Start

### System Requirements
- Python 3.8+
- Docker (Recommended)
- Make utility

### Supported Operating Systems
- **macOS** (Primary development environment)
- **Windows** (Requires command adjustments)
- **Linux** (Compatible)

## 📋 Project Structure

```
OSRSTracker/
├── backend/                 # Backend logic
│   ├── player_info.py      # Player data fetching module
│   ├── item_prices.py      # Item price lookup (To be implemented)
│   └── item_trends_graphs.py # Item trend graphs (To be implemented)
├── templates/               # Frontend templates
│   ├── stats.html          # Player statistics page
│   ├── economy.html        # Economy data analysis page
│   └── style.css           # Style sheets
├── src/                     # Static resources
│   ├── img_site.json       # Skill icon mapping
│   └── next_level.json     # Experience required for next level
├── Dockerfile              # Docker configuration
├── Makefile                # Build scripts
├── requirements.txt        # Python dependencies
└── routing.py             # Flask routing configuration
```

## 🔧 Installation & Deployment

### For macOS/Linux Users

1. **Fetch Player Data**
   ```bash
   make api_test USER=YourOSRSUsername
   ```
   This command will:
   - Clean previous cached data
   - Fetch complete data for the specified player from OSRS official API
   - Generate the following files:
     - `backend/skill_stats.json` (Skill data, backward compatible)
     - `backend/YourOSRSUsername_complete_data.json` (Complete player data)
     - `backend/YourOSRSUsername_skills.csv` (Skills in CSV format)
     - `backend/YourOSRSUsername_activities.csv` (Activities in CSV format)
     - `backend/YourOSRSUsername_bosses.csv` (Boss kills in CSV format)

2. **Start Web Application**
   ```bash
   make run
   ```
   This command will:
   - Build Docker image
   - Start container on port 8080
   - Automatically open browser at `http://localhost:8080/`

3. **Clean Environment**
   ```bash
   make clean
   ```
   This command will:
   - Stop and remove Docker container
   - Delete generated data files

### For Windows Users

Since the Makefile is primarily designed for Unix systems, Windows users can execute the corresponding commands manually:

1. **Fetch Player Data**
   ```powershell
   python backend/player_info.py get_skills YourOSRSUsername
   ```

2. **Start Application**
   ```powershell
   docker build -t my-app:1.0 .
   docker run --name my-app -p 8080:8080 -d my-app:1.0
   ```

## 🎮 Features

### Implemented Features

✅ **Player Data Tracking**
- Real-time fetching of player skill levels, experience, and rankings
- Support for all 23 skills data
- Activity and minigame statistics
- Boss kill tracking records
- Dual format export support (JSON and CSV)

✅ **Web Interface Display**
- Responsive Bootstrap design
- Pixel-style UI interface
- Skill category display (Combat, Gathering, Crafting, etc.)
- Real-time data visualization

✅ **Data Validation & Processing**
- Username format validation
- Data integrity checks
- Error handling mechanisms

### Planned Features

🔄 **Economy Data Analysis**
- Item market price lookup
- Historical price trend analysis
- Market supply-demand charts
- Personalized investment recommendations

🔄 **Advanced Statistics**
- Player progress prediction
- Level-up time estimation
- Achievement completion analysis

## 🧪 Test Usernames

Here are some valid OSRS usernames that can be used for testing:

- `Apple`
- `Lelalt`

Usage example:
```bash
make api_test USER=Apple
```

## 🛠️ Development Guide

### Local Development

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

2. Run Flask application directly:
   ```bash
   python routing.py
   ```

3. Access at: `http://localhost:8080/`

### Code Structure Explanation

- **backend/player_info.py**: Core data fetching module responsible for OSRS API communication
- **routing.py**: Main Flask application file defining routes and page rendering logic
- **templates/stats.html**: Main display page using Jinja2 template engine
- **src/img_site.json**: Skill icon URL mapping configuration

### API Endpoints

Currently supported routes:
- `/` - Player skill statistics homepage
- `/economy` - Economy data analysis page (To be completed)
- `/login` - Login functionality (To be implemented)

## 📊 Data Schema

### Skill Data Structure
```json
{
  "skill_name": "Attack",
  "rank": 12345,
  "level": 99,
  "xp": 13034431
}
```

### Activity Data Structure
```json
{
  "activity_name": "Clue Scrolls All",
  "rank": 54321,
  "score": 150
}
```

### Boss Data Structure
```json
{
  "boss_name": "Zulrah",
  "rank": 98765,
  "kills": 234
}
```

## ⚠️ Important Notes

1. **API Limitations**: OSRS official API has rate limiting, please avoid frequent calls
2. **Data Accuracy**: All data comes directly from Jagex official API to ensure accuracy
3. **Username Standards**: Usernames must follow OSRS rules (1-12 characters, alphanumeric and underscores only)
4. **Docker Port**: Ensure port 8080 is not occupied by other applications

## 🤝 Contribution Guidelines

Issues and Pull Requests are welcome to help improve the project!

## 📄 License

This project is for learning and entertainment purposes only. Please comply with OSRS terms of service.

---

*Project is actively under development, more features coming soon!**