# Smart-library-management-system
This is a Smart Library Management System (SLMS) coursework in C++.

## Structure
- `src_cpp/` C++ source code
- `docs/requirements.md` Requirements, scope, assumptions
- `docs/uml.md` UML class diagram (Mermaid)
- `docs/pseudocode.md` Pseudocode for key flows
- `docs/test-plan.md` Test strategy and cases
- `docs/demo.md` Demo walkthrough

## Build and Run (MSYS2 MinGW64)
From the project root in MSYS2 MinGW64:
```
/mingw64/bin/g++ -std=c++17 -O2 -o slms_cpp.exe src_cpp/main.cpp
./slms_cpp.exe
```

## Sample Accounts
- Member: `alice` / `pass1`
- Member: `bob` / `pass2`
- Librarian: `lina` / `lib1`
- Admin: `adam` / `admin1`

## Notes
- In-memory data only.
- Borrow limit, reservation expiry, and loan period are configurable by admin.
