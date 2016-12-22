---
title: "泛型類別 (C# 程式設計手冊) | Microsoft Docs"
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
  - "C# 語言, 泛型類別"
  - "泛型 [C#], 類別"
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
caps.latest.revision: 30
caps.handback.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 泛型類別 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

泛型類別會封裝並非特定資料型別獨有的作業。  泛型類別的最常見用法，就是搭配如連結清單、雜湊資料表、堆疊、佇列、樹狀架構及其他的集合使用。  無論所儲存的資料型別為何，將項目加入集合或是從集合移除項目的作業，基本上都會以相同的方式執行。  
  
 對於大多數需要集合類別的案例，建議的方法是使用 .NET Framework 類別庫 \(Class Library\) 所提供的類別。  如需使用這些類別的詳細資訊，請參閱[.NET Framework 類別庫中的泛型](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md)。  
  
 一般而言，會從現有的具象類別開始建立泛型類別，然後一次將多個型別變更為型別參數，直到達到一般化與可用性的最佳平衡點為止。  當建立您自己的泛型類別時，必須考慮下列重要事項：  
  
-   要一般化為型別參數的型別。  
  
     一般的規則是，能夠參數化的型別越多，程式碼的彈性和可重複使用性就會越高。  然而，太過度的一般化會產生其他開發人員難以閱讀或了解的程式碼。  
  
-   要套用至型別參數的條件約束 \(如果有\) \(請參閱[類型參數的條件約束](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)\)。  
  
     好的規則是盡可能套用最多的條件約束，同時仍然可以讓您處理必須處理的型別。  例如，如果知道泛型類別只要搭配參考型別使用，就應該套用類別條件約束。  這可以避免搭配實值型別誤用類別，並且能夠讓您在 `T` 上使用 `as` 運算子，以及檢查 null 值。  
  
-   是否要將泛型行為因數化至基底類別和子類別。  
  
     因為泛型類別可以當做基底類別，所以在此適用與非泛型類別相同的設計考量。  請參閱本主題中稍後說明關於繼承自泛型基底類別的規則。  
  
-   是否要實作一個或多個泛型介面。  
  
     例如，如果設計的類別將用來建立泛型架構集合中的項目，您可能需要實作像是 <xref:System.IComparable%601> 的介面，其中 `T` 是類別的型別。  
  
 如需簡單泛型類別的範例，請參閱[泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)。  
  
 型別參數和條件約束的規則有幾個泛型類別行為含意，尤其與繼承和成員存取範圍有關。  在繼續進行之前，您應該先了解某些詞彙。  若是泛型類別，`Node<T>,` 用戶端程式碼可以參考該類別，方法是藉由指定型別引數以建立封閉式建構型別 \(`Node<int>`\)，  或者，也可以不指定型別參數 \(例如在指定泛型基底類別時\) 以建立開放式的建構型別 \(`Node<T>`\)。  泛型類別可以繼承自具象、封閉式或開放式建構基底類別：  
  
 [!CODE [csProgGuideGenerics#16](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideGenerics#16)]  
  
 非泛型 \(也就是具象\) 類別可以繼承自封閉式的建構基底類別，但是不能繼承自開放式建構類別或型別參數，因為在執行階段時用戶端程式碼無法提供產生基底類別時所需要的型別引數。  
  
 [!CODE [csProgGuideGenerics#17](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideGenerics#17)]  
  
 繼承自開放式建構型別的泛型類別，必須提供任何基底類別型別參數的型別引數，並且引數不能與繼承類別共用，如同下列程式碼範例所示範：  
  
 [!CODE [csProgGuideGenerics#18](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideGenerics#18)]  
  
 繼承自開放式建構型別的泛型類別必須指定 \(或代表\) 基底型別上條件約束的超集：  
  
 [!CODE [csProgGuideGenerics#19](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideGenerics#19)]  
  
 泛型型別可以使用多個型別參數和條件約束，如下所示：  
  
 [!CODE [csProgGuideGenerics#20](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideGenerics#20)]  
  
 開放式和封閉式的建構型別都可以用來當做方法參數：  
  
 [!CODE [csProgGuideGenerics#21](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideGenerics#21)]  
  
 如果泛型類別會實作介面，則該類別的所有執行個體都可轉型為該介面。  
  
 泛型類別是不變的。  也就是說，如果輸入參數指定 `List<BaseClass>`，則當您嘗試提供 `List<DerivedClass>` 時，便會發生編譯時期錯誤。  
  
## 請參閱  
 <xref:System.Collections.Generic>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [泛型](../../../csharp/programming-guide/generics/index.md)   
 [儲存列舉程式的狀態](http://go.microsoft.com/fwlink/?LinkId=112390)   
 [繼承謎題，第一部分](http://go.microsoft.com/fwlink/?LinkId=112380)