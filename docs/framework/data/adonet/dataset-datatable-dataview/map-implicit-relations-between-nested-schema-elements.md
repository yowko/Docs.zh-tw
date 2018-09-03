---
title: 在巢狀結構描述項目之間進行隱含關聯對應
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 3c0b5356479d31a3caad8438618e7cf7dc4e10e8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485569"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="ed3fb-102">在巢狀結構描述項目之間進行隱含關聯對應</span><span class="sxs-lookup"><span data-stu-id="ed3fb-102">Map Implicit Relations Between Nested Schema Elements</span></span>
<span data-ttu-id="ed3fb-103">XML 結構描述定義語言 (XSD) 結構描述可以是互呈巢狀的複雜型別。</span><span class="sxs-lookup"><span data-stu-id="ed3fb-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="ed3fb-104">在這樣的情況下，對應處理序會在 <xref:System.Data.DataSet> 內套用預設對應並建立下列各項：</span><span class="sxs-lookup"><span data-stu-id="ed3fb-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
-   <span data-ttu-id="ed3fb-105">為每個複雜型別 (父和子) 建立一個資料表。</span><span class="sxs-lookup"><span data-stu-id="ed3fb-105">One table for each of the complex types (parent and child).</span></span>  
  
-   <span data-ttu-id="ed3fb-106">如果沒有唯一的條件約束存在父代上，一個額外主索引鍵資料行每個資料表定義名為*TableName*_Id 所在*TableName*是父資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="ed3fb-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
-   <span data-ttu-id="ed3fb-107">識別額外的資料行的主索引鍵的父資料表上的主索引鍵條件約束 (藉由設定**IsPrimaryKey**屬性設 **，則為 True**)。</span><span class="sxs-lookup"><span data-stu-id="ed3fb-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="ed3fb-108">條件約束的名稱為 Constraint*#* 何處*#* 是 1、 2、 3，依此類推。</span><span class="sxs-lookup"><span data-stu-id="ed3fb-108">The constraint is named Constraint*#* where *#* is 1, 2, 3, and so on.</span></span> <span data-ttu-id="ed3fb-109">例如，第一個條件約束的預設名稱是 Constraint1。</span><span class="sxs-lookup"><span data-stu-id="ed3fb-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
-   <span data-ttu-id="ed3fb-110">子資料表中的外部索引鍵條件約束將另一個資料行識別為外部索引鍵，此外部索引鍵參考至父資料表的主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="ed3fb-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="ed3fb-111">名為條件約束*ParentTable_ChildTable*何處*ParentTable*是父資料表的名稱並*ChildTable*是子資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="ed3fb-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
-   <span data-ttu-id="ed3fb-112">父資料表和子資料表間的資料關聯。</span><span class="sxs-lookup"><span data-stu-id="ed3fb-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="ed3fb-113">下列範例示範結構描述所在**OrderDetail**是子元素**順序**。</span><span class="sxs-lookup"><span data-stu-id="ed3fb-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
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
  
 <span data-ttu-id="ed3fb-114">XML 結構描述對應處理序內建立下列**資料集**:</span><span class="sxs-lookup"><span data-stu-id="ed3fb-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
-   <span data-ttu-id="ed3fb-115">**順序**並**OrderDetail**資料表。</span><span class="sxs-lookup"><span data-stu-id="ed3fb-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
-   <span data-ttu-id="ed3fb-116">Unique 條件約束**順序**資料表。</span><span class="sxs-lookup"><span data-stu-id="ed3fb-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="ed3fb-117">請注意， **IsPrimaryKey**屬性設定為 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="ed3fb-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
-   <span data-ttu-id="ed3fb-118">上的外部索引鍵條件約束**OrderDetail**資料表。</span><span class="sxs-lookup"><span data-stu-id="ed3fb-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
-   <span data-ttu-id="ed3fb-119">之間的關聯性**順序**並**OrderDetail**資料表。</span><span class="sxs-lookup"><span data-stu-id="ed3fb-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="ed3fb-120">**巢狀**此關聯性的屬性設定為 **，則為 True**因為**Order**並**OrderDetail**元素的巢狀結構描述中.</span><span class="sxs-lookup"><span data-stu-id="ed3fb-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ed3fb-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed3fb-121">See Also</span></span>  
 [<span data-ttu-id="ed3fb-122">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="ed3fb-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="ed3fb-123">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="ed3fb-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="ed3fb-124">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="ed3fb-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
