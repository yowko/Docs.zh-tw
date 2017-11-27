---
title: "從 XML 結構描述 (XSD) 衍生資料集關聯式結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0aae23c295401d4b9565c35d4d47c5ab913029d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a><span data-ttu-id="fcc8b-102">從 XML 結構描述 (XSD) 衍生資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="fcc8b-102">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>
<span data-ttu-id="fcc8b-103">這個章節提供如何從 XML 結構描述定義語言 (XSD) 結構描述文件來建置 `DataSet` 關聯式結構描述的概觀。</span><span class="sxs-lookup"><span data-stu-id="fcc8b-103">This section provides an overview of how the relational schema of a `DataSet` is built from an XML Schema definition language (XSD) schema document.</span></span> <span data-ttu-id="fcc8b-104">一般情況下，每個`complexType`結構描述元素的子元素，在中，所產生的資料表`DataSet`。</span><span class="sxs-lookup"><span data-stu-id="fcc8b-104">In general, for each `complexType` child element of a schema element, a table is generated in the `DataSet`.</span></span> <span data-ttu-id="fcc8b-105">資料表結構由複雜型別的定義來決定。</span><span class="sxs-lookup"><span data-stu-id="fcc8b-105">The table structure is determined by the definition of the complex type.</span></span> <span data-ttu-id="fcc8b-106">資料表會建立在`DataSet`結構描述中的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="fcc8b-106">Tables are created in the `DataSet` for top-level elements in the schema.</span></span> <span data-ttu-id="fcc8b-107">不過，會僅針對建立資料表的最上層`complexType`項目時`complexType`內的另一個巢狀項目`complexType`中的項目大小寫的巢狀`complexType`元素會對應至`DataTable`內`DataSet`。</span><span class="sxs-lookup"><span data-stu-id="fcc8b-107">However, a table is only created for a top-level `complexType` element when the `complexType` element is nested inside another `complexType` element, in which case the nested `complexType` element is mapped to a `DataTable` within the `DataSet`.</span></span>  
  
 <span data-ttu-id="fcc8b-108">如需 XSD 的詳細資訊，請參閱全球資訊網協會 (W3C) XML 結構描述第 0： 入門建議事項，XML 結構描述第 1 部分： 結構建議和 XML 結構描述第 2 部分： datatypes > 建議，位於[http://www.w3.org/](http://www.w3.org/TR/)。</span><span class="sxs-lookup"><span data-stu-id="fcc8b-108">For more information about the XSD, see the World Wide Web Consortium (W3C) XML Schema Part 0: Primer Recommendation, the XML Schema Part 1: Structures Recommendation, and the XML Schema Part 2: Datatypes Recommendation, located at [http://www.w3.org/](http://www.w3.org/TR/).</span></span>  
  
 <span data-ttu-id="fcc8b-109">下列範例會示範 XML 結構描述位置`customers`是元素的子元素`MyDataSet`項目，這是**資料集**項目。</span><span class="sxs-lookup"><span data-stu-id="fcc8b-109">The following example demonstrates an XML Schema where `customers` is the child element of the `MyDataSet` element, which is a **DataSet** element.</span></span>  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element name="customers" >   
           <xs:complexType >  
             <xs:sequence>  
               <xs:element name="CustomerID" type="xs:integer"   
                            minOccurs="0" />  
               <xs:element name="CompanyName" type="xs:string"   
                            minOccurs="0" />  
               <xs:element name="Phone" type="xs:string" />  
             </xs:sequence>  
           </xs:complexType>  
          </xs:element>  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 <span data-ttu-id="fcc8b-110">上述範例中，`customers` 項目為複雜型別項目。</span><span class="sxs-lookup"><span data-stu-id="fcc8b-110">In the preceding example, the element `customers` is a complex type element.</span></span> <span data-ttu-id="fcc8b-111">因此，複雜型別定義會經過剖析，而對應處理序則會產生下列表格。</span><span class="sxs-lookup"><span data-stu-id="fcc8b-111">Therefore, the complex type definition is parsed, and the mapping process creates the following table.</span></span>  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 <span data-ttu-id="fcc8b-112">資料表內每個資料行的資料型別都衍生自對應項目的 XML 結構描述型別或指定屬性。</span><span class="sxs-lookup"><span data-stu-id="fcc8b-112">The data type of each column in the table is derived from the XML Schema type of the corresponding element or attribute specified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fcc8b-113">如果項目`customers`是簡單的 XML 結構描述資料類型例如**整數**，不會產生資料表。</span><span class="sxs-lookup"><span data-stu-id="fcc8b-113">If the element `customers` is of a simple XML Schema data type such as **integer**, no table is generated.</span></span> <span data-ttu-id="fcc8b-114">因為資料表僅會針對複雜型別的最上層項目產生。</span><span class="sxs-lookup"><span data-stu-id="fcc8b-114">Tables are only created for the top-level elements that are complex types.</span></span>  
  
 <span data-ttu-id="fcc8b-115">在下列的 XML 結構描述，**結構描述**項目具有兩個項目子系，`InStateCustomers`和`OutOfStateCustomers`。</span><span class="sxs-lookup"><span data-stu-id="fcc8b-115">In the following XML Schema, the **Schema** element has two element children, `InStateCustomers` and `OutOfStateCustomers`.</span></span>  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="InStateCustomers" type="customerType" />  
   <xs:element name="OutOfStateCustomers" type="customerType" />  
    <xs:complexType name="customerType" >  
  
     </xs:complexType>  
  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element ref="customers" />  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 <span data-ttu-id="fcc8b-116">`InStateCustomers` 和 `OutOfStateCustomers` 子項目均為複雜型別項目 (`customerType`)。</span><span class="sxs-lookup"><span data-stu-id="fcc8b-116">Both the `InStateCustomers` and the `OutOfStateCustomers` child elements are complex type elements (`customerType`).</span></span> <span data-ttu-id="fcc8b-117">因此，對應處理序會產生下列兩個相同資料表中的`DataSet`。</span><span class="sxs-lookup"><span data-stu-id="fcc8b-117">Therefore, the mapping process generates the following two identical tables in the `DataSet`.</span></span>  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="fcc8b-118">本章節內容</span><span class="sxs-lookup"><span data-stu-id="fcc8b-118">In This Section</span></span>  
 [<span data-ttu-id="fcc8b-119">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="fcc8b-119">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="fcc8b-120">說明用來建立唯一外部索引鍵條件約束中的 XML 結構描述項目`DataSet`。</span><span class="sxs-lookup"><span data-stu-id="fcc8b-120">Describes the XML Schema elements used to create unique and foreign key constraints in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="fcc8b-121">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="fcc8b-121">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="fcc8b-122">說明用來在資料表資料行間建立關聯的 XML 結構描述項目`DataSet`。</span><span class="sxs-lookup"><span data-stu-id="fcc8b-122">Describes the XML Schema elements used to create relations between table columns in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="fcc8b-123">XML 結構描述條件約束和關聯性</span><span class="sxs-lookup"><span data-stu-id="fcc8b-123">XML Schema Constraints and Relationships</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 <span data-ttu-id="fcc8b-124">描述如何隱含建立關聯時建立條件約束中的使用 XML 結構描述項目`DataSet`。</span><span class="sxs-lookup"><span data-stu-id="fcc8b-124">Describes how relations are created implicitly when using XML Schema elements to create constraints in a `DataSet`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fcc8b-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="fcc8b-125">Related Sections</span></span>  
 [<span data-ttu-id="fcc8b-126">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="fcc8b-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="fcc8b-127">描述如何載入及保存資料與關聯式結構`DataSet`為 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="fcc8b-127">Describes how to load and persist the relational structure and data in a `DataSet` as XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcc8b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcc8b-128">See Also</span></span>  
 [<span data-ttu-id="fcc8b-129">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="fcc8b-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
