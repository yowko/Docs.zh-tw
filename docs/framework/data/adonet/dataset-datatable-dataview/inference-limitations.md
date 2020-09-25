---
title: 推斷限制
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 9d8191be137661200e1a6b84d68328c1202880ca
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172771"
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
  
 針對 "Document1"，推斷進程會產生名為 "DocumentElement" 的 **資料集** 和名為 "Element1" 的資料表，因為 "Element1" 是重複的元素。  
  
 **資料集：** DocumentElement  
  
 **資料表：** Element1  
  
|Element1_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
 不過，對於 "Document2.xsl"，推斷進程會產生名為 "NewDataSet" 的 **資料集** 和名為 "DocumentElement" 的資料表。 Element1 會被推斷為資料行，因為它沒有屬性和項目子系。  
  
 **資料集：** NewDataSet  
  
 **資料表：** DocumentElement  
  
|Element1|  
|--------------|  
|Text1|  
  
 這兩份 XML 文件原本可能意圖要產生相同的結構描述，但是根據每份文件包含的項目，推斷程序產生了相當不同的結果。  
  
 若要避免從 XML 檔產生架構時可能發生的差異，我們建議您使用 XML 架構定義語言 (XSD) 或 XML 資料減少 (XDR 在從 XML 載入 **資料集** 時所) 的資料，來明確指定架構。 如需有關使用 XML 架構明確指定 **資料集** 架構的詳細資訊，請參閱 [從 XML 架構衍生資料集關聯式結構 (XSD) ](deriving-dataset-relational-structure-from-xml-schema-xsd.md)。  
  
## <a name="see-also"></a>另請參閱

- [從 XML 推斷資料集關聯式結構](inferring-dataset-relational-structure-from-xml.md)
- [從 XML 載入資料集](loading-a-dataset-from-xml.md)
- [從 XML 載入資料集結構描述資訊](loading-dataset-schema-information-from-xml.md)
- [在資料集中使用 XML](using-xml-in-a-dataset.md)
- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
