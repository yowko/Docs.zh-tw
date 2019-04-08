---
title: 從 XML 推斷資料集關聯式結構
ms.date: 03/30/2017
ms.assetid: cd2f41c6-6785-420e-aa43-3ceb0bdccdce
ms.openlocfilehash: 9a9dc7d94728ea797a8930d3f77068fdd3ebfb5c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191533"
---
# <a name="inferring-dataset-relational-structure-from-xml"></a>從 XML 推斷資料集關聯式結構
<xref:System.Data.DataSet> 的關聯式結構或結構描述是由資料表、資料行、條件約束和關聯所組成。 從 XML 載入 <xref:System.Data.DataSet> 時，可預先定義結構描述，也可從正在載入的 XML 中，明確或透過介面建立。 如需載入的結構描述和內容的詳細資訊<xref:System.Data.DataSet>從 XML，請參閱[從 XML 載入 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)並[從 XML 載入資料集結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)。  
  
 如果的結構描述<xref:System.Data.DataSet>正在建立從 XML 的慣用的方法是明確指定使用 XML 結構描述定義語言 (XSD) 結構描述 (如中所述[衍生資料集關聯式結構從 XML 結構描述 (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)) 或 XML 資料精簡 (XDR)。 如果 XML 中沒有可用的 XML 結構描述或 XDR 結構描述，可從 XML 項目和屬性的結構推斷出 <xref:System.Data.DataSet> 的結構描述。  
  
 本節藉由顯示 XML 項目和屬性及其結構，以及產生的推斷 <xref:System.Data.DataSet> 結構描述，說明 <xref:System.Data.DataSet> 結構描述的推斷規則。  
  
 推斷程序中並不需要包含 XML文件中的所有屬性。 符合命名空間的屬性可包含對 XML 文件重要、但對 <xref:System.Data.DataSet> 結構描述不重要的中繼資料。 您可以使用 <xref:System.Data.DataSet.InferXmlSchema%2A>，指定在推斷處理序中要忽略的命名空間。 如需詳細資訊，請參閱 <<c0> [ 從 XML 載入資料集結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [資料集結構描述推斷程序摘要](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/summary-of-the-dataset-schema-inference-process.md)  
 提供進階摘要，說明從 XML 推斷 <xref:System.Data.DataSet> 結構描述的規則。  
  
 [推斷資料表](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)  
 說明被推斷為 <xref:System.Data.DataSet> 中資料表的 XML 項目。  
  
 [推斷資料行](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-columns.md)  
 說明被推斷為資料表資料行的 XML 項目和屬性。  
  
 [推斷關聯性](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-relationships.md)  
 說明針對巢狀推斷資料表建立的 <xref:System.Data.DataRelation> 和 <xref:System.Data.ForeignKeyConstraint> 物件。  
  
 [推斷項目文字](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-element-text.md)  
 說明建立為 XML 項目內文字的資料行，並說明 XML 項目中的文字何時會被忽略。  
  
 [推斷限制](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inference-limitations.md)  
 討論結構描述推論的限制。  
  
## <a name="related-sections"></a>相關章節  
 [在資料集中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 說明 <xref:System.Data.DataSet> 物件如何與 XML 資料互動。  
  
 [從 XML 結構描述 (XSD) 衍生資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 說明根據 XML 結構描述定義語言 (XSD) 結構描述所建立的 <xref:System.Data.DataSet> 關聯式結構 (或結構描述)。  
  
 [ADO.NET 概觀](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 描述 ADO.NET 的架構和元件，以及如何使用它們來存取現有資料來源和管理應用程式資料。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET Managed 提供者和DataSet開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
