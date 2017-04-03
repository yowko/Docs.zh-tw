---
title: "分組資料 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2ef56a843117bb8b7409b10ef33ca83175849b9f
ms.lasthandoff: 03/13/2017

---
# <a name="grouping-data-c"></a>分組資料 (C#)
分組指的是將資料放在群組中，好讓每一個群組中的項目共用共同的屬性。  
  
 下圖顯示一系列字元的分組結果。 每個群組的索引鍵是字元。  
  
 ![LINQ 群組作業](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")  
  
 分組資料項目的標準查詢運算子方法詳列於下一節。  
  
## <a name="methods"></a>方法  
  
|方法名稱|描述|C# 查詢運算式語法|更多資訊|  
|-----------------|-----------------|---------------------------------|----------------------|  
|GroupBy|共用共同屬性的群組項目。 每個群組由 <xref:System.Linq.IGrouping%602> 物件表示。|`group … by`<br /><br /> -或-<br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName>|  
|ToLookup|將項目根據索引鍵選取器函式插入到 <xref:System.Linq.Lookup%602> (一對多字典) 中。|不適用。|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-example"></a>查詢運算式語法範例  
 下列程式碼範例使用 `group by` 子句，將整數依奇偶數分組至清單。  
  
```csharp  
List<int> numbers = new List<int>() { 35, 44, 200, 84, 3987, 4, 199, 329, 446, 208 };  
  
IEnumerable<IGrouping<int, int>> query = from number in numbers  
                                         group number by number % 2;  
  
foreach (var group in query)  
{  
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");  
    foreach (int i in group)  
        Console.WriteLine(i);  
}  
  
/* This code produces the following output:  
  
    Odd numbers:  
    35  
    3987  
    199  
    329  
  
    Even numbers:  
    44  
    200  
    84  
    4  
    446  
    208  
*/  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq>   
 [標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [group 子句](../../../../csharp/language-reference/keywords/group-clause.md)   
 [如何：建立巢狀群組](../../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)   
 [如何：依副檔名分組檔案 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)   
 [如何：分組查詢結果](../../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)   
 [如何：在分組作業上執行子查詢](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)   
 [如何：使用群組將檔案分割成許多檔案 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
