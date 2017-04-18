---
title: "將 XML 結構描述 (XSD) keyref 條件約束對應至 DataSet 條件約束 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 將 XML 結構描述 (XSD) keyref 條件約束對應至 DataSet 條件約束
**keyref** 項目允許您在文件內的項目間建立連結。  這與關聯式資料庫中的外部索引鍵關聯性很類似。  如果結構描述指定 **keyref** 項目，則在結構描述對應處理序中，項目會轉換為 <xref:System.Data.DataSet> 資料表內資料行上對應的外部索引鍵條件約束。  依預設，**keyref** 項目也會產生關聯，並在關聯上指定 **ParentTable**、**ChildTable**、**ParentColumn** 和 **ChildColumn** 屬性。  
  
 下列表格列出您可在 **keyref** 項目中指定的 **msdata** 屬性。  
  
|屬性名稱|描述|  
|----------|--------|  
|**msdata:ConstraintOnly**|如果在結構描述的 **keyref** 項目上指定 **ConstraintOnly\="true"**，則會建立條件約束，但不會建立關聯。  如果這個屬性並未指定 \(或已設定為 **False**\)，則會在 **DataSet** 中同時建立條件約束和關聯。|  
|**msdata:ConstraintName**|如果指定 **ConstraintName** 屬性，則它的值會被當成條件約束名稱使用。  否則，會由結構描述內 **keyref** 項目之 **Name** 屬性提供 **DataSet** 內的條件約束名稱。|  
|**msdata:UpdateRule**|如果結構描述內的 **keyref** 項目指定了 **UpdateRule** 屬性，則它的值會指派給 **DataSet** 內的 **UpdateRule** 條件約束屬性。  否則 **UpdateRule** 屬性會設定為 **Cascade**。|  
|**msdata:DeleteRule**|如果結構描述內的 **keyref** 項目指定了 **DeleteRule** 屬性，則它的值會指派給 **DataSet** 內的 **DeleteRule** 條件約束屬性。  否則 **DeleteRule** 屬性會設定為 **Cascade**。|  
|**msdata:AcceptRejectRule**|如果結構描述內的 **keyref** 項目指定了 **AcceptRejectRule** 屬性，則它的值會指派給 **DataSet** 內的 **AcceptRejectRule** 條件約束屬性。  否則 **AcceptRejectRule** 屬性會設定為 **None**。|  
  
 下列範例所包含的結構描述會在 **Order** 項目的 **OrderNumber** 項目子系，以及 **OrderDetail** 項目的 **OrderNo** 項目子系之間，指定 **key** 和 **keyref** 的關聯性。  
  
 範例中，**OrderDetail** 的 **OrderNumber** 項目子系會參考 **Order** 項目的 **OrderNo** 索引鍵項目子系。  
  
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
  
 XML 結構描述定義語言 \(XSD\) 結構描述對應處理產生了下列具有兩個資料表的 **DataSet**：  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 此外，**DataSet** 還會定義下列的條件約束：  
  
-   **Order** 資料表上唯一的條件約束。  
  
    ```  
  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
-   **Order** 和 **OrderDetail** 資料表間的關聯性。  **Nested** 屬性會設定為 **False**，因為這兩個項目在結構描述內並未巢狀化。  
  
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
  
-   **OrderDetail** 資料表上的外部索引鍵條件約束。  
  
    ```  
  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## 請參閱  
 [將 XML 結構描述 \(XSD\) 條件約束對應至 DataSet 條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)   
 [從 XML 結構描述 \(XSD\) 產生 DataSet 關聯](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)