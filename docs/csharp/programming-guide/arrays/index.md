---
title: "陣列 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "陣列 [C#]"
  - "C# 語言, 陣列"
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
caps.latest.revision: 33
caps.handback.revision: 33
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 陣列 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

您可以在陣列資料結構中儲存多個相同類型的變數。  您會指定陣列項目的類型以宣告陣列。  
  
 `type[] arrayName;`  
  
 下列範例會分別建立一維、多維和不規則陣列：  
  
 [!code-cs[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]  
  
## 陣列概觀  
 陣列有下列屬性：  
  
-   陣列可以是[一維](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)、[多維](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)或[不規則](../../../csharp/programming-guide/arrays/jagged-arrays.md)。  
  
-   維度的數目和每個維度的長度會在建立陣列執行個體時確立。  在執行個體的存留期中，這些值無法變更。  
  
-   數值陣列元素的預設值會設定為零，而參考元素則設定為 null。  
  
-   不規則陣列是指包含陣列的陣列，因此其元素為參考類型，而且會初始化為 `null`。  
  
-   陣列是以零為起始索引，即包含 `n` 個元素的陣列建立索引時，會從 `0` 開始，一直到 `n-1` 為止。  
  
-   陣列元素可以是任何類型，包括陣列類型。  
  
-   陣列類型是從抽象基底類型 <xref:System.Array> 衍生的[參考類型](../../../csharp/language-reference/keywords/reference-types.md)。  由於此類型會實作 <xref:System.Collections.IEnumerable> 和 <xref:System.Collections.Generic.IEnumerable%601>，您可以在 C\# 中的所有陣列上使用 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 反覆運算。  
  
## 相關章節  
  
-   [陣列當做物件](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [搭配陣列使用 foreach](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [傳遞陣列當做引數](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
-   [使用 ref 和 out 傳遞陣列](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)  
  
-   [初探 Visual C\# 2010](http://go.microsoft.com/fwlink/?LinkId=221214) 中的[深入了解變數](http://go.microsoft.com/fwlink/?LinkId=221230)  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [集合](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)   
 [Array Collection Type](http://msdn.microsoft.com/zh-tw/8a9964de-8941-47b1-a3cf-a01bc88db9e8)