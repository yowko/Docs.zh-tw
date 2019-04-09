---
title: 推斷資料行
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 53e77f624c5af8f61a32d5b1399d2728f32011a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107200"
---
# <a name="inferring-columns"></a>推斷資料行
ADO.NET 從 XML 文件中判斷要將哪些項目推斷成 <xref:System.Data.DataSet> 的資料表後，接著就會推斷這些資料表的資料行。 ADO.NET 2.0 導入了新結構描述推斷引擎，可推斷每個強型別的資料型別**simpleType**項目。 在舊版中中的資料型別推斷**simpleType**項目向來**xsd: string**。  
  
## <a name="migration-and-backward-compatibility"></a>移轉和回溯相容性  
 **ReadXml**方法會採用類型的引數**InferSchema**。 這個引數可讓您指定與舊版本相容的推斷行為。 可用的值**InferSchema**列舉型別會顯示下表中。  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 將簡單型別永遠推斷為 <xref:System.String>，以提供回溯相容性 (Backward Compatibility)。  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 推斷強型別資料型別。 若用於 <xref:System.Data.DataTable>，則會擲回例外狀況 (Exception)。  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 忽略任何內嵌結構描述，並將資料讀入現有的 <xref:System.Data.DataSet> 結構描述中。  
  
## <a name="attributes"></a>屬性  
 中所定義[推斷資料表](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)，具有屬性的項目會推斷為資料表。 然後，該項目的屬性會推斷為資料表的資料行。 **ColumnMapping**資料行的屬性會設定為**MappingType.Attribute**，以確保為屬性將寫入的資料行名稱，如果結構描述會寫回至 XML。 屬性的值儲存在資料表的資料列中。 例如，請考量下列 XML：  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 推斷程序會產生一個名為資料表**Element1**具有兩個資料行**attr1**並**attr2**。 **ColumnMapping**的兩個資料行的屬性會設定為**MappingType.Attribute**。  
  
 **資料集：** DocumentElement  
  
 **資料表：** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## <a name="elements-without-attributes-or-child-elements"></a>沒有屬性或項目子系的項目  
 如果項目沒有項目子系或屬性，則會推斷為資料行。 **ColumnMapping**資料行的屬性會設定為**MappingType.Element**。 項目子系的文字儲存在資料表的資料列中。 例如，請考量下列 XML：  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 推斷程序會產生一個名為資料表**Element1**具有兩個資料行**ChildElement1**並**ChildElement2**。 **ColumnMapping**的兩個資料行的屬性會設定為**MappingType.Element**。  
  
 **資料集：** DocumentElement  
  
 **資料表：** Element1  
  
|ChildElement1|ChildElement2|  
|-------------------|-------------------|  
|Text1|Text2|  
  
## <a name="see-also"></a>另請參閱

- [從 XML 推斷資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [從 XML 載入資料集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [從 XML 載入資料集結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [在資料集中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET Managed 提供者和DataSet開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
