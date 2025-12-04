Digital Clock with Task Reminders

This project is a **cross-platform digital clock and task reminder system** written in C.  
It continuously displays the current date, time, and day of the week, while also managing a list of user-defined tasks. At the scheduled time, the program alerts the user with a beep and reminder message.

##Features
- **Digital Clock**: Displays live time in `HH:MM:SS` format with date and weekday.
- **Task Scheduling**:
  - Enter tasks with names and times in 12-hour format (AM/PM).
  - Automatically converts to 24-hour format internally.
- **Reminders**:
  - Alerts with a beep and message when a task time is reached.
  - Shows countdown (`Starts in HH:MM:SS`) until the task begins.
- **Cross-Platform Support**:
  - Works on **Windows** (`cls`, `Sleep`, `Beep`).
  - Works on **Linux/Unix** (`clear`, `sleep`, `printf("\a")`).
- **Automatic Rollover**: Handles next-day rollover if a task time has already passed.

---

## Dependencies
The program uses the following header files:

```c
#include <stdio.h>     // Input/output functions
#include <time.h>      // System time functions
#include <string.h>    // String handling
#include <ctype.h>     // Character handling

#ifdef _WIN32
    #include <windows.h>   // Windows-specific functions
#else
    #include <unistd.h>    // Unix/Linux-specific functions
#endif
```

---

## 📂 Data Structure
Tasks are stored in a `struct`:

```c
typedef struct {
    char name[100];
    int hour24, minute;
    int reminded;
} Task;
```

- `name` → Task name  
- `hour24`, `minute` → Scheduled time (24-hour format)  
- `reminded` → Flag to track if reminder has been triggered  

---

## How It Works
1. User specifies the number of tasks.  
2. For each task:
   - Enter task name.
   - Enter time in 12-hour format (`HH MM AM/PM`).  
   - Program converts to 24-hour format and stores it.  
3. Infinite loop:
   - Clears screen.
   - Displays clock.
   - Shows tasks with countdown/reminders.
   - Pauses for 1 second before refreshing.

---

## Example Run
```
How many tasks (1-20)? 2
Enter task 1 name: Study
Enter time for "Study" (HH MM AM/PM): 10 30 AM
Enter task 2 name: Lunch
Enter time for "Lunch" (HH MM AM/PM): 1 00 PM
```

**Output (live updating):**
```
=== Digital Clock ===
04-12-2025 (Thu)
10:29:55
=====================
Task: Study           | At 10:30 | Starts in 00:00:05
Task: Lunch           | At 13:00 | Starts in 02:30:05
```

---

## Compilation & Execution
### On Windows:
```bash
gcc clock.c -o clock
clock.exe
```

### On Linux/Unix:
```bash
gcc clock.c -o clock
./clock
```

---

## Notes
- Maximum tasks: **20** (defined by `MAX_TASKS`).  
- Uses **conditional compilation** for portability.  
- Reminder resets if the task is more than 1 minute away again.  
- Beep sound may vary depending on OS and terminal support.  

---

## Use Case
This project is ideal for:
- Learning **modular C programming**.  
- Demonstrating **time handling, string manipulation, and character classification**.  
- Showcasing **cross-platform development** in academic presentations or viva exams.  

---
