---
title: "XML 結構描述條件約束和關聯性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e450954e4b0e51057e98dd329fe26c38f0ebbb05
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="xml-schema-constraints-and-relationships"></a>XML 結構描述條件約束和關聯性
在 XML 結構描述定義語言 (XSD) 結構描述中，您可以指定條件約束 (唯一的索引鍵和 keyref 條件約束) 和關聯性 (使用**msdata: relationship**註解)。 這個主題會說明 XML 結構描述中指定的條件約束和關聯性如何經過解譯以產生 <xref:System.Data.DataSet>。  
  
 一般而言，在 XML 結構描述中，您可以指定**msdata: relationship**註解，如果您想要產生中的關聯性**資料集**。 如需詳細資訊，請參閱[產生從 XML 結構描述 (XSD) 的資料集關聯](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)。 指定條件約束 (唯一的索引鍵和 keyref) 如果您想要產生的條件約束**資料集**。 請注意，索引鍵條件約束和 keyref 條件約束也用於產生關聯性，詳情請見這個主題的後續說明。  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a>從索引鍵條件約束和 keyref 條件約束產生關聯性  
 而不是指定**msdata: relationship**註釋，您可以指定索引鍵和 keyref XML 結構描述對應處理序時使用，以產生而不是只是條件約束的關聯性的條件約束**資料集**。 不過，如果您指定`msdata:ConstraintOnly="true"`中**keyref**項目，**資料集**會包含條件約束，而不會包含關聯性。  
  
 下列範例顯示 XML 結構描述，其中包含**順序**和**OrderDetail**無巢狀項目。 結構描述也指定索引鍵條件約束和 keyref 條件約束。  
  
```xml  
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
  
 **資料集**XML 結構描述對應處理程序包括期間產生**順序**和**OrderDetail**資料表。 此外，**資料集**包含關聯性和條件約束。 下列範例會顯示這些關聯性和條件約束。 請注意，未指定結構描述**msdata: relationship**註解; 相反地，將索引鍵和 keyref 條件約束用來產生關聯。  
  
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
  
 在先前的結構描述範例中，**順序**和**OrderDetail**無巢狀項目。 下列的結構描述範例中，這些項目則為巢狀化。 不過，沒有**msdata: relationship**註解指定; 因此，假設具有隱含關聯。 如需詳細資訊，請參閱[地圖隱含關聯性之間巢狀結構描述元素](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)。 結構描述也指定索引鍵條件約束和 keyref 條件約束。  
  
```xml  
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
  
 **資料集**所產生的 XML 結構描述對應處理序包含兩個資料表：  
  
```  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 **資料集**也包含兩個關聯性 (其中根據**msdata: relationship**附註和其他基礎的索引鍵和 keyref 條件約束) 和各種條件約束。 下列範例顯示關聯和條件約束。  
  
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
  
 如果 keyref 條件約束參考巢狀資料表包含**msdata: isnested ="true"**註釋，**資料集**會建立單一巢狀關聯性為基礎的 keyref 條件約束和相關/唯一索引鍵條件約束。  
  
## <a name="see-also"></a>請參閱  
 [從 XML 結構描述 (XSD) 衍生資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
