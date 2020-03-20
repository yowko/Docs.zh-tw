---
title: 在巢狀結構描述項目之間進行隱含關聯對應
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: dc5b81fd06f2860283c8c5fa028af4b945e2b1e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150959"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>在巢狀結構描述項目之間進行隱含關聯對應
XML 結構描述定義語言 (XSD) 結構描述可以是互呈巢狀的複雜型別。 在這樣的情況下，對應處理序會在 <xref:System.Data.DataSet> 內套用預設對應並建立下列各項：  
  
- 為每個複雜型別 (父和子) 建立一個資料表。  
  
- 如果父項上不存在唯一約束，則每個表定義（稱為*表Name）_Id*一個額外的主鍵列，*其中表名稱*是父表的名稱。  
  
- 父表上的主鍵約束將附加列標識為主鍵（通過將**IsPrimaryKey**屬性設置為**True）。** 此條件約束的名稱為 Constraint\#，其中 \# 為 1、2、3 等。 例如，第一個條件約束的預設名稱是 Constraint1。  
  
- 子資料表中的外部索引鍵條件約束將另一個資料行識別為外部索引鍵，此外部索引鍵參考至父資料表的主索引鍵。 約束*ParentTable_ChildTable命名*，其中*parentTable*是父表的名稱，*子表*是子表的名稱。  
  
- 父資料表和子資料表間的資料關聯。  
  
 下面的示例顯示了**OrderDetail**是**Order**的子項目的架構。  
  
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
  
 XML 架構映射過程在**DataSet**中創建以下內容：  
  
- **訂單**和**訂單詳細資訊**表。  
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- **訂單**表上的唯一約束。 請注意 **，IsPrimaryKey**屬性設置為**True**。  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id
    IsPrimaryKey: True  
    ```  
  
- **"訂單詳細資訊**"表上的外鍵約束。  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id
    RelatedTable: Order  
    RelatedColumns: Order_Id
    ```  
  
- **訂單**和**訂單詳細資訊**表之間的關係。 此關係的**嵌套**屬性設置為**True，** 因為 **"訂單"** 和"**訂單詳細資訊"** 元素嵌套在架構中。  
  
    ```text  
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
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
