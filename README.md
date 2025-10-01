# 📝 Interactive Todo List Application

A feature-rich, modern Todo List web application built with Django and vanilla JavaScript. Features a beautiful dark theme, task frequency categorization, smart reminders with custom ringtones, and an advanced completed tasks management system.

![Django](https://img.shields.io/badge/Django-5.1.5-green)
![Python](https://img.shields.io/badge/Python-3.13.7-blue)
![License](https://img.shields.io/badge/License-MIT-yellow)

## ✨ Features

### 🎯 Core Functionality
- ✅ Create, read, update, and delete tasks
- ✅ Mark tasks as complete/incomplete
- ✅ Set due dates with datetime picker
- ✅ Task frequency categorization (None, Weekly, Monthly, Yearly)
- ✅ Automatic timestamp tracking (created_at, completed_at)

### 🎨 User Interface
- 🌙 Modern dark theme with soft gradient background
- 📱 Responsive design with sidebar layout
- ✨ Smooth animations and transitions
- 🎯 Single Page Application (SPA) with client-side navigation
- 📊 Upcoming tasks widget in sidebar

### 🔍 Advanced Completed Tasks Management
- 🔎 Search tasks by title
- 📅 Date range filtering (From/To)
- 🔄 Multiple sorting options (newest/oldest, A→Z/Z→A)
- ☑️ Bulk restore/delete with checkboxes
- 📥 Export to CSV functionality
- ⚡ Real-time filtering without page reload

### 🔔 Smart Reminder System
- ⏰ Automatic overdue task detection
- 🔊 Custom ringtone using Web Audio API
- 📳 Phone vibration support (if available)
- 🔁 Repeating sound alerts every 3 seconds
- 🎵 Melodic beep pattern (880Hz-660Hz sequence)

### 🔌 RESTful API
- 📡 JSON API endpoints (no Django REST Framework required)
- 🔄 Full CRUD operations via API
- 📝 Supports GET, POST, PATCH, DELETE methods

## 🚀 Quick Start

### Prerequisites
- Python 3.13+ installed
- pip package manager

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/YOUR_USERNAME/todo-list-app.git
cd todo-list-app
```

2. **Create virtual environment**
```bash
python -m venv .venv
```

3. **Activate virtual environment**
- Windows:
```bash
.\.venv\Scripts\activate
```
- macOS/Linux:
```bash
source .venv/bin/activate
```

4. **Install dependencies**
```bash
pip install django
```

5. **Run migrations**
```bash
python manage.py migrate
```

6. **Create superuser (optional)**
```bash
python manage.py createsuperuser
```

7. **Start development server**
```bash
python manage.py runserver
```

8. **Open in browser**
```
http://127.0.0.1:8000/
```

## 📱 Usage

### Creating Tasks
1. Enter task title in the input field
2. Optionally set a due date
3. Select frequency (None, Weekly, Monthly, Yearly)
4. Click "Add Task"

### Managing Tasks
- **Complete:** Click "Complete" button on any task
- **Delete:** Click "Delete" button to remove task
- **View by Frequency:** Tasks automatically categorize into sections

### Completed Tasks Page
1. Click "Completed Tasks" in navigation
2. Use search box to filter by title
3. Set date range to filter by completion date
4. Select sort order from dropdown
5. Check multiple tasks for bulk actions
6. Click "Restore" to move back to active
7. Click "Delete" to permanently remove
8. Click "Export CSV" to download data

### Reminders
- Set a due date in the past to test reminders
- Reminder popup appears automatically
- Sound plays and repeats every 3 seconds
- Click × to dismiss

## 🛠️ Technology Stack

- **Backend:** Django 5.1.5
- **Frontend:** Vanilla JavaScript (ES6+)
- **Database:** SQLite3
- **Styling:** Custom CSS with CSS Variables
- **Audio:** Web Audio API
- **Architecture:** Single Page Application (SPA)

## 📂 Project Structure

```
todo_project/
├── manage.py
├── db.sqlite3
├── .gitignore
├── README.md
├── PROJECT_SUMMARY.md
├── todo_project/
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
└── todo/
    ├── models.py
    ├── views.py
    ├── urls.py
    ├── admin.py
    ├── migrations/
    └── templates/
        └── todo/
            ├── todo_list.html
            ├── completed_tasks.html
            └── contact.html
```

## 🎨 Color Scheme

The app uses a carefully crafted dark theme:

```css
--bg: #2c3e50;           /* Main background */
--text: #ecf0f1;         /* Primary text */
--card-bg: #34495e;      /* Card background */
--list-bg: #3d5a80;      /* List items */
--accent1: #3498db;      /* Blue accent */
--accent2: #2ecc71;      /* Green accent */
```

## 🔌 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/tasks/` | List all tasks |
| POST | `/api/tasks/` | Create new task |
| GET | `/api/tasks/<id>/` | Get task details |
| PATCH | `/api/tasks/<id>/` | Update task |
| DELETE | `/api/tasks/<id>/` | Delete task |

### Example API Request

**Create Task:**
```bash
curl -X POST http://127.0.0.1:8000/api/tasks/ \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Buy groceries",
    "due_date": "2025-10-05T10:00:00",
    "frequency": "weekly"
  }'
```

## 🗄️ Database Schema

### Task Model
```python
class Task(models.Model):
    title = CharField(max_length=200)
    completed = BooleanField(default=False)
    created_at = DateTimeField(default=timezone.now)
    due_date = DateTimeField(null=True, blank=True)
    completed_at = DateTimeField(null=True, blank=True)
    frequency = CharField(max_length=10, choices=FREQUENCY_CHOICES)
```

## 🔐 Admin Panel

Access the Django admin at: `http://127.0.0.1:8000/admin/`

Default credentials (if you used the quick setup):
- Username: `admin`
- Password: `admin123`

**⚠️ Change these credentials in production!**

## 🌟 Future Enhancements

- [ ] User authentication and multi-user support
- [ ] Task categories and tags
- [ ] Priority levels (High/Medium/Low)
- [ ] Subtasks and checklists
- [ ] Dark/Light theme toggle
- [ ] Email notifications
- [ ] Calendar integration
- [ ] Mobile app version
- [ ] Task notes and descriptions
- [ ] File attachments

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 📧 Contact

**Email:** todo@gmail.com  
**Phone:** 1597642305

## 🙏 Acknowledgments

- Built with Django framework
- Inspired by modern task management apps
- Uses Web Audio API for custom sounds

---

**⭐ If you find this project useful, please consider giving it a star!**

Made with ❤️ using Django
