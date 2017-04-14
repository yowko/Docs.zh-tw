---
title: "將 XML 結構描述 (XSD) 索引鍵條件約束對應至 DataSet 條件約束 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 將 XML 結構描述 (XSD) 索引鍵條件約束對應至 DataSet 條件約束
您可以在結構描述中使用 **key** 項目，指定項目或屬性的索引鍵條件約束。  具有指定索引鍵條件約束的項目或屬性，在任何結構描述執行個體中都必須具有唯一的值，且不可具有 Null 值。  
  
 索引鍵條件約束類似唯一的條件約束，唯一的不同處定義索引鍵條件約束的資料行不能有 Null 值。  
  
 下表列出您可在 **key** 項目中指定的 **msdata** 屬性。  
  
|屬性名稱|描述|  
|----------|--------|  
|**msdata:ConstraintName**|如果指定這個屬性，則它的值會被當成條件約束名稱使用。  否則會由 **name** 屬性提供條件約束名稱的值。|  
|**msdata:PrimaryKey**|如果出現 `PrimaryKey="true"`，則 **IsPrimaryKey** 條件約束屬性會設為 **true**，使它成為主索引鍵。  **AllowDBNull** 資料行屬性設為 **false**，因為主索引鍵不能具有 Null 值。|  
  
 指定了索引鍵條件約束的結構描述在轉換過程中，對應處理序會在資料表上建立唯一的條件約束，而條件約束中每個資料行的 **AllowDBNull** 資料行屬性會設為 **false**。  除非您已經在 **key** 項目上指定 `msdata:PrimaryKey="true"`，不然唯一的條件約束的 **IsPrimaryKey** 屬性也會被設為 **false**。  它與結構描述 \(其中 `PrimaryKey="true"`\) 中唯一的條件約束相同。  
  
 下列結構描述範例中，**key** 項目指定 **CustomerID** 項目的索引鍵條件約束。  
  
```  
<xs:schema id="cod"  
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
        <xs:element name="CompanyName" type="xs:string" minOccurs="0" />  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:key  msdata:PrimaryKey="true"  
       msdata:ConstraintName="KeyCustID"  
          name="KeyConstCustomerID" >  
     <xs:selector xpath=".//Customers" />  
     <xs:field xpath="CustomerID" />  
    </xs:key>  
 </xs:element>  
</xs:schema>   
```  
  
 **key** 項目指定 **Customers** 項目的 **CustomerID** 項目子系值，必須具有唯一的值，且不可為 Null 值。  轉譯 XML 結構描述定義語言 \(XSD\) 結構描述的過程中，對應處理序會建立下表：  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 XML 結構描述對應也會在 **CustomerID** 資料行上建立 **UniqueConstraint**，如下列 <xref:System.Data.DataSet> 所示。  \(為了便於了解，此處僅顯示相關屬性\)。  
  
```  
  
      DataSetName: MyDataSet  
TableName: customers  
  ColumnName: CustomerID  
      AllowDBNull: False  
      Unique: True  
  ConstraintName: KeyCustID  
      Table: customers  
      Columns: CustomerID   
      IsPrimaryKey: True  
```  
  
 在產生的 **DataSet** 中，會將 **UniqueConstraint** 的 **IsPrimaryKey** 屬性設為 **true**，因為結構描述在 **key** 項目中指定了 `msdata:PrimaryKey="true"`。  
  
 **DataSet** 中 **UniqueConstraint** 的 **ConstraintName** 屬性值，即是結構描述中 **key** 項目內指定的 **msdata:ConstraintName** 屬性值。  
  
## 請參閱  
 [將 XML 結構描述 \(XSD\) 條件約束對應至 DataSet 條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)   
 [從 XML 結構描述 \(XSD\) 產生 DataSet 關聯](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)