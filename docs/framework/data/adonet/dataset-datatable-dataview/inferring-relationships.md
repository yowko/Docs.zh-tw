---
title: "推斷關聯性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 41c73ac31105cdae0a23c2367211747dee8d44f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="inferring-relationships"></a>推斷關聯性
若被推斷為資料表的項目具有子項目，且子項目也被推斷為資料表，則兩個資料表間會建立 <xref:System.Data.DataRelation>。 新的資料行名稱為**ParentTableName_Id**加入父項目建立的資料表和子元素所建立的資料表。 **ColumnMapping**此識別欄位的屬性會設定為**MappingType.Hidden**。 將會自動遞增主索引鍵的父資料表，資料行，並將用於**DataRelation**兩個資料表之間。 新增的身分識別資料行的資料型別會**System.Int32**，其他所有推斷資料行的資料類型，而是**System.String**。 A<xref:System.Data.ForeignKeyConstraint>與**DeleteRule** = **Cascade**也會建立在父和子資料表中使用新的資料行。  
  
 例如，請考量下列 XML：  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 推斷程序將會產生兩個資料表： **Element1**和**ChildElement1**。  
  
 **Element1**資料表會有兩個資料行： **Element1_Id**和**ChildElement2**。 **ColumnMapping**屬性**Element1_Id**資料行設定**MappingType.Hidden**。 **ColumnMapping**屬性**ChildElement2**資料行設定**MappingType.Element**。 **Element1_Id**資料行將設為主索引鍵的**Element1**資料表。  
  
 **ChildElement1**資料表會有三個資料行： **attr1**， **attr2**和**Element1_Id**。 **ColumnMapping**屬性**attr1**和**attr2**欄將會設定為**MappingType.Attribute**。 **ColumnMapping**屬性**Element1_Id**資料行設定**MappingType.Hidden**。  
  
 A **DataRelation**和**ForeignKeyConstraint**將會使用建立**Element1_Id**這兩個資料表的資料行。  
  
 **資料集：** DocumentElement  
  
 **Table:** Element1  
  
|Element1_Id|ChildElement2|  
|------------------|-------------------|  
|0|Text2|  
  
 **Table:** ChildElement1  
  
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
  
 **DeleteRule:**重疊顯示  
  
 **AcceptRejectRule:**無  
  
## <a name="see-also"></a>另請參閱  
 [從 XML 推斷資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [從 XML 載入資料集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [從 XML 載入資料集結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [巢狀 Datarelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
