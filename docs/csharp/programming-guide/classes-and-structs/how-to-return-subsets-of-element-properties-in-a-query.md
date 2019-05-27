---
title: 作法：在查詢中傳回項目屬性的子集 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: acff804d87d67bf8758b97ad04805359bb3f2e32
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586073"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>作法：在查詢中傳回項目屬性的子集 (C# 程式設計手冊)
如果下列兩個條件都成立，請在查詢運算式中使用匿名型別：  
  
- 您只要傳回每個來源項目的部分屬性。  
  
- 您不需要儲存執行查詢所在之方法範圍外的查詢結果。  
  
 如果您只要從每個來源項目傳回一個屬性或欄位，只要在 `select` 子句中使用點運算子即可。 例如，若只要傳回每個 `student` 的 `ID`，請如下所示撰寫 `select` 子句：  
  
```  
select student.ID;  
```  
  
## <a name="example"></a>範例  
 下列範例示範如何使用匿名型別，只傳回每個來源項目中符合指定條件的屬性子集。  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 請注意，如果未指定名稱，匿名型別會針對來源項目的屬性使用其名稱。 若要為匿名型別中的屬性指定新名稱，請如下所示撰寫 `select` 陳述式：  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 如果您在上述範例中嘗試這樣做，則必須同時變更 `Console.WriteLine` 陳述式：  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
若要執行此程式碼，請將該類別複製貼入 System.Linq 指示詞為 `using` 的 C# 主控台應用程式。
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [匿名類型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)
