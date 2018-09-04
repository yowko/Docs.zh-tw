---
title: 推斷關聯性
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 7dc3fb0c6098d636e640aaf52b72a404c1486492
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565587"
---
# <a name="inferring-relationships"></a>推斷關聯性
若被推斷為資料表的項目具有子項目，且子項目也被推斷為資料表，則兩個資料表間會建立 <xref:System.Data.DataRelation>。 新的資料行名稱取代**ParentTableName_Id**會新增至父元素中，建立的資料表和子元素所建立的資料表。 **ColumnMapping**此識別欄位的屬性會設定為**MappingType.Hidden**。 將會自動遞增主索引鍵的父資料表，資料行，並將用於**DataRelation**兩個資料表之間。 新增的身分識別資料行的資料型別會**System.Int32**，其他所有推斷的資料行的資料型別，即**System.String**。 A<xref:System.Data.ForeignKeyConstraint>具有**DeleteRule** = **Cascade**也會建立在父和子資料表中使用新的資料行。  
  
 例如，請考量下列 XML：  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 推斷程序會產生兩個資料表： **Element1**並**ChildElement1**。  
  
 **Element1**資料表會有兩個資料行： **Element1_Id**並**ChildElement2**。 **ColumnMapping**屬性**Element1_Id**資料行都會設定為**MappingType.Hidden**。 **ColumnMapping**屬性**ChildElement2**資料行都會設定為**MappingType.Element**。 **Element1_Id**資料行都會設定為的主索引鍵**Element1**資料表。  
  
 **ChildElement1**資料表會有三個資料行： **attr1**， **attr2**並**Element1_Id**。 **ColumnMapping**屬性**attr1**並**attr2**資料行都會設定為**MappingType.Attribute**。 **ColumnMapping**屬性**Element1_Id**資料行都會設定為**MappingType.Hidden**。  
  
 A **DataRelation**並**ForeignKeyConstraint**將會使用建立**Element1_Id**兩個資料表的資料行。  
  
 **資料集：** DocumentElement  
  
 **資料表：** Element1  
  
|Element1_Id|ChildElement2|  
|------------------|-------------------|  
|0|Text2|  
  
 **資料表：** ChildElement1  
  
|attr1|attr2|Element1_Id|  
|-----------|-----------|------------------|  
|value1|value2|0|  
  
 **DataRelation:** Element1_ChildElement1  
  
 **ParentTable:** Element1  
  
 **ParentColumn:** Element1_Id  
  
 **ChildTable:** ChildElement1  
  
 **ChildColumn:** Element1_Id  
  
 **巢狀：** ，則為 True  
  
 **ForeignKeyConstraint:** Element1_ChildElement1  
  
 **資料行：** Element1_Id  
  
 **ParentTable:** Element1  
  
 **ChildTable:** ChildElement1  
  
 **DeleteRule:** 重疊顯示  
  
 **AcceptRejectRule:** None  
  
## <a name="see-also"></a>另請參閱  
 [從 XML 推斷資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [從 XML 載入資料集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [從 XML 載入資料集結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [巢狀 DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
