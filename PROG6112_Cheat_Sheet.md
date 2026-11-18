# PROG6112 Code Template Cheat Sheet

Every complete file below was compiled (Java 21, source level 17) and run, and its JUnit tests passed on JUnit 5 and JUnit 4.13. Shorter excerpts were cut from those files and compiled on their own as well. Swing forms were opened on a virtual screen and their buttons and menus clicked. Textbook references are to Farrell, *Java Programming* 10th ed. (section, printed page).

## Index

Find the rubric line you're working on, then jump to its template. If a paper looks like 2025 or the mock, start from **Master Q1** and **Master Q2** at the bottom and only change the marked lines.

| Template | What it gives you | Rubric line(s) it answers | Question type | Textbook |
| --- | --- | --- | --- | --- |
| T0 | NetBeans project, package, class, test and import steps | Program compiles and executes (2) | All | 1.5, 1.7 (p.25) |
| T1 | 1D + 2D arrays, nested loops, total / average / max / min | Arrays declared and populated; Printing and calculating total, average, highest, lowest | Q1 console | 8.1-8.3, 8.8 (p.267-303), 6.6 (p.220) |
| T2 | Row and column totals and averages, Math.round, integer vs double division | Total per movie or agent; average per province | Q1 | 8.8 (p.300), App. C (p.595) |
| T3 | Count values over or under a constant | Sales over/under limit tests; pass/fail counts | Q2 | 2.1 (p.39), 4.8 (p.140) |
| T4 | Interface + implementing class, constructor, getters/setters, passing arrays | Interface created (5); class implements interface (5-10) | Q1 + Q2 | 9.12 (p.371), 4.2-4.6 (p.117-131), 8.6 (p.289) |
| T5 | JUnit tests: int, double + delta, String, boolean | Each named unit test (5 each) | Q1 + Q2 | Not in textbook; use JUnit docs |
| T6 | printf / String.format report with aligned columns | Printing of rows and columns (5) | Q1 | App. C.2 (p.597) |
| T7 | Swing form (hand-coded and GUI Builder), JMenuBar, shared methods | GUI form with all objects (10); menu system (5); report in text area (10); code efficiency (2) | Q2 | 14.2-14.7 (p.547-567) |
| T8 | JComboBox filled in a loop, selected item and index | Populating the combo box (4-5) | Q2 data capture | 14.9 (p.575) |
| T9 | JList + DefaultListModel | Print to list box; populate list from file | 2022-type GUI | Not in textbook |
| T10 | Write a text file: BufferedWriter, PrintWriter, append, textbook Path style | File saved correctly with report contents (5) | Q2 | 11.4-11.5 (p.452-459) |
| T11 | Read a text file back: BufferedReader, Scanner, split into arrays | Reading from the sequential file (10) | Q2 variation | 11.4 (p.454-456), 11.5 (p.457) |
| T12 | JTextField input, parse with try-catch, validation rules, JOptionPane | Validation performed correctly (5); validation test (5) | Q2 data capture | 7.4 (p.249), 10.2 (p.397), 2.7 (p.64), 5.6 (p.178) |
| T13 | Parallel arrays: search, add with max N, top performer | Top movie/agent; save to arrays; error when full | Q1 / 2022-type | 8.5 (p.284) |
| Master Q1 | Complete console solution with CHANGE THIS markers | All Q1 lines (30) | Q1 | - |
| Master Q2 | Complete GUI solution (both styles) with Load, Save, Read-back and Clear | All Q2 lines (60) | Q2 | - |

**Conventions used in every template** (change them if your assignments used something else):

- **Maven project** ("Java with Maven"), package `com.mycompany.<projectname>`, **JUnit 5**. For an **Ant project with JUnit 4**, only the two test imports change. T5 shows both.
- One NetBeans project per question (for example `StudentMarksReport` for Q1 and `StudentMarksApp` for Q2), both saved in your exam folder.
- Interface method names are **copied from the paper in PascalCase**. Everything else you write uses camelCase (`loadMarks()`, `txtResults`).
- Control names use prefixes: `btn` button, `txt` text field or area, `lbl` label, `cmb` combo box, `lst` list, `mnu` menu item.
- Limits and rates are `public static final` constants written in CAPITALS (`SALES_LIMIT`, `PASS_MARK`, `VAT_RATE`).
- Each source file starts with a comment that ends with the AI disclosure line (see the Tips doc).

## T0 - NetBeans setup steps

**Use for:** the start of every question. This earns the "Program(s) compile and execute" marks and keeps the marker's job easy.

**Create the project (Maven, matches these templates)**

1. File > New Project > **Java with Maven** > **Java Application** > Next.
2. Project Name: `StudentMarksReport` (CHANGE THIS). Project Location: your exam folder or the designated space. Group Id stays `com.mycompany`. The package fills in as `com.mycompany.studentmarksreport`. Click Finish.
3. NetBeans creates `StudentMarksReport.java` with an empty `main`. That file is your Q1 report class.

**Ant instead:** File > New Project > **Java with Ant** > Java Application, then tick *Create Main Class*. Tests then use JUnit 4 (see T5).

**Add files** (in the Projects window, right-click the package under *Source Packages*):

- New > **Java Interface...** > name it exactly as the paper says (`IStudentMarks`).
- New > **Java Class...** > the class name from the paper (`StudentMarks`).
- New > **JFrame Form...** for a GUI Builder form. If it's not in the menu: New > Other > Swing GUI Forms > JFrame Form.
- After typing `implements IStudentMarks` the line turns red. Click the lightbulb (or press **Alt+Enter**) and choose **Implement all abstract methods**. NetBeans writes every method header with `@Override` for you.

**Create the tests**

1. Right-click the class (for example `StudentMarks.java`) > **Tools > Create/Update Tests** (Ctrl+Shift+U).
2. Framework: JUnit. Keep *Test Packages* and the same package. Untick the extra options (setUp, tearDown, default bodies) so the file stays short. Click OK.
3. Delete any generated `testXxx()` methods that end in `fail("The test case is a prototype.")`. Then type the paper's test names exactly (T5).
4. Run them: right-click the test file > **Test File** (Ctrl+F6), or right-click the project > **Test** (Alt+F6). Green bar = pass.

**Keyboard shortcuts you'll use**

| Shortcut | Does |
| --- | --- |
| Ctrl+Shift+I | Fix imports (adds the `import` lines you need) |
| Alt+Shift+F | Format the code (fixes indentation, which helps the practice marks) |
| F6 / Shift+F6 | Run project / run the open file |
| Ctrl+F6 | Test the open file |
| Alt+Enter | Lightbulb fixes (implement methods, add import, create field) |
| Ctrl+Space | Auto-complete |
| Ctrl+R (on a name) | Rename everywhere |

**Choose which class runs (Maven):** right-click project > Properties > Run > Main Class > Browse. Pick the form for Q2.

**If `org.junit.jupiter` cannot be found (Maven):** Create/Update Tests normally adds JUnit for you. If it doesn't, paste this inside `<dependencies>` in `pom.xml`, then right-click the project > Build with Dependencies:

```xml
<dependency>
    <groupId>org.junit.jupiter</groupId>
    <artifactId>junit-jupiter-api</artifactId>
    <version>5.10.1</version>
    <scope>test</scope>
</dependency>
```

Maven downloads this from the internet. Do the T0 steps once in the exam lab during setup time, so you know the download works there.

## T1 - 1D and 2D arrays with nested loops

**Use for:** every Q1. Rubric: "Declaration and population of single and two-dimensional arrays" plus "Printing and calculating the total, average, highest and lowest". Textbook 8.1-8.2 (p.267-271), 8.8 (p.300-303), 6.6 nested loops (p.220).

```java
// 1D arrays: one name per row and one heading per column - CHANGE THIS
String[] students = {"Thabo", "Aisha", "Liam"};
String[] assessments = {"TEST 1", "TEST 2", "ASSIGN", "EXAM"};

// 2D array: copy the paper's table row by row - CHANGE THIS
int[][] marks = {
    {65, 72, 58, 80},     // row 0 = Thabo
    {45, 38, 52, 49},     // row 1 = Aisha
    {90, 85, 78, 88}      // row 2 = Liam
};

// TOTAL: visit every cell with a nested loop
int total = 0;
for (int row = 0; row < marks.length; row++) {            // marks.length = number of ROWS
    for (int col = 0; col < marks[row].length; col++) {   // marks[row].length = COLUMNS in that row
        total += marks[row][col];
    }
}

// AVERAGE: total / number of values, cast to double first
int count = 0;
for (int row = 0; row < marks.length; row++) {
    count += marks[row].length;
}
double average = (double) total / count;

// MAX (change > to < and the name to get MIN)
int highest = marks[0][0];                // start with a real value, never 0
for (int row = 0; row < marks.length; row++) {
    for (int col = 0; col < marks[row].length; col++) {
        if (marks[row][col] > highest) {
            highest = marks[row][col];
        }
    }
}
```

**How it works, line by line**

- `String[] students = {...}` declares a 1D array and fills it in one step. `students[0]` is "Thabo".
- `int[][] marks = {{...}, {...}}` makes a table. Each inner `{...}` is one row, and `marks[1][2]` is row 1, column 2 (52).
- `marks.length` is the number of rows (3). `marks[row].length` is the number of columns in that row (4). Using `.length` instead of typing 3 or 4 means the code still works if the data changes.
- The outer `for` picks a row and the inner `for` walks along that row, so every cell is visited once.
- `(double) total / count` turns total into a double before dividing. Without the cast, `800 / 12` would give `66`, not `66.67`.
- Max and min start from `marks[0][0]`. Starting from 0 would make the minimum wrong, because no mark is below 0.

**NetBeans:** type these inside the class from T4 as separate methods (one per calculation), not all inside `main`. Separate methods earn the "class with separate methods" mark and keep `main` short.

## T2 - Row and column totals, averages and rounding

**Use for:** "total sales for each movie" (2024), "total per agent" (2023), "average per province" (2022), "average per student" (likely). Textbook 8.8 (p.300), Appendix C (p.595).

```java
/** Total of ONE row - pass the row number. */
public int rowTotal(int[][] marks, int row) {
    int total = 0;
    for (int col = 0; col < marks[row].length; col++) {
        total += marks[row][col];
    }
    return total;
}

/** Average of ONE row. */
public double rowAverage(int[][] marks, int row) {
    return (double) rowTotal(marks, row) / marks[row].length;
}

/** Total of ONE column - the row changes, the column stays fixed. */
public int columnTotal(int[][] marks, int col) {
    int total = 0;
    for (int row = 0; row < marks.length; row++) {
        total += marks[row][col];
    }
    return total;
}

/** Average of ONE column. */
public double columnAverage(int[][] marks, int col) {
    return (double) columnTotal(marks, col) / marks.length;
}
```

When the interface takes a **1D** row (2023/2024 style, `int TotalMovieSales(int[] movieTicketSales)`), pass one row of the 2D array:

```java
int[] totals = new int[movies.length];                 // parallel to movies[]
for (int row = 0; row < ticketSales.length; row++) {
    totals[row] = movieTickets.TotalMovieSales(ticketSales[row]);   // ticketSales[row] is an int[]
}
```

**Rounding cheat table** (all tested):

| You need | Code | 2200 / 6 example |
| --- | --- | --- |
| Nearest whole number | `Math.round(average)` | 367 |
| Two decimals as a number | `Math.round(value * 100) / 100.0` | 366.67 |
| Two decimals in text | `String.format("%.2f", average)` | "366.67" |
| Drop the decimals (2022 sample) | `int avg = total / count;` (int / int) | 366 |
| Thousands separators | `String.format("%,d", 4300000)` | "4,300,000" |

Match the sample. 2025 shows 367 (rounded). 2022 shows R 1,166,666 for 3,500,000 / 3 (truncated, so int division). Return the **unrounded double** from the class method and round only when printing, so the test can use a delta.

## T3 - Counting values over or under a constant

**Use for:** `GetSalesOverLimit`, `GetSalesUnderLimit`, pass and fail counts. Textbook 2.1 constants (p.39), 4.8 static/constant fields (p.140).

```java
public static final int SALES_LIMIT = 500;     // CHANGE THIS: name + value from the paper

@Override
public int GetSalesOverLimit() {
    int count = 0;
    for (int row = 0; row < productSales.length; row++) {
        for (int col = 0; col < productSales[row].length; col++) {
            if (productSales[row][col] > SALES_LIMIT) {    // "over" = greater than
                count++;
            }
        }
    }
    return count;
}

/** Every value is either over or not, so reuse the method above (no repeated loop). */
@Override
public int GetSalesUnderLimit() {
    return getNumberOfSales() - GetSalesOverLimit();
}

/** Helper: how many values are in the array. */
private int getNumberOfSales() {
    int count = 0;
    for (int row = 0; row < productSales.length; row++) {
        count += productSales[row].length;
    }
    return count;
}
```

- `public static final` = one shared value that can't change. CAPITALS show it's a constant. The rubric and the mock both say "stored as a constant".
- **Read the comparison word carefully:** "over / greater than" uses `>`; "at least / pass with 50" uses `>=`; "under" usually means everything that is not over. Write the rule you chose in a comment.
- Subtracting from the total count avoids a second identical loop. That's the "code efficiency" mark.
- "Years / students processed" = `productSales.length` (rows). Never type `return 2;` — the rubric line says *calculated from the array*.

## T4 - Interface and the class that implements it

**Use for:** "Interface created" (5) and "Class created that implements the interface with the required methods" (5-10). Textbook 9.12 (p.371), 9.3 @Override (p.337), 4.2-4.7 classes, data hiding, constructors, `this` (p.117-137), 8.6 passing arrays (p.289).

**Style A: methods receive the array** (Q1 in 2025 and the mock)

```java
public interface IStudentMarks {                 // CHANGE THIS: exact name from the paper
    int TotalMarks(int[][] marks);               // copy every line exactly - PascalCase included
    double AverageMark(int[][] marks);
    int HighestMark(int[][] marks);
    int LowestMark(int[][] marks);
}

public class StudentMarks implements IStudentMarks {
    @Override
    public int TotalMarks(int[][] marks) {
        // T1 total loop here
    }
    // ...one @Override method per interface line
}
```

**Style B: no-argument Get methods; the class stores the array** (Q2 in 2025 and the mock)

```java
public class StudentMarks implements IStudentMarks {

    public static final int PASS_MARK = 50;       // constant (T3)

    private final int[][] studentMarks;           // private = encapsulation

    public StudentMarks(int[][] studentMarks) {   // constructor receives the array
        this.studentMarks = studentMarks;         // this.field = parameter
    }

    @Override
    public int[][] GetStudentMarks() {            // "getter" for the array
        return studentMarks;
    }

    @Override
    public int GetStudentsProcessed() {
        return studentMarks.length;               // rows = students/years processed
    }
    // ...GetTotalMarks, GetPassCount, GetFailCount, GetAverageMark (T1 + T3)
}
```

**Style C: data class + validate** (Q2 in 2023 and 2024): a plain class with private fields, a constructor, and a getter/setter per field.

```java
public class MovieTicketData {
    private String movieName;
    private int numberOfTickets;
    private double ticketPrice;

    public MovieTicketData(String movieName, int numberOfTickets, double ticketPrice) {
        this.movieName = movieName;
        this.numberOfTickets = numberOfTickets;
        this.ticketPrice = ticketPrice;
    }

    public String getMovieName() { return movieName; }
    public void setMovieName(String movieName) { this.movieName = movieName; }
    // ...same pattern for the other fields
}
```

- An interface only lists **what** methods exist. The class supplies **how** they work. If one method is missing, the class won't compile. That's why "Implement all abstract methods" (Alt+Enter) is so useful.
- `@Override` tells the compiler and the marker that this method comes from the interface.
- `private` fields + public getters = data hiding (textbook 4.4, p.126). It shows up in the good-practice mark.
- If the paper has two different interfaces with the same name (Q1 and Q2), keep them in **separate projects**.

**NetBeans:** right-click package > New > Java Interface; paste the paper's code. New > Java Class; add `implements IName`; press Alt+Enter > *Implement all abstract methods*; replace each `throw new UnsupportedOperationException(...)` with your code.

## T5 - JUnit tests

**Use for:** every named unit test, worth 5 marks each and 20-30 per paper. JUnit isn't in the textbook, so learn this one by heart.

```java
package com.mycompany.studentmarksapp;                 // same package as the class

import static org.junit.jupiter.api.Assertions.assertEquals;   // JUnit 5 (Maven)
import org.junit.jupiter.api.Test;
// JUnit 4 (Ant) instead:
// import static org.junit.Assert.assertEquals;
// import org.junit.Test;

public class StudentMarksTest {

    // same data as the paper, so the expected answers are known
    private final int[][] marksData = {
        {65, 72, 58, 80},
        {45, 38, 52, 49},
        {90, 85, 78, 88}
    };

    @Test
    public void GetPassCount_ReturnsNumberOfPasses() {        // EXACT name from the paper
        StudentMarks marks = new StudentMarks(marksData);    // 1. arrange
        assertEquals(9, marks.GetPassCount());               // 2. act + assert (expected, actual)
    }

    @Test
    public void GetAverageMark_ReturnsAverage() {
        StudentMarks marks = new StudentMarks(marksData);
        assertEquals(66.67, marks.GetAverageMark(), 0.01);   // double: (expected, actual, delta)
    }
}
```

**Other assertions** (all exist in JUnit 4 and 5 with the same arguments):

| Result type | Assertion | Example from the papers |
| --- | --- | --- |
| int | `assertEquals(2, sales.GetSalesOverLimit());` | 2025 over limit |
| double | `assertEquals(342.0, mt.CalculateTotalTicketPrice(3, 100), 0.01);` | 2024 VAT |
| String | `assertEquals("Oppenheimer", mt.TopMovie(movies, totals));` | 2024 top movie |
| index | `assertEquals(0, agent.TopEstateAgent(totals));` | 2023 top agent |
| boolean false | `assertFalse(mt.ValidateData(badData));` | 2023/2024 validation |
| boolean true | `assertTrue(mt.ValidateData(goodData));` | valid input |
| "not this value" | `assertNotEquals(800.0, ea.CalculateCommission("800000", "10"), 0.01);` | 2023 "calculated unsuccessfully" |

- Order is **expected first, actual second**. Swapping them still passes, but the failure message reads backwards.
- A `double` without a delta is a common mistake. JUnit 5 compares exactly, and `2200.0 / 6` is never exactly 366.67.
- Work out the expected value by hand from the paper's data and write the sum in a comment. Markers like seeing `// 300+150+700+250+200+600 = 2200`.
- Tests that need the class's constant can use it: `assertEquals(400, SurfSales.SALES_TARGET);` is a free extra.
- The paper writes names like `TopAgent_ReturnsTopPosition()`. The `()` is part of a method call, not the name.

## T6 - Formatted console report with printf

**Use for:** "Printing of rows and columns in the report" (5) and making the output match the sample. Textbook Appendix C.2 printf (p.597).

```java
String line = "--------------------------------------------------";
System.out.println("STUDENT MARKS REPORT - 2026");      // CHANGE THIS: title from sample
System.out.println(line);

// heading row: an empty 10-wide cell, then each heading 8 wide
System.out.printf("%-10s", "");
for (int col = 0; col < assessments.length; col++) {
    System.out.printf("%8s", assessments[col]);
}
System.out.println();

// data rows: name left-aligned, numbers right-aligned under the headings
for (int row = 0; row < marks.length; row++) {
    System.out.printf("%-10s", students[row]);
    for (int col = 0; col < marks[row].length; col++) {
        System.out.printf("%8d", marks[row][col]);
    }
    System.out.println();
}
System.out.println(line);
System.out.printf("%-16s%d%n", "Total marks:", calc.TotalMarks(marks));
System.out.printf("%-16s%d%n", "Average mark:", Math.round(calc.AverageMark(marks)));
```

| Code | Meaning | Output |
| --- | --- | --- |
| `%-10s` | text, left-aligned in 10 spaces | ` Thabo      ` |
| `%8s` / `%8d` | text / whole number, right-aligned in 8 | `     TEST 1 ` / `       65 ` |
| `%8.2f` | decimal with 2 places, 8 wide | `    66.67 ` |
| `%,d` / `%,.0f` | thousands separators | `4,300,000` |
| `%n` | new line (use instead of `\n` in printf) |  |
| `String.format(...)` | the same codes, but returns a String (for text areas and files) |  |

- The heading and the data use the **same widths**, so the columns line up.
- Copy the sample's words exactly ("Total sales:", "Average sales:"). Markers compare against the sample screenshot.
- Print the rows and columns even if the sample only shows the totals. The rubric line asks for them (2025).

## T7 - Swing form with a menu bar and shared methods

**Use for:** Q2 "GUI form created with all objects" (10), "Creating the menu system" (5), "Report produced as per the sample and displayed in the text area" (10), and the General Requirements "code efficiency" mark. Textbook 14.2 JFrame (p.547), 14.3 JLabel (p.552), 14.4 layout managers (p.555), 14.5 extending JFrame (p.557), 14.6 JTextField/JButton (p.559), 14.7 events and `getSource()` (p.563-567). JMenuBar and JTextArea aren't taught in the textbook; they follow the same pattern as JButton.

**The one rule that earns the efficiency mark:** put the logic in **one private method per action** (`loadMarks()`, `saveMarks()`, `clearForm()`). Each button handler and each menu handler then contains only one line that calls it. Never copy the load code into the menu handler.

### Option 1 - GUI Builder (JFrame Form) - fastest in the exam

1. Right-click package > New > **JFrame Form...** > name `StudentMarksForm` > Finish. The **Design** view opens.
2. From the **Palette** (Window > IDE Tools > Palette, or Ctrl+Shift+8), drag onto the form:
   - 2 x **Button** (Swing Controls)
   - 1 x **Text Area** (it arrives inside a scroll pane, which is fine)
   - 1 x **Label**
   - 1 x **Menu Bar** (Swing Menus). It arrives with **File** and **Edit** menus.
3. For each control: right-click > **Edit Text** to set what the user sees ("Load Marks"). Then right-click > **Change Variable Name...** to set the code name (`btnLoad`, `btnSave`, `txtResults`, `lblProcessed`). Good names count towards the practice marks.
4. Text area: select it, then in **Properties** untick **editable** (this writes `txtResults.setEditable(false)`). A JLabel can't be typed in, so it's already read-only.
5. Menus: click the **Edit** menu > Edit Text > `Tools`. Right-click **File** > *Add From Palette* > **Menu Item** > Edit Text `Exit` > rename `mnuExit`. Right-click **Tools** > add three Menu Items: `Load Marks`, `Save Marks`, `Clear` (rename `mnuLoad`, `mnuSave`, `mnuClear`).
6. Events: **double-click** each button. For a menu item, right-click it in the **Navigator** > Events > Action > actionPerformed. NetBeans switches to **Source** and creates an empty method.
7. Type **one line** into each generated handler, then type the shared methods below `initComponents()`.

```java
// ---- inside the generated handlers: ONE line each ----
private void btnLoadActionPerformed(java.awt.event.ActionEvent evt) {
    loadMarks();
}
private void mnuLoadActionPerformed(java.awt.event.ActionEvent evt) {
    loadMarks();                        // same method as the button = no duplicate code
}
private void btnSaveActionPerformed(java.awt.event.ActionEvent evt) {
    saveMarks();
}
private void mnuSaveActionPerformed(java.awt.event.ActionEvent evt) {
    saveMarks();
}
private void mnuClearActionPerformed(java.awt.event.ActionEvent evt) {
    clearForm();
}
private void mnuExitActionPerformed(java.awt.event.ActionEvent evt) {
    System.exit(0);                     // closes the application
}

// ---- your shared methods (typed by you, under initComponents) ----
private void loadMarks() {
    StudentMarks marks = new StudentMarks(MARKS_DATA);          // T4 class
    txtResults.setText("Total Marks: " + marks.GetTotalMarks() + "\n"
            + "Average Mark: " + Math.round(marks.GetAverageMark()) + "\n"
            + "Marks passed: " + marks.GetPassCount() + "\n"
            + "Marks failed: " + marks.GetFailCount());
    lblProcessed.setText("Students Processed: " + marks.GetStudentsProcessed());
}

private void clearForm() {
    txtResults.setText("");
    lblProcessed.setText("Students Processed: ");
}
// saveMarks() = T10; the data constant goes at the top of the class:
// private static final int[][] MARKS_DATA = { {65, 72, 58, 80}, {45, 38, 52, 49}, {90, 85, 78, 88} };
```

- The grey code (`initComponents()` and the variable list at the bottom) belongs to NetBeans. **Never edit it by hand**; change things in the Design view instead.
- If a handler is named `jButton1ActionPerformed`, you created the event before renaming. That's fine, it still works. To tidy it, rename the variable first next time.
- `setText` replaces all the text in a text area. `append` adds to the end of it.
- Run the form: right-click `StudentMarksForm.java` > Run File (Shift+F6). For F6, set it as the main class (T0).

### Option 2 - Hand-coded (textbook Chapter 14 style)

The full tested version is in **Master Q2**. This is the skeleton showing how buttons and menu items reach the same method through **one** `actionPerformed`:

```java
public class StudentMarksForm extends JFrame implements ActionListener {

    private final JButton btnLoad = new JButton("Load Marks");
    private final JTextArea txtResults = new JTextArea(8, 24);
    private final JLabel lblProcessed = new JLabel("Students Processed: ");
    private final JMenuItem mnuLoad = new JMenuItem("Load Marks");
    private final JMenuItem mnuExit = new JMenuItem("Exit");

    public StudentMarksForm() {
        super("Student Marks Application");             // window title
        setSize(340, 340);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new BorderLayout(5, 5));             // NORTH / CENTER / SOUTH areas

        JMenuBar menuBar = new JMenuBar();             // menu bar > menus > menu items
        JMenu mnuFile = new JMenu("File");
        JMenu mnuTools = new JMenu("Tools");
        mnuFile.add(mnuExit);
        mnuTools.add(mnuLoad);
        menuBar.add(mnuFile);
        menuBar.add(mnuTools);
        setJMenuBar(menuBar);

        add(btnLoad, BorderLayout.NORTH);
        txtResults.setEditable(false);                 // read-only output
        add(new JScrollPane(txtResults), BorderLayout.CENTER);
        add(lblProcessed, BorderLayout.SOUTH);

        btnLoad.addActionListener(this);               // the form listens to each control
        mnuLoad.addActionListener(this);
        mnuExit.addActionListener(this);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        Object source = e.getSource();                 // which control was clicked?
        if (source == btnLoad || source == mnuLoad) {
            loadMarks();                               // shared method
        } else if (source == mnuExit) {
            System.exit(0);
        }
    }
    // loadMarks(), saveMarks(), clearForm() exactly as in Option 1
}
```

Imports for the hand-coded form (Ctrl+Shift+I adds them): `java.awt.BorderLayout`, `java.awt.GridLayout`, `java.awt.event.ActionEvent`, `java.awt.event.ActionListener`, and `javax.swing.*` classes (`JButton`, `JFrame`, `JLabel`, `JMenu`, `JMenuBar`, `JMenuItem`, `JOptionPane`, `JPanel`, `JScrollPane`, `JTextArea`).

- `extends JFrame` makes the class a window. `implements ActionListener` lets it receive clicks (14.7).
- `BorderLayout` gives five areas. A `JPanel` with `new GridLayout(rows, cols, gapX, gapY)` stacks several controls neatly in one area.
- `e.getSource()` returns the control that was clicked. Comparing it with `==` works because it is the same object (p.566).
- `JScrollPane` adds scroll bars when the text grows.

## T8 - Combo box (JComboBox) filled in a loop

**Use for:** "Populating the combo box with the correct values" (4-5 marks in 2022, 2023 and 2024), or picking a student or row. Textbook 14.9 (p.575-577).

```java
private static final String[] LOCATIONS = {"Cape Town", "Durban", "Pretoria"};   // CHANGE THIS
private final JComboBox<String> cmbLocation = new JComboBox<>();

// in the constructor (GUI Builder: after initComponents();)
for (int i = 0; i < LOCATIONS.length; i++) {
    cmbLocation.addItem(LOCATIONS[i]);
}

// reading the choice
String location = (String) cmbLocation.getSelectedItem();   // the text, e.g. "Durban"
int index = cmbLocation.getSelectedIndex();                 // the position, e.g. 1 (-1 = nothing)

// resetting on Clear
cmbLocation.setSelectedIndex(0);

// numbers in a loop: "1 Year", "2 Years" ... "5 Years" (2022)
for (int year = 1; year <= 5; year++) {
    cmbYears.addItem(year == 1 ? "1 Year" : year + " Years");
}
```

- `JComboBox<String>` says the box holds Strings, so `addItem` checks the type (textbook p.576).
- `getSelectedItem()` returns an `Object`, so cast it: `(String)`.
- `getSelectedIndex()` is handy when the combo box matches the rows of your 2D array: `marks[index]` is that student's row.
- **GUI Builder:** you *can* type items in Properties > model, but filling it from an array in a loop shows more skill and is what "populated" means. Remove the default "Item 1, Item 2..." first: Properties > model > clear the list. Then set the type: Properties > **Code** tab > Type Parameters `<String>`.
- Compare two combo choices with `.equals`, never `==`: `if (start.equals(end))` (2022 same-destination check, textbook 7.3 p.241).

## T9 - List box (JList + DefaultListModel)

**Use for:** 2022-style "print the details to a list box" or "populate the list box from the file". Not in the textbook. The model holds the items and the JList displays them.

```java
private final DefaultListModel<String> listModel = new DefaultListModel<>();
private final JList<String> lstMarks = new JList<>(listModel);      // hand-coded
// GUI Builder: drag a List, rename it lstMarks, then in the constructor after initComponents():
//     lstMarks.setModel(listModel);

listModel.addElement("Thabo: 65");          // add a line
listModel.clear();                          // empty the list (do this before re-printing)
int selected = lstMarks.getSelectedIndex(); // -1 when nothing is selected
if (selected != -1) {
    listModel.remove(selected);             // remove the selected line
}
int howMany = listModel.size();             // number of lines
```

- Call `clear()` before printing again, or the same items appear twice. That's a classic "minor error" deduction.
- `addElement` in a loop over parallel arrays (T13) prints each record. Add a `"******"` line between records to match the 2022 sample.
- Import: `javax.swing.DefaultListModel` and `javax.swing.JList`.

## T12 - Text fields, input validation and JOptionPane

**Use for:** "Validation performed correctly" (5), a validation unit test (5), the "maximum reached" error (2022), "Destinations cannot be the same" (2022), and a 0-100 mark range if marks are typed in. Textbook 7.3 empty strings (p.245), 7.4 converting String to numbers (p.249), 10.2 try-catch (p.397), 5.6 range checks (p.178), 2.7 JOptionPane (p.64), 6.2 validating data (p.208).

```java
/** true when the text is null, empty or only spaces */
public static boolean isEmpty(String text) {
    return text == null || text.trim().isEmpty();
}

/** true when the text is a number greater than zero (decimals allowed) */
public static boolean isPositiveNumber(String text) {
    if (isEmpty(text)) {
        return false;
    }
    try {
        return Double.parseDouble(text.trim()) > 0;
    } catch (NumberFormatException ex) {      // letters typed instead of a number
        return false;
    }
}

/** true when the text is a whole number from 0 to 100 */
public static boolean isValidMark(String text) {
    if (!isWholeNumber(text)) {               // isWholeNumber = same as above with Integer.parseInt
        return false;
    }
    int mark = Integer.parseInt(text.trim());
    return mark >= MIN_MARK && mark <= MAX_MARK;
}
```

**In the form** (read, convert, validate, then process):

```java
int numberOfTickets;
double ticketPrice;
try {
    numberOfTickets = Integer.parseInt(txtNumberOfTickets.getText().trim());
    ticketPrice = Double.parseDouble(txtTicketPrice.getText().trim());
} catch (NumberFormatException ex) {
    JOptionPane.showMessageDialog(this, "Please enter numbers for the tickets and the price.");
    return;                                   // stop - do not calculate with bad data
}
MovieTicketData data = new MovieTicketData((String) cmbMovie.getSelectedItem(),
        numberOfTickets, ticketPrice);
if (!movieTickets.ValidateData(data)) {        // the interface's ValidateData method
    JOptionPane.showMessageDialog(this, "Invalid data: values must be greater than 0.");
    return;
}
// ...calculate, display, save
```

**ValidateData in the class** (2024 rules: name not empty, price > 0, tickets > 0):

```java
@Override
public boolean ValidateData(MovieTicketData movieTicketData) {
    if (movieTicketData.getMovieName() == null
            || movieTicketData.getMovieName().trim().isEmpty()) {
        return false;
    }
    if (movieTicketData.getTicketPrice() <= 0) {
        return false;
    }
    if (movieTicketData.getNumberOfTickets() <= 0) {
        return false;
    }
    return true;
}
```

**JOptionPane quick reference** (`import javax.swing.JOptionPane;`):

| Need | Code |
| --- | --- |
| Plain message (2022 "Maximum inspection count reached!") | `JOptionPane.showMessageDialog(this, "Maximum inspection count reached!");` |
| Error icon | `JOptionPane.showMessageDialog(this, "Enter a whole number from 0 to 100.", "Invalid mark", JOptionPane.ERROR_MESSAGE);` |
| Ask for text | `String name = JOptionPane.showInputDialog(this, "Enter a name:");` (returns null if Cancel is clicked) |
| Yes/No | `int answer = JOptionPane.showConfirmDialog(this, "Exit?"); if (answer == JOptionPane.YES_OPTION) { ... }` |

Use `this` inside a form so the dialog appears over the window. Use `null` in a console program.

- `return;` after an error message stops the method, so bad data never reaches the calculation.
- `.trim()` removes spaces the user typed by accident.
- A text field set to read-only: `txtTotal.setEditable(false);` (GUI Builder: untick *editable*). Use this if the paper says "read-only" and you chose a text field instead of a label.

## T10 - Writing a text file

**Use for:** "The file was saved correctly with the report contents" (5). The 2022 version ("Saving to the sequential file") was worth 10. Textbook 11.4 writing to a file (p.454), 11.5 sequential files and BufferedWriter (p.457-458). FileWriter and PrintWriter aren't in the textbook but are the shortest way to write a file.

**Version A - BufferedWriter + FileWriter** (used in every memo):

```java
private static final String FILE_NAME = "data.txt";          // CHANGE THIS: exact name from the paper
private static final String STARS = "******************************";

private void saveMarks() {
    if (txtResults.getText().isEmpty()) {                   // nothing loaded yet
        JOptionPane.showMessageDialog(this, "Please load the data first.");
        return;
    }
    try {
        BufferedWriter writer = new BufferedWriter(new FileWriter(FILE_NAME));
        writer.write("DATA LOG");                           // CHANGE THIS: heading from the sample
        writer.newLine();
        writer.write(STARS);
        writer.newLine();
        writer.write(txtResults.getText());                 // everything in the text area
        writer.newLine();
        writer.write(STARS);
        writer.newLine();
        writer.close();                                     // without close() the file can stay EMPTY
        JOptionPane.showMessageDialog(this, "Data saved to " + FILE_NAME);
    } catch (IOException ex) {
        JOptionPane.showMessageDialog(this, "Error saving file: " + ex.getMessage());
    }
}
```

Imports: `java.io.BufferedWriter`, `java.io.FileWriter`, `java.io.IOException`.

**Version B - PrintWriter** (println like `System.out`):

```java
try {
    PrintWriter writer = new PrintWriter(new FileWriter(fileName));
    for (int i = 0; i < lines.length; i++) {
        writer.println(lines[i]);
    }
    writer.close();
} catch (IOException ex) {
    System.out.println("Error writing file: " + ex.getMessage());
}
```

**Version C - append instead of overwrite** (2022 travel log keeps every trip): `new FileWriter(fileName, true)`. The `true` means "add to the end".

**Version D - textbook style** (Farrell 11.4, Path + Files):

```java
Path file = Paths.get(fileName);
try {
    BufferedWriter writer = new BufferedWriter(
            new OutputStreamWriter(Files.newOutputStream(file)));
    writer.write(text, 0, text.length());
    writer.newLine();
    writer.close();
} catch (IOException ex) {
    System.out.println("Message: " + ex);
}
```

- A plain name like `"data.txt"` saves the file in the **project folder** (next to `pom.xml` or `build.xml`), not in `src`. Open it in the Files tab (Ctrl+2) to check it before you submit.
- `newLine()` puts each part on its own line, which matches the Notepad sample.
- The try-catch is required: the compiler won't accept file code that ignores `IOException` (textbook 10.2, 10.6).
- Match the sample exactly: the heading text, the number of asterisks and the order of the lines.

## T11 - Reading a text file back

**Use for:** the lecturer's hint ("saves the marks to a text file **and reads them back**") and 2022 Q3 "Reading from the sequential file" (10) + "Populating the list box" (6). Textbook 11.4 reading from a file (p.454-456), 11.5 readLine loop and `split` (p.459).

**Version A - BufferedReader, line by line into a text area or list**

```java
private void readSavedFile() {
    File file = new File(FILE_NAME);
    if (!file.exists()) {                          // avoid an error before the first save
        JOptionPane.showMessageDialog(this, "No saved file yet - save first.");
        return;
    }
    txtResults.setText("");                        // (list: listModel.clear();)
    try {
        BufferedReader reader = new BufferedReader(new FileReader(file));
        String line = reader.readLine();           // first line (null if the file is empty)
        while (line != null) {                     // null = end of file
            txtResults.append(line + "\n");        // (list: listModel.addElement(line);)
            line = reader.readLine();              // next line
        }
        reader.close();
    } catch (IOException ex) {
        JOptionPane.showMessageDialog(this, "Error reading file: " + ex.getMessage());
    }
}
```

Imports: `java.io.BufferedReader`, `java.io.File`, `java.io.FileReader`, `java.io.IOException`.

**Version B - Scanner on a file** (Scanner is in the textbook from 2.6):

```java
try {
    Scanner input = new Scanner(new File(fileName));
    while (input.hasNextLine()) {
        contents += input.nextLine() + "\n";
    }
    input.close();
} catch (FileNotFoundException ex) {
    System.out.println("File not found: " + fileName);
}
```

**Version C - read "name,mark" lines back into arrays** (if the paper saves raw data instead of a report):

```java
int count = 0;
try {
    BufferedReader reader = new BufferedReader(new FileReader(fileName));
    String line = reader.readLine();
    while (line != null && count < names.length) {     // never overflow the array
        String[] parts = line.split(",");              // "Thabo,65" -> ["Thabo", "65"]
        names[count] = parts[0];
        marks[count] = Integer.parseInt(parts[1].trim());
        count++;
        line = reader.readLine();
    }
    reader.close();
} catch (IOException | NumberFormatException ex) {
    System.out.println("Error reading records: " + ex.getMessage());
}
```

- Read the next line **at the bottom** of the loop. If you forget it, the loop never ends.
- To show the file automatically when the form opens (2022 Q3.3), call the read method at the end of the constructor.

## T13 - Parallel arrays: search, add with a maximum, top performer

**Use for:** "Determine and display the top performing movie" (5), "TopEstateAgent" (test 5), 2022 "save up to five inspections to arrays" (10) and "Error message when more than five" (3). Textbook 8.5 (p.284).

```java
// parallel arrays: the SAME index belongs to the same record
private static final int MAX_RECORDS = 5;                    // CHANGE THIS
private final String[] names = new String[MAX_RECORDS];
private final int[] marks = new int[MAX_RECORDS];
private int count = 0;                                       // slots used so far

// ADD with a maximum (2022 pattern)
if (count >= MAX_RECORDS) {
    JOptionPane.showMessageDialog(this, "Maximum inspection count reached!");
    return;
}
names[count] = txtName.getText().trim();
marks[count] = mark;
count++;

// TOP performer: index of the biggest total, then the matching name
int topIndex = 0;
for (int i = 1; i < totals.length; i++) {
    if (totals[i] > totals[topIndex]) {
        topIndex = i;
    }
}
String top = names[topIndex];        // 2024 TopMovie returns this String; 2023 returns topIndex

// SEARCH by name (linear search): -1 means not found
int found = -1;
for (int i = 0; i < count; i++) {
    if (names[i].equalsIgnoreCase(searchName.trim())) {
        found = i;
        break;
    }
}
```

- Loop to `count`, not to `names.length`, so you skip the empty (null) slots.
- Read the interface's return type. `String TopMovie(...)` returns the name, but `int TopEstateAgent(...)` returns the **position**, and `main` then prints `agents[topIndex]`.

## Master Q1 - console report (fill in the blanks)

**Project:** `StudentMarksReport` (Maven). Four files. Tested: 4/4 tests pass, and the output is shown below. Covers every Q1 rubric line in 2025 and the mock.

**Adapting it in about 10 minutes**

1. Rename with **Ctrl+R** on each name (class, interface, methods) so every use updates together: `IStudentMarks` > the paper's interface, `StudentMarks` > the paper's class, and each method name > the paper's.
2. Replace the three arrays in `main` with the paper's table. Change the title, dashes and summary labels to match the sample.
3. Delete the optional extras (average column, passes, top student) if the paper doesn't ask for them, or keep the ones it does.
4. In the test: rename both tests exactly, put in the paper's data, and work out the expected values by hand.

**IStudentMarks.java**

```java
package com.mycompany.studentmarksreport;

/**
 * CHANGE THIS: copy the interface from the paper EXACTLY
 * (same interface name, same PascalCase method names, same parameter types).
 */
public interface IStudentMarks {

    int TotalMarks(int[][] marks);

    double AverageMark(int[][] marks);

    int HighestMark(int[][] marks);

    int LowestMark(int[][] marks);
}
```

**StudentMarks.java**

```java
package com.mycompany.studentmarksreport;

/**
 * MASTER Q1 class. CHANGE THIS: class name, interface name, method names.
 * The four interface methods cover total / average / highest / lowest.
 * The extra public methods (row and column results, pass count) are ready
 * in case the paper asks for them - delete the ones you do not need.
 */
public class StudentMarks implements IStudentMarks {

    // CHANGE THIS: the limit from the paper (pass mark, sales limit, target...)
    public static final int PASS_MARK = 50;

    /** @return the sum of every value in the 2D array */
    @Override
    public int TotalMarks(int[][] marks) {
        int total = 0;
        for (int row = 0; row < marks.length; row++) {
            for (int col = 0; col < marks[row].length; col++) {
                total += marks[row][col];
            }
        }
        return total;
    }

    /** @return total / number of values (a double - round it only when printing) */
    @Override
    public double AverageMark(int[][] marks) {
        return (double) TotalMarks(marks) / countValues(marks);
    }

    /** @return the largest value in the array */
    @Override
    public int HighestMark(int[][] marks) {
        int highest = marks[0][0];
        for (int row = 0; row < marks.length; row++) {
            for (int col = 0; col < marks[row].length; col++) {
                if (marks[row][col] > highest) {
                    highest = marks[row][col];
                }
            }
        }
        return highest;
    }

    /** @return the smallest value in the array */
    @Override
    public int LowestMark(int[][] marks) {
        int lowest = marks[0][0];
        for (int row = 0; row < marks.length; row++) {
            for (int col = 0; col < marks[row].length; col++) {
                if (marks[row][col] < lowest) {
                    lowest = marks[row][col];
                }
            }
        }
        return lowest;
    }

    // ---------- OPTIONAL EXTRAS (not in the interface) ----------

    /** @return how many values are in the whole array */
    public int countValues(int[][] marks) {
        int count = 0;
        for (int row = 0; row < marks.length; row++) {
            count += marks[row].length;
        }
        return count;
    }

    /** @return the total of ONE row (e.g. one student's marks) */
    public int rowTotal(int[][] marks, int row) {
        int total = 0;
        for (int col = 0; col < marks[row].length; col++) {
            total += marks[row][col];
        }
        return total;
    }

    /** @return the average of ONE row */
    public double rowAverage(int[][] marks, int row) {
        return (double) rowTotal(marks, row) / marks[row].length;
    }

    /** @return the total of ONE column (e.g. one test for every student) */
    public int columnTotal(int[][] marks, int col) {
        int total = 0;
        for (int row = 0; row < marks.length; row++) {
            total += marks[row][col];
        }
        return total;
    }

    /** @return the average of ONE column */
    public double columnAverage(int[][] marks, int col) {
        return (double) columnTotal(marks, col) / marks.length;
    }

    /** @return how many values are AT OR ABOVE the pass mark (>= : 50 passes) */
    public int countPasses(int[][] marks) {
        int count = 0;
        for (int row = 0; row < marks.length; row++) {
            for (int col = 0; col < marks[row].length; col++) {
                if (marks[row][col] >= PASS_MARK) {
                    count++;
                }
            }
        }
        return count;
    }

    /** @return the index of the row with the highest total (top student) */
    public int topRowIndex(int[][] marks) {
        int topIndex = 0;
        for (int row = 1; row < marks.length; row++) {
            if (rowTotal(marks, row) > rowTotal(marks, topIndex)) {
                topIndex = row;
            }
        }
        return topIndex;
    }
}
```

**StudentMarksReport.java** (the main class NetBeans created)

```java
package com.mycompany.studentmarksreport;

/**
 * MASTER Q1 - console report from a 1D array of names and a 2D array of figures.
 * CHANGE THIS: title, names, column headings, data, labels on summary lines.
 *
 * AI disclosure: study templates prepared with Claude (Anthropic) were used
 * while revising; this code was typed, adapted and tested by me.
 */
public class StudentMarksReport {

    public static void main(String[] args) {
        // CHANGE THIS: row names (1D array) - one per row of the 2D array
        String[] students = {"Thabo", "Aisha", "Liam"};
        // CHANGE THIS: column headings (1D array) - one per column
        String[] assessments = {"TEST 1", "TEST 2", "ASSIGN", "EXAM"};
        // CHANGE THIS: the table from the paper, row by row
        int[][] marks = {
            {65, 72, 58, 80},
            {45, 38, 52, 49},
            {90, 85, 78, 88}
        };

        StudentMarks calc = new StudentMarks();
        String line = "--------------------------------------------------";

        System.out.println("STUDENT MARKS REPORT - 2026");   // CHANGE THIS
        System.out.println(line);

        // heading row: blank first column, then each column heading
        System.out.printf("%-10s", "");
        for (int col = 0; col < assessments.length; col++) {
            System.out.printf("%8s", assessments[col]);
        }
        System.out.printf("%9s%n", "AVERAGE");                   // optional extra column

        // data rows: name, each value, then the row average
        for (int row = 0; row < marks.length; row++) {
            System.out.printf("%-10s", students[row]);
            for (int col = 0; col < marks[row].length; col++) {
                System.out.printf("%8d", marks[row][col]);
            }
            System.out.printf("%9d%n", Math.round(calc.rowAverage(marks, row)));
        }

        System.out.println(line);
        // CHANGE THIS: labels must match the paper's sample exactly
        System.out.println("Total marks:   " + calc.TotalMarks(marks));
        System.out.println("Average mark:  " + Math.round(calc.AverageMark(marks)));
        System.out.println("Highest mark:  " + calc.HighestMark(marks));
        System.out.println("Lowest mark:   " + calc.LowestMark(marks));
        // optional extras - delete if not asked for
        System.out.println("Marks passed:  " + calc.countPasses(marks));
        System.out.println("Top student:   " + students[calc.topRowIndex(marks)]);
        System.out.println(line);
    }
}
```

**StudentMarksTest.java** (Test Packages, same package)

```java
package com.mycompany.studentmarksreport;

import static org.junit.jupiter.api.Assertions.assertEquals;
import org.junit.jupiter.api.Test;

/**
 * MASTER Q1 tests. CHANGE THIS: test method names must be EXACTLY the
 * names in the paper's table; expected values come from the paper's data.
 */
public class StudentMarksTest {

    private final int[][] marks = {
        {65, 72, 58, 80},
        {45, 38, 52, 49},
        {90, 85, 78, 88}
    };

    private final StudentMarks calc = new StudentMarks();

    @Test
    public void CalculateTotalMarks_ReturnsTotalMarks() {
        // int result: assertEquals(expected, actual)
        assertEquals(800, calc.TotalMarks(marks));
    }

    @Test
    public void AverageMark_ReturnsAverageMark() {
        // double result: assertEquals(expected, actual, delta)
        assertEquals(66.67, calc.AverageMark(marks), 0.01);
    }

    @Test
    public void HighestMark_ReturnsHighestMark() {
        assertEquals(90, calc.HighestMark(marks));
    }

    @Test
    public void LowestMark_ReturnsLowestMark() {
        assertEquals(38, calc.LowestMark(marks));
    }
}
```

**Output when run (F6):**

```text
STUDENT MARKS REPORT - 2026
--------------------------------------------------
            TEST 1  TEST 2  ASSIGN    EXAM  AVERAGE
Thabo           65      72      58      80       69
Aisha           45      38      52      49       46
Liam            90      85      78      88       85
--------------------------------------------------
Total marks:   800
Average mark:  67
Highest mark:  90
Lowest mark:   38
Marks passed:  9
Top student:   Liam
--------------------------------------------------
```

## Master Q2 - GUI with Load, Save, Read-back and Clear (fill in the blanks)

**Project:** `StudentMarksApp` (Maven). Four files. Tested: 4/4 tests pass. The form was opened on a virtual screen and its buttons and menus were clicked, and `marks.txt` was written and read back. Covers every Q2 rubric line in 2025 and the mock, plus the read-back variation.

**Adapting it in about 15 minutes**

1. Interface: paste the paper's interface over `IStudentMarks` (Ctrl+R to rename the file and its uses). Alt+Enter in the class > *Implement all abstract methods* adds anything you're missing.
2. Class: the constant name and value, `>` or `>=`, and the Get method names.
3. Form: the data array, button and menu texts, title, file name, file heading, and the label text ("Years Processed"). Delete the *Read Saved File* menu item and `readSavedFile()` if the paper doesn't ask for reading back.
4. Tests: the paper's two names and the expected counts, worked out by hand.
5. GUI Builder instead? Build the form as in **T7 Option 1**, then paste `loadMarks()`, `saveMarks()`, `readSavedFile()` and `clearForm()` from below. The class and test files stay the same.

**IStudentMarks.java**

```java
package com.mycompany.studentmarksapp;

/**
 * MASTER Q2 interface. CHANGE THIS: copy the paper's interface EXACTLY.
 */
public interface IStudentMarks {

    int[][] GetStudentMarks();

    int GetTotalMarks();

    int GetPassCount();

    int GetFailCount();

    int GetStudentsProcessed();

    double GetAverageMark();
}
```

**StudentMarks.java**

```java
package com.mycompany.studentmarksapp;

/**
 * MASTER Q2 class: stores the 2D array and answers the Get... methods.
 * CHANGE THIS: class name, constant name/value, comparison (> or >=).
 */
public class StudentMarks implements IStudentMarks {

    // CHANGE THIS: limit from the paper, stored ONCE as a constant
    public static final int PASS_MARK = 50;

    // private + final: set once in the constructor, read through the getters
    private final int[][] studentMarks;

    /** @param studentMarks one row per student, one column per assessment */
    public StudentMarks(int[][] studentMarks) {
        this.studentMarks = studentMarks;
    }

    @Override
    public int[][] GetStudentMarks() {
        return studentMarks;
    }

    @Override
    public int GetTotalMarks() {
        int total = 0;
        for (int row = 0; row < studentMarks.length; row++) {
            for (int col = 0; col < studentMarks[row].length; col++) {
                total += studentMarks[row][col];
            }
        }
        return total;
    }

    /** CHANGE THIS if the paper says "over" (use >) instead of "at least" (>=). */
    @Override
    public int GetPassCount() {
        int count = 0;
        for (int row = 0; row < studentMarks.length; row++) {
            for (int col = 0; col < studentMarks[row].length; col++) {
                if (studentMarks[row][col] >= PASS_MARK) {
                    count++;
                }
            }
        }
        return count;
    }

    /** Every mark is a pass or a fail, so fails = all marks - passes. */
    @Override
    public int GetFailCount() {
        return countMarks() - GetPassCount();
    }

    /** Worked out from the array (number of rows), never typed in. */
    @Override
    public int GetStudentsProcessed() {
        return studentMarks.length;
    }

    @Override
    public double GetAverageMark() {
        return (double) GetTotalMarks() / countMarks();
    }

    /** Helper so the counting loop is written once. */
    private int countMarks() {
        int count = 0;
        for (int row = 0; row < studentMarks.length; row++) {
            count += studentMarks[row].length;
        }
        return count;
    }
}
```

**StudentMarksForm.java** (hand-coded; the main class)

```java
package com.mycompany.studentmarksapp;

import java.awt.BorderLayout;
import java.awt.GridLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JMenu;
import javax.swing.JMenuBar;
import javax.swing.JMenuItem;
import javax.swing.JOptionPane;
import javax.swing.JPanel;
import javax.swing.JScrollPane;
import javax.swing.JTextArea;

/**
 * MASTER Q2 - HAND-CODED version (textbook Chapter 14 style).
 * Load / Save buttons, read-only text area, read-only label, menu bar.
 * Every button and its menu item call ONE shared method.
 * CHANGE THIS: titles, labels, data, file name, header line.
 *
 * AI disclosure: study templates prepared with Claude (Anthropic) were used
 * while revising; this code was typed, adapted and tested by me.
 */
public class StudentMarksForm extends JFrame implements ActionListener {

    // CHANGE THIS: the data "in memory" (rows = students, columns = assessments)
    private static final int[][] MARKS_DATA = {
        {65, 72, 58, 80},
        {45, 38, 52, 49},
        {90, 85, 78, 88}
    };
    private static final String FILE_NAME = "marks.txt";                 // CHANGE THIS
    private static final String STARS = "******************************";

    private final JButton btnLoad = new JButton("Load Marks");           // CHANGE THIS
    private final JButton btnSave = new JButton("Save Marks");           // CHANGE THIS
    private final JTextArea txtResults = new JTextArea(8, 24);
    private final JLabel lblProcessed = new JLabel("Students Processed: ");

    private final JMenuItem mnuExit = new JMenuItem("Exit");
    private final JMenuItem mnuLoad = new JMenuItem("Load Marks");
    private final JMenuItem mnuSave = new JMenuItem("Save Marks");
    private final JMenuItem mnuReadFile = new JMenuItem("Read Saved File");  // only if asked
    private final JMenuItem mnuClear = new JMenuItem("Clear");

    public StudentMarksForm() {
        super("Student Marks Application");                              // CHANGE THIS
        setSize(340, 340);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new BorderLayout(5, 5));

        // ---- menu bar: File > Exit ; Tools > Load, Save, Read, Clear ----
        JMenuBar menuBar = new JMenuBar();
        JMenu mnuFile = new JMenu("File");
        JMenu mnuTools = new JMenu("Tools");
        mnuFile.add(mnuExit);
        mnuTools.add(mnuLoad);
        mnuTools.add(mnuSave);
        mnuTools.add(mnuReadFile);
        mnuTools.add(mnuClear);
        menuBar.add(mnuFile);
        menuBar.add(mnuTools);
        setJMenuBar(menuBar);

        // ---- buttons on top, text area in the middle, label at the bottom ----
        JPanel buttonPanel = new JPanel(new GridLayout(2, 1, 5, 5));
        buttonPanel.add(btnLoad);
        buttonPanel.add(btnSave);
        add(buttonPanel, BorderLayout.NORTH);

        txtResults.setEditable(false);                 // output only
        add(new JScrollPane(txtResults), BorderLayout.CENTER);
        add(lblProcessed, BorderLayout.SOUTH);         // JLabel is read-only

        // ---- register the form as the listener for every control ----
        btnLoad.addActionListener(this);
        btnSave.addActionListener(this);
        mnuExit.addActionListener(this);
        mnuLoad.addActionListener(this);
        mnuSave.addActionListener(this);
        mnuReadFile.addActionListener(this);
        mnuClear.addActionListener(this);
    }

    /** One place decides which shared method each click runs. */
    @Override
    public void actionPerformed(ActionEvent e) {
        Object source = e.getSource();
        if (source == btnLoad || source == mnuLoad) {
            loadMarks();
        } else if (source == btnSave || source == mnuSave) {
            saveMarks();
        } else if (source == mnuReadFile) {
            readSavedFile();
        } else if (source == mnuClear) {
            clearForm();
        } else if (source == mnuExit) {
            System.exit(0);
        }
    }

    /** Load: create the object from the array, calculate, display. */
    private void loadMarks() {
        StudentMarks marks = new StudentMarks(MARKS_DATA);
        txtResults.setText("Total Marks: " + marks.GetTotalMarks() + "\n"
                + "Average Mark: " + Math.round(marks.GetAverageMark()) + "\n"
                + "Marks passed: " + marks.GetPassCount() + "\n"
                + "Marks failed: " + marks.GetFailCount());
        lblProcessed.setText("Students Processed: " + marks.GetStudentsProcessed());
    }

    /** Save: header, stars, the text area's text, stars -> marks.txt. */
    private void saveMarks() {
        if (txtResults.getText().isEmpty()) {
            JOptionPane.showMessageDialog(this, "Please load the marks first.");
            return;
        }
        try {
            BufferedWriter writer = new BufferedWriter(new FileWriter(FILE_NAME));
            writer.write("MARKS LOG");                     // CHANGE THIS: header from sample
            writer.newLine();
            writer.write(STARS);
            writer.newLine();
            writer.write(txtResults.getText());
            writer.newLine();
            writer.write(STARS);
            writer.newLine();
            writer.close();
            JOptionPane.showMessageDialog(this, "Marks saved to " + FILE_NAME);
        } catch (IOException ex) {
            JOptionPane.showMessageDialog(this, "Error saving file: " + ex.getMessage());
        }
    }

    /** Read back: show every line of marks.txt in the text area. */
    private void readSavedFile() {
        File file = new File(FILE_NAME);
        if (!file.exists()) {
            JOptionPane.showMessageDialog(this, "No saved file yet - save the marks first.");
            return;
        }
        txtResults.setText("");
        try {
            BufferedReader reader = new BufferedReader(new FileReader(file));
            String line = reader.readLine();
            while (line != null) {               // null = end of the file
                txtResults.append(line + "\n");
                line = reader.readLine();
            }
            reader.close();
        } catch (IOException ex) {
            JOptionPane.showMessageDialog(this, "Error reading file: " + ex.getMessage());
        }
    }

    /** Clear: empty the text area and reset the label. */
    private void clearForm() {
        txtResults.setText("");
        lblProcessed.setText("Students Processed: ");
    }

    public static void main(String[] args) {
        StudentMarksForm form = new StudentMarksForm();
        form.setLocationRelativeTo(null);
        form.setVisible(true);
    }
}
```

**StudentMarksTest.java**

```java
package com.mycompany.studentmarksapp;

import static org.junit.jupiter.api.Assertions.assertEquals;
import org.junit.jupiter.api.Test;

/**
 * MASTER Q2 tests. CHANGE THIS: exact test names from the paper.
 */
public class StudentMarksTest {

    private final int[][] marksData = {
        {65, 72, 58, 80},
        {45, 38, 52, 49},
        {90, 85, 78, 88}
    };

    @Test
    public void GetPassCount_ReturnsNumberOfPasses() {
        StudentMarks marks = new StudentMarks(marksData);
        // 45, 38 and 49 are below 50, so 12 - 3 = 9 passes
        assertEquals(9, marks.GetPassCount());
    }

    @Test
    public void GetFailCount_ReturnsNumberOfFails() {
        StudentMarks marks = new StudentMarks(marksData);
        assertEquals(3, marks.GetFailCount());
    }

    @Test
    public void GetStudentsProcessed_ReturnsNumberOfRows() {
        StudentMarks marks = new StudentMarks(marksData);
        assertEquals(3, marks.GetStudentsProcessed());
    }

    @Test
    public void GetAverageMark_ReturnsAverage() {
        StudentMarks marks = new StudentMarks(marksData);
        assertEquals(66.67, marks.GetAverageMark(), 0.01);
    }
}
```

**Text area after Load:** `Total Marks: 800` / `Average Mark: 67` / `Marks passed: 9` / `Marks failed: 3`, and the label reads `Students Processed: 3`.

**marks.txt after Save** (in the project folder):

```text
MARKS LOG
******************************
Total Marks: 800
Average Mark: 67
Marks passed: 9
Marks failed: 3
******************************
```

**Clicks tested:** Read Saved File before saving shows "No saved file yet". Save before Load shows "Please load the marks first". Load > Save > Clear > Read Saved File shows the file's 7 lines in the text area.
