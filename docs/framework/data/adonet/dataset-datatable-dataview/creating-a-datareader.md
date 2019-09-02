---
title: 建立 DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: cb39ead1fe15e3bfcf67370e4675dcae3bbf9801
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203891"
---
# <a name="creating-a-datareader"></a>建立 DataReader
<xref:System.Data.DataTable> 和 <xref:System.Data.DataSet> 類別 (Class) 具有 <xref:System.Data.DataTable.CreateDataReader%2A> 方法，可以用一或多個唯讀的順向結果集來傳回 <xref:System.Data.DataTable> 的內容或 <xref:System.Data.DataSet> 物件的 <xref:System.Data.DataSet.Tables%2A> 集合內容。  
  
## <a name="example"></a>範例  
 下列的主控台應用程式會建立 <xref:System.Data.DataTable> 執行個體 (Instance)。 然後, 此範例會將<xref:System.Data.DataTable>填滿的加入至<xref:System.Data.DataTable.CreateDataReader%2A>呼叫方法的程式, 以逐一查看包含在內<xref:System.Data.DataTableReader>的結果。  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 此範例會在主控台視窗中顯示以下輸出：  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [DataTableReader](datatablereaders.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
