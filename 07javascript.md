{value: 3, done: false}
{value: 4, done: true}
{value: undefined, done: true}

It works that way because what is being defined is an iterator. The next method allows to find the next element of the iterator. The error occurs when the next value of the iterator does not exist.