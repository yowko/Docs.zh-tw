---
title: "如何：在查詢中傳回項目屬性的子集 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "匿名類型 [C#], 針對項目屬性的子集"
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# 如何：在查詢中傳回項目屬性的子集 (C# 程式設計手冊)
在這些條件都適用時，於查詢運算式中使用匿名型別：  
  
-   您希望只傳回每個來源項目的部分屬性。  
  
-   您不需要在執行查詢之方法的範圍外儲存查詢結果。  
  
 如果您只要傳回每個來源項目的一個屬性或欄位，則您可以只在 `select` 子句中使用點運算子。  例如，若只要傳回每個 `student` 的 `ID`，請寫入如下的 `select` 子句：  
  
```  
select student.ID;  
```  
  
## 範例  
 下列範例顯示如何使用匿名型別只傳回每個來源項目屬性的子集，該項目符合特定條件。  
  
 [!code-cs[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#31)]  
  
 請注意，如果未指定名稱，匿名型別會針對來源項目的屬性使用其名稱。  若要給予匿名型別中的屬性新名稱，請寫入如下的 `select` 陳述式：  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 如果您在前述範例嘗試這樣做，則 `Console.WriteLine` 陳述式也必須變更：  
  
```  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## 編譯程式碼  
  
-   若要執行這個程式碼，請將該類別複製並貼上至在 [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)] 中所建立的 Visual C\# 主控台應用程式專案。  根據預設，這個專案是以 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 3.5 版為目標，而且有 System.Core.dll 的參考，以及 System.Linq 的 `using` 指示詞。  如果專案中缺少一個或多個要求，您可以手動加入。  如需詳細資訊，請參閱 [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md)。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [匿名類型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)