# Type System

With the focus for quantum algorithm being more towards what should be achieved rather than on a problem representation in terms of data structures, taking a more functional perspective on language design is a natural choice. At the same time, the type system is a powerful mechanism that can be leveraged for program analysis and other compile-time checks that facilitate formulating robust code. 

All in all, the Q# type system is fairly minimalist, in the sense that there isn't an explicit notion of classes or interfaces as one might be used to from classical languages like C# or Java. We also take a somewhat pragmatic approach making incremental progress, such that certain construct are not yet fully integrated into the type system. An example are functors, which can be used within expressions but don't yet have a representation in the type system. Correspondingly, they cannot currently be assigned or passed as arguments, similar as it is the case for type parametrized callables.
We expect to make incremental progress in extending the type system to be more complete, and balance immediate needs with longer-term plans. 

## Available Types

All types in Q# are [immutable](https://github.com/microsoft/qsharp-language/blob/main/Specifications/Language/4_TypeSystem/Immutability.md#immutability). 

Type | Description
---------|----------
 `Unit` | Represents a singleton type whose only value is `()`.
 `Int` | Represents a 64-bit signed integer. [Values](https://github.com/microsoft/qsharp-language/blob/main/Specifications/Language/3_Expressions/ValueLiterals.md#int-literals) range from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.
 `BigInt` | Represents signed integer [values](https://github.com/microsoft/qsharp-language/blob/main/Specifications/Language/3_Expressions/ValueLiterals.md#bigint-literals) of any size.
 `Double` | Represents a double-precision 64-bit floating-point number. [Values](https://github.com/microsoft/qsharp-language/blob/main/Specifications/Language/3_Expressions/ValueLiterals.md#double-literals) range from -1.79769313486232e308 to 1.79769313486232e308 as well as NaN (not a number).
 `Bool` | Represents Boolean [values](https://github.com/microsoft/qsharp-language/blob/main/Specifications/Language/3_Expressions/ValueLiterals.md#bool-literals). Possible values are `true` or `false`.
 `String` | Represents text as [values](https://github.com/microsoft/qsharp-language/blob/main/Specifications/Language/3_Expressions/ValueLiterals.md#string-literals) that consist of a sequence of UTF-16 code units. 
 `Qubit` | Represents an opaque identifier by which virtual quantum memory can be addressed. [Values](https://github.com/microsoft/qsharp-language/blob/main/Specifications/Language/3_Expressions/ValueLiterals.md#qubit-literals) of type `Qubit` are instantiated via allocation.
 `Result` | Represents the result of a projective measurement onto the eigenspaces of a quantum operator with eigenvalues ±1. Possible [values](https://github.com/microsoft/qsharp-language/blob/main/Specifications/Language/3_Expressions/ValueLiterals.md#result-literals) are `Zero` or `One`. 
 `Pauli` | Represents a single-qubit Pauli matrix. Possible [values](https://github.com/microsoft/qsharp-language/blob/main/Specifications/Language/3_Expressions/ValueLiterals.md#pauli-literals) are `PauliI`, `PauliX`, `PauliY`, or `PauliZ`.
 `Range` | Represents an ordered sequence of equally spaced `Int` values. [Values](https://github.com/microsoft/qsharp-language/blob/main/Specifications/Language/3_Expressions/ValueLiterals.md#range-literals) may represent sequences in ascending or descending order.
 Array | Represents [values](https://github.com/microsoft/qsharp-language/blob/main/Specifications/Language/3_Expressions/ValueLiterals.md#array-literals) that each contain a sequence of values of the same type.
 Tuple | Represents [values](https://github.com/microsoft/qsharp-language/blob/main/Specifications/Language/3_Expressions/ValueLiterals.md#tuple-literals) that each contain a fixed number of items of different types. Tuples containing a single element are equivalent to the element they contain.
 User defined type | Represents a [user defined type](https://github.com/microsoft/qsharp-language/blob/main/Specifications/Language/1_ProgramStructure/2_TypeDeclarations.md#type-declarations) consisting of named and anonymous items of different types. [Values](https://github.com/microsoft/qsharp-language/blob/main/Specifications/Language/3_Expressions/ValueLiterals.md#literals-for-user-defined-types) are instantiated by invoking the constructor. 
 Operation | Represents a non-deterministic [callable](https://github.com/microsoft/qsharp-language/blob/main/Specifications/Language/4_TypeSystem/OperationsAndFunctions.md#operations-and-functions) that takes one (possibly tuple-valued) input argument returns one (possibly tuple-valued) output. Calls to operation [values](https://github.com/microsoft/qsharp-language/blob/main/Specifications/Language/3_Expressions/ValueLiterals.md#operation-literals) may have side effects and the output may vary for each call even when invoked with the same argument.
 Function | Represents a deterministic [callable](https://github.com/microsoft/qsharp-language/blob/main/Specifications/Language/4_TypeSystem/OperationsAndFunctions.md#operations-and-functions) that takes one (possibly tuple-valued) input argument returns one (possibly tuple-valued) output. Calls to function [values](https://github.com/microsoft/qsharp-language/blob/main/Specifications/Language/3_Expressions/ValueLiterals.md#function-literals) do not have side effects and the output is will always be the same given the same input. 


← [Back to Index](https://github.com/microsoft/qsharp-language/tree/main/Specifications/Language#index)