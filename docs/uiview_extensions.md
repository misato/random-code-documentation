Here is a UIView extension to handle layout stuff programatically (fill in superview, center in view, etc)

```swift
//
//  UIView+Layout.swift
//

import UIKit

//
// Funtions related to layout to be used when creating a view programatically
//
extension UIView {
    
    func fillInSuperview() {
        guard let superview = superview else {
            print("This view has no superview. Call `addSubview(view: UIView)` before using this method.")
            return
        }
        
        translatesAutoresizingMaskIntoConstraints = false
        topAnchor.constraint(equalTo: superview.topAnchor).isActive = true
        leadingAnchor.constraint(equalTo: superview.leadingAnchor).isActive = true
        widthAnchor.constraint(equalTo: superview.widthAnchor).isActive = true
        heightAnchor.constraint(equalTo: superview.heightAnchor).isActive = true
        
    }
    
    func centerInSuperview() {
        guard let superview = superview else {
            print("This view has no superview. Call `addSubview(view: UIView)` before using this method.")
            return
        }
        translatesAutoresizingMaskIntoConstraints = false
        centerXAnchor.constraint(equalTo: superview.centerXAnchor).isActive = true
        centerYAnchor.constraint(equalTo: superview.centerYAnchor).isActive = true
        
    }
    
    // Use this in the init of your view so it loads its nib automatically
    // The nib file must be called the same as your View class
    func loadFromNib() {
        guard let view = Bundle.main.loadNibNamed(String(describing: type(of: self)), owner: self, options: nil)?[0] as! UIView? else {
            print("The nib called \(String(describing: type(of: self))) couldn't be loaded.")
            return
        }
        
        addSubview(view)
        view.fillInSuperview()
    }
    
}

```