---
title: DataTableReader
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 911a45dad3d5d82ab5e5752b1c12f7d8a6ab1563
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202314"
---
# <a name="datatablereaders"></a>DataTableReader

<xref:System.Data.DataTableReader> 會以一個或多個唯讀順向結果集的形式來呈現 <xref:System.Data.DataTable> 或 <xref:System.Data.DataSet> 的內容。  
  
 當您從**DataTable**建立**DataTableReader**時，產生的**DataTableReader**物件會包含一個結果集，其中包含與建立它的**datatable**相同的資料，但已標示為已刪除的任何資料列除外。 資料行的顯示順序與原始 **DataTable**中的順序相同。  
  
 **DataTableReader**可能包含多個結果集（如果是藉由呼叫來建立） <xref:System.Data.DataSet.CreateDataReader%2A> 。 結果會與**資料集**物件集合中的**datatable**順序相同 <xref:System.Data.DataSet.Tables%2A> 。  
  
## <a name="in-this-section"></a>本節內容  

 [建立 DataReader](creating-a-datareader.md)  
 討論如何建立 **DataTableReader** 物件。  
  
 [導覽 DataTable](navigating-datatables.md)  
 描述如何使用 **Read** 方法來移動 **DataTableReader**的內容。  
  
## <a name="see-also"></a>另請參閱

- [在 ADO.NET 中傳送和修改資料](../retrieving-and-modifying-data.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
