---
title: 指定未巢狀放置之項目間的關聯
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: bee427c6cdf76792773ea827c8772b276ff29c31
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150814"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="84556-102">指定未巢狀放置之項目間的關聯</span><span class="sxs-lookup"><span data-stu-id="84556-102">Specify Relations Between Elements with No Nesting</span></span>
<span data-ttu-id="84556-103">項目未巢狀化時，不會建立任何隱含關聯，</span><span class="sxs-lookup"><span data-stu-id="84556-103">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="84556-104">但是，可以使用**msdata：關係**注釋顯式指定未嵌套的元素之間的關係。</span><span class="sxs-lookup"><span data-stu-id="84556-104">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="84556-105">下面的示例顯示了一個 XML 架構，其中**msdata：關係**注釋在未嵌套的 **"訂單"** 和"**訂單詳細資訊"** 元素之間指定。</span><span class="sxs-lookup"><span data-stu-id="84556-105">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="84556-106">**msdata：關係**注釋被指定為**架構**元素的子項目。</span><span class="sxs-lookup"><span data-stu-id="84556-106">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
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
  
 <span data-ttu-id="84556-107">XML 架構定義語言 （XSD） 架構映射過程<xref:System.Data.DataSet>創建一個帶有**訂單**和**訂單詳細資訊**的表以及這兩個表之間指定的關係，如下所示。</span><span class="sxs-lookup"><span data-stu-id="84556-107">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```text  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber
ChildTable: OrderDetail  
ChildColumns: OrderNo
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="84556-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84556-108">See also</span></span>

- [<span data-ttu-id="84556-109">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="84556-109">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="84556-110">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="84556-110">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- <span data-ttu-id="84556-111">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="84556-111">[ADO.NET Overview](../ado-net-overview.md)</span></span>
