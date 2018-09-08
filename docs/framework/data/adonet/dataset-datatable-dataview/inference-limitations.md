---
title: 推斷限制
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: d113df98cdd339300b3e75ceda49a56d4f346d3c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44190674"
---
# <a name="inference-limitations"></a>推斷限制
根據每份文件的 XML 項目，當您執行從 XML 推斷 <xref:System.Data.DataSet> 結構描述的處理序時，可能會得到不同的結構描述。 例如，請考量下列 XML 文件。  
  
 Document1:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Document2:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 針對 「 文件 1 」，推斷程序會產生**資料集**名為"DocumentElement 」 和名為"Element1，"因為 「 Element1 」 是重複的項目。  
  
 **資料集：** DocumentElement  
  
 **資料表：** Element1  
  
|Element1_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
 不過，針對 「 Document2"，推斷程序會產生**資料集**名為"NewDataSet"和名為"DocumentElement。 」 Element1 會被推斷為資料行，因為它沒有屬性和項目子系。  
  
 **資料集：** NewDataSet  
  
 **資料表：** DocumentElement  
  
|Element1|  
|--------------|  
|Text1|  
  
 這兩份 XML 文件原本可能意圖要產生相同的結構描述，但是根據每份文件包含的項目，推斷程序產生了相當不同的結果。  
  
 若要避免從 XML 文件產生結構描述時，可能會發生不一致，我們建議您明確指定載入時，使用 XML 結構描述定義語言 (XSD) 或 XML 資料精簡 (XDR) 結構描述**資料集**從XML。 如需有關明確指定**資料集**結構描述與 XML 結構描述，請參閱[衍生的資料集關聯式結構從 XML 結構描述 (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)。  
  
## <a name="see-also"></a>另請參閱  
 [從 XML 推斷資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [從 XML 載入資料集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [從 XML 載入資料集結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
