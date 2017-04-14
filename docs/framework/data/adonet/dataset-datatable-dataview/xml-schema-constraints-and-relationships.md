---
title: "XML 結構描述條件約束和關聯性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# XML 結構描述條件約束和關聯性
您可以在 XML 結構描述定義語言 \(XSD\) 結構描述中，指定條件約束 \(唯一的、索引鍵和 keyref 條件約束\) 以及關聯性 \(使用 **msdata:Relationship** 註釋\)。  這個主題會說明 XML 結構描述中指定的條件約束和關聯性如何經過解譯以產生 <xref:System.Data.DataSet>。  
  
 一般而言，如果您想在 **DataSet** 內只產生關聯性，則可以在 XML 結構描述內指定 **msdata:Relationship** 註釋。  如需詳細資訊，請參閱[從 XML 結構描述 \(XSD\) 產生 DataSet 關聯](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)。  如果您要在 **DataSet** 中產生條件約束，則需要指定條件約束 \(唯一的、索引鍵和 keyref 條件約束\)。  請注意，索引鍵條件約束和 keyref 條件約束也用於產生關聯性，詳情請見這個主題的後續說明。  
  
## 從索引鍵條件約束和 keyref 條件約束產生關聯性  
 取代指定 **msdata:Relationship** 註釋，您可以指定索引鍵條件約束和 keyref 條件約束，這些條件約束會在 XML 結構描述對應處理序期間，在 **DataSet** 中不只產生條件約束，也會產生關聯性。  但是，如果在 **keyref** 項目中指定 `msdata:ConstraintOnly="true"`，**DataSet** 將只包含條件約束，而不包含關聯性。  
  
 下列範例所顯示的 XML 結構描述包含無巢狀的 **Order** 和 **OrderDetail** 項目，  結構描述也指定索引鍵條件約束和 keyref 條件約束。  
  
```  
<xs:schema id="MyDataSet" xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:integer" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 XML 結構描述對應處理序期間產生的 **DataSet** 包含 **Order** 和 **OrderDetail** 資料表。  此外，**DataSet** 也包含關聯性和條件約束。  下列範例會顯示這些關聯性和條件約束。  請注意，結構描述未指定 **msdata:Relationship** 註釋，而是使用索引鍵條件約束和 keyref 條件約束產生關聯。  
  
```  
....ConstraintName: OrderNumberKey  
....Type: UniqueConstraint  
....Table: Order  
....Columns: OrderNumber  
....IsPrimaryKey: False  
  
....ConstraintName: OrderNoRef  
....Type: ForeignKeyConstraint  
....Table: OrderDetail  
....Columns: OrderNo  
....RelatedTable: Order  
....RelatedColumns: OrderNumber  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
```  
  
 在上一個結構描述範例中，**Order** 和 **OrderDetail** 項目無巢狀化。  下列的結構描述範例中，這些項目則為巢狀化。  不過這個範例中沒有指定 **msdata:Relationship** 註釋，所以我們假設這些項目具有隱含關聯。  如需詳細資訊，請參閱[對應巢狀結構描述項目間的隱含關聯](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)。  結構描述也指定索引鍵條件約束和 keyref 條件約束。  
  
```  
<xs:schema id="MyDataSet" xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:integer" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 從 XML 結構描述對應處理序產生的 **DataSet** 包括兩個資料表：  
  
```  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 **DataSet** 也包含兩個關聯性 \(一個以 **msdata:relationship** 註釋為基礎，另一個採用索引鍵條件約束和 keyref 條件約束\) 和各種條件約束。  下列範例顯示關聯和條件約束。  
  
```  
..RelationName: Order_OrderDetail  
..ParentTable: Order  
..ParentColumns: Order_Id  
..ChildTable: OrderDetail  
..ChildColumns: Order_Id  
..ParentKeyConstraint: Constraint1  
..ChildKeyConstraint: Order_OrderDetail  
..Nested: True  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
  
..ConstraintName: OrderNumberKey  
..Type: UniqueConstraint  
..Table: Order  
..Columns: OrderNumber  
..IsPrimaryKey: False  
  
..ConstraintName: Constraint1  
..Type: UniqueConstraint  
..Table: Order  
..Columns: Order_Id  
..IsPrimaryKey: True  
  
..ConstraintName: Order_OrderDetail  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: Order_Id  
..RelatedTable: Order  
..RelatedColumns: Order_Id  
  
..ConstraintName: OrderNoRef  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: OrderNo  
..RelatedTable: Order  
..RelatedColumns: OrderNumber  
```  
  
 如果 keyref 條件約束參考的巢狀資料表包含 **msdata:IsNested\="true"** 註釋，則 **DataSet** 會以 keyref 條件約束和相關的唯一的\/索引鍵條件約束，建立單一巢狀關聯性。  
  
## 請參閱  
 [從 XML 結構描述 \(XSD\) 衍生 DataSet 關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)