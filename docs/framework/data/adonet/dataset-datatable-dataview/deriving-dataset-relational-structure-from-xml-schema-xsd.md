---
title: 從 XML 結構描述 (XSD) 衍生資料集關聯式結構
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 76fd0126f32eb2b22a12ee0b67e1f81794ff9445
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195290"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a><span data-ttu-id="fa920-102">從 XML 結構描述 (XSD) 衍生資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="fa920-102">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>
<span data-ttu-id="fa920-103">這個章節提供如何從 XML 結構描述定義語言 (XSD) 結構描述文件來建置 `DataSet` 關聯式結構描述的概觀。</span><span class="sxs-lookup"><span data-stu-id="fa920-103">This section provides an overview of how the relational schema of a `DataSet` is built from an XML Schema definition language (XSD) schema document.</span></span> <span data-ttu-id="fa920-104">一般情況下，每個`complexType`結構描述元素的子項目，在中，所產生的資料表`DataSet`。</span><span class="sxs-lookup"><span data-stu-id="fa920-104">In general, for each `complexType` child element of a schema element, a table is generated in the `DataSet`.</span></span> <span data-ttu-id="fa920-105">資料表結構由複雜型別的定義來決定。</span><span class="sxs-lookup"><span data-stu-id="fa920-105">The table structure is determined by the definition of the complex type.</span></span> <span data-ttu-id="fa920-106">資料表會建立在`DataSet`結構描述中的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="fa920-106">Tables are created in the `DataSet` for top-level elements in the schema.</span></span> <span data-ttu-id="fa920-107">不過，如果資料表僅建立最上層`complexType`項目時`complexType`項目放到另一個巢狀`complexType`項目，在這種情況下巢狀`complexType`元素會對應到`DataTable`內`DataSet`。</span><span class="sxs-lookup"><span data-stu-id="fa920-107">However, a table is only created for a top-level `complexType` element when the `complexType` element is nested inside another `complexType` element, in which case the nested `complexType` element is mapped to a `DataTable` within the `DataSet`.</span></span>  
  
 <span data-ttu-id="fa920-108">如需有關 XSD 的詳細資訊，請參閱 World Wide Web Consortium (W3C) [XML 結構描述第 0： 入門建議事項](https://www.w3.org/TR/xmlschema-0/)，則[XML 結構描述第 1 部分： 結構建議事項](https://www.w3.org/TR/xmlschema-1/)，和[XML結構描述第 2 部分： Datatypes > 建議](https://www.w3.org/TR/xmlschema-2/)。</span><span class="sxs-lookup"><span data-stu-id="fa920-108">For more information about the XSD, see the World Wide Web Consortium (W3C) [XML Schema Part 0: Primer Recommendation](https://www.w3.org/TR/xmlschema-0/), the [XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/), and the [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>  
  
 <span data-ttu-id="fa920-109">下列範例示範 XML 結構描述所在`customers`是子元素`MyDataSet`項目，也就是**資料集**項目。</span><span class="sxs-lookup"><span data-stu-id="fa920-109">The following example demonstrates an XML Schema where `customers` is the child element of the `MyDataSet` element, which is a **DataSet** element.</span></span>  
  
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
  
 <span data-ttu-id="fa920-110">上述範例中，`customers` 項目為複雜型別項目。</span><span class="sxs-lookup"><span data-stu-id="fa920-110">In the preceding example, the element `customers` is a complex type element.</span></span> <span data-ttu-id="fa920-111">因此，複雜型別定義會經過剖析，而對應處理序則會產生下列表格。</span><span class="sxs-lookup"><span data-stu-id="fa920-111">Therefore, the complex type definition is parsed, and the mapping process creates the following table.</span></span>  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 <span data-ttu-id="fa920-112">資料表內每個資料行的資料型別都衍生自對應項目的 XML 結構描述型別或指定屬性。</span><span class="sxs-lookup"><span data-stu-id="fa920-112">The data type of each column in the table is derived from the XML Schema type of the corresponding element or attribute specified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa920-113">如果項目`customers`這類是簡單的 XML 結構描述資料型別的**整數**，不會產生資料表。</span><span class="sxs-lookup"><span data-stu-id="fa920-113">If the element `customers` is of a simple XML Schema data type such as **integer**, no table is generated.</span></span> <span data-ttu-id="fa920-114">因為資料表僅會針對複雜型別的最上層項目產生。</span><span class="sxs-lookup"><span data-stu-id="fa920-114">Tables are only created for the top-level elements that are complex types.</span></span>  
  
 <span data-ttu-id="fa920-115">下列 XML 結構描述**結構描述**項目有兩個項目子系`InStateCustomers`和`OutOfStateCustomers`。</span><span class="sxs-lookup"><span data-stu-id="fa920-115">In the following XML Schema, the **Schema** element has two element children, `InStateCustomers` and `OutOfStateCustomers`.</span></span>  
  
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
  
 <span data-ttu-id="fa920-116">`InStateCustomers` 和 `OutOfStateCustomers` 子項目均為複雜型別項目 (`customerType`)。</span><span class="sxs-lookup"><span data-stu-id="fa920-116">Both the `InStateCustomers` and the `OutOfStateCustomers` child elements are complex type elements (`customerType`).</span></span> <span data-ttu-id="fa920-117">因此，對應處理序會產生下列兩個相同資料表中的`DataSet`。</span><span class="sxs-lookup"><span data-stu-id="fa920-117">Therefore, the mapping process generates the following two identical tables in the `DataSet`.</span></span>  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="fa920-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="fa920-118">In This Section</span></span>  
 [<span data-ttu-id="fa920-119">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="fa920-119">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="fa920-120">描述用來建立唯一外部索引鍵條件約束中的 XML 結構描述項目`DataSet`。</span><span class="sxs-lookup"><span data-stu-id="fa920-120">Describes the XML Schema elements used to create unique and foreign key constraints in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="fa920-121">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="fa920-121">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="fa920-122">描述用來建立資料表中的資料行之間的關聯性的 XML 結構描述項目`DataSet`。</span><span class="sxs-lookup"><span data-stu-id="fa920-122">Describes the XML Schema elements used to create relations between table columns in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="fa920-123">XML 結構描述條件約束和關聯性</span><span class="sxs-lookup"><span data-stu-id="fa920-123">XML Schema Constraints and Relationships</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 <span data-ttu-id="fa920-124">描述如何隱含建立關聯時建立條件約束中的使用 XML 結構描述項目`DataSet`。</span><span class="sxs-lookup"><span data-stu-id="fa920-124">Describes how relations are created implicitly when using XML Schema elements to create constraints in a `DataSet`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fa920-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="fa920-125">Related Sections</span></span>  
 [<span data-ttu-id="fa920-126">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="fa920-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="fa920-127">描述如何載入及保存資料與關聯式結構`DataSet`為 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="fa920-127">Describes how to load and persist the relational structure and data in a `DataSet` as XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa920-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa920-128">See Also</span></span>  
 [<span data-ttu-id="fa920-129">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="fa920-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
