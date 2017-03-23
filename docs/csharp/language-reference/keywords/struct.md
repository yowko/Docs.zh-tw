---
title: "struct (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "struct_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "struct 關鍵字 [C#]"
  - "結構 [C#], struct 關鍵字"
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
caps.latest.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 23
---
# struct (C# 參考)
`struct` 類型是實值類型，通常可用來封裝一小組相關變數，例如矩形的座標，或詳細目錄中某個項目的特性。  下列範例示範簡單結構宣告：  
  
```  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## 備註  
 結構還包含[建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)、[常數](../../../csharp/programming-guide/classes-and-structs/constants.md)、[欄位](../../../csharp/programming-guide/classes-and-structs/fields.md)、[方法](../../../csharp/programming-guide/classes-and-structs/methods.md)、[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)、[索引子](../../../csharp/programming-guide/indexers/index.md)、[運算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)、[事件](../../../csharp/programming-guide/events/index.md)和[巢狀類型](../../../csharp/programming-guide/classes-and-structs/nested-types.md)，不過如果需要數個這類成員，您應該考慮以類別來取代類型。  
  
 如需範例，請參閱 [使用結構](../../../csharp/programming-guide/classes-and-structs/using-structs.md)。  
  
 結構可以實作介面，但無法繼承自其他結構。  因此，結構成員無法宣告為 `protected`。  
  
 如需詳細資訊，請參閱[結構](../../../csharp/programming-guide/classes-and-structs/structs.md)。  
  
## 範例  
 如需範例與詳細資訊，請參閱[使用結構](../../../csharp/programming-guide/classes-and-structs/using-structs.md)。  
  
## C\# 語言規格  
 如需範例，請參閱 [使用結構](../../../csharp/programming-guide/classes-and-structs/using-structs.md)。  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [預設值表](../../../csharp/language-reference/keywords/default-values-table.md)   
 [內建類型資料表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [類型](../../../csharp/language-reference/keywords/types.md)   
 [實值類型](../../../csharp/language-reference/keywords/value-types.md)   
 [Class \- 類別](../../../csharp/language-reference/keywords/class.md)   
 [interface](../../../csharp/language-reference/keywords/interface.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)