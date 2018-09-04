---
title: DataView
ms.date: 03/30/2017
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
ms.openlocfilehash: 75719e91daba189c1d93491a1db26acc80100bea
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514748"
---
# <a name="dataviews"></a>DataView
<xref:System.Data.DataView> 允許您為儲存在 <xref:System.Data.DataTable> 內的資料建立不同的檢視，這是資料繫結應用程式中常用的功能。 使用**DataView**可以公開資料表以不同排序順序中的資料，您可以依資料列狀態或根據篩選條件運算式來篩選資料。  
  
 A **DataView**提供動態檢視的資料在基礎**DataTable**： 內容、 順序和成員資格反映的變更發生時。 此行為不同於**選取 **方法**DataTable**，以傳回<xref:System.Data.DataRow>特定的篩選和/或排序順序為基礎的資料表中的陣列： thiscontent 反映的變更基礎資料表，但其成員資格和順序仍維持靜態。 動態功能**DataView**適合用來資料繫結的應用程式。  
  
 A **DataView**您提供一組資料，很像資料庫檢視，您可以套用不同的排序和篩選準則的動態檢視。 與資料庫檢視，不過，不同**DataView**無法被視為資料表，而無法提供聯結資料表的檢視。 此外，您也不能排除來源資料表中的資料行，也不能附加來源資料表中不存在的資料行 (如計算資料行)。  
  
 您可以使用<xref:System.Data.DataView.DataViewManager%2A>管理中的所有資料表的檢視設定**資料集**。 **DataViewManager**提供便利的方式來管理每個資料表的預設檢視設定。 將控制項繫結至多個資料表時**資料集**繫結至**DataViewManager**是理想的選擇。  
  
## <a name="in-this-section"></a>本節內容  
 [建立 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataview.md)  
 描述如何建立**DataView** for **DataTable**。  
  
 [排序和篩選資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 描述如何設定的屬性**DataView**符合特定篩選準則，傳回的資料列的子集，或以特定的排序順序傳回資料。  
  
 [DataRow 和 DataRowView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarows-and-datarowviews.md)  
 描述如何存取所公開的資料**DataView**。  
  
 [尋找資料列](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)  
 描述如何尋找特定資料列**DataView**。  
  
 [子檢視和關聯](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/childviews-and-relations.md)  
 描述如何建立從父子式關聯性使用的資料檢視**DataView**。  
  
 [修改 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/modifying-dataviews.md)  
 描述如何修改的資料在基礎**DataTable**透過**DataView**，包括啟用或停用更新。  
  
 [處理 DataView 事件](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataview-events.md)  
 描述如何使用**ListChanged**事件，以接收通知時的內容或順序**DataView**正在更新。  
  
 [管理 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/managing-dataviews.md)  
 描述如何使用**DataViewManager**來管理**DataView**設定中每個資料表**資料集**。  
  
## <a name="related-sections"></a>相關章節  
 [ASP.NET Web 應用程式](https://msdn.microsoft.com/library/a812d7b7-049e-4234-a4c2-6acf690301f6)  
 提供 ASP.NET 應用程式、Web Form 和 Web 服務的建立概觀和詳細的步驟程序。  
  
 [Windows 應用程式](https://msdn.microsoft.com/library/a6bb2180-09b1-4738-b9fd-7fb05fc92f23)  
 提供有關使用 Windows Form 和主控台應用程式的詳細資訊。  
  
 [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 描述**資料集**物件及如何使用它來管理應用程式資料。  
  
 [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 描述**DataTable**物件，以及如何使用它來管理應用程式資料本身，或做為一部分**DataSet**。  
  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 說明 ADO.NET 的架構和元件，以及如何使用 ADO.NET 來存取現有資料來源和管理應用程式資料。  
  
## <a name="see-also"></a>另請參閱  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
