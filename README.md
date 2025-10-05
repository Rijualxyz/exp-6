import java.io.*;
class Student implements Serializable {
    int studentID;
    String name;
    String grade;
    Student(int studentID, String name, String grade) {
        this.studentID = studentID;
        this.name = name;
        this.grade = grade;
    }
}
public class Exp6 {
    public static void main(String[] args) {
        Student s1 = new Student(101, "Riya", "A");
        try {
            ObjectOutputStream out = new ObjectOutputStream(new FileOutputStream("student.ser"));
            out.writeObject(s1);
            out.close();
            ObjectInputStream in = new ObjectInputStream(new FileInputStream("student.ser"));
            Student s2 = (Student) in.readObject();
            in.close();
            System.out.println("Student ID: " + s2.studentID);
            System.out.println("Name: " + s2.name);
            System.out.println("Grade: " + s2.grade);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
