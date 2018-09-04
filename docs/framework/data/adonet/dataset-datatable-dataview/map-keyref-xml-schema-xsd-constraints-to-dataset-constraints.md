---
title: 將 keyref XML 結構描述 (XSD) 條件約束對應至資料集條件約束
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 86bc1961fb23b0b2f98a2849eaabd4eecd65cd64
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43533053"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>將 keyref XML 結構描述 (XSD) 條件約束對應至資料集條件約束
**Keyref**元素可讓您建立文件內的項目之間的連結。 這與關聯式資料庫中的外部索引鍵關聯性很類似。 如果指定了結構描述**keyref**項目，項目會轉換至對應外部索引鍵條件約束的資料表中的資料行的結構描述對應程序<xref:System.Data.DataSet>。 根據預設， **keyref**項目也會產生關聯，以**ParentTable**， **ChildTable**， **ParentColumn**，以及**ChildColumn**在關聯上指定的屬性。  
  
 下表列出**msdata**您可以在指定的屬性**keyref**項目。  
  
|屬性名稱|描述|  
|--------------------|-----------------|  
|**msdata:ConstraintOnly**|如果**ConstraintOnly ="true"** 上指定**keyref**結構描述中的項目，建立條件約束，但不會建立關聯。 如果未指定此屬性 (或設為**假**)，條件約束和關聯性會建立於**資料集**。|  
|**msdata:ConstraintName**|如果**ConstraintName**指定屬性，則會使用該值做為條件約束的名稱。 否則，請**名稱**屬性**keyref**結構描述中的項目提供中的條件約束名稱**資料集**。|  
|**msdata:UpdateRule**|如果**UpdateRule**屬性中指定**keyref**結構描述中的項目，其值指派給**UpdateRule**中的條件約束屬性**資料集**。 否則**UpdateRule**屬性設定為**Cascade**。|  
|**msdata:DeleteRule**|如果**DeleteRule**屬性中指定**keyref**結構描述中的項目，其值指派給**DeleteRule**中的條件約束屬性**資料集**。 否則**DeleteRule**屬性設定為**Cascade**。|  
|**msdata:AcceptRejectRule**|如果**AcceptRejectRule**屬性中指定**keyref**結構描述中的項目，其值指派給**AcceptRejectRule** 中的條件約束屬性**資料集**。 否則**AcceptRejectRule**屬性設定為**無**。|  
  
 下列範例包含指定的結構描述**金鑰**並**keyref**之間的關聯性**OrderNumber**子項目**順序**項目和**OrderNo**子項目**OrderDetail**項目。  
  
 在範例中， **OrderNumber**子項目**OrderDetail**項目是指**OrderNo**的索引鍵的子項目**順序**項目。  
  
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
  
 XML 結構描述定義語言 (XSD) 結構描述對應處理會產生下列**資料集**具有兩個資料表：  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 颾魤 ㄛ**資料集**定義下列條件約束：  
  
-   Unique 條件約束**順序**資料表。  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
-   之間的關聯性**順序**並**OrderDetail**資料表。 **巢狀**屬性設定為**False**因為兩個項目無巢狀結構描述中。  
  
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
  
-   上的外部索引鍵條件約束**OrderDetail**資料表。  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a>另請參閱  
 [將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [從 XML 結構描述 (XSD) 產生資料集關聯](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
