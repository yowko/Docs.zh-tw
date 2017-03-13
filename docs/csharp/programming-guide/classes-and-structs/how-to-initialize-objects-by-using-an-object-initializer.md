---
title: "如何：使用物件初始設定式初始化物件 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "物件初始設定式 [C#], 使用方法"
  - "物件 [C#], 初始化"
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
caps.latest.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 20
---
# 如何：使用物件初始設定式初始化物件 (C# 程式設計手冊)
您可以使用物件初始設定式以宣告方式初始化型別物件，而不需明確叫用型別的建構函式。  
  
 下列範例顯示如何使用有具名物件的物件初始設定式。  編譯器會先存取預設執行個體建構函式接著處理成員初始化管理物件初始設定式。  因此，如果預設建構函式在類別中宣告為 `private`，需要公用存取的物件初始設定式將會失敗。  
  
 如果定義匿名型別，您必須使用物件初始設定式。  如需詳細資訊，請參閱[如何：在查詢中傳回項目屬性的子集](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md)。  
  
## 範例  
 下列範例顯示如何使用物件初始設定式來初始化新的 `StudentName` 型別。  
  
 [!code-cs[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]  
  
## 範例  
 下列範例顯示如何使用集合初始設定式初始化 `StudentName` 型別的集合。  請注意，集合初始設定式是一系列以逗號分隔的物件初始設定式。  
  
 [!code-cs[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]  
  
## 編譯程式碼  
 若要執行這個程式碼，請將該類別複製並貼上至在 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 中所建立的 Visual C\# 主控台應用程式專案。  如需詳細資訊，請參閱[How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md)。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)