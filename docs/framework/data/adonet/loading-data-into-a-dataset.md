---
title: 將資料載入至資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 0f50638beb50220d06daef7bbd6002b319a92476
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622958"
---
# <a name="loading-data-into-a-dataset"></a>將資料載入至資料集
<xref:System.Data.DataSet> 物件必須先填入 (Populate) 資料，然後您才能使用 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 來查詢它。 目前有許多不同的方式可以填入 <xref:System.Data.DataSet>。 例如，您可以使用[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]來查詢資料庫，並將結果載入<xref:System.Data.DataSet>。 如需詳細資訊，請參閱 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)。  
  
 另一種將資料載入 <xref:System.Data.DataSet> 的常見方式是使用 <xref:System.Data.Common.DataAdapter> 類別 (Class)，從資料庫中擷取資料。 下列範例將說明這種方式。  
  
## <a name="example"></a>範例  
 這則範例會使用 <xref:System.Data.Common.DataAdapter>，在 AdventureWorks 資料庫中查詢是否有 2002 年的銷售資訊，然後將結果載入 <xref:System.Data.DataSet>。 當 <xref:System.Data.DataSet> 已經填入資料之後，您就可以使用 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 來針對它撰寫查詢。 `FillDataSet`方法，在此範例中用於在此範例會查詢[LINQ to DataSet 範例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)。 如需詳細資訊，請參閱 <<c0> [ 查詢的資料集](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)。  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a>另請參閱
- [LINQ to DataSet 概觀](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)
- [查詢資料集](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [LINQ to DataSet 範例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
