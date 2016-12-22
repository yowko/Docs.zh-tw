---
title: "將陣列當做物件 (C# 程式設計手冊) | Microsoft Docs"
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
  - "陣列 [C#], 為物件"
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 將陣列當做物件 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

在 C\# 中，陣列是實際物件，而不只是如 C 和 C\+\+ 中之連續記憶體的可定址區域。  <xref:System.Array> 是所有陣列型別的抽象基底型別。  您可以使用 <xref:System.Array> 的屬性和其他類別成員。  例如，可以使用 <xref:System.Array.Length%2A> 屬性取得陣列的長度。  下列程式碼將 `numbers` 陣列的長度 \(亦即 `5`\) 指派給變數 `lengthOfNumbers`：  
  
 [!code-cs[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <xref:System.Array> 類別還提供了許多其他有用的方法和屬性，例如，排序、搜尋和複製陣列。  
  
## 範例  
 本範例使用 <xref:System.Array.Rank%2A> 屬性顯示陣列的維度數目。  
  
 [!code-cs[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [陣列](../../../csharp/programming-guide/arrays/index.md)   
 [一維陣列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [多維陣列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)   
 [不規則陣列](../../../csharp/programming-guide/arrays/jagged-arrays.md)