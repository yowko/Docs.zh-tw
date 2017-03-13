---
title: "Constant and Literal Data Types (Visual Basic) | Microsoft Docs"
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
  - "declaring constants, literal data types"
  - "data types [Visual Basic], declaring"
  - "constants, declaring"
  - "explicit declarations"
  - "literals, coercing data type"
  - "declarations, data types"
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Constant and Literal Data Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

常值 \(Literal\) 會表示本身的值，而非變數值或運算式的結果，例如號碼 3 或字串 "Hello"。  常數為有意義的名稱，可取代常值並在整個程式中維持相同的值，與可能變更值的變數相反。  
  
 當 [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) 為 `Off`，而 [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) 為 `On` 時，您必須明確宣告所有常數和資料型別。  在下列範例中，`MyByte` 資料型別明確地宣告為 `Byte` 資料型別：  
  
 [!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 當 `Option Infer` 為 `On`，或 `Option Strict` 為 `Off` 時，您可以宣告常數，而不指定具有 `As` 子句的資料型別。  編譯器會從運算式的型別判斷常數的型別。  依預設值，數值整數常值會轉換成 `Integer` 資料型別。  浮點數值 \(Floating\-Point Number\) 的預設資料型別為 `Double`，關鍵字 `True` 和 `False` 則指定 `Boolean` 常數。  
  
## 常值和型別強制  
 在某些情形下，您可能會要將常值強制為特定的資料型別；例如，將特別大的整數常值指派給 `Decimal` 型別的變數。  下列範例會產生錯誤：  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 錯誤的產生是因為常值的表示方式。  `Decimal` 資料型別可以有上述這麼大的值，但是這個常值已隱含地表示為 `Long`，因此就無法這麼做。  
  
 您可以使用兩種方式將常值強制為特定的資料型別：一是附加型別字元，另一則是將它放在封入字元中。  型別字元或封入字元都必須直接放在常值之前和 \(或\) 之後，中間不能有空格或是任何字元。  
  
 若要讓前面的範例可以正常運作，您可以將 `D` 型別字元附加到常值，這可以讓常值表示為 `Decimal`：  
  
 [!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 下列的範例示範型別字元和封入字元的正確用法：  
  
 [!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 下表說明 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中可用的封入字元和型別字元。  
  
||||  
|-|-|-|  
|資料型別|封入字元|附加的型別字元|  
|`Boolean`|\(無\)|\(無\)|  
|`Byte`|\(無\)|\(無\)|  
|`Char`|「|C|  
|`Date`|\#|\(無\)|  
|`Decimal`|\(無\)|D 或 @|  
|`Double`|\(無\)|R 或 \#|  
|`Integer`|\(無\)|I 或 %|  
|`Long`|\(無\)|L 或 &|  
|`Short`|\(無\)|S|  
|`Single`|\(無\)|F 或 \!|  
|`String`|「|\(無\)|  
  
## 請參閱  
 [User\-Defined Constants](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)   
 [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)   
 [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Option Explicit Statement](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)