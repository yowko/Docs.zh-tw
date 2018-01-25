---
title: "實值型別 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 281b811f2a8a1f2c364405b563f9f103899b492c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="value-types-c-reference"></a>實值類型 (C# 參考)
實值型別包含兩種主要類別：  
  
-   [結構](../../../csharp/language-reference/keywords/struct.md)  
  
-   [列舉](../../../csharp/language-reference/keywords/enum.md)  
  
 結構分成下列類別：  
  
-   數值類型  
  
    -   [整數型別](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [浮點類型](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
    -   [decimal](../../../csharp/language-reference/keywords/decimal.md)  
  
-   [bool](../../../csharp/language-reference/keywords/bool.md)  
  
-   使用者定義結構。  
  
## <a name="main-features-of-value-types"></a>實值型別的主要功能  
 根據實值型別的變數直接包含值。 將一個實值型別變數指派給另一個實值型別變數會複製包含的值。 這與指派參考型別變數不同，後者會複製物件的參考，而不是物件本身。  
  
 所有實值型別都是隱含地衍生自 <xref:System.ValueType?displayProperty=nameWithType>。  
  
 與參考型別不同，您無法從實值型別衍生新的類型。 不過，就像參考型別，結構可以實作介面。  
  
 與參考型別不同，實值型別不能包含 `null` 值。 不過，[可為 Null 的類型](../../../csharp/programming-guide/nullable-types/index.md)功能允許將實值型別指派給 `null`。  
  
 每種實值型別都具有初始化該類型預設值的隱含預設建構函式。 如需實值型別預設值的資訊，請參閱[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)。  
  
## <a name="main-features-of-simple-types"></a>簡單類型的主要功能  
 所有簡單類型 (C# 語言的必要項目) 是 .NET Framework System 類型的別名。 例如，[int](../../../csharp/language-reference/keywords/int.md) 是 <xref:System.Int32?displayProperty=nameWithType> 的別名。 如需完整的別名清單，請參閱[內建類型表](../../../csharp/language-reference/keywords/built-in-types-table.md)。  
  
 在編譯時間，會評估常數運算式 (其運算元都是簡單類型常數)。  
  
 簡單類型可以使用常值進行初始化。 例如，'A' 是類型 `char` 的常值，而 2001 是類型 `int` 的常值。  
  
## <a name="initializing-value-types"></a>初始化實值型別  
 必須先初始化 C# 中的區域變數，再使用它們。 例如，您可以宣告區域變數，而不進行初始化，如下列範例所示：  
  
```  
int myInt;  
```  
  
 您不能先使用它，再將它初始化。 您可以使用下列陳述式來初始化執行個體：  
  
```  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 這個陳述式相當於下列陳述式：  
  
```  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 當然，您可以有相同陳述式中的宣告和初始化，如下列範例所示：  
  
```  
int myInt = new int();  
```  
  
 -或-  
  
```  
int myInt = 0;  
```  
  
 使用 [new](../../../csharp/language-reference/keywords/new.md) 運算子會呼叫特定類型的預設建構函式，並將預設值指派給變數。 在上述範例中，預設建構函式已將 `0` 值指派給 `myInt`。 如需呼叫預設建構函式來指派值的詳細資訊，請參閱[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)。  
  
 如果要使用使用者定義型別，請使用 [new](../../../csharp/language-reference/keywords/new.md) 來叫用預設建構函式。 例如，下列陳述式會叫用 `Point` 結構的預設建構函式：  
  
```  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 在此呼叫之後，會視為已明確指派結構，也就是說，其所有成員都已初始化為其預設值。  
  
 如需 new 運算子的詳細資訊，請參閱 [new](../../../csharp/language-reference/keywords/new.md)。  
  
 如需格式化數值類型輸出的資訊，請參閱[格式化數值結果表](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)。  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [型別](../../../csharp/language-reference/keywords/types.md)  
 [型別的參考表](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [參考型別](../../../csharp/language-reference/keywords/reference-types.md)
