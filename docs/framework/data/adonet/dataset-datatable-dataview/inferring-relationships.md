---
title: 推斷關聯性
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 92a4953dc7f5119ffbf171ff2a7bf5b58e896638
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204766"
---
# <a name="inferring-relationships"></a>推斷關聯性
若被推斷為資料表的項目具有子項目，且子項目也被推斷為資料表，則兩個資料表間會建立 <xref:System.Data.DataRelation>。 系統會將名稱為**ParentTableName_Id**的新資料行加入至針對父元素所建立的資料表, 以及為子項目建立的資料表。 此識別欄位的**ColumnMapping**屬性將會設定為**MappingType。** 此資料行將會是父資料表的自動遞增主鍵, 並會用於這兩個數據表之間的**DataRelation** 。 加入之識別欄位的資料類型會是 system.string, 而不像所有其他推斷資料行的資料類型, 也就是**system.string**。 具有 DeleteRule**Cascade 的**會同時使用父資料表和子資料工作表中的新資料行建立。 <xref:System.Data.ForeignKeyConstraint>  =   
  
 例如，請考量下列 XML：  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 推斷處理序會產生兩個資料表：**Element1**和**ChildElement1**。  
  
 **Element1**資料表會有兩個數據行:**Element1_Id**和**ChildElement2**。 **Element1_Id**資料行的**ColumnMapping**屬性會設定為**MappingType。 Hidden**。 **ChildElement2**資料行的**ColumnMapping**屬性會設定為**MappingType。** **Element1_Id**資料行會設定為**Element1**資料表的主要索引鍵。  
  
 **ChildElement1**資料表會有三個數據行: **attr1**、 **attr2**和**Element1_Id**。 **Attr1**和**attr2**資料行的**ColumnMapping**屬性將會設定為**MappingType. Attribute**。 **Element1_Id**資料行的**ColumnMapping**屬性會設定為**MappingType。 Hidden**。  
  
 會使用兩個數據表中的**Element1_Id**資料行來建立**DataRelation**和**ForeignKeyConstraint** 。  
  
 **集中**DocumentElement  
  
 **目錄**Element1  
  
|Element1_Id|ChildElement2|  
|------------------|-------------------|  
|0|Text2|  
  
 **目錄**ChildElement1  
  
|attr1|attr2|Element1_Id|  
|-----------|-----------|------------------|  
|value1|value2|0|  
  
 **DataRelation**Element1_ChildElement1  
  
 **ParentTable**Element1  
  
 **ParentColumn**Element1_Id  
  
 **ChildTable**ChildElement1  
  
 **ChildColumn**Element1_Id  
  
 **嵌套**True  
  
 **ForeignKeyConstraint**Element1_ChildElement1  
  
 **排**Element1_Id  
  
 **ParentTable**Element1  
  
 **ChildTable**ChildElement1  
  
 **DeleteRule**Cascade  
  
 **AcceptRejectRule**無  
  
## <a name="see-also"></a>另請參閱

- [從 XML 推斷資料集關聯式結構](inferring-dataset-relational-structure-from-xml.md)
- [從 XML 載入資料集](loading-a-dataset-from-xml.md)
- [從 XML 載入資料集結構描述資訊](loading-dataset-schema-information-from-xml.md)
- [巢狀 DataRelation](nesting-datarelations.md)
- [在 DataSet 中使用 XML](using-xml-in-a-dataset.md)
- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
