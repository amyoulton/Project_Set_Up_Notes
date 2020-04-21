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

# Wildcard Searching

You can perform wildcard searching with Active Record using LIKE within "where" method:

    Question.where(['title LIKE ?', '%Last%'])

If you are using Postgres client, you can use ILIKE for case-insensitive searching:

    Question.where(['title ILIKE ?', '%Last%'])

Note that in above queries we used a syntax that used '?' to insert variable into a SQL query.
This is important to avoid SQL injection if the variable component is actually a user input such as search term.

## .limit

    Question.limit(10)

This will give us back 10 first questions that are returned from the query

## .order

    Question.order(:created_at)

This will order the fetched records by created_at. by default is ASC and f you want them in descending order do:

    Question.order(created_at: :DESC)

# Chaining

You can chain the where, limit, order, offset, and many others to compose more sophisticated queries for example:

    Question.where(['view_count > ?', 10]).where(['title ILIKE ?', 'a']).order(id: :DESC).limit(10).offset(10)

Note: offset will skip first 10 records from the above query

#### The SQL equivalent:

    SELECT "questions".* FROM "questions" WHERE (view_count > 10) AND (title ILIKE 'a') ORDER BY id DESC LIMIT 10 OFFSET 10

Another example:

    Question.where(['view_count < ?', 10]).where(['body ILIKE ?', '%question%']).order(id: :DESC).limit(1).offset(1)

# Update Records

Once you've selected one or more records, you have ability to update them.
There are many setting attributes:

    q = Question.find 10
    q.title = "Some new title"
    q.save
    q.view_count += 1
    q.save

## .update_attributes or .update

    q = Question.find 10
    q.update({ title: 'Updated Title', body: 'Updated body' }) or
    q.update_attribute(:title, 'Updated Title') or
    q.update_attributes(title: 'Updated Title', body: 'Updated body')

# Deleting Records

## .destroy

    q = Question.find 10
    q.destroy

## .delete

    q = Question.find 10
    q.delete

Using .delete skips executing callback methods after_destroy and before_destroy and also skips deleting or nullifying associated records in the :dependant option with associtations. Generally, avoid using ".delete" in favor of ".destroy". There are only few cases when you want to use ".delete".
