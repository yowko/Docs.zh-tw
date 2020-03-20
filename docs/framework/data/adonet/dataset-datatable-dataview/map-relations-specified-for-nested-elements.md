---
title: 針對巢狀項目指定的關聯進行對應
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: cd652f51f01dcfa16a8b707f35c658043c20670d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150892"
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="0d799-102">針對巢狀項目指定的關聯進行對應</span><span class="sxs-lookup"><span data-stu-id="0d799-102">Map Relations Specified for Nested Elements</span></span>
<span data-ttu-id="0d799-103">架構可以包括**msdata：關係**注釋，以顯式指定架構中任意兩個元素之間的映射。</span><span class="sxs-lookup"><span data-stu-id="0d799-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="0d799-104">msdata 中指定的兩個元素 **：關係**可以在架構中嵌套，但不必嵌套。</span><span class="sxs-lookup"><span data-stu-id="0d799-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="0d799-105">映射過程使用**msdata：** 架構中的關係來生成兩列之間的主鍵/外鍵關係。</span><span class="sxs-lookup"><span data-stu-id="0d799-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="0d799-106">下面的示例顯示了一個 XML 架構，其中**OrderDetail**元素是**order**的子項目。</span><span class="sxs-lookup"><span data-stu-id="0d799-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="0d799-107">**msdata：關係**標識此父子關係，並指定結果**訂單**表的**OrderNumber**列與生成的**訂單詳細資訊**表的 **"訂單無**"列相關。</span><span class="sxs-lookup"><span data-stu-id="0d799-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
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
          <xs:annotation>  
           <xs:appinfo>  
            <msdata:Relationship name="OrdODRelation"
                                msdata:parent="Order"
                                msdata:child="OrderDetail"
                                msdata:parentkey="OrderNumber"
                                msdata:childkey="OrderNo"/>  
           </xs:appinfo>  
          </xs:annotation>  
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
  
 <span data-ttu-id="0d799-108">XML 結構描述對應處理序會在 <xref:System.Data.DataSet> 內建立下列各項：</span><span class="sxs-lookup"><span data-stu-id="0d799-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="0d799-109">**訂單**和**訂單詳細資訊**表。</span><span class="sxs-lookup"><span data-stu-id="0d799-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- <span data-ttu-id="0d799-110">**訂單**和**訂單詳細資訊**表之間的關係。</span><span class="sxs-lookup"><span data-stu-id="0d799-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="0d799-111">此關係的**嵌套**屬性設置為**True，** 因為 **"訂單"** 和"**訂單詳細資訊"** 元素嵌套在架構中。</span><span class="sxs-lookup"><span data-stu-id="0d799-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="0d799-112">對應處理序未建立任何條件約束。</span><span class="sxs-lookup"><span data-stu-id="0d799-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d799-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d799-113">See also</span></span>

- [<span data-ttu-id="0d799-114">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="0d799-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="0d799-115">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="0d799-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- <span data-ttu-id="0d799-116">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="0d799-116">[ADO.NET Overview](../ado-net-overview.md)</span></span>
