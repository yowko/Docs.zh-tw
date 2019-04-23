---
title: 在資料集中使用 XML
ms.date: 03/30/2017
ms.assetid: 35138159-e199-49ec-baf7-1ec6777e171e
ms.openlocfilehash: 9e586ff0c6f28dd5919bc8b1bc640389a5cad610
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087415"
---
# <a name="using-xml-in-a-dataset"></a>在資料集中使用 XML
透過 ADO.NET，您可以從 XML 資料流或文件填滿 <xref:System.Data.DataSet>。 您可以使用 XML 資料流或文件，為 <xref:System.Data.DataSet> 提供資料、結構描述資訊或同時提供這兩者。 由 XML 資料流或文件提供的資訊，可與 <xref:System.Data.DataSet> 中的現有資料或結構描述資訊結合。  
  
 ADO.NET 也可讓您建立 <xref:System.Data.DataSet> 的 XML 表示 (可具備或不具備其結構描述)，以便透過 HTTP 將 <xref:System.Data.DataSet> 傳輸給另一個應用程式或啟用 XML 的平台使用。 在 <xref:System.Data.DataSet> 的 XML 表示中，資料是以 XML 撰寫的；而結構描述如果是內嵌在表示中，則是以 XML 結構描述定義語言 (XSD) 所撰寫。 XML 和 XML 結構描述可讓您用方便的格式將 <xref:System.Data.DataSet> 的內容傳輸給遠端用戶端，也可以從遠端用戶端傳出。  
  
## <a name="in-this-section"></a>本節內容  
 [DiffGram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 提供 DiffGram 的詳細資訊，這是用來讀取和寫入 <xref:System.Data.DataSet> 內容的 XML 格式。  
  
 [從 XML 載入資料集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 討論從 XML 文件載入 <xref:System.Data.DataSet> 內容時，需要考慮的不同選項。  
  
 [將資料集內容當作 XML 資料寫入](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 討論如何將 <xref:System.Data.DataSet> 的內容產生為 XML 資料，以及您可以使用的不同 XML 格式選項。  
  
 [從 XML 載入資料集結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 討論可從 XML 載入 <xref:System.Data.DataSet> 之結構描述的 <xref:System.Data.DataSet> 方法。  
  
 [將資料集結構描述資訊當作 XSD 寫入](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)  
 討論 XML 結構描述的使用方式，以及如何從 <xref:System.Data.DataSet> 產生 XML 結構描述。  
  
 [資料集和 XmlDataDocument 同步處理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 討論 .NET Framework 中有哪些可用功能可同步存取單一資料集的關聯式和階層式檢閱，以及如何在 <xref:System.Data.DataSet> 與 <xref:System.Xml.XmlDataDocument> 之間建立同步關係。  
  
 [巢狀 DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 討論將 <xref:System.Data.DataRelation> 的內容表示為 XML 資料時，巢狀 <xref:System.Data.DataSet> 物件的重要性，並描述如何建立這些關聯性。  
  
 [從 XML 結構描述 (XSD) 衍生資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 說明從 XML 結構描述中建立的 <xref:System.Data.DataSet> 之關聯式結構 (或結構描述)。  
  
 [從 XML 推斷資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 說明從 XML 項目推斷時所建立的 <xref:System.Data.DataSet> 關聯式結構或結構描述。  
  
## <a name="related-sections"></a>相關章節  
 [ADO.NET 概觀](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 說明 ADO.NET 的架構和元件，以及如何使用它們來存取現有資料來源和管理應用程式資料。  
  
## <a name="see-also"></a>另請參閱

- [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
