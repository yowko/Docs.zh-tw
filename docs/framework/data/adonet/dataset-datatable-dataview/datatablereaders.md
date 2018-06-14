---
title: DataTableReader
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 8305629bb267805cd79455e2edf990e72a12dc10
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756094"
---
# <a name="datatablereaders"></a>DataTableReader
<xref:System.Data.DataTableReader> 會以一個或多個唯讀順向結果集的形式來呈現 <xref:System.Data.DataTable> 或 <xref:System.Data.DataSet> 的內容。  
  
 當您建立**DataTableReader**從**DataTable**，產生**DataTableReader**物件包含一個結果集具有相同的資料為**DataTable**它是用來建立，除了已標示為已刪除的任何資料列。 資料行出現在相同的順序，與原始**DataTable**。  
  
 A **DataTableReader**可能包含多個結果集，如果它由呼叫建立<xref:System.Data.DataSet.CreateDataReader%2A>。 結果會依照相同順序**Datatable**中**資料集**物件的<xref:System.Data.DataSet.Tables%2A>集合。  
  
## <a name="in-this-section"></a>本節內容  
 [建立 DataReader](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 討論如何建立**DataTableReader**物件。  
  
 [導覽 DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 說明如何使用**讀取**方法來移動的內容**DataTableReader**。  
  
## <a name="see-also"></a>另請參閱  
 [在 ADO.NET 中擷取和修改資料](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
