---
title: "將 XML 結構描述 (XSD) 的唯一條件約束對應至 DataSet 條件約束 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 將 XML 結構描述 (XSD) 的唯一條件約束對應至 DataSet 條件約束
XML 結構描述定義語言 \(XSD\) 結構描述中，**unique** 項目是用來指定項目或屬性上條件約束的唯一性。  在將 XML 結構描述轉譯到關聯式結構描述的處理序中，會將 XML 結構描述內項目或屬性上指定的唯一的條件約束 \(Constraint\)，對應到所產生的對應 <xref:System.Data.DataSet> 內 <xref:System.Data.DataTable> 的唯一的條件約束。  
  
 下表列出您可在 **unique** 項目中指定的 **msdata** 屬性。  
  
|屬性名稱|描述|  
|----------|--------|  
|**msdata:ConstraintName**|如果指定這個屬性，則它的值會被當成條件約束名稱使用。  否則會由 **name** 屬性提供條件約束名稱的值。|  
|**msdata:PrimaryKey**|如果 **unique** 項目中出現 `PrimaryKey="true"`，則會將 **IsPrimaryKey** 屬性設定為 **true** 以建立唯一的條件約束。|  
  
 下列範例會顯示使用 **unique** 項目指定唯一性條件約束的 XML 結構描述。  
  
```  
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
   <xs:unique      
msdata:ConstraintName="UCustID"      
name="UniqueCustIDConstr" >        
<xs:selector xpath=".//Customers" />        
<xs:field xpath="CustomerID" />      
</xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 結構描述中的 **unique** 項目指定文件執行個體中所有 **Customers** 項目的 **CustomerID** 項目子系值必須是唯一的。  建置 **DataSet** 的過程中，對應處理序會讀取這個結構描述並產生下列表格：  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 對應處理序也會在 **CustomerID** 資料行上建立唯一的條件約束，如下列 **DataSet** 所示   \(為了便於了解，此處僅顯示相關屬性\)。  
  
```  
  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID  
      Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID   
      IsPrimaryKey: False  
```  
  
 產生的 **DataSet** 中，唯一的條件約束的 **IsPrimaryKey** 屬性設定為 **False**。  資料行上的 **unique** 屬性指出 **CustomerID** 資料行值必須是唯一的 \(但是也可以由資料行的 **AllowDBNull** 屬性指定為 Null 參考\)。  
  
 如果您修改結構描述，並將選擇性的 **msdata:PrimaryKey** 屬性值設定為 **True**，即可在資料表上建立唯一的條件約束。  將 **AllowDBNull** 資料行屬性設定為 **False**，並將條件約束的 **IsPrimaryKey** 屬性設定為 **True**，即可使 **CustomerID** 資料行成為主索引鍵資料行。  
  
 您可以在 XML 結構描述中，將唯一的條件約束指定給合併的項目或屬性。  下列範例會說明如何藉由在結構描述中新增其他的 **xs:field** 項目，以指定 **CustomerID** 與 **CompanyName** 值組合，讓這些值在任何狀況中，對所有 **Customers** 而言都是唯一的。  
  
```  
  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 這是產生之 **DataSet** 中建立的條件約束。  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## 請參閱  
 [將 XML 結構描述 \(XSD\) 條件約束對應至 DataSet 條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)   
 [從 XML 結構描述 \(XSD\) 產生 DataSet 關聯](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)