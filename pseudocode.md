# Pseudocode

## Main Program Flow

seed books, users, and rules
loop
  prompt login (username, password)
  if authenticate fails -> show error and continue
  if role == Member -> show member menu
  if role == Librarian -> show librarian menu
  if role == Admin -> show admin menu
  if user chooses logout -> return to login
end loop


## Borrow Book

function borrowBook(member, bookId, today):
  book = catalog.findById(bookId)
  if book not found -> return "Book not found"
  expire reservations older than rules.reservationExpiryDays
  if book.status == RESERVED and reservation not by member -> return "Book reserved"
  if book.status == BORROWED -> return "Book already borrowed"
  if member.activeLoansCount >= rules.borrowLimit -> return "Borrow limit reached"

  dueDate = today + rules.loanDays
  create new Loan(book, member, today, dueDate)
  mark book.status = BORROWED
  notify(member, "Borrowed with due date " + dueDate)
  return "Borrowed successfully"


## Return Book

function returnBook(member, bookId, today):
  loan = find active loan by member and bookId
  if not found -> return "Loan not found"
  mark loan.returned = true
  if reservations exist for book -> book.status = RESERVED
  notify(nextMember, "Reservation available")
  else -> book.status = AVAILABLE
  return "Return successful"


## Reserve Book

function reserveBook(member, bookId, today):
  book = catalog.findById(bookId)
  if book not found -> return "Book not found"
  if book.status == AVAILABLE -> return "Book available; please borrow"
  if member already reserved this book -> return "Already reserved"
  create Reservation(book, member, today)
  book.status = RESERVED
  notify(member, "Reservation placed")
  return "Reservation successful"


## Overdue Report

function getOverdueLoans(today):
  overdue = []
  for each loan in loans:
    if not loan.returned and loan.dueDate < today:
      add loan to overdue
  return overdue

