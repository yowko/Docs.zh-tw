---
title: 將 keyref XML 結構描述 (XSD) 條件約束對應至資料集條件約束
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: b5ffe69886b08903feab4373b1cd5c5244b3b3b9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784521"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>將 keyref XML 結構描述 (XSD) 條件約束對應至資料集條件約束
**Keyref**元素可讓您在檔內的元素之間建立連結。 這與關聯式資料庫中的外部索引鍵關聯性很類似。 如果架構指定**keyref**專案，則在架構對應程式期間，專案會轉換為數據表<xref:System.Data.DataSet>中資料行上對應的外鍵條件約束。 根據預設， **keyref**元素也會產生關聯性，並在關聯上指定**ParentTable**、 **ChildTable**、 **ParentColumn**和**ChildColumn**屬性。  
  
 下表列出您可以在**keyref**元素中指定的**msdata**屬性。  
  
|屬性名稱|描述|  
|--------------------|-----------------|  
|**msdata:ConstraintOnly**|如果在架構的**keyref**元素上指定**ConstraintOnly = "true"** ，則會建立條件約束，但不會建立關聯性。 如果未指定這個屬性（或設定為**False**），則會在**資料集中**建立條件約束和關聯性。|  
|**msdata:ConstraintName**|如果已指定**ConstraintName**屬性，則會使用其值做為條件約束的名稱。 否則，在架構中， **keyref**元素的**name**屬性會提供**資料集**內的條件約束名稱。|  
|**msdata:UpdateRule**|如果在架構的**keyref**專案中指定了**UpdateRule**屬性，其值會指派給**DataSet**中的**UpdateRule**條件約束屬性。 否則， **UpdateRule**屬性會設定為**Cascade**。|  
|**msdata:DeleteRule**|如果在架構的**keyref**專案中指定了**DeleteRule**屬性，其值會指派給**DataSet**中的**DeleteRule**條件約束屬性。 否則， **DeleteRule**屬性會設定為**Cascade**。|  
|**msdata:AcceptRejectRule**|如果在架構的**keyref**專案中指定了**AcceptRejectRule**屬性，其值會指派給**DataSet**中的**AcceptRejectRule**條件約束屬性。 否則， **AcceptRejectRule**屬性會設定為**None**。|  
  
 下列範例包含的架構，會指定**Order**元素的**OrderNumber**子專案與**OrderDetail**的**OrderNo**子項目之間的索引**鍵**和**keyref**關聯性。元素.  
  
 在範例中， **OrderDetail**元素的**OrderNumber**子項目會參考**Order**元素的**OrderNo** key 子項目。  
  
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
  
 XML 架構定義語言（XSD）架構對應進程會產生具有兩個數據表的下列**資料集**：  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 此外，**資料集會**定義下列條件約束：  
  
- **Order**資料表上的 unique 條件約束。  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- **Order**和**OrderDetail**資料表之間的關聯性。 **Nested**屬性會設定為**False** ，因為這兩個元素並未嵌套在架構中。  
  
    ```  
              ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
- **OrderDetail**資料表上的 foreign key 條件約束。  
  
    ```  
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
- [ADO.NET 概觀](../ado-net-overview.md)
