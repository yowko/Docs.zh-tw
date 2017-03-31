---
title: "轉換資料型別 (C#) | Microsoft Docs"
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
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
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
ms.openlocfilehash: 922e2f26c5f8ded260644e8effa043b03b721020
ms.lasthandoff: 03/13/2017

---
# <a name="converting-data-types-c"></a>轉換資料型別 (C#)
轉換方法會變更輸入物件的類型。  
  
 LINQ 查詢中的轉換作業可用於各種應用程式。 下列是一些範例：  
  
-   <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName> 方法可以用來隱藏類型之標準查詢運算子的自訂實作。  
  
-   <xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName> 方法可以用來啟用非參數化集合以進行 LINQ 查詢。  
  
-   <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>、<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>、<xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> 和 <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName> 方法可以用來強制立即執行查詢，而不是延後到列舉查詢。  
  
## <a name="methods"></a>方法  
 下表列出執行資料型別轉換的標準查詢運算子方法。  
  
 此表格中名稱開頭為"As" 的轉換方法會變更來源集合的靜態類型，而不是列舉它。 名稱開頭為 "To" 的方法會列舉來源集合，並將項目放入對應的集合類型。  
  
|方法名稱|描述|C# 查詢運算式語法|更多資訊|  
|-----------------|-----------------|---------------------------------|----------------------|  
|AsEnumerable|傳回為 <xref:System.Collections.Generic.IEnumerable%601> 的輸入類型。|不適用。|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>|  
|AsQueryable|將 (泛型) <xref:System.Collections.IEnumerable> 轉換為 (泛型) <xref:System.Linq.IQueryable>。|不適用。|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName>|  
|Cast|將集合的項目轉型為指定的類型。|使用類型明確的範圍變數。 例如: <br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName>|  
|OfType|根據可轉型為所指定類型的能力來篩選值。|不適用。|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName>|  
|ToArray|將集合轉換為陣列。 這個方法會強制執行查詢。|不適用。|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>|  
|ToDictionary|根據索引鍵選取器函式，將項目放入 <xref:System.Collections.Generic.Dictionary%602>。 這個方法會強制執行查詢。|不適用。|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>|  
|ToList|將集合轉換為 <xref:System.Collections.Generic.List%601>。 這個方法會強制執行查詢。|不適用。|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>|  
|ToLookup|根據索引鍵選取器函式，將項目放入 <xref:System.Linq.Lookup%602> (一對多字典)。 這個方法會強制執行查詢。|不適用。|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-example"></a>查詢運算式語法範例  
 下列程式碼範例會先使用類型明確的範圍變數將類型轉型為子類型，再存取只能在子類型上使用的成員。  
  
```csharp  
class Plant  
{  
    public string Name { get; set; }  
}  
  
class CarnivorousPlant : Plant  
{  
    public string TrapType { get; set; }  
}  
  
static void Cast()  
{  
    Plant[] plants = new Plant[] {  
        new CarnivorousPlant { Name = "Venus Fly Trap", TrapType = "Snap Trap" },  
        new CarnivorousPlant { Name = "Pitcher Plant", TrapType = "Pitfall Trap" },  
        new CarnivorousPlant { Name = "Sundew", TrapType = "Flypaper Trap" },  
        new CarnivorousPlant { Name = "Waterwheel Plant", TrapType = "Snap Trap" }  
    };  
  
    var query = from CarnivorousPlant cPlant in plants  
                where cPlant.TrapType == "Snap Trap"  
                select cPlant;  
  
    foreach (Plant plant in query)  
        Console.WriteLine(plant.Name);  
  
    /* This code produces the following output:  
  
        Venus Fly Trap  
        Waterwheel Plant  
    */  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq>   
 [標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [from 子句](../../../../csharp/language-reference/keywords/from-clause.md)   
 [LINQ 查詢運算式](../../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [如何：使用 LINQ 查詢 ArrayList (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
