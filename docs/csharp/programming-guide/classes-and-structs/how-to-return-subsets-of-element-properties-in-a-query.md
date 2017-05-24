---
title: "如何：在查詢中傳回項目屬性的子集 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3849d26506278fede6642530c60b6ec418f39464
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>如何：在查詢中傳回項目屬性的子集 (C# 程式設計手冊)
如果下列兩個條件都成立，請在查詢運算式中使用匿名型別：  
  
-   您只要傳回每個來源項目的部分屬性。  
  
-   您不需要儲存執行查詢所在之方法範圍外的查詢結果。  
  
 如果您只要從每個來源項目傳回一個屬性或欄位，只要在 `select` 子句中使用點運算子即可。 例如，若只要傳回每個 `student` 的 `ID`，請如下所示撰寫 `select` 子句：  
  
```  
select student.ID;  
```  
  
## <a name="example"></a>範例  
 下列範例示範如何使用匿名型別，只傳回每個來源項目中符合指定條件的屬性子集。  
  
 [!code-cs[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]  
  
 請注意，如果未指定名稱，匿名型別會針對來源項目的屬性使用其名稱。 若要為匿名型別中的屬性指定新名稱，請如下所示撰寫 `select` 陳述式：  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 如果您在上述範例中嘗試這樣做，則必須同時變更 `Console.WriteLine` 陳述式：  
  
```  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   若要執行此程式碼，請將該類別複製並貼到 [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] 中所建立的 Visual C# 主控台應用程式專案。 根據預設，此專案是以 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 3.5 版為目標，而且會有 System.Core.dll 的參考，以及 System.Linq 的 `using` 指示詞。 如果專案中遺漏上述一或多個需求，您可以手動新增這些需求。   
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [匿名型別](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)
