---
title: 指定未巢狀放置之項目間的關聯
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: e33a445d4ef969c73ab9756c5aa5116fae67ea66
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739176"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="336ad-102">指定未巢狀放置之項目間的關聯</span><span class="sxs-lookup"><span data-stu-id="336ad-102">Specify Relations Between Elements with No Nesting</span></span>
<span data-ttu-id="336ad-103">項目未巢狀化時，不會建立任何隱含關聯，</span><span class="sxs-lookup"><span data-stu-id="336ad-103">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="336ad-104">不過，您可以明確指定不使用巢狀的項目之間的關聯**msdata: relationship**註釋。</span><span class="sxs-lookup"><span data-stu-id="336ad-104">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="336ad-105">下列範例顯示 XML 結構描述所在**msdata: relationship**註解會指定之間**順序**並**OrderDetail**項目，不是巢狀結構。</span><span class="sxs-lookup"><span data-stu-id="336ad-105">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="336ad-106">**Msdata: relationship**註解會指定為的子元素**結構描述**項目。</span><span class="sxs-lookup"><span data-stu-id="336ad-106">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
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
  
 <span data-ttu-id="336ad-107">XML 結構描述定義語言 (XSD) 結構描述對應處理會建立<xref:System.Data.DataSet>具有**順序**並**OrderDetail**資料表和關聯性，如下所示，指定兩個資料表之間。</span><span class="sxs-lookup"><span data-stu-id="336ad-107">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber   
ChildTable: OrderDetail  
ChildColumns: OrderNo   
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="336ad-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="336ad-108">See also</span></span>
- [<span data-ttu-id="336ad-109">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="336ad-109">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="336ad-110">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="336ad-110">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="336ad-111">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="336ad-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
