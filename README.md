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


UiKit Vs SwiftUI Code Example :
————————————————

This is a simple application that just takes the name inputted by a user and adds this name to a label. 

We only have two cells in this example. The first cell contains the text field that the user will use in order to input their name. The second cell contains the label which will be updated every time the text field is updated.
We have to first tell the text field at line 18, “hey, call the method ‘textFieldDidChange’ when the value of the text field has changed.” Secondly, in the ‘textFieldDidChange’ method we grab the state or value of the text field and update the text inside of our label.

import UIKit

class ViewController: UITableViewController {
  var textLabel: UILabel?
  
  lazy var textField: UITextField! = { [unowned self] in
    let textField = UITextField()
    textField.translatesAutoresizingMaskIntoConstraints = false
    textField.placeholder = "Enter your name"
    textField.addTarget(self, action: #selector(textFieldDidChange), for: .editingChanged)
    return textField
  }()
  
  @objc func textFieldDidChange(_ textField: UITextField) {
    guard let newText = textField.text else {
      return
    }
    textLabel?.text = "Your name is \(newText)"
  }
  
  override func viewDidLoad() {
    super.viewDidLoad()
    tableView.register(UITableViewCell.self, forCellReuseIdentifier: "TextFieldCell")
    tableView.register(UITableViewCell.self, forCellReuseIdentifier: "LabelCell")
  }

  override func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
    return 2
  }
  
  override func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
    let cell: UITableViewCell
    if indexPath.row == 0 {
      cell = tableView.dequeueReusableCell(withIdentifier: "TextFieldCell", for: indexPath)
      cell.contentView.addSubview(textField)
      setConstraint(in: cell)
    }else{
      cell = tableView.dequeueReusableCell(withIdentifier: "LabelCell", for: indexPath)
      textLabel = cell.textLabel
      textLabel?.text = "Your name is \("")"
    }
    return cell
  }
  
  private func setConstraint(in cell: UITableViewCell){
    textField.leadingAnchor.constraint(equalTo: cell.leadingAnchor, constant: 16).isActive = true
    textField.topAnchor.constraint(equalTo: cell.topAnchor).isActive = true
    textField.trailingAnchor.constraint(equalTo: cell.trailingAnchor, constant: -16).isActive = true
    textField.bottomAnchor.constraint(equalTo: cell.bottomAnchor).isActive = true
  }

}

———————————————————

In this example, we see the @State attribute at line 2. This tells swift that it needs to update the name property. Line 6 lets swift know you are updating this variable with this text field, but also you are displaying the data in this variable. Therefore, when the text field is updated so is our state variable. This is called a two-way binding. That is, we are using the state variable to display the data but swift is also updating the state of the variable when it needs too. Lastly, in line 7, we bind our state variable to the text label. Notice how there is no dollar sign because we are only reading the variable in this line. There is no way to update it!

struct ContentView: View {
    @State private var name = ""

    var body: some View {
        Form {
            TextField("Enter your name", text: $name)
            Text("Your name is \(name)")
        }
    }
}

——————————————————————
