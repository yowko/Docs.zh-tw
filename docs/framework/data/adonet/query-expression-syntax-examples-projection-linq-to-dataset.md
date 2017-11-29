---
title: "查詢運算式語法範例：投影 (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 48c9f5ed-76bf-4228-ab10-5217bbb295a3
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9aab649eebdccc480f4681da5e3d9499cb62eab6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="query-expression-syntax-examples-projection--linq-to-dataset"></a>查詢運算式語法範例：投影 (LINQ to DataSet)
此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Select%2A> 和 <xref:System.Linq.Enumerable.SelectMany%2A> 方法並搭配查詢運算式語法來查詢 <xref:System.Data.DataSet>。  
  
 `FillDataSet`這些範例中使用的方法會指定於[載入資料至資料集](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)。  
  
 此主題中的範例將使用 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表。  
  
 本主題中的範例使用下列`using` / `Imports`陳述式：  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 如需詳細資訊，請參閱[How to： 建立 LINQ to DataSet 專案在 Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md)。  
  
## <a name="select"></a>選取  
  
### <a name="example"></a>範例  
 這則範例會使用 <xref:System.Linq.Enumerable.Select%2A> 方法來傳回 `Product` 資料表中的所有資料列，並顯示產品名稱。  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a>範例  
 這則範例會使用 <xref:System.Linq.Enumerable.Select%2A> 來單獨傳回產品名稱的序列 (Sequence)。  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple2)]  
  
## <a name="selectmany"></a>SelectMany  
  
### <a name="example"></a>範例  
 這則範例會使用 `From …, …` (<xref:System.Linq.Enumerable.SelectMany%2A> 方法的對等項目) 來選取 `TotalDue` 少於 500.00 的所有訂單。  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a>範例  
 這則範例會使用 `From …, …` (<xref:System.Linq.Enumerable.SelectMany%2A> 方法的對等項目) 來選取在 2002 年 10 月 1 日或之後下單的所有訂單。  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a>範例  
 這則範例會使用 `From …, …` (<xref:System.Linq.Enumerable.SelectMany%2A> 方法的對等項目) 來選取訂單總金額超過 10000.00 的所有訂單，並使用 `From` 指派來避免要求總金額兩次。  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a>另請參閱  
 [載入資料至資料集](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [LINQ to DataSet 範例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [標準查詢運算子概觀](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
