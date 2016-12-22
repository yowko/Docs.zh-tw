---
title: "interface (C# 參考) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "interface_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "介面關鍵字 [C#]"
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
caps.latest.revision: 29
caps.handback.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# interface (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

介面只包含[方法](../../../csharp/programming-guide/classes-and-structs/methods.md)、[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)、[事件](../../../csharp/programming-guide/events/index.md)或[索引](../../../visual-basic/reference/command-line-compiler/index.md)的簽章。  類別或結構，其實作的介面必須實作在介面定義中指定的介面成員。  在下列範例中，類別 `ImplementationClass` 必須實作名為 `SampleMethod` 的方法，該方法沒有參數並會傳回 `void`。  
  
 如需詳細資訊與範例，請參閱[介面](../../../csharp/programming-guide/interfaces/index.md)。  
  
## 範例  
 [!code-cs[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]  
  
 介面可以是命名空間 \(Namespace\) 或類別的成員，而且可以包含下列成員的簽章：  
  
-   [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [屬性](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [索引子](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [事件](../../../csharp/language-reference/keywords/event.md)  
  
 介面可以繼承一個或多個基底介面。  
  
 當基底型別 \(Base Type\) 清單包含基底類別和介面時，基底類別一定會排在清單的第一個。  
  
 實作介面的類別能夠明確實作該介面的成員。  明確實作的成員只能經由該介面的執行個體 \(Instance\) 來存取，不能經由類別執行個體存取。  
  
 如需詳細資訊以及明確介面實作的程式碼範例，請參閱[明確介面實作](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)。  
  
## 範例  
 下列範例示範了介面實作。  在這個範例中，介面包含屬性宣告，類別則包含實作。  實作 `IPoint` 之類別的任何執行個體，都有整數屬性 `x` 和 `y`。  
  
 [!code-cs[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [參考類型](../../../csharp/language-reference/keywords/reference-types.md)   
 [介面](../../../csharp/programming-guide/interfaces/index.md)   
 [使用屬性](../../../csharp/programming-guide/classes-and-structs/using-properties.md)   
 [使用索引子](../../../csharp/programming-guide/indexers/using-indexers.md)   
 [Class \- 類別](../../../csharp/language-reference/keywords/class.md)   
 [struct](../../../csharp/language-reference/keywords/struct.md)   
 [介面](../../../csharp/programming-guide/interfaces/index.md)