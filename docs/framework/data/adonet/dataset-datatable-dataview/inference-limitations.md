---
title: 推斷限制
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 10347abc5b01edb4ec6fbf97221d44f4bfb88f54
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784585"
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
  
 對於 "Document1"，推斷程式會產生名為 "DocumentElement" 的**資料集**，以及名為 "Element1" 的資料表，因為 "Element1" 是重複的元素。  
  
 **集中**DocumentElement  
  
 **目錄**Element1  
  
|Element1_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
 不過，針對 "Document2.docx"，推斷程式會產生名為 "NewDataSet" 的**資料集**，以及名為 "DocumentElement" 的資料表。 Element1 會被推斷為資料行，因為它沒有屬性和項目子系。  
  
 **集中**NewDataSet  
  
 **目錄**DocumentElement  
  
|Element1|  
|--------------|  
|Text1|  
  
 這兩份 XML 文件原本可能意圖要產生相同的結構描述，但是根據每份文件包含的項目，推斷程序產生了相當不同的結果。  
  
 若要避免從 XML 檔產生架構時可能發生的不一致，我們建議您在從 XML 載入**資料集**時，使用 xml 架構定義語言（XSD）或 Xml 資料精簡（XDR）明確地指定架構。 如需明確指定具有 XML 架構之**資料集**架構的詳細資訊，請參閱[從 XML 架構（XSD）衍生資料集關聯式結構](deriving-dataset-relational-structure-from-xml-schema-xsd.md)。  
  
## <a name="see-also"></a>另請參閱

- [從 XML 推斷資料集關聯式結構](inferring-dataset-relational-structure-from-xml.md)
- [從 XML 載入資料集](loading-a-dataset-from-xml.md)
- [從 XML 載入資料集結構描述資訊](loading-dataset-schema-information-from-xml.md)
- [在 DataSet 中使用 XML](using-xml-in-a-dataset.md)
- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET 概觀](../ado-net-overview.md)
