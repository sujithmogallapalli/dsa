# Strings

## Character.isDigit(char)
- Checks if character is a digit
- Safer & readable than manual comparison

## Character.isLetterOrDigit()
- Checks if character is a letter or digit

## Character.toLowerCase()
- Converts a character to lower case

## str.startsWith()
- Checks if the passed string is starts with str.

## str.codePointCount(0, str.length()) 
- To find string length with unicode characters

## str.codePoints()
- If String contains Unicode chars like emojis it will be useful to traverse.
- Returns int array
---------------------------------------------------------------------
# Mathematical

## Math.abs()
- ease of use for negative values
---------------------------------------------------------------------
# Exceptions

## NumberFormatException
- Occurs while converting an integer if it exceeds MAX or MIN values
---------------------------------------------------------------------
# Arrays

## Arrays.copyOfRange()
- Arrays.copyOfRange(arr, leftIndex, rightIndex);

## Arrays.toString(intArray)
- To convert an array to string
---------------------------------------------------------------------
# Collections

## getOrDefault(num, defaultValue)
- Useful for hashing

## Map iteration using stream
- hashes.entrySet().stream()
  .filter(ele -> ele.getValue() == 1)
  .findFirst()
  .get()
  .getKey()

## map.putIfAbsent(key, new ArrayList<>()) 
- useful while working with hashing of array of arrays

## new ArrayList<>(map.values()) 
- to convert Collection<List<String>> to List<List<String>>