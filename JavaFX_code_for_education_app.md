# My_Java_Codes
#My_JavaFX_Code_for_education_application
import javafx.application.Application;
import javafx.geometry.Insets;
import javafx.scene.Scene;
import javafx.scene.control.*;
import javafx.scene.layout.GridPane;
import javafx.stage.Stage;

interface Learner {
    void learn();
}

abstract class Person {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public abstract void introduce();

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }
}

class Student extends Person implements Learner {
    private String major;

    public Student(String name, int age, String major) {
        super(name, age);
        this.major = major;
    }

    @Override
    public void introduce() {
        System.out.println("I am a student.");
    }

    @Override
    public void learn() {
        System.out.println("I am learning.");
    }
}

class Teacher extends Person implements Learner {
    private String subject;

    public Teacher(String name, int age, String subject) {
        super(name, age);
        this.subject = subject;
    }

    @Override
    public void introduce() {
        System.out.println("I am a teacher.");
    }

    @Override
    public void learn() {
        System.out.println("I am also learning.");
    }
}

public class PersonalEducationApp extends Application {

    public static void main(String[] args) {
        launch(args);
    }

    @Override
    public void start(Stage primaryStage) {
        primaryStage.setTitle("Personal Education App");

        GridPane grid = new GridPane();
        grid.setPadding(new Insets(10, 10, 10, 10));
        grid.setVgap(5);
        grid.setHgap(5);

        // Name label
        Label nameLabel = new Label("Name:");
        GridPane.setConstraints(nameLabel, 0, 0);
        grid.getChildren().add(nameLabel);

        // Name input field
        TextField nameInput = new TextField();
        GridPane.setConstraints(nameInput, 1, 0);
        grid.getChildren().add(nameInput);

        // Age label
        Label ageLabel = new Label("Age:");
        GridPane.setConstraints(ageLabel, 0, 1);
        grid.getChildren().add(ageLabel);

        // Age input field
        TextField ageInput = new TextField();
        GridPane.setConstraints(ageInput, 1, 1);
        grid.getChildren().add(ageInput);

        // Major/Subject label
        Label majorLabel = new Label("Major/Subject:");
        GridPane.setConstraints(majorLabel, 0, 2);
        grid.getChildren().add(majorLabel);

        // Major/Subject input field
        TextField majorInput = new TextField();
        GridPane.setConstraints(majorInput, 1, 2);
        grid.getChildren().add(majorInput);

        // Buttons
        Button studentButton = new Button("Create Student");
        GridPane.setConstraints(studentButton, 0, 3);
        grid.getChildren().add(studentButton);

        Button teacherButton = new Button("Create Teacher");
        GridPane.setConstraints(teacherButton, 1, 3);
        grid.getChildren().add(teacherButton);

        // Output label
        Label outputLabel = new Label();
        GridPane.setConstraints(outputLabel, 0, 4);
        GridPane.setColumnSpan(outputLabel, 2);
        grid.getChildren().add(outputLabel);

        studentButton.setOnAction(event -> {
            String name = nameInput.getText();
            int age = Integer.parseInt(ageInput.getText());
            String major = major
