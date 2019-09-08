---
title: 以方法為基礎的查詢語法範例：設定運算子 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa93af15-28af-4b5e-846b-897308410edb
ms.openlocfilehash: 481c0ed7e39b8f958ccdae01e4589d54b3ff2446
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783585"
---
# <a name="method-based-query-syntax-examples-set-operators-linq-to-dataset"></a>以方法為基礎的查詢語法範例：設定運算子 (LINQ to DataSet)
本主題中的範例將<xref:System.Linq.Enumerable.Distinct%2A>示範如何使用、、 <xref:System.Linq.Enumerable.Except%2A> <xref:System.Linq.Enumerable.Intersect%2A>和<xref:System.Linq.Enumerable.Union%2A>運算子，針對資料列集執行以值為基礎的比較作業。[將資料載入資料集](loading-data-into-a-dataset.md)的詳細<xref:System.Data.DataRowComparer>資訊，請參閱[比較 datarow](comparing-datarows-linq-to-dataset.md) 。  
  
 在`FillDataSet`這些範例中使用的方法，是在將[資料載入至資料集](loading-data-into-a-dataset.md)中時指定。  
  
 此主題中的範例將使用 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表。  
  
 本主題中的範例會使用下列`using` / `Imports`語句：  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 如需詳細資訊，請參閱[如何：在 Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md)中建立 LINQ to DataSet 專案。  
  
## <a name="distinct"></a>Distinct  
  
### <a name="example"></a>範例  
 這則範例會使用 <xref:System.Linq.Enumerable.Distinct%2A> 方法來移除序列 (Sequence) 中的重複項目。  
  
 [!code-csharp[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#distinctrows)]
 [!code-vb[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#distinctrows)]  
  
## <a name="except"></a>Except  
  
### <a name="example"></a>範例  
 這則範例會使用 <xref:System.Linq.Enumerable.Except%2A> 方法來傳回在第一份資料表中出現但沒有在第二份資料表中出現的連絡人。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#except2)]
 [!code-vb[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#except2)]  
  
## <a name="intersect"></a>Intersect  
  
### <a name="example"></a>範例  
 這則範例會使用 <xref:System.Linq.Enumerable.Intersect%2A> 方法來傳回在這兩份資料表中都出現的連絡人。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
## <a name="union"></a>Union  
  
### <a name="example"></a>範例  
 這則範例會使用 <xref:System.Linq.Enumerable.Union%2A> 方法來傳回在其中一份資料表中出現的唯一連絡人。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#union2)]
 [!code-vb[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#union2)]  
  
## <a name="see-also"></a>另請參閱

- [將資料載入至資料集](loading-data-into-a-dataset.md)
- [LINQ to DataSet 範例](linq-to-dataset-examples.md)
- [標準查詢運算子概觀 (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [標準查詢運算子概觀 (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
