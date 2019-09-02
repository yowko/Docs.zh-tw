---
title: 從 XML 結構描述 (XSD) 衍生資料集關聯式結構
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 29b905c42f15cad4eb8521c4d702b56093982445
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203786"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a><span data-ttu-id="8f8a3-102">從 XML 結構描述 (XSD) 衍生資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="8f8a3-102">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>
<span data-ttu-id="8f8a3-103">這個章節提供如何從 XML 結構描述定義語言 (XSD) 結構描述文件來建置 `DataSet` 關聯式結構描述的概觀。</span><span class="sxs-lookup"><span data-stu-id="8f8a3-103">This section provides an overview of how the relational schema of a `DataSet` is built from an XML Schema definition language (XSD) schema document.</span></span> <span data-ttu-id="8f8a3-104">一般而言, 針對架構專案`complexType`的每個子項目, 會`DataSet`在中產生資料表。</span><span class="sxs-lookup"><span data-stu-id="8f8a3-104">In general, for each `complexType` child element of a schema element, a table is generated in the `DataSet`.</span></span> <span data-ttu-id="8f8a3-105">資料表結構由複雜型別的定義來決定。</span><span class="sxs-lookup"><span data-stu-id="8f8a3-105">The table structure is determined by the definition of the complex type.</span></span> <span data-ttu-id="8f8a3-106">資料表會在架構中`DataSet`的最上層元素中建立。</span><span class="sxs-lookup"><span data-stu-id="8f8a3-106">Tables are created in the `DataSet` for top-level elements in the schema.</span></span> <span data-ttu-id="8f8a3-107">不過, 只有`complexType`當元素在另一個`complexType`專案中嵌套時`complexType` , 才會針對最上層元素建立資料表, 在此`DataTable`情況下, `complexType` `DataSet`嵌套專案會對應至內的。</span><span class="sxs-lookup"><span data-stu-id="8f8a3-107">However, a table is only created for a top-level `complexType` element when the `complexType` element is nested inside another `complexType` element, in which case the nested `complexType` element is mapped to a `DataTable` within the `DataSet`.</span></span>  
  
 <span data-ttu-id="8f8a3-108">如需有關 XSD 的詳細資訊, 請參閱全球資訊網協會 (W3C [) XML 架構第0部分:入門建議](https://www.w3.org/TR/xmlschema-0/) [, XML 架構第一部:結構建議](https://www.w3.org/TR/xmlschema-1/) [和 XML 架構第二部分:Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/) (XML 結構描述第 2 部分：資料類型建議)。</span><span class="sxs-lookup"><span data-stu-id="8f8a3-108">For more information about the XSD, see the World Wide Web Consortium (W3C) [XML Schema Part 0: Primer Recommendation](https://www.w3.org/TR/xmlschema-0/), the [XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/), and the [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>  
  
 <span data-ttu-id="8f8a3-109">下列範例示範 XML 架構, 其中`customers`是專案的子`MyDataSet`專案, 也就是**DataSet**元素。</span><span class="sxs-lookup"><span data-stu-id="8f8a3-109">The following example demonstrates an XML Schema where `customers` is the child element of the `MyDataSet` element, which is a **DataSet** element.</span></span>  
  
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
  
 <span data-ttu-id="8f8a3-110">上述範例中，`customers` 項目為複雜型別項目。</span><span class="sxs-lookup"><span data-stu-id="8f8a3-110">In the preceding example, the element `customers` is a complex type element.</span></span> <span data-ttu-id="8f8a3-111">因此，複雜型別定義會經過剖析，而對應處理序則會產生下列表格。</span><span class="sxs-lookup"><span data-stu-id="8f8a3-111">Therefore, the complex type definition is parsed, and the mapping process creates the following table.</span></span>  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 <span data-ttu-id="8f8a3-112">資料表內每個資料行的資料型別都衍生自對應項目的 XML 結構描述型別或指定屬性。</span><span class="sxs-lookup"><span data-stu-id="8f8a3-112">The data type of each column in the table is derived from the XML Schema type of the corresponding element or attribute specified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8f8a3-113">如果元素`customers`是簡單的 XML 架構資料類型 (例如**整數**), 則不會產生任何資料表。</span><span class="sxs-lookup"><span data-stu-id="8f8a3-113">If the element `customers` is of a simple XML Schema data type such as **integer**, no table is generated.</span></span> <span data-ttu-id="8f8a3-114">因為資料表僅會針對複雜型別的最上層項目產生。</span><span class="sxs-lookup"><span data-stu-id="8f8a3-114">Tables are only created for the top-level elements that are complex types.</span></span>  
  
 <span data-ttu-id="8f8a3-115">在下列 XML 架構中,**架構**元素有兩個專案子系`InStateCustomers` , `OutOfStateCustomers`和。</span><span class="sxs-lookup"><span data-stu-id="8f8a3-115">In the following XML Schema, the **Schema** element has two element children, `InStateCustomers` and `OutOfStateCustomers`.</span></span>  
  
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
  
 <span data-ttu-id="8f8a3-116">`InStateCustomers` 和 `OutOfStateCustomers` 子項目均為複雜型別項目 (`customerType`)。</span><span class="sxs-lookup"><span data-stu-id="8f8a3-116">Both the `InStateCustomers` and the `OutOfStateCustomers` child elements are complex type elements (`customerType`).</span></span> <span data-ttu-id="8f8a3-117">因此, 對應進程會在中`DataSet`產生下列兩個相同的資料表。</span><span class="sxs-lookup"><span data-stu-id="8f8a3-117">Therefore, the mapping process generates the following two identical tables in the `DataSet`.</span></span>  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="8f8a3-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="8f8a3-118">In This Section</span></span>  
 [<span data-ttu-id="8f8a3-119">將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束</span><span class="sxs-lookup"><span data-stu-id="8f8a3-119">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="8f8a3-120">描述用來在中`DataSet`建立唯一和外鍵條件約束的 XML 架構專案。</span><span class="sxs-lookup"><span data-stu-id="8f8a3-120">Describes the XML Schema elements used to create unique and foreign key constraints in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="8f8a3-121">從 XML 結構描述 (XSD) 產生資料集關聯</span><span class="sxs-lookup"><span data-stu-id="8f8a3-121">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="8f8a3-122">描述用來在的`DataSet`資料表資料行之間建立關聯的 XML 架構元素。</span><span class="sxs-lookup"><span data-stu-id="8f8a3-122">Describes the XML Schema elements used to create relations between table columns in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="8f8a3-123">XML 結構描述條件約束和關聯性</span><span class="sxs-lookup"><span data-stu-id="8f8a3-123">XML Schema Constraints and Relationships</span></span>](xml-schema-constraints-and-relationships.md)  
 <span data-ttu-id="8f8a3-124">描述在中`DataSet`使用 XML 架構專案來建立條件約束時, 如何隱含建立關聯性。</span><span class="sxs-lookup"><span data-stu-id="8f8a3-124">Describes how relations are created implicitly when using XML Schema elements to create constraints in a `DataSet`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8f8a3-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="8f8a3-125">Related Sections</span></span>  
 [<span data-ttu-id="8f8a3-126">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="8f8a3-126">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="8f8a3-127">描述如何在中`DataSet`將關聯式結構和資料載入和保存為 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="8f8a3-127">Describes how to load and persist the relational structure and data in a `DataSet` as XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f8a3-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f8a3-128">See also</span></span>

- [<span data-ttu-id="8f8a3-129">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="8f8a3-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
