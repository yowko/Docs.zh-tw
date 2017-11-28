---
title: "將 unique XML 結構描述 (XSD) 條件約束對應至資料集條件約束"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 66183768b5b48608dc69a4021b27816595c43b4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>將 unique XML 結構描述 (XSD) 條件約束對應至資料集條件約束
中的 XML 結構描述定義語言 (XSD) 結構描述**唯一**項目會指定元素或屬性上條件約束的唯一性。 在將 XML 結構描述轉譯到關聯式結構描述的處理序中，會將 XML 結構描述內項目或屬性上指定的唯一的條件約束 (Constraint)，對應到所產生的對應 <xref:System.Data.DataTable> 內 <xref:System.Data.DataSet> 的唯一的條件約束。  
  
 下表概述**msdata**屬性中，您可以指定**唯一**項目。  
  
|屬性名稱|說明|  
|--------------------|-----------------|  
|**即**|如果指定這個屬性，則它的值會被當成條件約束名稱使用。 否則，**名稱**屬性提供條件約束名稱的值。|  
|**msdata**|如果`PrimaryKey="true"`存在於**唯一**項目，以建立唯一條件約束**IsPrimaryKey**屬性設定為**true**。|  
  
 下列範例顯示 XML 結構描述使用**唯一**項目指定唯一性條件約束。  
  
```xml  
<xs:schema id="SampleDataSet"   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:integer"   
           minOccurs="0"/>  
        <xs:element name="CompanyName" type="xs:string"   
           minOccurs="0"/>  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
  
 <xs:element name="SampleDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:unique     msdata:ConstraintName="UCustID"     name="UniqueCustIDConstr" >       <xs:selector xpath=".//Customers" />       <xs:field xpath="CustomerID" />     </xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 **唯一**結構描述中的元素會指定所有**客戶**文件中的項目執行個體的值**CustomerID**子元素必須是唯一。 在建置**資料集**，對應處理序讀取這個結構描述，並產生下列資料表：  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 對應處理序也上建立 unique 條件約束**CustomerID**資料行，如下所示**資料集**。 (為了便於了解，此處僅顯示相關屬性)。  
  
```  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID       Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID   
      IsPrimaryKey: False  
```  
  
 在**資料集**所產生， **IsPrimaryKey**屬性設定為**False**的唯一條件約束。 **唯一**資料行上的屬性是指出**CustomerID**必須是唯一的資料行值 (但可以是 null 參考，所指定**AllowDBNull**屬性的資料行）。  
  
 如果您修改結構描述，並設定選擇性**msdata**屬性值，以**True**，資料表上建立 unique 條件約束。 **AllowDBNull**資料行屬性設定為**False**，而**IsPrimaryKey**屬性設定為條件約束**True**，即可使**CustomerID**資料行主索引鍵資料行。  
  
 您可以在 XML 結構描述中，將唯一的條件約束指定給合併的項目或屬性。 下列範例示範如何指定的組合**CustomerID**和**CompanyName**值必須是唯一的所有**客戶**在任何情況下，由加入另一個**customers**結構描述中的項目。  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 這是建立在產生的條件約束**資料集**。  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>另請參閱  
 [將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [從 XML 結構描述 (XSD) 產生資料集關聯](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
