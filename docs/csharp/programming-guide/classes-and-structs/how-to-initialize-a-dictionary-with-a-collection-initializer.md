---
title: "如何：使用集合初始設定式來初始化字典 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "集合初始設定式 [C#]，字典"
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
caps.latest.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 10
---
# 如何：使用集合初始設定式來初始化字典 (C# 程式設計手冊)
<xref:System.Collections.Generic.Dictionary%602> 包含索引鍵\/值組的集合。  它的 <xref:System.Collections.Generic.Dictionary%602.Add%2A> 方法會採用兩個參數，一個針對索引鍵，另一個針對值。  若要初始化 <xref:System.Collections.Generic.Dictionary%602>，或其 `Add` 方法採用多個參數的任何集合，請將每個參數集以括號括住，如下列範例所示。  
  
## 範例  
 在下列程式碼範例中，<xref:System.Collections.Generic.Dictionary%602> 是以型別 `StudentName` 的執行個體進行初始化。  
  
 [!code-cs[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 請注意，每個集合的項目中都有兩組括號。  最內層的括號會括住 `StudentName` 的物件初始設定式，最外層的括號會括住機碼值組，這組值會加入到 `students` <xref:System.Collections.Generic.Dictionary%602>。  最後，括號會括住目錄的整個集合初始設定式。  
  
## 編譯程式碼  
 若要執行這個程式碼，請將該類別複製並貼上至在 [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)] 中所建立的 Visual C\# 主控台應用程式專案。  根據預設，這個專案是以 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 3.5 版為目標，而且有 System.Core.dll 的參考，以及 System.Linq 的 using 指示詞。  如果專案中缺少一個或多個要求，您可以手動加入。  如需詳細資訊，請參閱[How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md)。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)