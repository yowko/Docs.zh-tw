---
title: 推斷項目文字
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: b32d8f3f89a16166ffc0e903ef1f63c3b97a249c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762711"
---
# <a name="inferring-element-text"></a>推斷項目文字
如果項目包含文字，而且沒有任何子項目，來推斷為資料表 （具有屬性的項目） 或重複的項目，例如新的資料行名稱**TableName_Text**將加入至項目推斷的資料表。 項目中包含的文字會加入資料表中的資料列，並儲存在新資料行內。 **ColumnMapping**新資料行的屬性會設定為**MappingType.SimpleContent**。  
  
 例如，請考量下列 XML。  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 推斷程序將會產生名為的資料表**Element1**與兩個資料行： **attr1**和**Element1_Text**。 **ColumnMapping**屬性**attr1**資料行設定**MappingType.Attribute**。 **ColumnMapping**屬性**Element1_Text**資料行設定**MappingType.SimpleContent**。  
  
 **資料集：** DocumentElement  
  
 **Table:** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|value1|Text1|  
  
 如果項目包含文字，但是它的項目子系也包含文字，則不會有資料行加入資料表來儲存項目中包含的文字。 包含在項目中的文字會被忽略，而項目子系中的文字會被包含在資料表的資料列內。 例如，請考量下列 XML。  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 推斷程序將會產生名為的資料表**Element1**包含一個資料行名為**ChildElement1**。 文字**ChildElement1**項目將會包含在資料表中的資料列。 其他文字則被忽略。 **ColumnMapping**屬性**ChildElement1**資料行設定**MappingType.Element**。  
  
 **資料集：** DocumentElement  
  
 **Table:** Element1  
  
|ChildElement1|  
|-------------------|  
|Text2|  
  
## <a name="see-also"></a>另請參閱  
 [從 XML 推斷資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [從 XML 載入資料集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [從 XML 載入資料集結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
