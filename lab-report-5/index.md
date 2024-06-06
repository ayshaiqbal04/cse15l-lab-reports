### Canvas Post

**Student**

I'm having trouble with my Java program, which is supposed to read a text 
file and print its contents to the console. However, when I run my script, 
it only prints "File not found" even though the file exists in the same 
directory. I've attached relevant parts of my code.

Java File
```
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class FilePrinter {
    public static void main(String[] args) {
        try {
            BufferedReader reader = new BufferedReader(new FileReader("input.txt"));
            String line;
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }
            reader.close();
        } catch (IOException e) {
            System.out.println("File not found");
        }
    }
}
```

Bash File
```
javac FilePrinter.java
java FilePrinter
```

**TA**

It looks like your program is catching an `IOException`, which might be causing 
the "File not found" message. Can you try running `ls` in your terminal to ensure 
`input.txt` is in the correct directory? Also, try adding a print statement in 
the catch block to print the exception message.

Update your catch block like this:
```
} catch (IOException e) {
    System.out.println("File not found: " + e.getMessage());
}
```

Then, run your script again and share the output.

**Updated New Response**

New Code
```
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class FilePrinter {
    public static void main(String[] args) {
        try {
            BufferedReader reader = new BufferedReader(new FileReader("input.txt"));
            String line;
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }
            reader.close();
        } catch (IOException e) {
            System.out.println("File not found: " + e.getMessage());
        }
    }
}
```

Terminal Output
```
$ ./run_program.sh
File not found: input.txt (No such file or directory)
$ ls
FilePrinter.java  run_program.sh
```

**TA Follow Up Response**

The issue is that the file input.txt is not present in the directory where 
the script is being run. To fix this, ensure that input.txt is in the same 
directory as `run_program.sh` and `FilePrinter.java`.

How to Fix the Bug
Create a file named input.txt in the same directory as `FilePrinter.java` and 
`run_program.sh`. Then add the desired content to `input.txt`.

/project
  |-- FilePrinter.java
  |-- run_program.sh
  |-- input.txt

Now, when you run `./run_program.sh`, it should correctly print the contents of 
`input.txt`.

---

### Reflection

Talking to the TAs about internship application process during the last week was
incredibly valuable and interesting for me. Learning vim also was interesting as 
it allows me to be quicker and more productive when doing projects.