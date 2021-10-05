# 100DaysOfSwiftUI

Swift Ui Day 01
———————————
SwiftUI:
—————
SwiftUI is a user interface toolkit that lets us design apps in a “declarative” way.
Behind SwiftUI lies Swift itself

What is declarative programming ?
————————————————-
A style of building the structure and elements of computer programs — that expresses the logic of a computation without describing its control flow.
we can tell our applications what it should do and look like in different states and let itself handle moving in between those states.

It is important to know that SwiftUI does not replace UIKit. Instead, it is built on top of providing and an additional layer of abstractions for us.
A major advantage of using SwiftUI is allowing for cross-platform development for the  Apple Watch, Apple TV, MacBook Pro, and iPhone.

Let us say we tell SwiftUI to show a welcome message when we are logged in and to show a login button when we are logged out. Therefore, since we already told SwiftUI what to show, when we change the authentication state it will show the appropriate view without any more work from us.
To explain further, we are not telling the components of a declarative UI when they should show or hide, we just tell them all the rules we want them to follow and it worries about following them. 

UIKit:
————
UIKit use a programming paradigm that is known as “imperative programming”

What is imperative	programming ?
————————————————-
imperative programming is a programming paradigm that uses statements that change a program’s state.

let us say we might have a function or set of instructions to be called when a button is clicked.
The problems that come when using imperative UI frameworks are normally associated with the state of values we store in our code.

For example, a simple light switch can have two states, on or off. What if we have two light switches and each of the combinations cause different actions depending on their state. That is four different combinations. What if we now have three, four, or five switches? It can get complex quickly as we see.
