---
title: "Widening and Narrowing Conversions (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "widening conversions"
  - "narrowing conversions"
  - "conversions, type"
  - "data types [Visual Basic], changing"
  - "variables [Visual Basic], changing data type"
  - "conversions, exceptions during conversion"
  - "type conversion, exceptions during conversion"
  - "conversions, data type"
  - "conversions, narrowing"
  - "type conversion, narrowing"
  - "data type conversion, widening"
  - "data type conversion, narrowing"
  - "changing data types"
  - "type conversion, widening"
  - "data type conversion, exceptions during conversion"
  - "conversions, widening"
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Widening and Narrowing Conversions (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

型別轉換必須考慮轉換結果是否在目的資料型別範圍之內。  
  
 A *擴展轉換*的值變更成可以允許對原始資料的任意可能數值的資料型別。  「擴展轉換」\(Widening Conversion\) 會保留原始值，但可能會變更其表示方法。  若要將轉換為一個整數類資料型別，這是`Decimal`，或從`Char`到`String`。  
  
 「*縮小轉換*」\(Narrowing Conversion\) 會變更資料型別的值，而此資料型別可能無法存放一些可能值。  例如，分數的值會捨入則會轉換為整數型別，以及數字型別轉換成`Boolean` ，會降低到其中一個`True`或`False`。  
  
## 擴展轉換  
 下列資料表將說明標準的擴展轉換。  
  
|||  
|-|-|  
|資料型別|擴展為資料型別 <sup>1</sup>|  
|[SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Short](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double` <sup>2</sup>|  
|[Long](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double` <sup>2</sup>|  
|[ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double` <sup>2</sup>|  
|[Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double` <sup>2</sup>|  
|[Single](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|任何列舉型別 \([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)\)|其基礎整數類資料型別和任何的基礎型別擴大後的型別。|  
|[Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|`Char` 陣列|`Char` 陣列，`String`|  
|任何型別|[物件](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|所有的衍生型別 \(Derived Type\)|任何基底型別衍生來源 <sup>3</sup>。|  
|任何型別|它會實作任何介面。|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|任何的資料型別或物件型別而定。|  
  
 <sup>1</sup> 依定義，每個資料型別都會擴展至本身。  
  
 <sup>2</sup> 從 `Integer`、`UInteger`、`Long`、`ULong` 或 `Decimal` 轉換成 `Single` 或 `Double`，可能會導致精確度喪失，但決不會喪失其大小範圍。  因此這些轉換並不會使資料遺漏。  
  
 <sup>3</sup> 由衍生型別擴展轉換成其中一種基底型別，可能會讓人覺得意外。  原因是衍生型別包含有基底型別的所有成員，因此成為基底型別的執行個體。  反過來說，基底型別並不包含衍生型別所定義的成員。  
  
 在執行階段中進行的擴展轉換一定會成功，且決不會造成資料遺漏。  無論 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) 設定型別檢查 \(Type Checking\) 為 `On` 或 `Off`，您都可以執行隱含式擴展轉換。  
  
## 縮小轉換  
 標準的縮小轉換包括：  
  
-   上述表格中擴展轉換的反向轉換 \(不包括任何擴展至本身的型別\)  
  
-   [布林值 \(Boolean\)](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) 與任何數字型別 \(Numeric Type\) 之間的雙向轉換  
  
-   從任何數字型別轉換為任何列舉型別 \(`Enum`\)  
  
-   [字串](../../../../visual-basic/language-reference/data-types/string-data-type.md)與任何數字型別、`Boolean` 或[日期](../../../../visual-basic/language-reference/data-types/date-data-type.md)之間的雙向轉換  
  
-   從資料型別或物件型別轉換為從其衍生的型別  
  
 在執行階段中進行的縮小轉換不一定會成功，可能會失敗並造成資料遺漏。  若目的資料型別無法接受轉換的值，就會發生錯誤。  例如，數字轉換可能會導致溢位 \(Overflow\)。  除非 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) 設定型別檢查為 `Off`，否則編譯器 \(Compiler\) 不會允許您執行隱含式縮小轉換。  
  
> [!NOTE]
>  從 `For Each…Next` 集合中的項目轉換至迴圈控制變數時，會隱藏縮小轉換錯誤。  如需詳細資訊和範例，請參閱 [For Each...Next 陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) 中的＜縮小轉換＞一節。  
  
### 何時使用縮小轉換  
 當您知道將來源值轉換為目的資料型別時，不會產生錯誤或造成資料遺漏，就可以使用縮小轉換。  比方說，如果您有`String`您會知道包含"True"False"，您可以使用`CBool`關鍵字\] 以將它轉換成`Boolean`。  
  
## 轉換時的例外狀況  
 因為擴展轉換一定會成功，所以不會有例外狀況。  當縮小轉換失敗時，最可能擲回下列例外狀況：  
  
-   <xref:System.InvalidCastException> \- 如果兩個型別之間未定義轉換方式  
  
-   <xref:System.OverflowException> \- \(僅限整數型別\) 如果轉換值對目標型別 \(Target Type\) 來說太大  
  
 如果類別或結構定義 [CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)為來源或目標轉換運算子，`CType` 可能會擲回任何其認為適當的例外狀況。  此外，`CType` 可能會呼叫 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 函式或 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] 方法，並因此擲回各類例外狀況。  
  
## 參考型別轉換期間的變更  
 從「*參考型別*」\(Reference Type\) 進行的轉換只會複製值的指標。  在任何情況下都不會複製或變更值本身。  唯一會變更的就是存放指標的變數的資料型別。  在以下範例中，資料型別從衍生類別轉換為其基底類別，但轉換後兩變數所指向的物件並未變更。  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## 請參閱  
 [資料類型](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Conversions Between Strings and Other Types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [How to: Convert an Object to Another Type in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)