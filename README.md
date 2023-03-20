# Dynamic Array Function Blocks for TwinCAT

This repository contains function blocks for implementing dynamic arrays in TwinCAT PLC projects. The dynamic arrays are indexable and while loops are not necessary. They support all data types and are type-safe with some effort. The blocks use Beckhoff's FB_JsonDomParser. FB_JsonDomParser was slightly faster than FB_JsonDynDomParser in most tests, but the difference was minimal. All function blocks were tested without problems. The router memory remains constant, as does the time required to access an index. Nevertheless, it should be noted that this is ONLY a CONCEPT and should not be adopted without further ado.

The dynamic arrays in this repository include:

- FB_DynamicArrayBase64: A dynamic array using Base64 encoding, with 40x longer read times and 86x longer write times compared to a standard array.
- FB_DynamicArrayBinary: A dynamic array using HexBinary encoding, with 15.5x longer read times and 75x longer write times compared to a standard array.
- FB_DynamicArrayOfLReal: A dynamic array using direct LREAL coding as a string, with 7.8x longer read times and 9.5x longer write times compared to a standard array.  There is a possibility of information loss in this case.
- FB_DynamicArrayOfLint

## Usage

To use the dynamic array Function Blocks, you'll need to include the relevant blocks in your TwinCAT project and create instances of them. Here's an example of how to create and use an instance of `FB_DynamicArrayBase64`:

1. Declare an instance of `FB_DynamicArrayBase64`:

```pascal
VAR
  myDynamicArray: FB_DynamicArrayBase64;
END_VAR
```

2. Add an element to the array:
```pascal
myDynamicArray.AddLast(10.5);
```
3. Remove the last element from the array:
```pascal
myDynamicArray.RemoveLast();
```
4. Access an element at a specific index:
```pascal
VAR
  myValue: LREAL;
END_VAR
```
myDynamicArray.TryGetIndex(1, myValue);

Similarly, you can create and use instances of FB_DynamicArrayBinary and FB_DynamicArrayOfLREAL
