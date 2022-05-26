

![Schema for voting app](/assets/schema.jpg)

- Person
  * name

- Referenda
  * title
  - has_many :questions
  - has_many :votes
  - has_many :people, through :votes

- Vote
  - belongs_to :person
  - belongs_to :referenda
  - has_many :answers

- Answer
  * value
  - belongs_to :question
  - belongs_to :vote

- Question
  * body
  - belongs_to :referenda
  - has_many :answers
