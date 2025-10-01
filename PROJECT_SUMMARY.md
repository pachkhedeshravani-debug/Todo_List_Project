# Todo List Project - Complete Source Documentation

## Project Overview

**Project Name:** Interactive Todo List Application  
**Framework:** Django 5.1.5  
**Database:** SQLite3  
**Python Version:** 3.13.7  
**Location:** `C:\Users\LENOVO\Downloads\todo_project(zip)\todo_project\`

---

## Features Implemented

### Core Features
- ✅ Create, read, update, delete (CRUD) tasks
- ✅ Mark tasks as complete/incomplete
- ✅ Set due dates for tasks
- ✅ Task frequency categorization (None, Weekly, Monthly, Yearly)
- ✅ Automatic timestamp tracking (created_at, completed_at)

### Enhanced UI Features
- ✅ Single Page Application (SPA) with client-side navigation
- ✅ Dark theme with softer color palette
- ✅ Responsive layout with sidebar
- ✅ Interactive task lists with animations
- ✅ Upcoming tasks sidebar widget

### Completed Tasks Page Features
- ✅ Search by task title
- ✅ Date range filtering (From/To)
- ✅ Sorting (newest/oldest, A→Z/Z→A)
- ✅ Bulk restore/delete with checkboxes
- ✅ CSV export functionality
- ✅ Real-time filtering without page reload

### Reminder System
- ✅ Automatic overdue task detection
- ✅ Visual reminder popup
- ✅ Custom ringtone using Web Audio API
- ✅ Phone vibration support (if available)
- ✅ Repeating sound alerts every 3 seconds

### API Endpoints
- ✅ RESTful JSON API (no Django REST Framework)
- ✅ GET /api/tasks/ - List all tasks
- ✅ POST /api/tasks/ - Create task
- ✅ GET /api/tasks/<id>/ - Get task detail
- ✅ PATCH /api/tasks/<id>/ - Update task
- ✅ DELETE /api/tasks/<id>/ - Delete task

---

## Project Structure

```
todo_project/
├── manage.py
├── db.sqlite3
├── .venv/
├── todo_project/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
│   └── asgi.py
└── todo/
    ├── __init__.py
    ├── models.py
    ├── views.py
    ├── urls.py
    ├── admin.py
    ├── apps.py
    ├── tests.py
    ├── migrations/
    │   ├── 0001_initial.py
    │   ├── 0002_task.py
    │   ├── 0003_task_created_at.py
    │   ├── 0004_task_completed_at_task_due_date.py
    │   └── 0005_task_frequency.py
    ├── templates/
    │   └── todo/
    │       ├── todo_list.html
    │       ├── completed_tasks.html
    │       └── contact.html
    └── static/
        └── images/
```

---

## Database Schema

### Task Model
```python
class Task(models.Model):
    FREQUENCY_CHOICES = [
        ('', 'None'),
        ('weekly', 'Weekly'),
        ('monthly', 'Monthly'),
        ('yearly', 'Yearly'),
    ]
    
    title = models.CharField(max_length=200)
    completed = models.BooleanField(default=False)
    created_at = models.DateTimeField(default=timezone.now)
    due_date = models.DateTimeField(null=True, blank=True)
    completed_at = models.DateTimeField(null=True, blank=True)
    frequency = models.CharField(max_length=10, choices=FREQUENCY_CHOICES, default='', blank=True)
```

**Fields:**
- `id` - Auto-generated primary key
- `title` - Task description (max 200 chars)
- `completed` - Boolean flag
- `created_at` - Timestamp when task was created
- `due_date` - Optional deadline
- `completed_at` - Timestamp when marked complete
- `frequency` - Task recurrence (weekly/monthly/yearly/none)

---

## Key Files

### 1. Models (`todo/models.py`)
Defines the Task model with frequency choices and automatic timestamp handling.

### 2. Views (`todo/views.py`)
- `todo_list()` - Main page view, handles task creation
- `complete_task()` - Mark task as complete
- `delete_task()` - Delete task
- `completed_tasks()` - Completed tasks page
- `contact_us()` - Contact page
- `api_tasks()` - JSON API for listing/creating tasks
- `api_task_detail()` - JSON API for get/update/delete single task
- `serialize_task()` - Convert Task model to JSON

### 3. URLs (`todo/urls.py`)
```python
urlpatterns = [
    path('', views.todo_list, name='todo_list'),
    path('complete/<int:pk>/', views.complete_task, name='complete_task'),
    path('delete/<int:pk>/', views.delete_task, name='delete_task'),
    path('contact/', views.contact_us, name='contact_us'),
    path('completed/', views.completed_tasks, name='completed_tasks'),
    path('api/tasks/', views.api_tasks, name='api_tasks'),
    path('api/tasks/<int:pk>/', views.api_task_detail, name='api_task_detail'),
]
```

### 4. Main Template (`todo/templates/todo/todo_list.html`)
- Single Page Application with 3 sections: Home, Completed Tasks, Contact Us
- Dark theme with gradient background
- JavaScript-powered interactivity
- Web Audio API for reminder sounds
- Frequency-based task categorization

---

## Color Scheme (Dark Theme)

```css
:root {
    --bg: #2c3e50;                    /* Main background */
    --text: #ecf0f1;                  /* Primary text */
    --text-muted: #95a5a6;            /* Secondary text */
    --container-bg: rgba(52, 73, 94, 0.95);  /* Container */
    --card-bg: #34495e;               /* Card background */
    --card-border: #4a5f7f;           /* Borders */
    --shadow: rgba(0, 0, 0, 0.3);     /* Shadows */
    --nav-bg: rgba(44, 62, 80, 0.95); /* Navigation */
    --list-bg: #3d5a80;               /* List items */
    --accent1: #3498db;               /* Blue accent */
    --accent2: #2ecc71;               /* Green accent */
}
```

**Gradient Background:**
```css
background: linear-gradient(135deg, #2c3e50 0%, #34495e 50%, #3d5a80 100%);
```

---

## Admin Access

**Superuser Credentials:**
- Username: `admin`
- Password: `admin123`
- Email: `admin@example.com`

**Admin URL:** http://127.0.0.1:8000/admin/

---

## Running the Project

### 1. Start the Development Server
```bash
cd C:\Users\LENOVO\Downloads\todo_project(zip)\todo_project\
.\.venv\Scripts\python manage.py runserver 0.0.0.0:8000
```

### 2. Access the Application
- **Main App:** http://127.0.0.1:8000/
- **Admin Panel:** http://127.0.0.1:8000/admin/
- **Completed Tasks:** http://127.0.0.1:8000/completed/
- **Contact Us:** http://127.0.0.1:8000/contact/

### 3. API Endpoints
- **List Tasks:** GET http://127.0.0.1:8000/api/tasks/
- **Create Task:** POST http://127.0.0.1:8000/api/tasks/
- **Task Detail:** GET http://127.0.0.1:8000/api/tasks/1/
- **Update Task:** PATCH http://127.0.0.1:8000/api/tasks/1/
- **Delete Task:** DELETE http://127.0.0.1:8000/api/tasks/1/

---

## JavaScript Features

### Task Management
- `fetchTasks()` - Load tasks from API
- `createTask(title, dueDate, frequency)` - Create new task
- `updateTask(id, payload)` - Update task properties
- `deleteTask(id)` - Delete task
- `renderTasks(filter)` - Render tasks by category

### Reminder System
- `checkReminders()` - Check for overdue tasks (runs every 60 seconds)
- `playReminderSound()` - Generate beep pattern with Web Audio API
- `startRingtone()` - Start repeating sound
- `stopRingtone()` - Stop sound and clear interval

### Completed Tasks Features
- `applyFiltersAndRender()` - Filter by search/date/sort
- `selectedIds()` - Get checked task IDs
- `exportCSV()` - Download tasks as CSV file

---

## Contact Information

**Phone:** 1597642305  
**Email:** todo@gmail.com

---

## Future Enhancement Ideas

1. **User Authentication** - Multi-user support with login/logout
2. **Task Categories/Tags** - Organize tasks by project or category
3. **Priority Levels** - High/Medium/Low priority flags
4. **Subtasks** - Break down tasks into smaller steps
5. **Dark/Light Theme Toggle** - User preference switching
6. **Mobile App** - React Native or Flutter version
7. **Email Notifications** - Send reminders via email
8. **Calendar Integration** - Sync with Google Calendar
9. **Task Notes** - Add detailed descriptions
10. **File Attachments** - Attach documents to tasks

---

## Technologies Used

- **Backend:** Django 5.1.5
- **Frontend:** Vanilla JavaScript (ES6+)
- **Database:** SQLite3
- **CSS:** Custom CSS with CSS Variables
- **Audio:** Web Audio API
- **Icons/Fonts:** System fonts (Segoe UI)

---

## License

This project was created for educational purposes.

---

## Project Statistics

- **Total Files:** ~15 files
- **Lines of Code (HTML/CSS/JS):** ~1,000+ lines in main template
- **Lines of Code (Python):** ~150 lines
- **Database Tables:** 2 (Task, Todo - legacy)
- **API Endpoints:** 5
- **Pages:** 3 (Home, Completed, Contact)

---

**Last Updated:** September 30, 2025  
**Version:** 1.0.0
