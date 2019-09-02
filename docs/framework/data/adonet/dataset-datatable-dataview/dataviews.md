---
title: DataView
ms.date: 03/30/2017
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
ms.openlocfilehash: f362e4807bce4fb0e3e8c9ae8cdd6b4704fc28aa
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203798"
---
# <a name="dataviews"></a>DataView
<xref:System.Data.DataView> 允許您為儲存在 <xref:System.Data.DataTable> 內的資料建立不同的檢視，這是資料繫結應用程式中常用的功能。 您可以使用**DataView**, 以不同的排序次序來公開資料表中的資料, 而且您可以依資料列狀態或根據篩選運算式來篩選資料。  
  
 **DataView**提供基礎**DataTable**中資料的動態視圖: 內容、排序和成員資格會反映發生的變更。 此行為不同于**DataTable**的<xref:System.Data.DataRow> **Select**方法, 它會根據特定篩選和/或排序次序, 從資料表傳回陣列: 此內容反映基礎資料表的變更, 但其成員資格和順序維持靜態。 **DataView**的動態功能讓資料系結應用程式非常理想。  
  
 **DataView**提供您單一資料集的動態觀點, 與資料庫的觀點相似, 您可以套用不同的排序和篩選準則。 不過, 不同于資料庫檢視, **DataView**無法被視為資料表, 而且無法提供聯結資料表的觀點。 此外，您也不能排除來源資料表中的資料行，也不能附加來源資料表中不存在的資料行 (如計算資料行)。  
  
 您可以使用<xref:System.Data.DataView.DataViewManager%2A>來管理**資料集中**所有資料表的視圖設定。 **DataViewManager**提供便利的方式來管理每個資料表的預設 view 設定。 將控制項系結至**資料集**的多個資料表時, 系結至**DataViewManager**是理想的選擇。  
  
## <a name="in-this-section"></a>本節內容  
 [建立 DataView](creating-a-dataview.md)  
 描述如何建立**DataTable**的**DataView** 。  
  
 [排序和篩選資料](sorting-and-filtering-data.md)  
 描述如何設定**DataView**的屬性, 以傳回符合特定篩選準則的資料列子集, 或傳回特定排序次序的資料。  
  
 [DataRow 和 DataRowView](datarows-and-datarowviews.md)  
 描述如何存取**DataView**所公開的資料。  
  
 [尋找資料列](finding-rows.md)  
 描述如何尋找**DataView**中的特定資料列。  
  
 [子檢視和關聯](childviews-and-relations.md)  
 描述如何使用**DataView**建立來自父子式關聯性的資料檢視。  
  
 [修改 DataView](modifying-dataviews.md)  
 描述如何透過**DataView**修改基礎**DataTable**中的資料, 包括啟用或停用更新。  
  
 [處理 DataView 事件](handling-dataview-events.md)  
 描述當**DataView**的內容或順序更新時, 如何使用**ListChanged**事件來接收通知。  
  
 [管理 DataView](managing-dataviews.md)  
 描述如何使用**DataViewManager**來管理**資料集**內每個資料表的**DataView**設定。  
  
## <a name="related-sections"></a>相關章節  
 [ASP.NET Web 應用程式](https://docs.microsoft.com/previous-versions/655cec97(v=vs.100))  
 提供 ASP.NET 應用程式、Web Form 和 Web 服務的建立概觀和詳細的步驟程序。  
  
 [Windows 應用程式](https://docs.microsoft.com/previous-versions/ms184421(v=vs.100))  
 提供有關使用 Windows Form 和主控台應用程式的詳細資訊。  
  
 [DataSet、DataTable 和 DataView](index.md)  
 描述**DataSet**物件, 以及您可以如何使用它來管理應用程式資料。  
  
 [DataTable](datatables.md)  
 描述**DataTable**物件, 以及如何使用它來管理應用程式資料本身, 或做為**資料集**的一部分。  
  
 [ADO.NET](../index.md)  
 說明 ADO.NET 的架構和元件，以及如何使用 ADO.NET 來存取現有資料來源和管理應用程式資料。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
