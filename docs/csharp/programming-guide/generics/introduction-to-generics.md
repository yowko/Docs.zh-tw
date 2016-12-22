---
title: "泛型簡介 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "泛型 [C#], 關於泛型"
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
caps.latest.revision: 32
caps.handback.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 泛型簡介 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

泛型類別和方法將重複使用性、型別安全和高效率三者結合在一起，發揮了非泛型的類別和方法所無法提供的功能。  泛型最常搭配在這種型別上操作的集合和方法使用。  .NET Framework 2.0 版類別庫提供了新的命名空間 <xref:System.Collections.Generic>，其中包含多個以泛型為基礎的新集合類別。  一般建議，使用 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 2.0 版和更新版本的所有應用程式都應使用新的泛型集合類別，而不要使用舊版的非泛型對應類別，例如 <xref:System.Collections.ArrayList>。  如需詳細資訊，請參閱 [.NET Framework 類別庫中的泛型](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md)。  
  
 當然，您也可以建立自訂的泛型型別和方法，自行處理泛型化的問題，並設計型別安全而且效率高的模式。  在下列程式碼中，示範了一個簡單的泛型連結清單類別   \(在大部分情況下，您應該使用 .NET Framework 類別庫提供的 <xref:System.Collections.Generic.List%601> 類別，而不要自行建立類別\)。 這個範例在幾個地方使用了型別參數 `T`，這些地方通常需要使用具象型別來表示清單中儲存的項目型別。  這個參數可以用於：  
  
-   做為 `AddHead` 方法中的方法參數型別。  
  
-   做為公用方法 `GetNext` 的傳回型別，以及巢狀 `Node` 類別中的 `Data` 屬性。  
  
-   做為巢狀類別中私用成員資料的型別。  
  
 請注意，T 可用於巢狀 `Node` 類別。  當 `GenericList<T>` 以具象型別執行個體化時 \(例如執行個體化為 `GenericList<int>`\)，則每次出現的 `T` 項目都會以 `int` 取代。  
  
 [!CODE [csProgGuideGenerics#2](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideGenerics#2)]  
  
 下列程式碼範例示範用戶端程式碼如何使用泛型 `GenericList<T>` 類別建立整數清單。  您只要變更型別引數，就能輕鬆修改下列的程式碼來建立字串清單或其他任何自訂型別的清單：  
  
 [!CODE [csProgGuideGenerics#3](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideGenerics#3)]  
  
## 請參閱  
 <xref:System.Collections.Generic>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [泛型](../../../csharp/programming-guide/generics/index.md)