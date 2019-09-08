---
title: 在巢狀結構描述項目之間進行隱含關聯對應
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: f4b1b9e45f0cda976719b991c336463e0af05f12
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784431"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>在巢狀結構描述項目之間進行隱含關聯對應
XML 結構描述定義語言 (XSD) 結構描述可以是互呈巢狀的複雜型別。 在這樣的情況下，對應處理序會在 <xref:System.Data.DataSet> 內套用預設對應並建立下列各項：  
  
- 為每個複雜型別 (父和子) 建立一個資料表。  
  
- 如果父代上不存在 unique 條件約束，則每個資料表定義會有一個額外的主鍵資料行，名為*tablename*_Id，其中*TableName*是父資料表的名稱。  
  
- 父資料表上的 primary key 條件約束，可將其他資料行識別為主鍵（藉由將**IsPrimaryKey**屬性設定為**True**）。 此條件約束的名稱為 Constraint\#，其中 \# 為 1、2、3 等。 例如，第一個條件約束的預設名稱是 Constraint1。  
  
- 子資料表中的外部索引鍵條件約束將另一個資料行識別為外部索引鍵，此外部索引鍵參考至父資料表的主索引鍵。 條件約束名為*ParentTable_ChildTable* ，其中*ParentTable*是父資料表的名稱，而*ChildTable*是子資料工作表的名稱。  
  
- 父資料表和子資料表間的資料關聯。  
  
 下列範例顯示的架構，其中**OrderDetail**是**Order**的子項目。  
  
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
            <xs:element name="OrderNumber" type="xs:string" />  
            <xs:element name="EmpNumber" type="xs:string" />  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:string" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:choice>  
   </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 XML 架構對應進程會在**資料集中**建立下列內容：  
  
- **Order**和**OrderDetail**資料表。  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- **Order**資料表上的 unique 條件約束。 請注意， **IsPrimaryKey**屬性設定為**True**。  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
- **OrderDetail**資料表上的 foreign key 條件約束。  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
- **Order**和**OrderDetail**資料表之間的關聯性。 此關聯性的**Nested**屬性會設定為**True** ，因為**Order**和**OrderDetail**專案會嵌套在架構中。  
  
    ```  
    ParentTable: Order  
    ParentColumns: Order_Id   
    ChildTable: OrderDetail  
    ChildColumns: Order_Id   
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a>另請參閱

- [從 XML 結構描述 (XSD) 產生資料集關聯](generating-dataset-relations-from-xml-schema-xsd.md)
- [將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [ADO.NET 概觀](../ado-net-overview.md)
