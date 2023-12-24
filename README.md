# ELicov-ALtschool

1. WHAT IS THIS PROJECT ABOUT?

This is an Object Oriented Programming project geared at modelling and managing financial expenses.
The Code for the project is as follows:

import uuid
from datetime import datetime, timezone

class Expense:
    def __init__(self, title, amount):
        self.id = str(uuid.uuid4())
        self.title = title
        self.amount = amount
        self.created_at = datetime.utcnow()
        self.updated_at = self.created_at
    

    def update(self, title=None, amount=None):
        if title is not None:
            self.title = title
        if amount is not None:
            self.amount = amount
        self.updated_at = datetime.utcnow()        
    

    def to_dict(self):
        return {
            'id' : self.id,
            'title': self.title,
            'amount': self.amount,
            'created_at': self.created_at.isoformat(),
            'updated_at': self.updated_at.isoformat()
        }
    


class ExpenseDatabase:
    def __init__(self):
        self.expenses = []

    def add_expense(self, expense):
        self.expenses.append(Expense)

    def remove_expense(self,expense_id):
        self.expenses = [exp for exp in self.expenses if exp.id != expense_id]

    def get_expense_by_id(self, expense_id):
        for expense in self.expenses:
            if expense.id == expense_id:
                return expense
        return None
    
    def get_expense_by_title(self, title):
        return [expense for expense in self.expenses if expense.title == title]
    
    def to_dict(self):
        return [expense.to_dict() for expense in self.expenses]
2. To clone this project, the following steps should be taken:
   a) Copy the repository URL
   b) OPen a terminal on command prompt
   c)Navigate the the desired repository
   d) CLone the repository
   e) Enter github credentials
   f) Wait for the clone to complete
   
3. HOW THE CODE RUNS
   A) The 'uuid' module generates a unique identifier and the 'datetime' modeule to arrange timestamps.
   The '__init__' module initializes the attributes and the update method allows the updating of the timestamp.

    B) 'The ExpenseDB' class manages a collection of 'Expense' objects. The __init__ mehtod initializes the list of expenses, 'add_expense' adds an expense to the list, 'remove_expense' removes an expense by ID, 'get_expense_by_id' retrieves and expense by ID, 'get_expenses_by_title' retrieves expenses by title and 'to_dict' returns a list of dictionaries representing all expenses in the collection.
2.2
