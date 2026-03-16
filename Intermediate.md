Random Notes (Also worth looking up regarding numbers and floating point numbers is IEEE 754)

The output of "console.log([] + [])" is an empty string. JavaScript converts arrays and objects to strings when adding them. Arrays converted to strings, along with the contents inside. "+" is used to add two numbers, or combine two strings. With arrays and objects, they are converted to strings in this instance. So "[].toString()" is "" and "{}.toString" is "[object Object]". The contents of the object do not affect the output, but the contents of the array become strings too, so "[1,2] + [3,4]" becomes "[1,2].toString" which is "1,2", then becomes "1,2" + "3,4" which is "1,23,4". This is the same for string values in arrays as well.

So "[] + {}" without "console.log()" is still "[object Object]", however, "{} + []" without "console.log()" is 0.

"Console.log([] == false)" returns TRUE because in boolean conversions, FALSE is converted to 0. The empty array is converted to a string, "", then "" is converted to a number, 0.

"NaN" means Not a Number, and is not equal to anything including itself. So "NaN == NaN" and "NaN === NaN" are both FALSE. To check for NaN values, use "console.log(Number.isNaN(myNum))".

Adding decimals is tricky in JavaScript. "0.1 + 0.2" does not equal "0.3". Some decimal math equals what it should, such as "0.1 + 0.3 === 0.4", is TRUE. To math decimals, you can convert to a whole number first "0.1 * 10 + 0.2 * 10"

"[] == ![]" equals TRUE. The "!" is evaluated first, which makes "![]" equal FALSE. Then the array and FALSE are converted to FALSE, then to 0, which equals "0 == 0" which is TRUE.

Now "[] == []" and "{} == {}" are both false because an important rule, "Objects are compared by reference, not value". And these two statements reference different arrays / objects. This is the same when comparing them using ===.

So the reasons for "[] == ![]" being TRUE and "[] == []" being FALSE are different because the first comparison with "!" performs type coercion, whereas the second does not. Type coercion only occurs when the types are different, and in the first one "![]" becomes "false", and therefore the comparison is "[] == false", and type coercion occurs. This same conversion occurs with "let a = []; let b = [];" and doing "a == !b" (TRUE) and "a == b" (FALSE).

All objects are truethy, which explains the previous "![]" as well as why "Boolean([])" and "Boolean({})" both return TRUE.

Another special case built into JavaScript is "null == undefined". JavaScript has a special rule stating "null is loosely equal to undefined", meaning "null == undefined" returns TRUE. Null is of type "null" and undefined is type "undefined", so comparing these two with === is FALSE.

"typeof NaN" is number, even though NaN represents a value that is Not a Number. Special values like this, and Infinity and -Infinity are NaN, but still considered numbers in JavaScript.

All non-empty strings are truthy, so "Boolean('asdf')" is TRUE.

More type coercion occurs with "'false' == FALSE". 'false' becomes NaN because JavaScript converts the string to a number using Number('false'), so anything compared to NaN is false. But also FALSE becomes 0 due to type coercion. So the final comparison becomes "NaN == 0", which is FALSE.
