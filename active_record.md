# Active Record

### Fetch All Questions

    questions = Question.all

- this will give us back the list of questions as an object
- the object behaves like an array so you can call methods on it like (.each) and you
- can also chain it with other methods to do other types of operations and queries

### Creating A New Question

## To create a new question object in memory do:

    q = Question.new

#### you can also pass in a hash to the new method as in:

    q = Question.new({ title: 'To be or not to be', body: 'is that a question?', view_count: 0 })

#### or for short:

    q = Question.new title: 'To be or not to be', body: 'is that a question?', view_count: 0
