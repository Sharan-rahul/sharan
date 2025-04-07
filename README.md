mvc-project/
├── controller.py
├── model.py
├── view.py
└── main.py
class Student:
    def __init__(self):
        self.name = None
        self.roll_no = None

    def get_name(self):
        return self.name

    def get_roll_no(self):
        return self.roll_no

    def set_name(self, name):
        self.name = name

    def set_roll_no(self, roll_no):
        self.roll_no = roll_no
class StudentView:
    def print_student_details(self, student_name, student_roll_no):
        print("Student Details:")
        print(f"Name: {student_name}")
        print(f"Roll No: {student_roll_no}")
class StudentController:
    def __init__(self, model, view):
        self.model = model
        self.view = view

    def set_student_name(self, name):
        self.model.set_name(name)

    def get_student_name(self):
        return self.model.get_name()

    def set_student_roll_no(self, roll_no):
        self.model.set_roll_no(roll_no)

    def get_student_roll_no(self):
        return self.model.get_roll_no()

    def update_view(self):
        self.view.print_student_details(self.model.get_name(), self.model.get_roll_no())
from model import Student
from view import StudentView
from controller import StudentController

def main():
    # Create the model
    student = Student()
    student.set_name("John")
    student.set_roll_no("123")

    # Create the view
    view = StudentView()

    # Create the controller
    controller = StudentController(student, view)

    # Display initial details
    controller.update_view()

    # Update data
    controller.set_student_name("Michael")
    controller.update_view()

if __name__ == "__main__":
    main()
