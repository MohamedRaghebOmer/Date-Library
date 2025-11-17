# clsDate — C++ Date Utility Class

**A small, self-contained C++ class providing comprehensive date and time utilities.**

---

## Overview

`clsDate` is a handy C++ class that wraps common date/time operations in an easy-to-use API. It provides constructors, formatting, validation, arithmetic (add/subtract days, months, years), comparisons, calendar printing, and utility helpers such as business-day calculations and system date/time retrieval.

This code is suitable for educational projects, small tools, and apps where a light-weight date helper is needed without pulling in heavy date/time libraries.

---

## Key features

* Create dates from components or a `dd/mm/yyyy` string.
* System date and time retrieval (`GetSystemDate`, `GetSystemTime`, `GetSystemDateAndTime`).
* Validation (leap years, days-per-month checks).
* Date arithmetic: add/subtract days, weeks, months, years, decades, centuries, millennia.
* Business-day and weekend helpers (count business days, calculate return-from-vacation date).
* Date comparison helpers and difference-in-days calculation.
* Calendar printing (month and year view) to the console.
* Formatting helper: `Format` supports `dd`, `mm`, `yyyy` tokens.

---

## Files

This repository contains the `clsDate` header (single-file implementation). If you keep the code as-is, include the header in your project. Typical files to include in your project:

* `clsDate.h` (the full class code)
* `clsString.h` (utility used by `clsDate` for string operations)
* `Global.h` (project-wide definitions if used)

> If you prefer a separate compilation unit, split the implementation into `clsDate.h` (declarations) and `clsDate.cpp` (definitions), then add both to your Visual Studio project.

---

## Requirements

* Microsoft Visual Studio Community 2022 (recommended)
* C++ compiler with C++11 support or later

---

## Quick start (Visual Studio Community 2022)

1. Create a new **Empty Project** (or Console App) in Visual Studio Community 2022.
2. Add `clsDate.h` (and `clsString.h` / `Global.h` if required) to the project `Source Files` / `Header Files` as needed.
3. If you split the implementation into `.cpp`, add it to the project and build.
4. Include and use `clsDate` in your code:

```cpp
#include "clsDate.h"
#include <iostream>

int main()
{
    // Construct using system date
    clsDate today = clsDate::GetSystemDate();
    today.Print();

    // Construct from string
    clsDate d1("1/1/2000");
    std::cout << d1.Format("dd/mm/yyyy") << std::endl;

    // Add 10 days
    d1.AddDays(10);
    d1.Print();

    // Difference in days
    clsDate d2(15, 1, 2000);
    int diff = d1.GetDifferenceInDays(d2, true);
    std::cout << "Difference in days: " << diff << std::endl;

    return 0;
}
```

---

## API highlights (selection)

* `clsDate()` — default constructs to system date.
* `clsDate(const std::string &sDate)` — construct from `"dd/mm/yyyy"` string.
* `clsDate(short Day, short Month, short Year)` — construct from components.
* `static clsDate GetSystemDate()` — returns current system date.
* `static std::string GetSystemTime(bool use12HourFormat = false, const std::string Seperator = ":")` — returns time string.
* `bool IsValid()` / `static bool IsValidDate(clsDate &Date)` — validate date.
* `static int GetDifferenceInDays(clsDate Date1, clsDate Date2, bool IncludeEndDay = false)` — difference in days.
* `void AddDays(short Days)` / `static clsDate AddOneDay(clsDate &Date)` — date arithmetic.
* `static short CalculateBusinessDays(clsDate DateFrom, clsDate DateTo)` — business days between dates.
* `std::string Format(const std::string &DateFormat = "dd/mm/yyyy")` — custom formatting.

Refer to the header for the full method list and signatures.

---

## Suggested improvements

* Split the implementation into `.h` and `.cpp` for faster compile times and cleaner project structure.
* Add unit tests (e.g., using Google Test) to validate edge cases (leap years, end-of-month transitions).
* Add exceptions or error codes for invalid input parsing.
* Improve localization for month/day names if needed.

---

## Contributing

Contributions are welcome. Open an issue or submit a pull request. Keep changes focused and add tests for any bug fixes or behavioral changes.

---

## License

This project is released under the MIT License. See the `LICENSE` file for details.

---

## Contact

If you have questions or need help integrating `clsDate` into your project, open an issue or contact the repository owner.

*README generated for `clsDate` — ready to use.*
