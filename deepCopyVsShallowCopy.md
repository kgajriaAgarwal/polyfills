Shallow copy vs Deep Copy 👀

🔵 Shallow copy:
➡ A shallow copy of an object copies only the main object but doesn’t copy the inner/nested objects.
➡ A shallow copy is preferable when you want to copy an object that contains only primitives values like string, or number.
➡ If object fields contain another object, only the reference addresses are copied. Hence if you make a change in the nested object of a copied object, the nested object of the original object will also get changed.

Checkout this link for a shallow copy example👇
📍 Using object assign: https://lnkd.in/gQBeArag
📍 Using spread operator: https://lnkd.in/gU-KX-fT

🔵 Deep copy:
➡ A deep copy means that all of the values of the new variable are copied and disconnected from the original variable. 
➡ Hence changes in the copied variable will not affect the original one and vice-versa

Check out this link for a deep copy example👇
📍Using JSON.Parse(JSON.stringify): https://lnkd.in/giZ3mmVm
📍Using structured clone: https://lnkd.in/gBT67T-y