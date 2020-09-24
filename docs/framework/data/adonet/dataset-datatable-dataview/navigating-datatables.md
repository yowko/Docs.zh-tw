---
title: 導覽 DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: 9b7ed4ef1dbe141d8f6a1b6c6b9af2fd89e6c7af
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148304"
---
# <a name="navigating-datatables"></a>導覽 DataTable

<xref:System.Data.DataTableReader> 會以一或多個唯讀、順向結果集的形式，取得一或多個 <xref:System.Data.DataTable> 物件的內容。  
  
 如果 <xref:System.Data.DataTableReader> 是使用 <xref:System.Data.DataSet.CreateDataReader%2A> 方法而建立，則可能包含多個結果集。 有多個結果集時，<xref:System.Data.DataTableReader.NextResult%2A> 方法會將游標移到下一個結果集。 這是順向的處理序。 且不可能返回前一個結果集。  
  
## <a name="example"></a>範例  

 在下列範例中， `TestConstructor` 方法會建立兩個 <xref:System.Data.DataTable> 實例。 為了示範這個類別的這個函式 <xref:System.Data.DataTableReader> ，此範例會根據包含兩個**datatable**的陣列建立新的**DataTableReader** ，並執行簡單的作業，將前幾個資料行的內容列印到主控台視窗。  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [DataTableReader](datatablereaders.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
