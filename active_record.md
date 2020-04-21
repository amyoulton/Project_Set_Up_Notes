# Active Record

## Fetch All Questions

    questions = Question.all

- this will give us back the list of questions as an object
- the object behaves like an array so you can call methods on it like (.each) and you
- can also chain it with other methods to do other types of operations and queries

## Creating A New Question

### To Create a New Question Object in Memory do:

    q = Question.new

#### you can also pass in a hash to the new method as in:

    q = Question.new({ title: 'To be or not to be', body: 'is that a question?', view_count: 0 })

#### or for short:

    q = Question.new title: 'To be or not to be', body: 'is that a question?', view_count: 0

### To Save the Above Question into Questions Table:

    # q.save

#### this will save that above question into the questions table (persist it)

### To Create a Record Right Away:

you can create a record right away in the database using (.create) method as in:

    Question.create({ title: 'My Question Title', body: 'My question body', view_count: 1 })

# Fetching Records

## .first

    Question.first

This fetches the first record ordered by the id in an ascending order.

#### The SQL equivalent:

    SELECT "questions".* FROM "questions" ORDER BY "questions"."id" ASC LIMIT 1;

## .last

    Question.last

This fetches the last record ordered by the id in an ascending order.

#### The SQL equivalent:

    SELECT "questions".* FROM "questions" ORDER BY "qeustions"."id" DESC LIMIT 1;

## .find

    Question.find(1)

This finds records by their primary key which is likely id

## .find_by_x where x is the column name

    Question.find_by_title('My Last Question')

This finds a question with title this is exactly "My Last Question".

## .where

    Question.where({ title: 'My Last Question', body: 'The body of the question' })

# WILDCARD SEARCHING

You can perform wildcard searching with Active Record using LIKE within "where" method:

    Question.where(['title LIKE ?', '%Last%'])

If you are using Postgres client, you can use ILIKE for case-insensitive searching:

    Question.where(['title ILIKE ?', '%Last%'])

Note that in above queries we used a syntax that used '?' to insert variable into a SQL query.
This is important to avoid SQL injection if the variable component is actually a user input such as search term.

## .limit

    Question.limit(10)

This will give us back 10 first questions that are returned from the query
