---
title: "實值類型 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "cs.valuetypes"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 語言, 實值類型"
  - "類型 [C#], 實值類型"
  - "實值類型 [C#]"
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# 實值類型 (C# 參考)
實值型別包含兩個主要分類：  
  
-   [Structs](../../../csharp/language-reference/keywords/struct.md)  
  
-   [列舉](../../../csharp/language-reference/keywords/enum.md)  
  
 結構是在這些分類之內：  
  
-   數字型別 \(Numeric Type\)  
  
    -   [整數類資料型別](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [浮點型別](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
    -   [decimal](../../../csharp/language-reference/keywords/decimal.md)  
  
-   [bool](../../../csharp/language-reference/keywords/bool.md)  
  
-   使用者定義結構。  
  
## 實值型別的主要功能  
 直接以實值型別為基礎的變數，可包含值。  指派一個實值型別變數給其他實值型別變數，會複製所包含的值。  這和參考型別變數的指派不同，參考型別變數的指派會複製物件的參考，但不會複製物件本身。  
  
 所有實值型別都是自 <xref:System.ValueType?displayProperty=fullName> 隱含衍生而來。  
  
 不同於參考型別，您無法從實值型別衍生新型別。  然而，就像參考型別，結構可以實作介面。  
  
 不同於參考型別，實值型別不可包含 `null` 值。  不過， [可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md) 功能允許實值型別指派給 `null`。  
  
 每個實值型別都有隱含預設建構函式 \(Constructor\)，來初始化此種型別的預設值。  如需實值型別預設值的詳細資訊，請參閱[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)。  
  
## 簡單型別的主要功能  
 所有的簡單型別 \(是 C\# 語言所不可缺少的\) 都是 .NET Framework System 型別的別名。  例如，[int](../../../csharp/language-reference/keywords/int.md) 是 <xref:System.Int32?displayProperty=fullName> 的別名。  如需別名的完整清單，請參閱[內建類型資料表](../../../csharp/language-reference/keywords/built-in-types-table.md)。  
  
 運算元皆為簡單型別常數的常數運算式會在編譯 \(Compilation\) 時期評估。  
  
 簡單型別可以使用常值來初始化。  例如，'A' 是 `char` 型別的常值，而 2001 是 `int` 型別的常值。  
  
## 初始化實值型別  
 在 C\# 中，區域變數必須初始化之後才能使用。  例如，您可能沒有初始設定而宣告區域變數，如下列範例所示：  
  
```  
int myInt;  
```  
  
 在初始化之前您不能使用它。  您可以使用下列陳述式將其初始化：  
  
```  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 這個陳述等同於下列陳述式：  
  
```  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 當然，您可以在同一個陳述式裡宣告和初始化，如下列範例所示：  
  
```  
int myInt = new int();  
```  
  
 \- 或 \-  
  
```  
int myInt = 0;  
```  
  
 使用 [new](../../../csharp/language-reference/keywords/new.md) 運算子呼叫特定型別的預設建構函式，並且將預設值指派給變數。  在上述的範例裡，預設建構函式將值 `0` 指派給 `myInt`。  如需藉由呼叫預設建構函式來指派值的詳細資訊，請參閱[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)。  
  
 針對使用者定義型別，請使用 [new](../../../csharp/language-reference/keywords/new.md) 來叫用 \(Invoke\) 預設建構函式。  例如，下列陳述式叫用 `Point` 結構的預設建構函式：  
  
```  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 在這個呼叫之後，此結構將被視為已經明確的指派了，也就是，它的所有成員都已經初始化為它們的預設值。  
  
 如需 new 運算子的詳細資訊，請參閱 [new](../../../csharp/language-reference/keywords/new.md)。  
  
 如需格式化數字型別輸出的詳細資訊，請參閱[格式化數值結果表](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)。  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [類型](../../../csharp/language-reference/keywords/types.md)   
 [類型的參考表](../../../csharp/language-reference/keywords/reference-tables-for-types.md)   
 [參考類型](../../../csharp/language-reference/keywords/reference-types.md)