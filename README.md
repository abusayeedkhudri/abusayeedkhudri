class Task:
    def __init__(self, title, description, due_date):
        self.title = title
        self.description = description
        self.due_date = due_date
        self.completed = False

    def mark_as_completed(self):
        self.completed = True

    def __str__(self):
        status = "Completed" if self.completed else "Not Completed"
        return f"Title: {self.title}\nDescription: {self.description}\nDue Date: {self.due_date}\nStatus: {status}\n"


class TaskManager:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append(task)

    def view_tasks(self):
        for task in self.tasks:
            print(task)

def main():
    task_manager = TaskManager()

    while True:
        print("\nMenu:")
        print("1. Add Task")
        print("2. View Tasks")
        print("3. Mark Task as Completed")
        print("4. Exit")

        choice = input("Enter your choice (1/2/3/4): ")

        if choice == "1":
            title = input("Enter task title: ")
            description = input("Enter task description: ")
            due_date = input("Enter due date: ")

            new_task = Task(title, description, due_date)
            task_manager.add_task(new_task)
            print("Task added successfully!")

        elif choice == "2":
            task_manager.view_tasks()

        elif choice == "3":
            task_manager.view_tasks()
            task_index = int(input("Enter the index of the task to mark as completed: "))
            
            if 0 <= task_index < len(task_manager.tasks):
                task_manager.tasks[task_index].mark_as_completed()
                print("Task marked as completed!")

            else:
                print("Invalid task index.")

        elif choice == "4":
            print("Exiting the program. Goodbye!")
            break

        else:
            print("Invalid choice. Please enter a valid option.")

if __name__ == "__main__":
    main()

