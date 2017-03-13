---
title: "如何：建立列舉類型的新方法 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "列舉類型擴充性 [C#]"
  - "列舉 [C#]"
  - "擴充方法 [C#], 針對列舉"
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
caps.latest.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 7
---
# 如何：建立列舉類型的新方法 (C# 程式設計手冊)
您可以使用擴充方法，加入特定列舉型別 \(Enum Type\) 特有的功能。  
  
## 範例  
 在下列範例中，`Grades` 列舉型別 \(Enumeration\) 表示學生在班上可能會得到的成績 \(用字母表示\)。  擴充方法 `Passing` 會加入至 `Grades` 型別，這樣該型別的每個執行個體 \(Instance\) 現在會知道它代表的是否為及格分數。  
  
 [!code-cs[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 請注意，`Extensions` 類別 \(Class\) 也包含動態更新的靜態變數，而且擴充方法的傳回值會反映該變數的目前值。  此範例示範如何在幕後於定義擴充方法的靜態類別上直接叫用 \(Invoke\) 擴充方法。  
  
## 編譯程式碼  
 若要執行這個程式碼，請將它複製並貼上至在 [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)] 中所建立的 Visual C\# 主控台應用程式專案。  根據預設，這個專案是以 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 3.5 版為目標，而且有 System.Core.dll 的參考，以及 System.Linq 的 `using` 指示詞。  如果專案中缺少一個或多個要求，您可以手動加入。  如需詳細資訊，請參閱 [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md)。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [擴充方法](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)