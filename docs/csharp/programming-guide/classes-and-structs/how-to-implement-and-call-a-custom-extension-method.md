---
title: "如何：實作和呼叫自訂擴充方法 (C# 程式設計手冊) | Microsoft Docs"
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
  - "擴充方法 [C#], 實作和呼叫"
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：實作和呼叫自訂擴充方法 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

本主題將說明如何實作您自己的擴充方法中的任何型別的[。NET Framework 類別庫](完整.嗎？LinkID%20=%20217856)，或其他。您想要擴充的 NET 型別。  用戶端程式碼可以使用您的擴充方法，方法是將參考加入至包含擴充方法的 DLL，以及加入 [using](../../../csharp/language-reference/keywords/using-directive.md) 指示詞，該指示詞指定在其中定義擴充方法的命名空間。  
  
### 若要定義及呼叫擴充方法  
  
1.  定義靜態[類別](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)以包含擴充方法。  
  
     對用戶端程式碼而言類別必須是可見的。  如需存取範圍規則的詳細資訊，請參閱 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
2.  以至少與包含類別相同的可視性，將擴充方法實作為靜態方法。  
  
3.  方法的第一個參數會指定方法進行作業的型別，前面必須加上 [this](../../../csharp/language-reference/keywords/this.md) 修飾詞。  
  
4.  在呼叫程式碼中，加入 `using` 指示詞以指定包含擴充方法類別的[命名空間](../../../csharp/language-reference/keywords/namespace.md)。  
  
5.  呼叫方法，如同它們是型別上的執行個體方法一般。  
  
     請注意，呼叫程式碼未指定第一個參數，因為它代表要套用運算子的型別，而且編譯器已知道物件的型別。  您只需要透過 `n` 提供參數 2 的引數。  
  
## 範例  
 下列範例實作 `CustomExtensions.StringExtension` 類別中名為 `WordCount` 的擴充方法。  方法會在 <xref:System.String> 類別上作業，指定為第一個方法參數。  `CustomExtensions` 命名空間會匯入應用程式命名空間，且方法會在 `Main` 方法內部呼叫。  
  
 [!CODE [csProgGuideExtensionMethods#1](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideExtensionMethods#1)]  
  
## 編譯程式碼  
 若要執行這個程式碼，請將它複製並貼上至在 [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] 中所建立的 Visual C\# 主控台應用程式專案。  根據預設，這個專案是以 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 3.5 版為目標，而且有 System.Core.dll 的參考，以及 System.Linq 的 `using` 指示詞。  如果專案中缺少一個或多個要求，您可以手動加入。  如需詳細資訊，請參閱 [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md)。  
  
## .NET Framework 安全性  
 擴充方法沒有特定安全性弱點。  它們無法用於模擬型別上的現有方法，因為所有名稱衝突已使用型別自行定義的執行個體或靜態方法解決。  擴充方法無法存取擴充類別中的任何私用資料。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [擴充方法](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [this](../../../csharp/language-reference/keywords/this.md)   
 [命名空間](../../../csharp/language-reference/keywords/namespace.md)