---
title: "結構 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 語言, 結構"
  - "結構 [C#]"
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
caps.latest.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 31
---
# 結構 (C# 程式設計手冊)
結構 \(Struct\) 是使用 [struct](../../../csharp/language-reference/keywords/struct.md) 關鍵字所定義，例如：  
  
 [!code-cs[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/structs_1.cs)]  
  
 結構與類別所使用的語法幾乎相同，不過結構的限制比類別多：  
  
-   結構宣告內不能初始化欄位，除非將其宣告為 const 或 static。  
  
-   結構不可宣告預設建構函式 \(沒有參數的建構函式\) 或解構函式。  
  
-   結構是在指派時複製的。  當指派結構給新變數時，就會複製所有資料，而新變數所做的任何修改都不會變更原始複本的資料。  在使用如 Dictionary\<string, myStruct\> 的實際型別集合時，請務必謹記這一點。  
  
-   結構為實值型別，而類別則是參考型別。  
  
-   與類別不同的是，結構並不需要使用 `new` 運算子就能具現化。  
  
-   結構可以宣告含有參數的建構函式。  
  
-   結構無法從另一個結構或類別繼承而來，且它不能成為類別的基底。  所有結構都是從繼承自 `System.Object` 的 `System.ValueType` 直接繼承而來  
  
-   結構可實作介面  
  
-   結構可以用來當做可為 Null 的型別，而且可以對其指派 null 值。  
  
## 相關章節  
 如需詳細資訊，請參閱下列主題：  
  
-   [使用結構](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [可為 Null 的類型](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [如何：瞭解傳遞結構和傳遞類別參考給方法之間的差異](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [如何：在結構之間實作使用者定義的轉換](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [更多關於變數](完整.嗎？LinkId%20=%20221230) 在 [開頭 2010 視覺化 C\#](完整.嗎？LinkId%20=%20221214)  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [類別](../../../csharp/programming-guide/classes-and-structs/classes.md)