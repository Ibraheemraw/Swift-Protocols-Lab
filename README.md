
## Protocols Lab

## Instructions for lab submission 

1. Fork the assignment repo
1. Clone your Fork to your machine
1. Complete the lab
1. Push your changes to your Fork
1. Submit a Pull Request back to the assignment repo
1. Paste a link of the pull request on Canvas and submit

<pre> 
Question 1.
Create a Human class with two properties: name of type String, and age of type Int. You'll need to 
create a memberwise initializer for the class. Initialize two Human instances.

Make the Human class adopt the CustomStringConvertible. Print both of your previously initialized
Human objects.

Make the Human class adopt the Equatable protocol. Two instances of Human should be considered equal
if their names and ages are identical to one another. Print the result of a boolean expression 
evaluating whether or not your two previously initialized Human objects are equal to eachother
(using ==). Then print the result of a boolean expression evaluating whether or not your two
previously initialized Human objects are not equal to eachother (using !=).

Make the Human class adopt the Comparable protocol. Sorting should be based on age. Create another
three instances of a Human, then create an array called people of type [Human] with all of the
Human objects that you have initialized. Create a new array called sortedPeople of type [Human] 
that is the people array sorted by age.
</pre> 
"""
class Human: CustomStringConvertible, Equatable, Comparable {
var name: String
var age: Int
var description: String {
return "This person's name is: \(name) and this person age is: \(age)"
}
static func == (lhs: Human, rhs: Human) -> Bool {
return lhs.name == rhs.name && lhs.age == rhs.age
}
static func < (lhs: Human, rhs: Human) -> Bool {
return lhs.age < rhs.age
}
init(name: String, age: Int) {
self.name = name
self.age = age
}
}

//Instances of humas
let ash = Human.init(name: "Ash Ketchum", age: 10)
let naruto = Human.init(name: "Naruto Uzumaki", age: 16)

//comparing humans
if ash == naruto {
print("they are the same")
} else {
print("they are differnt")
}
//comparing the age of the these human
let sortedPeople: [Human] = [ash,naruto].sorted{$0 < $1}
"""

</br> </br> 


<pre> 
Question 2. 
Create a protocol called Vehicle with two requirements: a nonsettable numberOfWheels property of
type Int, and a function called drive().

Define a Car struct that implements the Vehicle protocol. numberOfWheels should return a value of 4,
and drive() should print "Vroom, vroom!" Create an instance of Car, print its number of wheels, 
then call drive().
"""
protocol Vehicle {
var numOfWheels: Int { get }
func drive()
}

struct Car: Vehicle, CustomStringConvertible {

var numOfWheels: Int {
return 4
}

func drive() {
print("Vroom, vroom!")
}
var description: String{
return "This car has \(numOfWheels) and when you turn on the engine it goes \(drive())"
}


}

let speedRacerCar = Car.init()
print(speedRacerCar)

"""
Define a Bike struct that implements the Vehicle protocol. numberOfWheels should return a value of 2,
and drive() should print "Begin pedaling!". Create an instance of Bike, print its number of wheels,
then call drive().
</pre>  
"""
struct Bike: Vehicle, CustomStringConvertible {

var numOfWheels: Int {
return 2
}
var description: String {
return "This bike has \(numOfWheels)"
}

func drive() {
print("Begin pedaling!")
}


}

//instance
let dirtBike = Bike.init()
print(dirtBike)
dirtBike.drive()

"""
</br> </br> 

<pre> 
Question 3. 
// Given the below two protocols, create a struct for penguin(a flightless bird) and an eagle.
Give your structs some properties and have them conform to the appropriate protocols.

protocol Bird {
 var name: String { get }
 var canFly: Bool { get }
}

protocol Flyable {
 var airspeedVelocity: Double { get }
}
</pre> 
"""
protocol Bird {
var name: String { get }
var canFly: Bool { get }
}

protocol Flyable {
var airspeedVelocity: Double { get }
}

struct Penguin: Bird, CustomStringConvertible {

var name: String {
return "Emperor penguin"
}

var canFly: Bool {
return false
}
var description: String {
return "The name of this bird is \(name): Can this bird fly? \(canFly)"
}


}

struct Egale: Bird, Flyable, CustomStringConvertible {

var name: String {
return "Golden eagle"
}

var canFly: Bool {
return true
}

var airspeedVelocity: Double {
return 200.0
}
var description: String {
return "This bird called: \(name): Are they able to fly? \(canFly). They have a air speed velocity of \(airspeedVelocity)mph"
}


}
//Instances
let empPenguin = Penguin.init()
print(empPenguin)

let goldenEgale = Egale.init()
print(goldenEgale)
"""
</br> </br> 

<pre>
Question 4. 
// Create a protocol called Transformation

// create a mutating method called transform

// Make an enum called SuperHero (have it conform to Transformation) and an instance of it named
bruceBanner. Make it so that when the transform function is called that bruceBanner turns from 
.notHulk to .hulk.

enum SuperHero: Transformation {
    // write code here.
}

Example Output: 
var bruceBanner = SuperHero.notHulk

bruceBanner.transform() . // hulk

bruceBanner.transform()  // notHulk
</pre> 
"""
protocol Transformation {

mutating func transform()
}
enum SuperHero: String, Transformation {

case peterParker
case spiderMan
case bruceBanner
case hulk

mutating func transform() {
switch self {
case .peterParker: self =  .spiderMan
print("Not Spider-Man")//"Not Spider-Man"
case .spiderMan: self = .peterParker
print("Friendly Neighborhood Spider Man")//"Friendly Neighborhood Spider Man"
case .bruceBanner: self = .hulk
print("HULLLLLLLKKKKKKKKK SMAAAAAAAAASHHHHHHHHHHHHHHH!")
case .hulk: self = .bruceBanner
print("I am back to my normal self. I hope he didn't hurt anyone")
}
}
}

var peterByStanLee = SuperHero.peterParker

peterByStanLee.transform()
peterByStanLee.transform()

var bruceByStanLee = SuperHero.bruceBanner
bruceByStanLee.transform()
bruceByStanLee.transform()


protocol communication {

}

"""
</br> </br> 

<pre>
Question 5. 
// 1. Create a protocol called Communication

// 2. Give it a property called talk, of type String, and assign it an explicit getter.

// 3. Create three Classes. Cow, Dog, Cat.

// 4. Have your three classes conform to Communication

// 5. talk should return a unique message for each animal when talk is called.

// 6. Put an instance of each of your Classes in an array.

// 7. Iterate over the array and have them print talk.
</pre> 

"""
protocol Communication {
var talk: String {get}


}

class Dog: Communication{
var talk: String {
return "The Dog goes: Woof!"
}


}
class Cow: Communication{
var talk: String {
return "The Cow goes: Moo!"
}


}
class Cat: Communication{
var talk: String {
return "The Cat goes: Meow!"
}


}


let houseCat = Cat.init()
let gaurdDog = Dog.init()
let farmCow = Cow.init()

let animals: [Communication] = [houseCat,gaurdDog,farmCow]

for animal in animals {
print(animal.talk)
}
"""
