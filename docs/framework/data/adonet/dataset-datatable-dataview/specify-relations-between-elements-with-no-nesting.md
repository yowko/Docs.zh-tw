---
title: 指定未巢狀放置之項目間的關聯
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: d6cd6f04a9fdeafe7c419b40023af6c71d553ac7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784276"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="1dde1-102">指定未巢狀放置之項目間的關聯</span><span class="sxs-lookup"><span data-stu-id="1dde1-102">Specify Relations Between Elements with No Nesting</span></span>
<span data-ttu-id="1dde1-103">項目未巢狀化時，不會建立任何隱含關聯，</span><span class="sxs-lookup"><span data-stu-id="1dde1-103">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="1dde1-104">不過，您可以使用**msdata： Relationship**注釋，明確指定不是以嵌套的元素之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="1dde1-104">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="1dde1-105">下列範例顯示的 XML 架構中， **msdata： Relationship**注釋是在**Order**和**OrderDetail**元素之間指定，而這些專案不是嵌套的。</span><span class="sxs-lookup"><span data-stu-id="1dde1-105">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="1dde1-106">**Msdata： Relationship**注釋會指定為**Schema**專案的子項目。</span><span class="sxs-lookup"><span data-stu-id="1dde1-106">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
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
           <xs:element name="OrderNo" type="xs:string" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNumber" type="xs:string" />  
           <xs:element name="EmpNumber" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  </xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrderDetailRelation"  
                            msdata:parent="Order"   
                            msdata:child="OrderDetail"   
                            msdata:parentkey="OrderNumber"   
                            msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
</xs:schema>  
```  
  
 <span data-ttu-id="1dde1-107">XML 架構定義語言（XSD）架構對應進程會建立<xref:System.Data.DataSet>具有**Order**和**OrderDetail**資料表的，以及在這兩個數據表之間指定的關聯性，如下所示。</span><span class="sxs-lookup"><span data-stu-id="1dde1-107">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber   
ChildTable: OrderDetail  
ChildColumns: OrderNo   
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="1dde1-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dde1-108">See also</span></span>

- [<span data-ttu-id="1dde1-109">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="1dde1-109">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="1dde1-110">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="1dde1-110">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="1dde1-111">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="1dde1-111">ADO.NET Overview</span></span>](../ado-net-overview.md)
