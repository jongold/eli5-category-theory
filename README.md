# ELI5 Category Theory

this stuff is made out to be complicated. it's not.

## Setoid
Has `equals`.
```js
Box(2).equals(Box(2)) // true
Box(2).equals(Box(3)) // false
```

## Semigroup
Has `concat`
```js
[1,2,3].concat([4,5,6]) // [1,2,3,4,5,6]
Add(5).concat(Add(10)) // Add(15)
Times(10).concat(Times(15)) // Times(150)
```

## Monoid
Has `empty`. this makes sense when you consider concatting it.
```js
List.empty ~= [ ]
[1,2,3]).concat([]) // [1,2,3]

Add.empty() // Add(0)
Add(5).concat(Add.empty()) // Add(5)

Times.empty() // Times(1)
Times(10).concat(Times.empty()) // Times(10)
```

## Functor
Has `map`
```js
[1,2,3].map(x => x + 1) // [2,3,4]

Right(5).map(x => x + 1) // Right(6)
Left('error').map(x => x + 1) // Left('error')
```

## Monad
Has `chain` (~= flatMap)
```js
Box(5).map(x => Box(x)) // Box(Box(5))
// chain 'unwraps' it
Box(5).chain(x => Box(x)) // Box(5)

readFile('foo.txt')
.map(contents => contents.toUpperCase())
.chain(contents => writeFile('bar.txt', contents))
```
