---
title: "如何：在 COM Interop 程式設計中使用索引的屬性 (C# 程式設計手冊) | Microsoft Docs"
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
  - "索引屬性 [C#]"
  - "Office 程式設計 [C#], 索引屬性"
  - "屬性 [C#], 索引"
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：在 COM Interop 程式設計中使用索引的屬性 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

「*索引的屬性*」\(Indexed Property\) 可改善具有參數的 COM 屬性用於 C\# 程式設計中的方式。  索引的屬性可與 Visual C\# 2010 中引入的其他功能搭配使用，例如[具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)、新的型別 \([dynamic](../../../csharp/language-reference/keywords/dynamic.md)\) 和[內嵌型別資訊](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)，以增強 Microsoft Office 程式設計功能。  
  
 在舊版的 C\# 中，只有在 `get` 方法沒有參數而且 `set` 方法僅有一個值參數時，才可以像屬性一樣存取方法。  不過，並非所有 COM 屬性都符合這些限制。  例如，Excel [Range](http://go.microsoft.com/fwlink/?LinkId=166053) 屬性具有的 `get` 存取子需要範圍名稱的參數。  在過去，您因為無法直接存取 `Range` 屬性，而必須改用 `get_Range` 方法 \(如下列範例所示\)。  
  
 [!CODE [csProgGuideIndexedProperties#1](../CodeSnippet/VS_Snippets_VBCSharp/csprogguideindexedproperties#1)]  
  
 但是，索引的屬性可讓您撰寫下列程式碼：  
  
 [!CODE [csProgGuideIndexedProperties#2](../CodeSnippet/VS_Snippets_VBCSharp/csprogguideindexedproperties#2)]  
  
> [!NOTE]
>  上述範例也用到[選擇性引數](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)功能 \(Visual C\# 2010 引入的新功能\)，可讓您省略 `Type.Missing`。  
  
 同樣地，若要在 Visual C\# 2008 和較舊版本中設定 [Range](http://go.microsoft.com/fwlink/?LinkId=179211) 物件的 `Value` 屬性，則需要兩個引數。  一個提供引數給用於指定範圍值型別的選擇性參數。  另一個則提供 `Value` 屬性的值。  在 Visual C\# 2010 以前，C\# 只允許一個引數。  因此，您不能使用一般 set 方法，而必須使用 `set_Value` 方法或不同的屬性 [Value2](http://go.microsoft.com/fwlink/?LinkId=166050)。  下列範例將說明這些技巧。  兩個方法都會將 A1 儲存格的值設為 `Name`。  
  
 [!CODE [csProgGuideIndexedProperties#3](../CodeSnippet/VS_Snippets_VBCSharp/csprogguideindexedproperties#3)]  
  
 但是，索引的屬性可讓您撰寫下列程式碼。  
  
 [!CODE [csProgGuideIndexedProperties#4](../CodeSnippet/VS_Snippets_VBCSharp/csprogguideindexedproperties#4)]  
  
 您不能建立自己的索引屬性。  此功能僅支援使用現有的索引屬性。  
  
## 範例  
 下列程式碼顯示完整範例。  如需如何設定專案以存取 Office API 的詳細資訊，請參閱 [如何：使用 Visual C\#  功能存取 Office Interop 物件](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)。  
  
 [!CODE [csProgGuideIndexedProperties#5](../CodeSnippet/VS_Snippets_VBCSharp/csprogguideindexedproperties#5)]  
  
## 請參閱  
 [具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)   
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)   
 [使用動態類型](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [如何：在 Office 程式設計中使用具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)   
 [如何：使用 Visual C\#  功能存取 Office Interop 物件](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)   
 [逐步解說：Office 程式設計](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)