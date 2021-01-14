---
title: 以方法為基礎的查詢語法範例：聯結 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4fd5ed2c-b03a-4054-a3ed-3ddb380d7d9d
ms.openlocfilehash: 9573b1bf9dad77567fee8801a5e612c7efd53b1e
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98187804"
---
# <a name="method-based-query-syntax-examples-join-linq-to-dataset"></a>以方法為基礎的查詢語法範例：聯結 (LINQ to DataSet)

在以彼此沒有可瀏覽關聯性之資料來源 (例如關聯式資料庫資料表) 為目標的查詢中，聯結 (Join) 是一項重要的作業。 兩個資料來源的聯結是指某個資料來源中的物件與另一個資料來源中共用相同屬性之物件的關聯。 如需詳細資訊，請參閱 [標準查詢運算子總覽 (c # ) ](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) 或 [標準查詢運算子總覽 (Visual Basic) ](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。  
  
 此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Join%2A> 方法並搭配方法查詢語法來查詢 <xref:System.Data.DataSet>。  
  
 `FillDataSet`這些範例中使用的方法是在將[資料載入資料集](loading-data-into-a-dataset.md)時指定。  
  
 此主題中的範例將使用 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表。  
  
 本主題中的範例使用下列 `using` / `Imports` 語句：  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 LINQ to DataSet 專案](how-to-create-a-linq-to-dataset-project-in-vs.md)。  
  
## <a name="join"></a>Join  
  
### <a name="example"></a>範例  

 這則範例會在 `Contact` 和 `SalesOrderHeader` 資料表上方執行聯結。  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a>範例  

 這則範例會在 `Contact` 和 `SalesOrderHeader` 資料表上方執行聯結，並依據連絡人識別碼分組結果。  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a>另請參閱

- [將資料載入至資料集](loading-data-into-a-dataset.md)
- [LINQ to DataSet 範例](linq-to-dataset-examples.md)
- [標準查詢運算子概觀 (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [標準查詢運算子概觀 (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
