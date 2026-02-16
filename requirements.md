# SLMS Requirements and Scope

## Scope
- Partial Smart Library Management System (SLMS) focused on core members, librarian, and admin workflows.
- Console-based C++ application with in-memory data (no database or web User intertface).

## Assumptions
- Users log in with a username/password stored in memory.
- Book data and user accounts are pre-seeded for demonstration.
- Time is represented using the system date.
- Only one active reservation per member per book is allowed.

## Functional Requirements (FR)
- FR1: Members can securely log in and view their active loans.
- FR2: Members can search books by title or author and view availability.
- FR3: Members can borrow books if they have fewer than the borrow limit.
- FR4: Members can return borrowed books and update availability.
- FR5: Members can reserve books that are currently borrowed.
- FR6: Librarians can add, update, and remove books.
- FR7: Librarians can process borrowing and reservation requests.
- FR8: Librarians can generate a report of overdue books.
- FR9: Administrators can create and remove member or librarian accounts.
- FR10: Administrators can configure library rules (borrow limit, loan days,
  reservation expiry, late penalty).
- FR11: The system updates book status automatically on borrow/return/reserve.
- FR12: The system sends notifications to members for due dates, overdue items,
  and available reservations.

## Non-Functional Requirements (NFR)
- NFR1: Actions such as borrowing or reserving complete within 1 second on a
  typical laptop or any device for the given dataset size.
- NFR2: The system uses object-oriented design with clear encapsulation and
  meaningful polymorphism.
- NFR3: The codebase is readable, well-structured, and uses consistent naming.
- NFR4: Input validation prevents invalid operations (e.g., borrowing
  unavailable books).

## Constraints
- C1: Members can borrow up to three books at once (default rule).
- C2: Reservations expire after three days if not collected (default rule).
- C3: Loan is up to 14 days Once borrowed (default rule).
- C4: Book status must be one of Available, Borrowed, or Reserved.
