---
title: "如何：從 bool? 安全轉型到 bool (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "轉型 [C#], 可為 null 的類型"
  - "可為 null 的類型 [C#], 將 bool? 轉型為 bool"
ms.assetid: e06e4274-a443-422d-8ef1-9dbf9df55237
caps.latest.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 9
---
# 如何：從 bool? 安全轉型到 bool (C# 程式設計手冊)
可為 null 的類型 `bool?` 包含三個不同的值：`true`、`false` 和 `null`。  因此，`bool?` 類型無法在某些條件中使用，例如搭配 `if`、`for` 或 `while` 使用。  例如，下列程式碼會造成編譯器錯誤。  
  
```  
bool? b = null;  
if (b) // Error CS0266.  
{  
}  
```  
  
 因為在條件內容中 `null` 表示的意義不明確，所以不允許這項動作。  若要在條件陳述式中使用 `bool?`，請先檢查其 <xref:System.Nullable%601.HasValue%2A> 屬性，確定其值不是 `null`，然後將它轉型為 `bool`。  如需詳細資訊，請參閱 [bool](../../../csharp/language-reference/keywords/bool.md)。  如果在 `bool?` 上以 `null` 值執行轉型，則會在條件測試中擲回 <xref:System.InvalidOperationException>。  下列範例會示範安全地從 `bool?` 轉型為 `bool` 的方式：  
  
## 範例  
  
```c#  
bool? test = null;  
// Other code that may or may not  
// give a value to test.  
if(!test.HasValue) //check for a value  
{  
    // Assume that IsInitialized  
    // returns either true or false.  
    test = IsInitialized();  
}  
if((bool)test) //now this cast is safe  
{  
   // Do something.  
}  
```  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [常值關鍵字](../../../csharp/language-reference/keywords/literal-keywords.md)   
 [可為 Null 的類型](../../../csharp/programming-guide/nullable-types/index.md)   
 [?? 運算子](../../../csharp/language-reference/operators/null-conditional-operator.md)