---
title: "Implicit and Explicit Conversions (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "conversions, type"
  - "variables [Visual Basic], changing data type"
  - "casting"
  - "conversions, data type"
  - "type conversion, implicit conversions"
  - "CType function, conversions"
  - "casting, data types"
  - "data type conversion, explicit"
  - "type conversion, explicit conversions"
  - "data types [Visual Basic], casting"
  - "conversions, implicit"
  - "explicit data type conversions"
  - "conversions"
  - "changing data types"
  - "conversions, explicit"
  - "data type conversion, implicit"
  - "implicit data type conversions"
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 25
---
# Implicit and Explicit Conversions (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

「*隱含轉換*」\(Implicit Conversion\) 在原始程式碼中不需要任何特殊語法。  在下列範例中，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 在將 `k` 指派給 `q` 之前，會將其值隱含轉換為單精確度浮點數。  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 「*明確轉換*」\(Explicit Conversion\) 會利用型別轉換關鍵字。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 提供數種這類關鍵字，會將括號中的運算式強制轉型為所要的資料型別。  這些關鍵字的用法就像函式一樣，但編譯器會以內嵌 \(Inline\) 的方式產生程式碼，因此要比執行函式呼叫來得稍快些。  
  
 以下是先前範例的擴充部分，其中 `CInt` 關鍵字會先將 `q` 的值轉換回整數，才會指派給 `k`。  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## 轉換關鍵字  
 下列資料表將說明可用的轉換關鍵字。  
  
||||  
|-|-|-|  
|型別轉換關鍵字|將運算式轉換為資料型別|轉換運算式可用的資料型別|  
|`CBool`|[Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|任何的數字型別 \(包括 `Byte`、`SByte` 和列舉型別\)、`String`、`Object`|  
|`CByte`|[Byte Data Type](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|任何的數字型別 \(包括 `SByte` 和列舉型別\)、`Boolean`、`String`、`Object`|  
|`CChar`|[Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`String`, `Object`|  
|`CDate`|[Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md)|`String`, `Object`|  
|`CDbl`|[Double Data Type](../../../../visual-basic/language-reference/data-types/double-data-type.md)|任何的數字型別 \(包括 `Byte`、`SByte` 和列舉型別\)、`Boolean`、`String`、`Object`|  
|`CDec`|[Decimal Data Type](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|任何的數字型別 \(包括 `Byte`、`SByte` 和列舉型別\)、`Boolean`、`String`、`Object`|  
|`CInt`|[Integer Data Type](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|任何的數字型別 \(包括 `Byte`、`SByte` 和列舉型別\)、`Boolean`、`String`、`Object`|  
|`CLng`|[Long Data Type](../../../../visual-basic/language-reference/data-types/long-data-type.md)|任何的數字型別 \(包括 `Byte`、`SByte` 和列舉型別\)、`Boolean`、`String`、`Object`|  
|`CObj`|[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)|任何型別|  
|`CSByte`|[SByte Data Type](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|任何的數字型別 \(包括 `Byte` 和列舉型別\)、`Boolean`、`String`、`Object`|  
|`CShort`|[Short Data Type](../../../../visual-basic/language-reference/data-types/short-data-type.md)|任何的數字型別 \(包括 `Byte`、`SByte` 和列舉型別\)、`Boolean`、`String`、`Object`|  
|`CSng`|[Single Data Type](../../../../visual-basic/language-reference/data-types/single-data-type.md)|任何的數字型別 \(包括 `Byte`、`SByte` 和列舉型別\)、`Boolean`、`String`、`Object`|  
|`CStr`|[String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md)|任何的數字型別 \(包括 `Byte`、`SByte` 和列舉型別\)、`Boolean`、`Char`、`Char` 陣列、`Date`、`Object`|  
|`CType`|跟在逗號 \(`,`\) 後的指定型別|當轉換為「*基礎資料型別*」\(Elementary Data Type\) \(包括基礎型別的陣列\) 時，和對應轉換關鍵字可用的型別相同<br /><br /> 當轉換為「*複合資料型別*」\(Composite Data Type\) 時，則它實作的介面和繼承而來的類別皆可用<br /><br /> 當轉換為您多載 `CType` 的類別或結構時，可用該類別或結構|  
|`CUInt`|[UInteger Data Type](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|任何的數字型別 \(包括 `Byte`、`SByte` 和列舉型別\)、`Boolean`、`String`、`Object`|  
|`CULng`|[ULong Data Type](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|任何的數字型別 \(包括 `Byte`、`SByte` 和列舉型別\)、`Boolean`、`String`、`Object`|  
|`CUShort`|[UShort Data Type](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|任何的數字型別 \(包括 `Byte`、`SByte` 和列舉型別\)、`Boolean`、`String`、`Object`|  
  
## CType 函式  
 [CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)會操作兩個引數。  首先是要轉換的運算式，接著是目的資料型別或物件類別。  請注意，第一個引數必須是運算式，而非型別。  
  
 `CType` 是「*內嵌函式*」\(Inline Function\)，這代表編譯的程式碼會進行轉換，而通常不會產生函式呼叫。  這會增加效能。  
  
 如需 `CType` 與其他型別轉換關鍵字的比較，請參閱 [DirectCast Operator](../../../../visual-basic/language-reference/operators/directcast-operator.md) 和 [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md)。  
  
### 基礎型別  
 以下範例將說明 `CType` 的用法。  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### 複合型別  
 您可以使用 `CType` 來將值轉換為複合資料型別以及基本型別。  您也可以使用它來將物件類別強制轉型為其介面中的一種型別，如以下範例所示。  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### 陣列型別  
 `CType` 也可以轉換陣列資料型別，如以下範例所示。  
  
```  
Dim v() As classV  
Dim obArray() As Object  
' Assume some object array has been assigned to obArray.  
' Check for run-time type compatibility.  
If TypeOf obArray Is classV()  
    ' obArray can be converted to classV.  
    v = CType(obArray, classV())  
End If  
```  
  
 如需詳細資訊和範例，請參閱[Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)。  
  
### 型別定義 CType  
 您可以在已經定義的類別或結構上定義 `CType`。  這樣可以讓您對類別或結構的型別值進行來回轉換。  如需詳細資訊和範例，請參閱 [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。  
  
> [!NOTE]
>  使用轉換關鍵字的值必須對目的資料型別來說是有效的，否則會發生錯誤。  例如，若您嘗試要將 `Long` 轉換為 `Integer`，`Long` 的值必須在 `Integer` 資料型別的有效範圍內。  
  
> [!CAUTION]
>  如果來源型別並非衍生自目的型別，指定 `CType` 從某一類別型別轉換成另一個型別會於執行階段失敗。  這類的失敗會擲回 <xref:System.InvalidCastException> 例外狀況。  
  
 然而，如果其中一個型別是已經定義的結構或類別，而且您已經在該結構或類別上定義 `CType`，則當轉換滿足 `CType` 的需求時，便會成功執行。  請參閱 [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。  
  
 執行明確轉換也可視為是將運算式「*轉型*」\(Casting\) 為指定的資料型別或物件類別。  
  
## 請參閱  
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Conversions Between Strings and Other Types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [How to: Convert an Object to Another Type in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)