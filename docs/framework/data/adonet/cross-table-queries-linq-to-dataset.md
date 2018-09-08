---
title: 跨資料表查詢 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
ms.openlocfilehash: 811d177b730a6a2160e37ef827a2456e6ac589e4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185872"
---
# <a name="cross-table-queries-linq-to-dataset"></a>跨資料表查詢 (LINQ to DataSet)
除了查詢單一資料表以外，您也可以在 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 中執行跨資料表查詢。 這是藉由使用*聯結*。 聯結是指某個資料來源中的物件與另一個資料來源中共用相同屬性之物件的關聯，例如產品或連絡人識別碼。 在物件導向的程式設計中，物件之間的關聯性相當容易瀏覽，因為每個物件都具有參考另一個物件的成員。 不過，在外部資料庫資料表中，瀏覽關聯性就沒有這麼直接。 資料庫資料表不包含內建關聯性。 在這些情況中，聯結作業可用來比對每個來源的項目。 例如，假設有兩個包含產品資訊和銷售資訊的資料表。此時，您可能會使用聯結作業，針對相同銷售訂單比對銷售資訊和產品。  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] Framework 提供兩個聯結運算子<xref:System.Linq.Enumerable.Join%2A>和<xref:System.Linq.Enumerable.GroupJoin%2A>。 這些運算子會執行*等聯結 （equi-join）*： 也就是聯結的比對兩個資料來源只有當索引鍵相等。 (相較之下，[!INCLUDE[tsql](../../../../includes/tsql-md.md)] 支援 `equals` 以外的聯結運算子，例如 `less than` 運算子)。  
  
 在關聯式資料庫詞彙中，<xref:System.Linq.Enumerable.Join%2A> 會實作內部聯結 (Inner Join)。 內部聯結是一種聯結類型，而這種聯結只會傳回在相對資料集內部具有相符項目的物件。  
  
 <xref:System.Linq.Enumerable.GroupJoin%2A>運算子具有不直接等同於關聯式資料庫規定; 它們會實作內部聯結和左方外部聯結的超集。 左方外部聯結是傳回的第一個 （左） 集合，每個元素的聯結，即使它在第二個集合中有任何相互關聯的項目。  
  
 如需有關聯結的詳細資訊，請參閱 <<c0> [ 聯結作業](https://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107)。  
  
## <a name="example"></a>範例  
 下列範例會針對 AdventureWorks 範例資料庫的 `SalesOrderHeader` 和 `SalesOrderDetail` 資料表執行傳統聯結，以便取得八月份的線上訂單。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>另請參閱  
 [查詢資料集](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [單一資料表查詢](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 [查詢具類型資料集](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 [聯結作業](https://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107)  
 [LINQ to DataSet 範例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
