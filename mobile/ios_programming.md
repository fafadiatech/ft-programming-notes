# Notes on iOS Programming {with Swift}

## Hide Keyboard {when touching outside text field}:

1. Implement UITextFieldDelegate
2. For text field specify current ViewController as delegate `self.txtInput.delegate = self`
3. Override `func touchesBegan` to have following lines `self.view.endEditing(true)`
4. If you want to hide the keyboard when "Return" is hit on the keyboard implement "textFieldShouldReturn" with "txtInput.resignFirstResponder()" and "retutn (true)"

## Peform Segue {Prounounced Seg-way}


