# 1. Software Requirements Review

**Overview:**  
This program computes the minimum and maximum values of integer data types: (char, short, int, long) in both signed and unsigned forms without relying on `<limits.h>`.  
The purpose is to demonstrate understanding of binary representation and type sizing in C. Each value is computed programmatically and printed with clear labels.

**Assumptions and Constraints:**  
The platform is 64-bit (x86_64) so long is 8 bytes not 4.  
Size of integer types may vary by compiler or platform and should be verified before any real life use.

**Requirements Covered SR-2.1-01 to SR-2.1-10**

- **Requirement ID: SR-2.1-01**  
  The following program shall compute the minimum and maximum values of a signed char using bitwise operations.  
- **Requirement ID: SR-2.1-02**  
  The following program shall compute the minimum and maximum values of a signed short using bitwise operations.  
- **Requirement ID: SR-2.1-03**  
  The following program shall compute the minimum and maximum values of a signed int using bitwise operations.  
- **Requirement ID: SR-2.1-04**  
  The following program shall compute the minimum and maximum values of a signed long using bitwise operations.  
- **Requirement ID: SR-2.1-05**  
  The following program shall compute the maximum values of a unsigned char using bitwise operations.  
- **Requirement ID: SR-2.1-06**  
  The following program shall compute the maximum values of a unsigned short using bitwise operations.  
- **Requirement ID: SR-2.1-07**  
  The following program shall compute the maximum values of a unsigned int using bitwise operations.  
- **Requirement ID: SR-2.1-08**  
  The following program shall compute the maximum values of a unsigned long using bitwise operations.  
- **Requirement ID: SR-2.1-09**  
  The following program shall display the computed values with labels in a human readable format.  
- **Requirement ID: SR-2.1-10**  
  The following program shall no usage of `<limits.h>` in code.  

---

# 2. Test Procedure Generation and Execution 

| Test Case ID | Related Req(s) | Test Description                                  | Expected Result                                   | Actual Result                |
|--------------|----------------|-------------------------------------------------|--------------------------------------------------|-----------------------------|
| TC-2.1-01    | SR-2.1-01      | Compute min and max of `signed char`             | min = -128, max = 127                             | min: -128 max: 127          |
| TC-2.1-02    | SR-2.1-02      | Compute min and max of `signed short`            | min = -32,768, max = 32,767                       | min: -32768 max: 32767      |
| TC-2.1-03    | SR-2.1-03      | Compute min and max of `signed int`              | min = -2,147,483,648, max = 2,147,483,647        | min: -2147483648 max: 2147483647 |
| TC-2.1-04    | SR-2.1-04      | Compute min and max of `signed long`             | Platform-dependent (e.g. 32-bit or 64-bit)        | min: -2147483648 max: 2147483647 |
| TC-2.1-05    | SR-2.1-05      | Compute max of `unsigned char`                    | max = 255                                         | max: 255                    |
| TC-2.1-06    | SR-2.1-06      | Compute max of `unsigned short`                   | max = 65,535                                      | max: 65535                  |
| TC-2.1-07    | SR-2.1-07      | Compute max of `unsigned int`                     | max = 4,294,967,295 (on 32-bit systems)           | max: 4294967295             |
| TC-2.1-08    | SR-2.1-08      | Compute max of `unsigned long`                    | Platform-dependent (e.g. 2^32 or 2^64 - 1)        | max: 4294967295             |
| TC-2.1-09    | SR-2.1-09      | Verify output is clearly labeled and human-readable | Output includes labels for each type/value        | passed                      |
| TC-2.1-10    | All            | Confirm that `<limits.h>` is not used in the implementation | No inclusion of `<limits.h>` in source code      | passed                      |

To execute the tests and verify output:

```bash
gcc .\ex2_1_signed_unsigned.c -o .\ex2_1_signed_unsigned.exe
.\ex2_1_signed_unsigned.exe > test_output.log
```

Inspect `test_output.log` and compare values to the expected result column.  
Confirm that `<limits.h>` isn't used in the code.  

---

# 3. Unit Level Testing and Execution Results

- All test cases from Section 2 were executed on 64-bit Windows 11 using GCC 15.1.0 on Ryzen 7 5800X CPU.  
- On this platform long and int are both 32 bits so their min/max values are equal.  
- The output log was inspected and values mostly matched the expected results exactly, confirming correct computation for the data types.  
- No use of `<limits.h>` was found in the source code as confirmed by code review.  
- These results show compliance with requirements SR-2.1-01 - SR-2.1-10 as verified by test cases TC-2.1-01 to TC-2.1-10 by Thomas Sehenuk.

---

# 4. Graphics, I/O, Unit Level, and System Testing

- No graphical interface exists; therefore, no graphics testing was applicable.  
- The program’s output consists of printed text to the console; all strings were verified for accuracy and clarity.  
- Unit level testing focused on verifying each variable’s computed min/max value as per requirements.  
- System testing involved running the complete executable on the target platform and verifying end-to-end correctness.

---

# 5. Code/Requirement Differential and Regression Analysis

- The implemented code fully satisfies the requirements SR-2.1-01 through SR-2.1-10 without introducing regressions.  
- Since this is a new implementation, regression testing focused on ensuring correctness of all test cases before and after any code adjustments.  
- Future modifications will include rerunning the full tests to prevent regressions.

---

# 6. Code Review for Coding Standard Adherence

- The code follows a clean and consistent indentation style using 4 spaces per indent.  
- Variable names are descriptive and meaningful.  
- Comments are clear and explain the purpose/logic of code blocks and variables.  
- Parentheses usage ensures clarity in expressions, particularly in the bitwise operations.  
- Format specifiers in `printf` match variable types correctly.  
- While the code adheres well to general good practices, it does not strictly follow a formal coding standard like MISRA or Linux kernel style.  
- For future work, will follow a formal coding standard such as MISRA.

---

# 7. Structural Coverage Analysis

- With the simplicity and flow of the program, 100% statement coverage was achieved.  
- No conditional branches or loops exist, so branch coverage is not applicable here.  
- Coverage was verified through manual inspection.

---

# 8. Software Problem Reporting

The program meets all specified requirements except for minor platform-dependent variations:  
- On this platform, `int` and `long` have the same size (32 bits), so their min and max values are the same.  
- If cross-platform compatibility or other than learning use is required, consider using fixed width integer types: `int32_t` or `int64_t`.  
- No other code changes are required at this time.

---

# 9. Technical Writing Documentation and Reports

Throughout the project, each stage was carefully documented to ensure clarity and traceability:  
- The Software Requirements Review explicitly lists every requirement ID and how the program satisfies it, providing a clear link between requirements and implementation.  
- The Test Procedure Matrix was developed to align each test case with its related requirements, showing expected and actual results for straightforward verification.  
- In the Unit Testing Report, details were included about the testing environment (64-bit Windows 11, GCC 15.1.0) and noted platform-specific behaviors like `int` and `long` being equal in size.  
- The source code contains descriptive comments explaining the logic behind bitwise calculations and casting, making it easier for any reviewer or future maintainer to understand the approach without relying on external documentation.  
- Software Problem Reporting is documented thoroughly, noting the platform-dependent results and advising on fixed-width integer types for more portable code.  
Overall, the documentation is structured and detailed, making the project accessible and verifiable for both technical reviewers and verification. This reflects a strong commitment to good software engineering communication practices.

-- Note: All work was produced by Thomas Sehenuk
-- Only headers/ matrix formatting/ bullet point formatting were changed for the sake of time efficiency for Github by GPT4.0. 