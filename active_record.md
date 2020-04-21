# Active Record

### Fetch All Questions

    questions = Question.all

- this will give us back the list of questions as an object
- the object behaves like an array so you can call methods on it like (.each) and you
- can also chain it with other methods to do other types of operations and queries

### Creating A New Question

## To Create a New Question Object in Memory do:

    q = Question.new

#### you can also pass in a hash to the new method as in:

    q = Question.new({ title: 'To be or not to be', body: 'is that a question?', view_count: 0 })

#### or for short:

    q = Question.new title: 'To be or not to be', body: 'is that a question?', view_count: 0

## To Save the Above Question into Questions Table:

    # q.save

#### this will save that above question into the questions table (persist it)

## To Create a Record Right Away:

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
