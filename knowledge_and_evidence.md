<style>

body {
    counter-reset: h2counter;
}

/* H1 - No numbering */
h1 {
    /* No counter reset or increment */
}

/* H2 - Level 1 numbering */
h2 {
    counter-reset: h3counter;
}

h2::before {
    counter-increment: h2counter;
    content: counter(h2counter) ". ";
}

/* H3 - Level 2 numbering */
h3 {
    counter-reset: h4counter;
}

h3::before {
    counter-increment: h3counter;
    content: counter(h2counter) "." counter(h3counter) " ";
}

/* H4 - Level 3 numbering (optional) */
h4 {
    counter-reset: h5counter;
}

h4::before {
    counter-increment: h4counter;
    content: counter(h2counter) "." counter(h3counter) "." counter(h4counter) " ";
}

</style>

# Evidence and Knowledge

This document includes instructions and knowledge questions that must be completed to receive a *Competent* grade on this portfolio task.

## Required evidence

### Answer all questions in this document

- Each answer should be complete, well-articulated, and within the specified word count limits (if added) for each question.
- Please make sure **all** external sources are properly cited.
- You must **use your own words**. Please include your full chat transcripts if you use generative AI in any way.
- Generative AI hallucinates, is not an authoritative source

### Make all the required modifications to the code

- Please follow the instructions in this document to make the changes needed to the code.

- When requested to upload evidence, upload all screenshots to `screenshots/` and embed them in this document. For example:

```markdown
![Example Running Code](screenshots/screenshot1.png)
```

- You must upload the code into your GitHub repository.
- While you can use a branch, your code should be in main when you submit.
- Upload a zip of this repository to Blackboard when you are ready to submit.
- You will be notified of your result via Blackboard
- However, if using GitHub classrooms, you may also receive additional feedback on GitHub directly

### Optional: Use of Raspberry Pi and SenseHat

Raspberry Pi or SenseHat is **optional** for this activity. You can use the included `sense_hat.py` file to simulate the SenseHat on your computer.

If you use a Pi, please **delete** the `sense_hat.py` file.

### Accessible version of the code

This project relies on visual patterns that appear on an LED matrix. If you have any accessibility requirements, you can use the `udl/accessible` branch to complete the project. This branch provides an accessible code version that uses text-based patterns instead of visual ones.

Please discuss this with your lecturer before using that branch.

## Specific Tasks & Questions

Address the following tasks and questions based on the code provided in this repository.

### Set up the project locally

1. Fork this repository (if not using GitHub Classrooms)
2. Clone your repository locally
3. Run the project locally by executing the `main.py` file
4. Evidence this by providing screenshots of the project directory structure and the output of the `main.py` file

![Local Execution (INSERT YOUR SCREENSHOT)](docs/abc_screenshots/running_smiley.jpg)

If you are running on a Raspberry Pi, you can use the following command to run the project and then screenshot the result:

```bash
ls
python3 main.py
```

### Fundamental code comprehension

 Answer each of the following questions **as they relate to that code** supplied by in this repository (ignore `sense_hat.py`):

1. Examine the code for the `smiley.py` file and provide  an example of a variable of each of the following types and their corresponding values (`_` should be replaced with the appropriate values):

   | Type                    | name  | value                                    |
   | ----------              |-------|------------------------------------------|
   | built-in primitive type | dimmed | True (in the dm_display method)          |
   | built-in composite type | self.pixels | A list of tuples representing RGB values |
   | user-defined type       | class | self.sense_hat        |

2. Fill in (`_`) the following table based on the code in `smiley.py`:

   | Object                   | Type   |
   | ------------             |--------|
   | self.pixels              | list   |
   | A member of self.pixels  | tuple  |
   | self                     | Smiley |

3. Examine the code for `smiley.py`, `sad.py`, and `happy.py`. Give an example of each of the following control structures using an example from **each** of these files. Include the first line and the line range:

   | Control Flow | File      | First line  | Line range |
   | ------------ |-----------|-------------|-----------|
   |  sequence    | smiley.py | Y = self.YELLOW | 15-25     |
   |  selection   | happy.py  | if wide_open | 31         |
   |  iteration   | happy.py  | for pixel in eyes:            | 30-31     |

4. Though everything in Python is an object, it is sometimes said to have four "primitive" types. Examining the three files `smiley.py`, `sad.py`, and `happy.py`, identify which of the following types are used in any of these files, and give an example of each (use an example from the code, if applicable, otherwise provide an example of your own):

   | Type                    | Used? | Example |
   | ----------------------- | --- | --------|
   | int                     | Yes | 255 (in RGB tuples)
   | float                   |No   | N/A
   | str                     |No   | N/A       |
   | bool                    |Yes  | True (parameter in dim_display)

5. Examining `smiley.py`, provide an example of a class variable and an instance variable (attribute). Explain **why** one is defined as a class variable and the other as an instance variable.

> Class variable: WHITE (in class Smiley)
> This is class variable because it represents a constant RGB colour value that is the same for every instance of Smiley (same for GREEN, RED, YELLOW, BLANK).
> Instance variable: self.pixels
> This is an instance variable because it represents the specific pixel pattern for an individual Smiley object. Each instance could potentially have a different pattern. 
6. Examine `happy.py`, and identify the constructor (initializer) for the `Happy` class:
   1. What is the purpose of a constructor (in general) and this one (in particular)?

   > The purpose of a constructor in general is to initialise an object's state by assigning initial values for attributes and preparing the object for use.
   > In particular, the __init__ constructor in Happy calls the (Smiley) constructor to initialise inherited attributes, then calls draw_mouth() and draw_eyes() methods to set up the specific appearance of a happy smiley face.

   2. What statement(s) does it execute (consider the `super` call), and what is the result?

   > The constructor in Happy executes super().__init_(), which calls the __init_ method of Smiley, initialising self.sense_hat and self.pixels. 
   > The result is that the base properties of the smiley are set up, then the Happy-specific attributes (eyes and mouth) are drawn.
-
### Code style

1. What code style is used in the code? Is it likely to be the same as the code style used in the SenseHat? Give to reasons as to why/why not:
   
> The Python code style follows fundamental PEP8 style, with consistent indentation, spacing and naming conventions. 
> The code style differs from what is used in SenseHat because sense_hat.py is more comprehensive and robust that is likely used more in a professional or production-level setting.

> References: 
> PEP8 - Style Guide for Python Code: https://peps.python.org/pep-0008/ 
> Real Python - Write More Pythonic Code: https://realpython.com/learning-paths/writing-pythonic-code/ 
> 
2. List three aspects of this convention you see applied in the code.

> Consistent naming of constants in uppercase (WHITE, YELLOW).
> Method names use lowercase with underscores (draw_mouth, draw_eyes).
> Docstrings are used for class and method descriptions.
> 
3. Give two examples of organizational documentation in the code.

> Docstrings for classes and methods, providing explanations for each function's purpose.
> Inline comments within methods, such as in draw_mouth and draw_eyes, to describe actions.

### Identifying and understanding classes

> Note: Ignore the `sense_hat.py` file when answering the questions below

1. List all the classes you identified in the project. Indicate which classes are base classes and which are subclasses. For subclasses, identify all direct base classes.
  
  Use the following table for your answers:

| Class Name | Super or Sub? | Direct parent(s) |
| Smiley | Super- | None |
| Happy    | Sub           | Smiley, Blinkable
|   Sad      |   Sub         |      Smiley     |

2. Explain the concept of abstraction, giving an example from the project (note "implementing an ABC" is **not** in itself an example of abstraction). (Max 150 words)

> Abstraction is the process of removing certain attributes to focus attention on details of greater importance. It models classes that represent concepts rather than specific details.
> Smiley is an abstract representation of a smiley face. It provides basic attributes and methods such as show() that are common to all smiley types.
> Happy and Sad classes extend Smiley to provide specific features like drawing happy or sad expressions. 
> 
> 
3. What is the name of the process of deriving from base classes? What is its purpose in this project? (Max 150 words)

>This process is known as inheritance. In this project, inheritance allows Happy and Sad classes to reuse the common functionality defined in Smiley,
>while adding or overriding methods for specific behaviours. This reduces code duplication and provides a clear structure for different smiley expressions.

> Reference: 
> Real Python - Inheritance and Composition: A Python OOP Guide: https://realpython.com/inheritance-composition-python/

### Compare and contrast classes

Compare and contrast the classes Happy and Sad.

1. What is the key difference between the two classes?
   > The key difference is that Happy has a blink method, while Sad does not.
   >
2. What are the key similarities?
   > Both classes inherit from Smiley, and they both override the draw_mouth and draw_eyes methods to create specific facial expressions.
   >
3. What difference stands out the most to you and why?
   > The absence of the blink method in Sad stands out because it limits Sad from performing the same animation as Happy.
   >
4. How does this difference affect the functionality of these classes
   > This difference affects the user experience because Happy is dynamic as it can blink, while Sad appears static.

### Where is the Sense(Hat) in the code?

1. Which class(es) utilize the functionality of the SenseHat?
   > Smiley is the main class that directly utilises SenseHat functionality.
   >
2. Which of these classes directly interact with the SenseHat functionalities?
   > Smiley directly interacts with the SenseHat API to set pixel colours on the LED display.
   >
3. Discuss the hiding of the SenseHAT in terms of encapsulation (100-200 Words)
   > The Smiley class demonstrates encapsulation by managing all interactions with the SenseHat within the class itself. 
   > By keeping the SenseHat interaction within Smiley, the rest of the project can use Smiley objects without needing to know how the SenseHat works internally. 
   > This encapsulation makes the program more modular, as changes to the SenseHat or its methods would only affect the Smiley class without affecting the rest of the project.
   > In the code, the SenseHat instance self.sense_hat is only accessible within the Smiley class. External code indirectly interacts with the SenseHat by calling 
   > Smiley methods such as draw_smiley() and clear_display().

  > Reference: 
  > Geek for Geeks - Encapsulation in Python: https://www.geeksforgeeks.org/encapsulation-in-python/

### Sad Smileys Can’t Blink (Or Can They?)

Unlike the `Happy` smiley, the current implementation of the `Sad` smiley does not possess the ability to blink. Let's first explore how blinking has been implemented in the Happy Smiley by examining the blink() method, which takes one argument that determines the duration of the blink.

**Understanding Blink Mechanism:**

1. Does the code's author believe that every `Smiley` should be able to blink? Explain.

> As the code only has Happy with a blink method, it suggests that the author doesn't consider blinking a universal trait of all smileys, 
> or that the blinking behaviour is specific to certain types of smileys.

2. For those smileys that blink, does the author expect them to blink in the same way? Explain.

> For smileys that do blink, the implementation allows customisation (e.g. the delay parameter in Happy), suggesting that each smiley could have its unique way of blinking.

3. Referring to the implementation of blink in the Happy and Sad Smiley classes, give a brief explanation of what polymorphism is.

> Polymorphism means "many forms", and it allows subclasses like Happy to define its own version of methods, such as blink.  
> Although Sad lacks blink, adding it would allow both classes share a common interface for blinking regardless of how it is implemented.
> In programming, polymorphism refers to methods, functions or operators with the same name but used for different types, or can be executed on 
> many objects or classes.
> 
> Reference: 
> Geeks for Geeks - Polymorphism in Python: https://www.geeksforgeeks.org/polymorphism-in-python/

4. How is inheritance used in the blink method, and why is it important for polymorphism?

> Inheritance lets Happy use methods from Smiley, while adding its unique blink behaviour. Polymorphism enables different smileys to be treated as instances of Smiley,
> with each responding to blink() based on its own implementation. This allows for flexibility in the project, as inheritance allows for polymorphic behaviour 
> in which a subclass can be treated as an instance of a parent class. 
> 
> Reference: 
> Shiksha Online - Difference Between Inheritance and Polymorphism: https://www.shiksha.com/online-courses/articles/difference-between-inheritance-and-polymorphism-blogId-153349
> 
1. **Implement Blink in Sad Class:**

   - Create a new method called `blink` within the Sad class. Ensure you use the same method signature as in the Happy class:

   ```python
   def blink(self, delay=0.25): 
        # Sets eyes to be closed
        self.draw_eyes(wide_open=False)
        self.show()
        time.sleep(delay)
   
        # Sets eyes to open
        self.draw_eyes(wide_open=True)
        self.show()

   ```

2. **Code Implementation:** Implement the code that allows the Sad smiley to blink. Use the implementation from the Happy Smiley as a reference. Ensure your new method functions similarly by controlling the blink duration through the `delay` argument.

3. **Testing the Implementation:**

- Test the new blink functionality on your Raspberry Pi or within the Python classes provided. You might need to adjust the `main.py` script to incorporate Sad Smiley's new blinking capability.

Include a screenshot of the sad smiley or the modified `main.py`:

![Sad Smiley Blinking](abc_screenshots/sad_blinking.jpg)

- Observe and document the Sad smiley as it blinks its eyes. Describe any adjustments or issues encountered during implementation.

  > Your answer here

  ### If It Walks Like a Duck…

  Previously, you implemented the blink functionality for the Sad smiley without utilizing the class `Blinkable`. Assuming you did not use `Blinkable` (even if you actually did), consider how the Sad smiley could blink similarly to the Happy smiley without this specific class.

  1. **Class Type Analysis:** What kind of class is `Blinkable`? Inspect its superclass for clues about its classification.

  > Blinkable is an abstract class by inheriting from ABC (Abstract Base Class) and using @abstractmethod on its blink method. 
  > This signifies that any class inheriting from Blinkable must implement the blink method to avoid being an abstract class itself.
  >

  2. **Class Implementation:** `Blinkable` is a class intended to be implemented by other classes. What generic term describes this kind of class, which is designed for implementation by others? **Clue**: Notice the lack of any concrete implementation and the naming convention.

  > The generic term for this kind of class is an interface or Abstract Base Class. The Blinkable class serves as a blueprint for other classes that need to implement the blinking behaviour. This is a common design pattern in which 
  > abstract classes define essential methods that must be implemented by any class that inherits from it. 
  > 
  > References: 
  > Real Python - Implementing an Interface in Python: https://realpython.com/python-interface/
  > Geeks for Geeks - Abstract Base Class in Python: https://www.geeksforgeeks.org/abstract-base-class-abc-in-python/

  3. **OO Principle Identification:** Regarding your answer to question (2), which Object-Oriented (OO) principle does this represent? Choose from the following and justify your answer in 1-2 sentences: Abstraction, Polymorphism, Inheritance, Encapsulation.

  > Abstraction, as it is the process of hiding the implementation details and exposing only the necessary functionality. The Blinkable class defines an abstract blink method, 
  > but it does not provide any implementation for how the blinking should be done. This forces subclasses to define its own implementation of the blink method, while keeping
  > the interface consistent. 
  > 
  > Reference: 
  > Geeks for Geeks - Abstraction in Python: https://www.geeksforgeeks.org/data-abstraction-in-python/

  4. **Implementation Flexibility:** Explain why you could grant the Sad Smiley a blinking feature similar to the Happy Smiley's implementation, even without directly using `Blinkable`.

  > This could be granted because as a dynamically typed language, Python allows for behaviour to be defined at runtime. Objects are defined by their behaviour rather than by their class or inheritance hierarchy. 
  > If the Sad smiley class includes a method that matches the functionality (such as a blink method), it can blink just like the Happy smiley, even though it does not inherit from Blinkable.
  > 
  > References:
  > Real Python - Python Type Checking (Guide): https://realpython.com/python-type-checking
  > Geeks for Geeks - Type Systems: Dynamic Typing, Static Typing & Duck Typing: https://www.geeksforgeeks.org/type-systemsdynamic-typing-static-typing-duck-typing/

  5. **Concept and Language Specificity:** In relation to your response to question (4), what is this capability known as, and why is it feasible in Python and many other dynamically typed languages but not in most statically typed programming languages like C#? **Clue** This concept is hinted at in the title of this section.

  > This capability is known as Duck Typing, which allows you to treat objects based on their methods and behaviours rather than their explicit type or 
  > inheritance. It is feasible in Python and other dynamically typed languages because they focus on an object's behaviour rather than its class or inheritance hierarchy, while statically typed
  > languages like C# require explicit interfaces or inheritance for the compiler to recognise shared behaviour. 
  > 
> References:
  > Real Python - Python Type Checking (Guide): https://realpython.com/python-type-checking
  > Geeks for Geeks - Type Systems: Dynamic Typing, Static Typing & Duck Typing: https://www.geeksforgeeks.org/type-systemsdynamic-typing-static-typing-duck-typing/

  ***

  ## Refactoring

  ### Does a Smiley Have to Be Yellow?

  While our current implementation predominantly features yellow smileys, emotional expressions like sickness or anger typically utilize colors like green, red, or orange. We'll explore the feasibility of integrating these colors into our smileys.

  1. **Defined Colors and Their Location:**

     1. Which colors are defined and in which class(s)?
        > The colours WHITE, GREEN, RED, YELLOW, and BLANK are defined as class variables in Smley.
     2. What type of variables hold these colors? Are the values expected to change during the program's execution? Explain your answer.
        > These are class variables. They are intended as constants, meaning their values are not expected to change during program execution. Defining colours as constants ensures consistency across all instances and avoids accidental modifications.
     3. Add the color blue to the appropriate class using the appropriate format and values.
        > class Smiley:
    WHITE = (255, 255, 255)
    GREEN = (0, 255, 0)
    RED = (255, 0, 0)
    YELLOW = (255, 255, 0)
    BLUE = (0, 0, 255)
    BLANK = (0, 0, 0)
  2. **Usage of Color Variables:**

     1. In which classes are the color variables used?
        > The colour variables are primarily used in Smiley to define the pixel colours.

  3. **Simple Method to Change Colors:**
  4. What is the easiest way you can think to change the smileys to green? Easiest, not necessarily the best!
     > The easiest way to change all smileys to green would be to redefine YELLOW in the Smiley class: YELLOW = GREEN

  Here's a revised version of the "Flexible Colors – Step 1" section for the smiley project, incorporating your specifications for formatting and content updates:

  ### Flexible Colors – Step 1

  Changing the color of the smileys once is straightforward, but it isn't very flexible. To facilitate various colors for smileys, it is advisable not to hardcode values in any class. This approach was identified earlier as a necessary change. Let's start by removing the built-in assumptions about color in our classes.

  1. **Add a method called `complexion` to the `Smiley` class:** Implement this instance method to return `self.YELLOW`. Using the term "complexion" instead of "color" provides a more abstract terminology that focuses on the meaning rather than implementation.

  2. **Refactor subclasses to use the `complexion` method:** Modify any subclass that directly accesses the color variable to instead utilize the new `complexion` method. This ensures that color handling is centralized and can be easily modified in the future.

  3. **Determine the applicable Object-Oriented principle:** Consider whether Abstraction, Polymorphism, Inheritance, or Encapsulation best applies to the modifications made in this step.

  4. **Verify the implementation:** Ensure that the modifications function as expected. The smileys should still display in yellow, confirming that the new method correctly replaces the direct color references.

  This step is crucial for setting up a more flexible system for color management in the smiley display logic, allowing for easy adjustments and extensions in the future.

  ### Flexible Colors – Step 2

  Having removed the hardcoded color values, we now enhance the base class to support dynamic color assignments more effectively.

  1. **Modify the `__init__()` method in the `Smiley` class:** Introduce a default argument named `complexion` and assign `YELLOW` as its default value. This allows the instantiation of smileys with customizable colors.

  2. **Introduce a new instance variable:** Create a variable called `my_complexion` and assign the `complexion` parameter to it. This step ensures that each smiley instance can maintain its own color state.

  3. **Rationale for `my_complexion`:** Using a distinct instance variable like `my_complexion` avoids potential conflicts with the method parameter names and clarifies that it is an attribute specific to the object.

  4. **Bulk rename:** We want to update our grid to use the value of complexion, but we have so many `Y`'s in the grid. Use your IDE's refactoring tool to rename all instances of the **symbol** `Y` to `X`. Where `X` is the value of the `complexion` variable. Include a screenshot evidencing you have found the correct refactor tool and the changes made.

  ![Bulk Rename](abc_screenshots/bulk_rename.jpg)

  5. **Update the `complexion` method:** Adjust this method to return `self.my_complexion`, ensuring that whatever color is assigned during instantiation is what the smiley displays.

  6. **Verification:** Run the updated code to confirm that Smileys still defaults to yellow unless specified otherwise.

  ### Flexible Colors – Step 3

  With the foundational changes in place, it's now possible to implement varied smiley colors for different emotional expressions.

  1. **Adjust the `Sad` class initialization:** In the `Sad` class's initializer method, change the superclass call to include the `complexion` argument with the value `self.BLUE`, as shown:

     ```python
     super().__init__(complexion=self.BLUE)
     ```

  2. **Test color functionality for the Sad smiley:** Execute the program to verify that the Sad smiley now appears blue.

  3. **Ensure the Happy smiley remains yellow:** Confirm that changes to the Sad smiley do not affect the default color of the Happy smiley, which should still display in yellow.

  4. **Design and Implement An Angry Smiley:** Create an Angry smiley class that inherits from the `Smiley` class. Set the color of the Angry smiley to red by passing `self.RED` as the `complexion` argument in the superclass call.

  ***
