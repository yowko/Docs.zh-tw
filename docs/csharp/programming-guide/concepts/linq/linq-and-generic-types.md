---
title: "LINQ and Generic Types (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "LINQ [C#], generic types"
  - "generic types [LINQ]"
  - "generics [LINQ]"
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# LINQ and Generic Types (C#)
[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 查詢是以 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] 2.0 版中就引進的泛型型別為基礎。  您不需要對泛型型別有相當程度的了解，就可以開始撰寫查詢。  不過，您可能需要了解兩個基本概念：  
  
1.  建立泛型集合類別 \(Class\) \(如 <xref:System.Collections.Generic.List%601>\) 的執行個體 \(Instance\) 時，請將 "T" 取代為清單中會包含之物件的型別。  例如，字串的清單是以 `List<string>` 表示，而 `Customer` 物件的清單則是以 `List<Customer>` 表示。  泛型清單是強型別的，而且優點多於以 <xref:System.Object> 形式儲存項目的集合。  如果您嘗試將 `Customer` 加入至 `List<string>`，就會在編譯時期接收到錯誤。  泛型集合不需要執行執行階段的型別轉換 \(Type Cast\)，因此十分容易使用。  
  
2.  <xref:System.Collections.Generic.IEnumerable%601> 這個介面可讓您使用 `foreach` 陳述式來列舉泛型集合類別。  就像 <xref:System.Collections.ArrayList> 等非泛型集合類別支援 <xref:System.Collections.IEnumerable>，泛型集合類別同樣可以支援 <xref:System.Collections.Generic.IEnumerable%601>。  
  
 如需泛型的詳細資訊，請參閱[泛型](../../../../csharp/programming-guide/generics/index.md)。  
  
## LINQ 查詢中的 IEnumerable\<T\> 變數  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 查詢變數的型別是 <xref:System.Collections.Generic.IEnumerable%601> 或諸如 <xref:System.Linq.IQueryable%601> 之類的衍生型別 \(Derived Type\)。  當您看到型別為 `IEnumerable<Customer>` 的查詢變數時，只表示查詢在執行時會產生由零個以上 `Customer` 物件組成的序列。  
  
 [!code-cs[csLINQGettingStarted#34](../../../../csharp/programming-guide/concepts/linq/codesnippet/csharp/GettingStarted/Class1.cs#34)]  
  
 如需詳細資訊，請參閱[Type Relationships in LINQ Query Operations](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)。  
  
## 讓編譯器處理泛型型別宣告  
 想要的話，您可以使用 [var](../../../../csharp/language-reference/keywords/var.md) 關鍵字來避免使用泛型語法。  `var` 關鍵字會指示編譯器 \(Compiler\) 查看 `from` 子句中指定的資料來源，來推斷查詢變數的型別。  下列範例在編譯後會產生與上一個範例相同的程式碼：  
  
 [!code-cs[csLINQGettingStarted#35](../../../../csharp/programming-guide/concepts/linq/codesnippet/csharp/GettingStarted/Class1.cs#35)]  
  
 `var` 關鍵字適用於當變數的型別很明顯，或不需要明確指定巢狀泛型型別 \(如群組查詢產生的型別\) 時。  一般而言，如果要使用 `var`，則建議您考慮到它會讓其他人更難看懂您的程式碼。  如需詳細資訊，請參閱[隱含類型區域變數](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)。  
  
## 請參閱  
 [Getting Started with LINQ in C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [泛型](../../../../csharp/programming-guide/generics/index.md)