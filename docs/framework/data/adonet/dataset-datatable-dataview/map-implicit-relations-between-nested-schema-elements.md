---
title: "對應巢狀結構描述項目間的隱含關聯 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 對應巢狀結構描述項目間的隱含關聯
XML 結構描述定義語言 \(XSD\) 結構描述可以是互呈巢狀的複雜型別。  在這樣的情況下，對應處理序會在 <xref:System.Data.DataSet> 內套用預設對應並建立下列各項：  
  
-   為每個複雜型別 \(父和子\) 建立一個資料表。  
  
-   如果父代上不存在唯一的條件約束，每個資料表定義便包括一個命名為 *TableName*\_Id \(這裡的 *TableName* 是父資料表的名稱\) 的額外主索引鍵資料行。  
  
-   父資料表中的主索引鍵條件約束將另一個資料行識別為主索引鍵 \(方法是將 **IsPrimaryKey** 屬性設定為 **True**\)。  該條件約束命名為 Constraint*\#* \(這裡的 *\#* 是 1、2 或 3 等等\)。  例如，第一個條件約束的預設名稱是 Constraint1。  
  
-   子資料表中的外部索引鍵條件約束將另一個資料行識別為外部索引鍵，此外部索引鍵參考至父資料表的主索引鍵。  該條件約束命名為 *ParentTable\_ChildTable*，這裡的 *ParentTable* 是父資料表的名稱，而 *ChildTable* 是子資料表的名稱。  
  
-   父資料表和子資料表間的資料關聯。  
  
 下列範例顯示的結構描述中，**OrderDetail** 為 **Order** 的項目子系。  
  
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
  
 XML 結構描述對應處理序會在 **DataSet** 內建立下列各項：  
  
-   **Order** 和 **OrderDetail** 資料表。  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
-   **Order** 資料表上唯一的條件約束。  請注意，**IsPrimaryKey** 屬性是設定為 **True**。  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
-   **OrderDetail** 資料表上的外部索引鍵條件約束。  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
-   **Order** 和 **OrderDetail** 資料表間的關聯性。  這項關聯性的 **Nested** 屬性設定為 **True**，因為 **Order** 和 **OrderDetail** 元素會巢狀化至結構描述內。  
  
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
  
## 請參閱  
 [從 XML 結構描述 \(XSD\) 產生 DataSet 關聯](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)   
 [將 XML 結構描述 \(XSD\) 條件約束對應至 DataSet 條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)