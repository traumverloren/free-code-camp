#### Make a Person

Fill in the object constructor with the following methods below:

```getFirstName()
getLastName()
getFullName()
setFirstName(first)
setLastName(last)
setFullName(firstAndLast)
```
Run the tests to see the expected output for each method.

The methods that take an argument must accept only one argument and it has to be a string.

These methods must be the only available means of interacting with the object.

After cleaning up:
```javascript

var Person = function(firstAndLast) {
    let fullName = firstAndLast;

    this.getFirstName = function () { return fullName.split(" ")[0]; };
    this.getLastName = function () { return fullName.split(" ")[1]; };
    this.getFullName = function () { return fullName; };
    this.setFirstName = function (name) {
      fullName = `${name} ${fullName.split(" ")[1]}`;
      return fullName;
    };
    this.setLastName = function (name) {
      fullName = `${fullName.split(" ")[0]} ${name}`;
      return fullName;
    };
    this.setFullName = function (name) {
      fullName = `${name}`;
      return fullName;
    };
};

var bob = new Person('Bob Ross');
bob.getFirstName();

```

First solution:
```javascript

var Person = function(firstAndLast) {
    let firstName = firstAndLast.split(" ")[0];
    let lastName = firstAndLast.split(" ")[1];
    let fullName = `${firstName} ${lastName}`;
    this.getFirstName = function () { return firstName; };
    this.getLastName = function () { return lastName; };
    this.getFullName = function () { return fullName; };
    this.setFirstName = function (first) {
      firstName = first;
      fullName = `${firstName} ${lastName}`;
      return fullName;
    };
    this.setLastName = function (last) {
      lastName = last;
      fullName = `${firstName} ${lastName}`;
      return fullName;
    };
    this.setFullName = function (firstAndLast) {
      firstName = firstAndLast.split(" ")[0];
      lastName = firstAndLast.split(" ")[1];
      fullName = `${firstName} ${lastName}`;
      return fullName;
    };
};

var bob = new Person('Bob Ross');
bob.getFirstName();
```
