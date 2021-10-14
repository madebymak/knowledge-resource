
# Python Notes

## Insert string variable
```
name = 'Dave'`
print(f'I am "{name}".')
```
<br>

## Import Secret Credentials
```
//config.yml (don't commit to repo)

store1:
	url: url
	login: dave
	password: password
```
```
import config

storeconf = config['store1']
base_url = (f'https://{storeconf['login']}:{storeconf['password']}@{storeconf['url']})
```
<br>

## Pass Statement
- the pass statement is a null statement
- pass is not ignored
- nothing happens when the pass is executed

<br>

```
Class Example:
	pass
```
```
def function(args):
    pass
```
<br>

##  Non-keyword *args Variables
-  used to pass a variable number of arguments (non-keyworded) to a function
<br>

```
>>> args = ("two", 3, 5)
>>> test_args_kwargs(*args)

arg1: two
arg2: 3
arg3: 5
```
<br>

## Keyworded **kwargs Variables
- used to pass a keyworded, variable-length argument list

```
>>> kwargs = {"arg3": 3, "arg2": "two","arg1":5}
>>> test_args_kwargs(**kwargs)

arg1: 5
arg2: two
arg3: 3
```
<br>

## List Comprehensions
`doubled_numbers = [n * 2 for n in numbers]` is equal to:

```
doubled_numbers = []
for n in numbers:
    doubled_numbers.append(n * 2)
```
<br>

- can also use list comprehension to get values from a class

example:
```
{k:v for k, v in <class>.__dict__.items() if not (k.startswith('__')
                                                             and k.endswith('__'))}
```
<br>

## Empty MyPy cache
```
cd server/
rm -fr .mypy_cache/
cd ..
```
<br>

## Any Syntax Shorthand
- returns true if any of the items are true
```
numbers = [-3,-2,-1,0,1]

// old
has_positives = False
for n in numbers:
	if n > 0:
		has_positive = True
		break

// new
has_positive = any(n > 0 for n in numbers)
```
<br>

## Simplify Sequence Comparison
- no need to check element of a list
- aka truth value testing
```
// instead of this
if len(list_of_items) > 0:
	item_picked = pick_item(list_of_items)

// use this
if list_of_items:
	item_picked = pick_item(list_of_items)
```
<br>
