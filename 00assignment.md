**PLEASE NOTE: Do not publicly post your answers on this Gist, please forward them to your recruiting contact instead ;-)**

### 1. Voting

Each voter can vote in zero or more referenda. Each referendum has one or more questions, and each question is a yes/no vote. Write the simplest normalized schema to describe this in generic SQL statements or as an entity-relationship diagram. Point out where the indexes would be if you want to quickly know the results of a given referendum question, but you never expect to query a single voter's voting record. In what way does the nature of the application affect your design judgment about privacy, and what effect would that have on normalization considerations?

### 2. Rewriting history with git

You've getting ready to submit a pull request to the coolapp repo. You branch contains two commits: M, followed by N. The lineage is this:

```
main:   X --> Y --> Z (HEAD commit is Z)
                     \
your-branch:          M --> N (HEAD commit is N)
```
You want to contribute the code back to the official coolapp repo, but you realize there is a really dumb typo in one of your **source code comments** (not commit messages) in commit M. You'd still like to submit the pull request as two commits M' and N', where M' is the fixed version of M, and N' is the same exact diff as N. How do you rewrite git history to make this happen? Is N' the same hash as N? Why or why not?

### 3. Import taxes

What actually happens when the Python interpreter executes an `import foo` instruction? Talk about good patterns as well as bad (anti-)patterns of using `import`. Use examples and explain what's going on "under the hood" of Python.

### 4. We're All Scratching Our Heads About This One

New code was released to multi-tier production environment and now the site is SO slow. But it worked great on the single-server staging environment, which has only half the CPU and half the RAM of the production servers!

Here's the code that's behaving poorly:
```
for article in session.query(Article)
                      .filter(Article.created_at >= date(date.today().year, 1, 1)):
    authors.add(article.author.name)
```

Here are the relevant model definitions:

```
from sqlalchemy import BigInteger, Column, ForeignKey, String, DateTime
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy.orm import relationship

Base = declarative_base()

class Author(Base):
    __tablename__ = 'authors'
    id = Column(BigInteger, primary_key=True)
    name = Column(String(255), nullable=False)
    def __init__(self, name):
        self.name = name

class Article(Base):
    __tablename__ = 'articles'
    id = Column(BigInteger, primary_key=True)
    title = Column(String(255), nullable=False)
    created_at = Column(DateTime, nullable=False)
    author_id = Column(BigInteger, ForeignKey('authors.id'), nullable=False)
    author = relationship('Author', backref='articles')
    def __init__(self, title, author, created_at):
        self.title = title
        self.author = author
        self.created_at = created_at
```

What's wrong? And why did it work well (enough) on the staging server?

Obviously the person who wrote this isn't a python/SQLAlchemy programmer. How would a python/SQLAlchemy programmer have written the code?

### 5. Unix tools

In one Unix command, find all of the files in `/tmp` whose **contents** contain the word "foobar" (case-insensitive), and list them all in order from most-recently created to least-recently created.

### 6. CSS

Usage of the "!important" CSS declaration is often frowned upon by front-end developers. What does the "!important" CSS declaration do? Why do front-end developers suggest using it with caution? What are some cases in which it makes sense to use it?

### 7. JavaScript

Take a look at the following:

```js
function *foo(x) {
  while (x < 4) {
    x += yield x;
  }
  return x;
}
var bar = foo(3);
console.log( bar.next(1) );
console.log( bar.next(1) );
console.log( bar.next(1) );
```
What is the output of this code snippet, and why does it behave in the way it does?