---
title: XML 結構描述條件約束和關聯性
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 2388d7c277ba1f01bea8d419e5aedf487b843ed7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150710"
---
# <a name="xml-schema-constraints-and-relationships"></a>XML 結構描述條件約束和關聯性
在 XML 架構定義語言 （XSD） 架構中，您可以指定約束（唯一、鍵和鍵ref約束）和關係（使用**msdata：關係**注釋）。 這個主題會說明 XML 結構描述中指定的條件約束和關聯性如何經過解譯以產生 <xref:System.Data.DataSet>。  
  
 通常，在 XML 架構中，如果只想在**DataSet**中生成關係，請指定**msdata：關係**注釋。 有關詳細資訊，請參閱從[XML 架構 （XSD） 生成資料集關係](generating-dataset-relations-from-xml-schema-xsd.md)。 如果要在**DataSet**中生成約束，請指定約束（唯一、鍵和鍵ref）。 請注意，索引鍵條件約束和 keyref 條件約束也用於產生關聯性，詳情請見這個主題的後續說明。  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a>從索引鍵條件約束和 keyref 條件約束產生關聯性  
 您可以指定鍵和鍵ref約束，這些約束在 XML 架構映射過程中不僅用於生成約束，而且生成**DataSet**中的關係，而不是指定**msdata：關係**注釋。 但是，如果在`msdata:ConstraintOnly="true"`**keyref**元素中指定 **，DataSet**將僅包含約束，並且不包括關係。  
  
 下面的示例顯示了一個 XML 架構，該架構包括**未嵌套的訂單**和**訂單詳細資訊**元素。 結構描述也指定索引鍵條件約束和 keyref 條件約束。  
  
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
  
 在 XML 架構映射過程中生成的**資料集**包括**訂單**和**訂單詳細資訊**表。 此外，**資料集**還包括關係和約束。 下列範例會顯示這些關聯性和條件約束。 請注意，架構未指定**msdata：關係**注釋;相反，鍵和鍵ref約束用於生成關係。  
  
```text
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
  
 在前面的架構示例中，**順序**和**訂單詳細資訊**元素不嵌套。 下列的結構描述範例中，這些項目則為巢狀化。 但是，未指定**msdata：關係**注釋指定;因此，假定了隱式關係。 有關詳細資訊，請參閱[嵌套架構元素之間的映射隱式關係](map-implicit-relations-between-nested-schema-elements.md)。 結構描述也指定索引鍵條件約束和 keyref 條件約束。  
  
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
  
 XML 架構映射過程產生的**資料集**包括兩個表：  
  
```text  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 **DataSet**還包括兩個關係（一個基於**msdata：關係**注釋，另一個基於鍵和鍵ref約束）和各種約束。 下列範例顯示關聯和條件約束。  
  
```text
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
  
 如果引用巢狀表格的 keyref 約束包含**msdata：IsNested_"true"** 注釋 **，DataSet**將創建基於 keyref 約束和相關唯一/鍵約束的單個嵌套關係。  
  
## <a name="see-also"></a>另請參閱

- [從 XML 結構描述 (XSD) 衍生資料集關聯式結構](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
