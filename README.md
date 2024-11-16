# E-Learning-Platform
E-learning Platform
• Admin:
o Manage users (add, update, delete instructor, student, and admin accounts).
o Manage course content, pricing, and schedules.
o Track course enrollments, payments, and completion rates.
o Assign roles and permissions to instructors and students.
o Generate reports on course performance and student progress.
• Instructor:
o Create and manage course content, assignments, and exams.
o Track student progress and provide feedback.
o View course enrollments and manage schedules.
o Manage personal profile and availability.
• Student:
o Enroll in courses and track learning progress.
o Complete assignments, exams, and view grades.
o Make payments for courses and manage subscriptions.
o Update personal details and manage account settings.



Code:

import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.layout.VBox;
import javafx.stage.Stage;

import java.util.ArrayList;
import java.util.List;

public class E_LearningPlatform extends Application {

    private static List<Course> courses = new ArrayList<>();

    @Override
    public void start(Stage primaryStage) {
        VBox root = new VBox(10);

        Button adminButton = new Button("Admin Login");
        adminButton.setOnAction(e -> showAdminDashboard(primaryStage));

        Button instructorButton = new Button("Instructor Login");
        instructorButton.setOnAction(e -> showInstructorDashboard(primaryStage));

        Button studentButton = new Button("Student Login");
        studentButton.setOnAction(e -> showStudentDashboard(primaryStage));

        root.getChildren().addAll(adminButton, instructorButton, studentButton);

        Scene scene = new Scene(root, 400, 200);
        primaryStage.setTitle("E-Learning Platform");
        primaryStage.setScene(scene);
        primaryStage.show();
    }

    private void showAdminDashboard(Stage stage) {
        VBox root = new VBox(10);
        Button addCourseButton = new Button("Add Course");
        Button viewCoursesButton = new Button("View Courses");

        addCourseButton.setOnAction(e -> addCourse("Java Basics", "John Doe"));
        viewCoursesButton.setOnAction(e -> viewCourses());

        root.getChildren().addAll(addCourseButton, viewCoursesButton);
        Scene scene = new Scene(root, 400, 200);
        stage.setScene(scene);
    }

    private void showInstructorDashboard(Stage stage) {
        VBox root = new VBox(10);
        Button createQuizButton = new Button("Create Quiz");
        Button viewSubmissionsButton = new Button("View Submissions");

        createQuizButton.setOnAction(e -> System.out.println("Quiz created!"));
        viewSubmissionsButton.setOnAction(e -> System.out.println("Viewing submissions!"));

        root.getChildren().addAll(createQuizButton, viewSubmissionsButton);
        Scene scene = new Scene(root, 400, 200);
        stage.setScene(scene);
    }

    private void showStudentDashboard(Stage stage) {
        VBox root = new VBox(10);
        Button enrollCourseButton = new Button("Enroll in Course");
        Button takeQuizButton = new Button("Take Quiz");

        enrollCourseButton.setOnAction(e -> enrollInCourse("Java Basics"));
        takeQuizButton.setOnAction(e -> System.out.println("Quiz started!"));

        root.getChildren().addAll(enrollCourseButton, takeQuizButton);
        Scene scene = new Scene(root, 400, 200);
        stage.setScene(scene);
    }

    private void addCourse(String courseName, String instructorName) {
        courses.add(new Course(courseName, instructorName));
        System.out.println("Course added: " + courseName);
    }

    private void viewCourses() {
        System.out.println("Available Courses:");
        for (Course course : courses) {
            System.out.println(course);
        }
    }

    private void enrollInCourse(String courseName) {
        boolean found = false;
        for (Course course : courses) {
            if (course.getCourseName().equals(courseName)) {
                found = true;
                System.out.println("Enrolled in course: " + courseName);
                break;
            }
        }
        if (!found) {
            System.out.println("Course not found: " + courseName);
        }
    }

    private static class Course {
        private String courseName;
        private String instructorName;

        public Course(String courseName, String instructorName) {
            this.courseName = courseName;
            this.instructorName = instructorName;
        }

        public String getCourseName() {
            return courseName;
        }

        public String getInstructorName() {
            return instructorName;
        }

        @Override
        public String toString() {
            return "Course: " + courseName + ", Instructor: " + instructorName;
        }
    }

    public static void main(String[] args) {
        launch(args);
    }
}
