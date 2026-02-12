## Character.isDigit(char)
- Checks if character is a digit
- Safer & readable than manual comparison

## Math.abs()
- ease of use for negative values

## NumberFormatException
- Occurs while converting an integer if it exceeds MAX or MIN values

## Arrays.copyOfRange()
- Arrays.copyOfRange(arr, leftIndex, rightIndex);

## getOrDefault(num, defaultValue)
- Useful for hashing

## Map iteration using stream
- hashes.entrySet().stream()
  .filter(ele -> ele.getValue() == 1)
  .findFirst()
  .get()
  .getKey()