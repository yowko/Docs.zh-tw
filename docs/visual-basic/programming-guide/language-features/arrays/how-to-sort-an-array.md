---
title: "How to: Sort An Array in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Array.Sort"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "arrays [Visual Basic], sorting"
  - "examples [Visual Basic], arrays"
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Sort An Array in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

這個範例宣告名為 `zooAnimals` 的 `String` 物件陣列，填入這個物件陣列，接著依字母順序排序。  
  
## 範例  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## 編譯程式碼  
 這個範例需要：  
  
-   Mscorlib.dll 和 <xref:System> 命名空間的存取。  
  
## 穩固程式設計  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   陣列為空白 \(<xref:System.ArgumentNullException> 類別\)  
  
-   陣列為多維 \(<xref:System.RankException> 類別\)  
  
-   陣列的一或多個元素未實作 <xref:System.IComparable> 介面 \(<xref:System.InvalidOperationException> 類別\)  
  
## 請參閱  
 <xref:System.Array.Sort%2A?displayProperty=fullName>   
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Troubleshooting Arrays](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)   
 [集合](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)   
 [For Each...Next 陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)