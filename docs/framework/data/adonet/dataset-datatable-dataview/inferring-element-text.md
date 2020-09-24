---
title: 推斷項目文字
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: 7389e24f39902edf041c3cd3502303b17fd008ba
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164684"
---
# <a name="inferring-element-text"></a>推斷項目文字

如果專案包含文字，而且沒有要推斷為數據表的子專案 (例如) 具有屬性或重複專案的元素，則會將名稱 **TableName_Text** 的新資料行加入至針對元素推斷的資料表中。 項目中包含的文字會加入資料表中的資料列，並儲存在新資料行內。 新資料行的**ColumnMapping**屬性將會設定為**MappingType。**  
  
 例如，請考量下列 XML。  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 推斷進程會產生名為 **Element1** 的資料表，其中包含兩個數據行： **attr1** 和 **Element1_Text**。 **Attr1**資料行的**ColumnMapping**屬性將會設定為**MappingType. Attribute**。 **Element1_Text**資料行的**ColumnMapping**屬性將會設定為**MappingType。**  
  
 **資料集：** DocumentElement  
  
 **資料表：** Element1  
  
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
  
 推斷進程會產生名為 **Element1** 的資料表，其中有一個名為 **ChildElement1**的資料行。 **ChildElement1**元素的文字將會包含在資料表的資料列中。 其他文字則被忽略。 **ChildElement1**資料行的**ColumnMapping**屬性將會設定為**MappingType. Element**。  
  
 **資料集：** DocumentElement  
  
 **資料表：** Element1  
  
|ChildElement1|  
|-------------------|  
|Text2|  
  
## <a name="see-also"></a>另請參閱

- [從 XML 推斷資料集關聯式結構](inferring-dataset-relational-structure-from-xml.md)
- [從 XML 載入資料集](loading-a-dataset-from-xml.md)
- [從 XML 載入資料集結構描述資訊](loading-dataset-schema-information-from-xml.md)
- [在資料集中使用 XML](using-xml-in-a-dataset.md)
- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
