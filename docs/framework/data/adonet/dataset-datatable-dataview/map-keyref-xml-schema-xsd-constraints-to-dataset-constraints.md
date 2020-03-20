---
title: 將 keyref XML 結構描述 (XSD) 條件約束對應至資料集條件約束
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 902b79b73f494ced0f54b29babff1b2e767bd47a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150879"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>將 keyref XML 結構描述 (XSD) 條件約束對應至資料集條件約束
**keyref**元素允許您在文檔中的元素之間建立連結。 這與關聯式資料庫中的外部索引鍵關聯性很類似。 如果架構指定**keyref**元素，則在架構映射過程中將元素轉換為 對<xref:System.Data.DataSet>表中的列的相應外鍵約束。 預設情況下 **，keyref**元素還會生成一個關係，該關係在關係上指定了**父表**、**子表**、**父列**和**子列**屬性。  
  
 下表概述了可在**keyref**元素中指定的**msdata**屬性。  
  
|屬性名稱|描述|  
|--------------------|-----------------|  
|**msdata:ConstraintOnly**|如果在架構中的**keyref**元素上指定了 **"約束唯一""true"，** 則將創建約束，但不創建任何關係。 如果未指定此屬性（或設置為**False），** 則約束和關係都在**DataSet 中**創建。|  
|**msdata:ConstraintName**|如果指定了 **"約束名稱"** 屬性，則其值將用作約束的名稱。 否則，架構中**keyref**元素**的名稱**屬性在**DataSet**中提供約束名稱。|  
|**msdata:UpdateRule**|如果在架構中的**keyref**元素中指定**了 UpdateRule**屬性，則其值將分配給**DataSet**中的**UpdateRule**約束屬性。 否則 **，UpdateRule**屬性將設置為**級聯**。|  
|**msdata:DeleteRule**|如果在架構中的**keyref**元素中指定**了 DeleteRule**屬性，則其值將分配給**DataSet**中的**DeleteRule**約束屬性。 否則 **，DeleteRule**屬性將設置為**級聯**。|  
|**msdata:AcceptRejectRule**|如果在架構中的**keyref**元素中指定了**AcceptRejectRule 屬性**，則其值將分配給**DataSet**中的**AcceptRejectRule**約束屬性。 否則，"**接受拒絕規則"** 屬性將設置為 **"無**"。|  
  
 下面的示例包含一個架構，該架構指定**Order**元素的**OrderNumber**子項目和**OrderDetail**元素的**OrderNo**子項目之間的**鍵**和**鍵 ref**關係。  
  
 在此示例中，"**訂單詳細資訊"** 元素的**OrderNumber**子項目引用**訂單**元素的 **"訂單無**"鍵子項目。  
  
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
  
 XML 架構定義語言 （XSD） 架構映射過程生成具有兩個表的以下**DataSet：**  
  
```text  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 此外，**資料集**定義以下約束：  
  
- **訂單**表上的唯一約束。  
  
    ```text
              Table: Order  
    Columns: OrderNumber
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- **訂單**和**訂單詳細資訊**表之間的關係。 **嵌套**屬性設置為**False，** 因為兩個元素未嵌套在架構中。  
  
    ```text
              ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
- **"訂單詳細資訊**"表上的外鍵約束。  
  
    ```text  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo
    RelatedTable: Order  
    RelatedColumns: OrderNumber
    ```  
  
## <a name="see-also"></a>另請參閱

- [將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [從 XML 結構描述 (XSD) 產生資料集關聯](generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
