---
title: 將資料載入至資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 53f0f5a589a0033c9612f0465dff090ab04e3fc4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794951"
---
# <a name="loading-data-into-a-dataset"></a>將資料載入至資料集
必須先填入物件，才能使用 LINQ to DataSet 來查詢它。 <xref:System.Data.DataSet> 目前有許多不同的方式可以填入 <xref:System.Data.DataSet>。 例如，您可以使用[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]來查詢資料庫，並將結果<xref:System.Data.DataSet>載入。 如需詳細資訊，請參閱 [LINQ to SQL](./sql/linq/index.md)。  
  
 另一種將資料載入 <xref:System.Data.DataSet> 的常見方式是使用 <xref:System.Data.Common.DataAdapter> 類別 (Class)，從資料庫中擷取資料。 下列範例可說明此點。  
  
## <a name="example"></a>範例  
 這則範例會使用 <xref:System.Data.Common.DataAdapter>，在 AdventureWorks 資料庫中查詢是否有 2002 年的銷售資訊，然後將結果載入 <xref:System.Data.DataSet>。 <xref:System.Data.DataSet>填入之後，您可以使用 LINQ to DataSet 針對它撰寫查詢。 此`FillDataSet`範例中的方法用於[LINQ to DataSet 範例](linq-to-dataset-examples.md)中的範例查詢。 如需詳細資訊，請參閱[查詢資料集](querying-datasets-linq-to-dataset.md)。  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a>另請參閱

- [LINQ to DataSet 概觀](linq-to-dataset-overview.md)
- [查詢資料集](querying-datasets-linq-to-dataset.md)
- [LINQ to DataSet 範例](linq-to-dataset-examples.md)
