---
title: DataTableReader
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 1559cde9cb786ccb2baf920347064b8b28d472c3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785352"
---
# <a name="datatablereaders"></a>DataTableReader
<xref:System.Data.DataTableReader> 會以一個或多個唯讀順向結果集的形式來呈現 <xref:System.Data.DataTable> 或 <xref:System.Data.DataSet> 的內容。  
  
 當您從**datatable**建立**DataTableReader**時，所產生的**DataTableReader**物件會包含一個結果集，其資料會與建立它的**datatable**相同，但已標示為的任何資料列除外刪除. 資料行會以與原始**DataTable**相同的順序出現。  
  
 如果**DataTableReader**是透過呼叫<xref:System.Data.DataSet.CreateDataReader%2A>來建立的，則可能包含多個結果集。 結果會與**資料集**物件<xref:System.Data.DataSet.Tables%2A>集合中的**datatable**順序相同。  
  
## <a name="in-this-section"></a>本節內容  
 [建立 DataReader](creating-a-datareader.md)  
 討論如何建立**DataTableReader**物件。  
  
 [導覽 DataTable](navigating-datatables.md)  
 描述如何使用**Read**方法，在**DataTableReader**的內容之間移動。  
  
## <a name="see-also"></a>另請參閱

- [在 ADO.NET 中擷取和修改資料](../retrieving-and-modifying-data.md)
- [ADO.NET 概觀](../ado-net-overview.md)
