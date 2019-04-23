---
title: 導覽 DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: 91db42acb0e09b8fc99b0ee710a60800d40938ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59112849"
---
# <a name="navigating-datatables"></a>導覽 DataTable
<xref:System.Data.DataTableReader> 會以一或多個唯讀、順向結果集的形式，取得一或多個 <xref:System.Data.DataTable> 物件的內容。  
  
 如果 <xref:System.Data.DataTableReader> 是使用 <xref:System.Data.DataSet.CreateDataReader%2A> 方法而建立，則可能包含多個結果集。 有多個結果集時，<xref:System.Data.DataTableReader.NextResult%2A> 方法會將游標移到下一個結果集。 這是順向的處理序。 且不可能返回前一個結果集。  
  
## <a name="example"></a>範例  
 在下列範例中，`TestConstructor`方法會建立兩個<xref:System.Data.DataTable>執行個體。 為了示範這個建構函式<xref:System.Data.DataTableReader>類別，此範例會建立新**DataTableReader**根據內含兩個陣列**DataTables**，並執行簡單的作業，前幾個資料行的內容列印至主控台視窗。  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [DataTableReader](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
