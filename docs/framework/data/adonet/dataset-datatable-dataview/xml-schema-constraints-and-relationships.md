---
title: XML 結構描述條件約束和關聯性
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 1ffb11814be14b3f9601abaad6e95c00f9f7a634
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202986"
---
# <a name="xml-schema-constraints-and-relationships"></a>XML 結構描述條件約束和關聯性
在 XML 架構定義語言 (XSD) 架構中, 您可以指定條件約束 (unique、key 和 keyref 條件約束) 和關聯性 (使用**msdata: Relationship**注釋)。 這個主題會說明 XML 結構描述中指定的條件約束和關聯性如何經過解譯以產生 <xref:System.Data.DataSet>。  
  
 一般來說, 在 XML 架構中, 如果您只想要在**資料集中**產生關聯性, 您可以指定**msdata: Relationship**注釋。 如需詳細資訊, 請參閱[從 XML 架構 (XSD) 產生資料集](generating-dataset-relations-from-xml-schema-xsd.md)關聯。 如果您想要在**資料集中**產生條件約束, 您可以指定條件約束 (unique、key 和 keyref)。 請注意，索引鍵條件約束和 keyref 條件約束也用於產生關聯性，詳情請見這個主題的後續說明。  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a>從索引鍵條件約束和 keyref 條件約束產生關聯性  
 您可以指定**msdata: Relationship**注釋, 而不是指定 [索引鍵] 和 [keyref 條件約束], 而在 XML 架構對應進程期間, 它不僅會產生條件約束, 也會產生**資料集**內的關聯性。 不過, 如果您在`msdata:ConstraintOnly="true"` **keyref**專案中指定,**資料集**只會包含條件約束, 而且不會包含關聯性。  
  
 下列範例顯示的 XML 架構包含不是嵌套的**Order**和**OrderDetail**元素。 結構描述也指定索引鍵條件約束和 keyref 條件約束。  
  
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
  
 XML 架構對應進程期間所產生的**資料集**包含**Order**和**OrderDetail**資料表。 此外,**資料集**還包含關聯性和條件約束。 下列範例會顯示這些關聯性和條件約束。 請注意, 此架構不會指定**msdata: Relationship**注釋;相反地, key 和 keyref 條件約束是用來產生關聯。  
  
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
  
 在先前的架構範例中, **Order**和**OrderDetail**元素不是嵌套的。 下列的結構描述範例中，這些項目則為巢狀化。 不過, 未指定**msdata: Relationship**注釋;因此, 會假設使用隱含關聯。 如需詳細資訊, 請參閱[對應嵌套架構元素之間的隱含](map-implicit-relations-between-nested-schema-elements.md)關聯。 結構描述也指定索引鍵條件約束和 keyref 條件約束。  
  
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
  
 XML 架構對應進程所產生的**資料集**包含兩個數據表:  
  
```  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 **DataSet**也包含兩個關聯性 (一個以**msdata: relationship**注釋為基礎, 另一個依據索引鍵和 keyref 條件約束) 和各種條件約束。 下列範例顯示關聯和條件約束。  
  
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
  
 如果參考嵌套資料表的 keyref 條件約束包含**msdata: IsNested = "true"** 注釋,**資料集**將會建立以 keyref 條件約束和相關 unique/key 條件約束為基礎的單一嵌套關聯性。  
  
## <a name="see-also"></a>另請參閱

- [從 XML 結構描述 (XSD) 衍生資料集關聯式結構](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
