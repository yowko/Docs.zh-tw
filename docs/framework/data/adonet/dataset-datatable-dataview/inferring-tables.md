---
title: 推斷資料表
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 38709f91e01c7f85d9e8482bdd49bc0892121f09
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2018
ms.locfileid: "43332849"
---
# <a name="inferring-tables"></a>推斷資料表
從 XML 文件推斷 <xref:System.Data.DataSet> 的結構描述時，ADO.NET 首先會決定要用哪些 XML 項目來表示資料表。 下列 XML 結構會導致資料表**資料集**結構描述：  
  
-   具有屬性的項目  
  
-   具有項目子系的項目  
  
-   重複項目  
  
## <a name="elements-with-attributes"></a>具有屬性的項目  
 具有指定屬性的項目會產生推斷資料表。 例如，請考量下列 XML：  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 推斷處理序會產生名為 Element1 的資料表。  
  
 **資料集：** DocumentElement  
  
 **資料表：** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|value1||  
|value2|Text1|  
  
## <a name="elements-with-child-elements"></a>具有項目子系的項目  
 具有項目子系的項目會產生推斷資料表。 例如，請考量下列 XML：  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 推斷處理序會產生名為 Element1 的資料表。  
  
 **資料集：** DocumentElement  
  
 **資料表：** Element1  
  
|ChildElement1|  
|-------------------|  
|Text1|  
  
 如果文件或根項目具有將推斷為資料行的屬性或項目子系，便會產生推斷資料表。 如果文件項目沒有屬性和任何子項目會推斷為資料行，將項目被推斷為**資料集**。 例如，請考量下列 XML：  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 推斷處理序會產生名為 DocumentElement 的資料表。  
  
 **資料集：** NewDataSet  
  
 **資料表：** DocumentElement  
  
|Element1|Element2|  
|--------------|--------------|  
|Text1|Text2|  
  
 另一個方法是考量下列 XML：  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 推斷程序會產生**資料集**名為"DocumentElement"，其中包含名為"Element1。 」  
  
 **資料集：** DocumentElement  
  
 **資料表：** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## <a name="repeating-elements"></a>重複項目  
 重複項目會產生單一推斷資料表。 例如，請考量下列 XML：  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 推斷處理序會產生名為 Element1 的資料表。  
  
 **資料集：** DocumentElement  
  
 **資料表：** Element1  
  
|Element1_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
## <a name="see-also"></a>另請參閱  
 [從 XML 推斷資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [從 XML 載入資料集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [從 XML 載入資料集結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
