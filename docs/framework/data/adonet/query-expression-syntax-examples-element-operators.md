---
title: 查詢運算式語法範例：項目運算子 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ca392dda-16e3-45c7-8d87-12d8d4ee0578
ms.openlocfilehash: 8690e4ec79dbe4b728695b073299ca3d21e7f098
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632591"
---
# <a name="query-expression-syntax-examples-element-operators-linq-to-dataset"></a>查詢運算式語法範例：項目運算子 (LINQ to DataSet)
此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.First%2A> 和 <xref:System.Linq.Enumerable.ElementAt%2A> 方法並搭配查詢運算式語法來取得 <xref:System.Data.DataRow> 中的 <xref:System.Data.DataSet> 項目。  
  
 `FillDataSet`這些範例中使用的方法指定於[載入資料至資料集](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)。  
  
 此主題中的範例將使用 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表。  
  
 本主題中的範例使用下列`using` / `Imports`陳述式：  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 如需詳細資訊，請參閱[＜How to：在 Visual Studio 中建立 LINQ to DataSet 專案](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md)。  
  
## <a name="elementat"></a>ElementAt  
  
### <a name="example"></a>範例  
 這則範例會使用 <xref:System.Linq.Enumerable.ElementAt%2A> 方法來擷取 `PostalCode` == "M4B 1V7" 的第五筆地址。  
  
 [!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]
 [!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]  
  
## <a name="first"></a>First  
  
### <a name="example"></a>範例  
 這則範例會使用 <xref:System.Linq.Enumerable.First%2A> 方法來傳回名字為 'Brooke' 的第一位連絡人。  
  
 [!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a>另請參閱
- [將資料載入至資料集](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [LINQ to DataSet 範例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [標準查詢運算子概觀](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
