---
title: 使用 XPathNavigator 存取強型別 XML 資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c283d3c87effcf9e898bb769cc8991da6cea453
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44199618"
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a><span data-ttu-id="eb383-102">使用 XPathNavigator 存取強型別 XML 資料</span><span class="sxs-lookup"><span data-stu-id="eb383-102">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>
<span data-ttu-id="eb383-103">做為 XPath 2.0 資料模型的執行個體，<xref:System.Xml.XPath.XPathNavigator> 類別可以包含對應至 Common Language Runtime (CLR) 型別的強型別資料。</span><span class="sxs-lookup"><span data-stu-id="eb383-103">As an instance of the XPath 2.0 data model, the <xref:System.Xml.XPath.XPathNavigator> class can contain strongly-typed data that maps to common language runtime (CLR) types.</span></span> <span data-ttu-id="eb383-104">根據 XPath 2.0 資料模型，只有項目及屬性才可以包含強型別資料。</span><span class="sxs-lookup"><span data-stu-id="eb383-104">According to the XPath 2.0 data model, only elements and attributes can contain strongly-typed data.</span></span> <span data-ttu-id="eb383-105"><xref:System.Xml.XPath.XPathNavigator> 類別提供可將 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 物件內的資料做為強型別資料進行存取的機制，以及將一種資料型別轉換為另一種型別的機制。</span><span class="sxs-lookup"><span data-stu-id="eb383-105">The <xref:System.Xml.XPath.XPathNavigator> class provides mechanisms for accessing data within an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object as strongly-typed data as well as mechanisms for converting from one data type to another.</span></span>  
  
## <a name="type-information-exposed-by-xpathnavigator"></a><span data-ttu-id="eb383-106">XPathNavigator 公開的型別資訊</span><span class="sxs-lookup"><span data-stu-id="eb383-106">Type Information Exposed by XPathNavigator</span></span>  
 <span data-ttu-id="eb383-107">就技術而言，XML 1.0 資料沒有型別，除非它是透過 DTD、XML 結構描述定義語言 (XSD) 結構描述或其他機制予以處理。</span><span class="sxs-lookup"><span data-stu-id="eb383-107">XML 1.0 data is technically without type, unless processed with a DTD, XML schema definition language (XSD) schema, or other mechanism.</span></span> <span data-ttu-id="eb383-108">某些類別的型別資訊，可以與 XML 項目或屬性相關聯。</span><span class="sxs-lookup"><span data-stu-id="eb383-108">There are a number of categories of type information that can be associated with an XML element or attribute.</span></span>  
  
-   <span data-ttu-id="eb383-109">簡單 CLR 型別：任何 XML 結構描述語言都無法直接支援 Common Language Runtime (CLR) 型別。</span><span class="sxs-lookup"><span data-stu-id="eb383-109">Simple CLR Types: None of the XML Schema languages support Common Language Runtime (CLR) types directly.</span></span> <span data-ttu-id="eb383-110">由於將簡單項目及屬性內容視為最適當的 CLR 型別很有用，因此在沒有結構描述資訊的情況下，所有的簡單內容都可以具有 <xref:System.String> 型別，並且任何加入的結構描述資訊都可能會將這個內容調整為更適當的型別。</span><span class="sxs-lookup"><span data-stu-id="eb383-110">Because it is useful to be able to view simple element and attribute content as the most appropriate CLR type, all simple content can be typed as <xref:System.String> in the absence of schema information with any added schema information potentially refining this content to a more appropriate type.</span></span> <span data-ttu-id="eb383-111">您可以利用 <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> 屬性，找到與簡單項目及屬性內容最相符的 CLR 型別。</span><span class="sxs-lookup"><span data-stu-id="eb383-111">You can find the best matching CLR type of simple element and attribute content by using the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property.</span></span> <span data-ttu-id="eb383-112">如需從結構描述內建型別對應至 CLR 型別的詳細資訊，請參閱 [System.Xml 類別中的型別支援](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="eb383-112">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
-   <span data-ttu-id="eb383-113">簡單 (CLR) 型別清單：具有簡單內容的項目或屬性可包含以空白字元分隔的值清單。</span><span class="sxs-lookup"><span data-stu-id="eb383-113">Lists of Simple (CLR) Types: An element or attribute with simple content can contain a list of values separated by white space.</span></span> <span data-ttu-id="eb383-114">這些值是透過 XML 結構描述指定為「清單型別」。</span><span class="sxs-lookup"><span data-stu-id="eb383-114">The values are specified by an XML Schema to be a "list type."</span></span> <span data-ttu-id="eb383-115">如果沒有 XML 結構描述，則會將此類簡單內容視為單一文字節點。</span><span class="sxs-lookup"><span data-stu-id="eb383-115">In the absence of an XML Schema, such simple content would be treated as a single text node.</span></span> <span data-ttu-id="eb383-116">當有 XML 結構描述可用時，這個簡單內容可公開為一系列原子值，並且每個值都有對應至 CLR 物件集合的簡單型別。</span><span class="sxs-lookup"><span data-stu-id="eb383-116">When an XML Schema is available, this simple content can be exposed as a series of atomic values each having a simple type that maps to a collection of CLR objects.</span></span> <span data-ttu-id="eb383-117">如需從結構描述內建型別對應至 CLR 型別的詳細資訊，請參閱 [System.Xml 類別中的型別支援](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="eb383-117">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
-   <span data-ttu-id="eb383-118">具型別值：具有簡單型別之已驗證結構描述的屬性或項目都會擁有具型別值。</span><span class="sxs-lookup"><span data-stu-id="eb383-118">Typed Value: A schema-validated attribute or element with a simple type has a typed value.</span></span> <span data-ttu-id="eb383-119">這個值為基本型別，如數字、字串或日期型別。</span><span class="sxs-lookup"><span data-stu-id="eb383-119">This value is a primitive type such as a numeric, string, or date type.</span></span> <span data-ttu-id="eb383-120">XSD 中的所有內建簡單型別都可以對應至 CLR 型別，因為 CLR 型別可做為更適合提供節點值之存取權的型別，而不是只做為 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="eb383-120">All the built-in simple types in XSD can be mapped to CLR types that provide access to the value of a node as a more appropriate type instead of just as a <xref:System.String>.</span></span> <span data-ttu-id="eb383-121">具有屬性或項目子系的項目會視為複雜型別。</span><span class="sxs-lookup"><span data-stu-id="eb383-121">An element with attributes or element children is considered to be a complex type.</span></span> <span data-ttu-id="eb383-122">具有簡單內容之複雜型別的具型別值 (做為子系的唯一文字節點)，與其內容之簡單型別的具型別值相同。</span><span class="sxs-lookup"><span data-stu-id="eb383-122">The typed value of a complex type with simple content (only text nodes as children) is the same as that of the simple type of its content.</span></span> <span data-ttu-id="eb383-123">具有複雜內容之複雜型別的具型別值 (一或多個項目子系)，是以 <xref:System.String> 型式傳回之所有子文字節點串連的字串值。</span><span class="sxs-lookup"><span data-stu-id="eb383-123">The typed value of a complex type with complex content (one or more child elements) is the string value of the concatenation of all its child text nodes returned as a <xref:System.String>.</span></span> <span data-ttu-id="eb383-124">如需從結構描述內建型別對應至 CLR 型別的詳細資訊，請參閱 [System.Xml 類別中的型別支援](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="eb383-124">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
-   <span data-ttu-id="eb383-125">結構描述語言特定的型別名稱：在大多數情況中，設為套用外部結構描述之副作用的 CLR 型別，都會用來提供節點值的存取權。</span><span class="sxs-lookup"><span data-stu-id="eb383-125">Schema-Language Specific Type Name: In most cases, the CLR types, which are set as a side-effect of applying an external schema, are used to provide access to the value of a node.</span></span> <span data-ttu-id="eb383-126">然而，有時您也可能想要檢查與套用至 XML 文件之特定結構描述相關聯的型別。</span><span class="sxs-lookup"><span data-stu-id="eb383-126">However, there may be situations where you may want to examine the type associated with a particular schema applied to an XML document.</span></span> <span data-ttu-id="eb383-127">例如，您可能想要搜尋 XML 文件，擷取根據附加的結構描述判定其具有型別內容 PurchaseOrder 的所有項目。</span><span class="sxs-lookup"><span data-stu-id="eb383-127">For example, you may wish to search through an XML document, extracting all elements that are determined to have content of type "PurchaseOrder" according to an attached schema.</span></span> <span data-ttu-id="eb383-128">這類資訊只會因結構描述驗證而加以設定，並且此資訊是透過 <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> 及 <xref:System.Xml.XPath.XPathNavigator> 屬性來進行存取。</span><span class="sxs-lookup"><span data-stu-id="eb383-128">Such type information can be set only as a result of schema validation and this information is accessed through the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> and <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="eb383-129">如需詳細資訊，請參閱下面的＜後結構描述驗證資訊集 (PSVI)＞一節。</span><span class="sxs-lookup"><span data-stu-id="eb383-129">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
-   <span data-ttu-id="eb383-130">結構描述語言特定的型別反映：在其他情況下，您可能要取得套用至 XML 文件之結構描述特定型別更詳細的資料。</span><span class="sxs-lookup"><span data-stu-id="eb383-130">Schema-Language Specific Type Reflection: In other cases, you may want to obtain further details of the schema-specific type applied to an XML document.</span></span> <span data-ttu-id="eb383-131">例如，在讀取 XML 檔案時，可能要擷取 XML 文件中每個有效節點的 `maxOccurs` 屬性，以執行部份自訂計算。</span><span class="sxs-lookup"><span data-stu-id="eb383-131">For example, when reading an XML file, you may want to extract the `maxOccurs` attribute for each valid node in the XML document in order to perform some custom calculation.</span></span> <span data-ttu-id="eb383-132">因為此資訊只會透過結構描述驗證來予以設定，所以它會透過 <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator> 屬性來進行存取。</span><span class="sxs-lookup"><span data-stu-id="eb383-132">Because this information is set only through schema validation, it is accessed through the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="eb383-133">如需詳細資訊，請參閱下面的＜後結構描述驗證資訊集 (PSVI)＞一節。</span><span class="sxs-lookup"><span data-stu-id="eb383-133">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
## <a name="xpathnavigator-typed-accessors"></a><span data-ttu-id="eb383-134">XPathNavigator 具型別存取子</span><span class="sxs-lookup"><span data-stu-id="eb383-134">XPathNavigator Typed Accessors</span></span>  
 <span data-ttu-id="eb383-135">下表顯示可用於存取節點相關型別資訊之 <xref:System.Xml.XPath.XPathNavigator> 類別的各種屬性及方法。</span><span class="sxs-lookup"><span data-stu-id="eb383-135">The following table shows the various properties and methods of the <xref:System.Xml.XPath.XPathNavigator> class that can be used to access the type information about a node.</span></span>  
  
|<span data-ttu-id="eb383-136">屬性</span><span class="sxs-lookup"><span data-stu-id="eb383-136">Property</span></span>|<span data-ttu-id="eb383-137">描述</span><span class="sxs-lookup"><span data-stu-id="eb383-137">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|<span data-ttu-id="eb383-138">包含有效節點的 XML 結構描述型別資訊。</span><span class="sxs-lookup"><span data-stu-id="eb383-138">This contains the XML schema type information for the node if it is valid.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|<span data-ttu-id="eb383-139">包含驗證後加入之節點的後結構描述驗證資訊集。</span><span class="sxs-lookup"><span data-stu-id="eb383-139">This contains the Post Schema Validation Infoset of the node that is added after validation.</span></span> <span data-ttu-id="eb383-140">包含 XML 結構描述型別資訊，以及有效性資訊。</span><span class="sxs-lookup"><span data-stu-id="eb383-140">This includes the XML schema type information, as well as validity information.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|<span data-ttu-id="eb383-141">節點之具型別值的 CLR 型別。</span><span class="sxs-lookup"><span data-stu-id="eb383-141">The CLR type of the typed value of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|<span data-ttu-id="eb383-142">其型別最符合節點之 XML 結構描述型別的一或多個 CLR 值的節點內容。</span><span class="sxs-lookup"><span data-stu-id="eb383-142">The content of the node as one or more CLR values whose type is the closest match to the XML schema type of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<span data-ttu-id="eb383-143">根據 <xref:System.String> 的 XPath 2.0 轉換規則，轉換為 <xref:System.Boolean> 值之目前節點的 `xs:boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="eb383-143">The <xref:System.String> value of the current node cast to a <xref:System.Boolean> value, according to the XPath 2.0 casting rules for `xs:boolean`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<span data-ttu-id="eb383-144">根據 <xref:System.String> 的 XPath 2.0 轉換規則，轉換為 <xref:System.DateTime> 值之目前節點的 `xs:datetime` 值。</span><span class="sxs-lookup"><span data-stu-id="eb383-144">The <xref:System.String> value of the current node cast to a <xref:System.DateTime> value, according to the XPath 2.0 casting rules for `xs:datetime`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<span data-ttu-id="eb383-145">根據 <xref:System.String> 的 XPath 2.0 轉換規則，轉換為 <xref:System.Double> 值之目前節點的 `xsd:double` 值。</span><span class="sxs-lookup"><span data-stu-id="eb383-145">The <xref:System.String> value of the current node cast to a <xref:System.Double> value, according to the XPath 2.0 casting rules for `xsd:double`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<span data-ttu-id="eb383-146">根據 <xref:System.String> 的 XPath 2.0 轉換規則，轉換為 <xref:System.Int32> 值之目前節點的 `xs:integer` 值。</span><span class="sxs-lookup"><span data-stu-id="eb383-146">The <xref:System.String> value of the current node cast to a <xref:System.Int32> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<span data-ttu-id="eb383-147">根據 <xref:System.String> 的 XPath 2.0 轉換規則，轉換為 <xref:System.Int64> 值之目前節點的 `xs:integer` 值。</span><span class="sxs-lookup"><span data-stu-id="eb383-147">The <xref:System.String> value of the current node cast to a <xref:System.Int64> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|<span data-ttu-id="eb383-148">根據 XPath 2.0 轉換規則，轉換為目標型別之節點的內容。</span><span class="sxs-lookup"><span data-stu-id="eb383-148">The contents of the node cast to the target type according to the XPath 2.0 casting rules.</span></span>|  
  
 <span data-ttu-id="eb383-149">如需從結構描述內建型別對應至 CLR 型別的詳細資訊，請參閱 [System.Xml 類別中的型別支援](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="eb383-149">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="the-post-schema-validation-infoset-psvi"></a><span data-ttu-id="eb383-150">後結構描述驗證資訊集 (PSVI)</span><span class="sxs-lookup"><span data-stu-id="eb383-150">The Post Schema Validation Infoset (PSVI)</span></span>  
 <span data-ttu-id="eb383-151">XML 結構描述處理器接受使用 XML 資訊集做為輸入，並將其轉換為後結構描述驗證資訊集 (PSVI)。</span><span class="sxs-lookup"><span data-stu-id="eb383-151">An XML Schema processor accepts an XML Infoset as input and converts it into a Post Schema Validation Infoset (PSVI).</span></span> <span data-ttu-id="eb383-152">PSVI 為原始輸入 XML 資訊集，內含在現有資訊項目中加入新的資訊項目及新屬性。</span><span class="sxs-lookup"><span data-stu-id="eb383-152">A PSVI is the original input XML infoset with new information items added and new properties added to existing information items.</span></span> <span data-ttu-id="eb383-153">有三大資訊類別會加入至 PSVI 中的 XML 資訊集，並且這些資訊是由 <xref:System.Xml.XPath.XPathNavigator> 公開。</span><span class="sxs-lookup"><span data-stu-id="eb383-153">There are three broad classes of information added to the XML Infoset in the PSVI that are exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
1.  <span data-ttu-id="eb383-154">驗證結果：是否已成功驗證項目或屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="eb383-154">Validation Outcomes: Information as to whether an element or attribute was successfully validated or not.</span></span> <span data-ttu-id="eb383-155">由 <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> 類別之 <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> 屬性的 <xref:System.Xml.XPath.XPathNavigator> 屬性公開。</span><span class="sxs-lookup"><span data-stu-id="eb383-155">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
2.  <span data-ttu-id="eb383-156">預設資訊：是否已透過結構描述中指定的預設值，取得項目或屬性值的相關指示。</span><span class="sxs-lookup"><span data-stu-id="eb383-156">Default Information: Indications as to whether the value of the element or attribute was obtained via default values specified in the schema or not.</span></span> <span data-ttu-id="eb383-157">由 <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> 類別之 <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> 屬性的 <xref:System.Xml.XPath.XPathNavigator> 屬性公開。</span><span class="sxs-lookup"><span data-stu-id="eb383-157">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
3.  <span data-ttu-id="eb383-158">型別附註：可能是型別定義或項目及屬性宣告之結構描述元件的參考。</span><span class="sxs-lookup"><span data-stu-id="eb383-158">Type Annotations: References to schema components that may be type definitions or element and attribute declarations.</span></span> <span data-ttu-id="eb383-159"><xref:System.Xml.XPath.XPathNavigator.XmlType%2A> 的 <xref:System.Xml.XPath.XPathNavigator> 屬性包含有效節點的特定型別資訊。</span><span class="sxs-lookup"><span data-stu-id="eb383-159">The <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property of the <xref:System.Xml.XPath.XPathNavigator> contains the specific type information of the node if it is valid.</span></span> <span data-ttu-id="eb383-160">如果節點的有效性是未知的 (例如在完成驗證後，又進行了編輯時)，</span><span class="sxs-lookup"><span data-stu-id="eb383-160">If the validity of a node is unknown, such as when it was validated then subsequently edited.</span></span> <span data-ttu-id="eb383-161">則 <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> 屬性會設為 `null`，但仍可從 <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> 類別之 <xref:System.Xml.XPath.XPathNavigator> 屬性中的各種屬性取得型別資訊。</span><span class="sxs-lookup"><span data-stu-id="eb383-161">then the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property is set to `null` but type information is still available from the various properties of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="eb383-162">下列範例會說明如何使用 <xref:System.Xml.XPath.XPathNavigator> 所公開之後結構描述驗證資訊集中的資訊。</span><span class="sxs-lookup"><span data-stu-id="eb383-162">The following example illustrates using information in the Post Schema Validation Infoset exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("books.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("published", "http://www.contoso.com/books")  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name)  
Console.WriteLine(navigator.SchemaInfo.Validity)  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("books.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("published", "http://www.contoso.com/books");  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name);  
Console.WriteLine(navigator.SchemaInfo.Validity);  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs);  
```  
  
 <span data-ttu-id="eb383-163">該範例採用 `books.xml` 檔案做為輸入。</span><span class="sxs-lookup"><span data-stu-id="eb383-163">The example takes the `books.xml` file as input.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="eb383-164">該範例也會採用 `books.xsd` 結構描述做為輸入。</span><span class="sxs-lookup"><span data-stu-id="eb383-164">The example also takes the `books.xsd` schema as input.</span></span>  
  
```xml  
<xs:schema xmlns="http://www.contoso.com/books"   
attributeFormDefault="unqualified" elementFormDefault="qualified"   
targetNamespace="http://www.contoso.com/books"   
xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="publishedType">  
        <xs:restriction base="xs:date">  
            <xs:minInclusive value="2003-01-01" />  
            <xs:maxInclusive value="2003-12-31" />  
        </xs:restriction>  
    </xs:simpleType>  
    <xs:complexType name="bookType">  
        <xs:sequence>  
            <xs:element name="title" type="xs:string"/>  
            <xs:element name="price" type="xs:decimal"/>  
            <xs:element name="published" type="publishedType"/>  
        </xs:sequence>  
    </xs:complexType>  
    <xs:complexType name="booksType">  
        <xs:sequence>  
            <xs:element name="book" type="bookType" />  
        </xs:sequence>  
    </xs:complexType>  
    <xs:element name="books" type="booksType" />  
</xs:schema>  
```  
  
## <a name="obtain-typed-values-using-valueas-properties"></a><span data-ttu-id="eb383-165">使用 ValueAs 屬性取得具型別值</span><span class="sxs-lookup"><span data-stu-id="eb383-165">Obtain Typed Values Using ValueAs Properties</span></span>  
 <span data-ttu-id="eb383-166">節點的具型別值可藉由存取 <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> 的 <xref:System.Xml.XPath.XPathNavigator> 屬性來擷取。</span><span class="sxs-lookup"><span data-stu-id="eb383-166">The typed value of a node can be retrieved by accessing the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="eb383-167">在某些情況下，您可能要將節點的具型別值轉換為不同的型別。</span><span class="sxs-lookup"><span data-stu-id="eb383-167">In certain cases you may want to convert the typed value of a node to a different type.</span></span> <span data-ttu-id="eb383-168">常見的範例是從 XML 節點取得數值。</span><span class="sxs-lookup"><span data-stu-id="eb383-168">A common example is to get a numeric value from an XML node.</span></span> <span data-ttu-id="eb383-169">例如，請考量下列未經驗證且不具型別的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="eb383-169">For example, consider the following unvalidated and untyped XML document.</span></span>  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="eb383-170">如果 <xref:System.Xml.XPath.XPathNavigator> 定位於 `price` 項目中，則 <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> 屬性為 `null`，<xref:System.Xml.XPath.XPathNavigator.ValueType%2A> 屬性為 <xref:System.String>，以及 <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> 屬性為字串 `10.00`。</span><span class="sxs-lookup"><span data-stu-id="eb383-170">If the <xref:System.Xml.XPath.XPathNavigator> is positioned on the `price` element the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property would be `null`, the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property would be <xref:System.String>, and the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property would be the string `10.00`.</span></span>  
  
 <span data-ttu-id="eb383-171">然而，仍有可能使用 <xref:System.Xml.XPath.XPathItem.ValueAs%2A>、<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>、<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A> 或 <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> 方法及屬性，將該值擷取為數值。</span><span class="sxs-lookup"><span data-stu-id="eb383-171">However, it is still possible to extract the value as a numeric value using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, or <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> method and properties.</span></span> <span data-ttu-id="eb383-172">下列範例說明如何使用 <xref:System.Xml.XPath.XPathItem.ValueAs%2A> 方法來執行此類轉換。</span><span class="sxs-lookup"><span data-stu-id="eb383-172">The following example illustrates performing such a cast using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A> method.</span></span>  
  
```vb  
Dim document As New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "")  
navigator.MoveToChild("book", "")  
navigator.MoveToChild("price", "")  
  
Dim price = navigator.ValueAs(GetType(Decimal))  
Dim discount As Decimal = 0.2  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * discount))  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "");  
navigator.MoveToChild("book", "");  
navigator.MoveToChild("price", "");  
  
Decimal price = (decimal)navigator.ValueAs(typeof(decimal));  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * (decimal)0.20));  
```  
  
 <span data-ttu-id="eb383-173">如需從結構描述內建型別對應至 CLR 型別的詳細資訊，請參閱 [System.Xml 類別中的型別支援](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="eb383-173">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb383-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb383-174">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="eb383-175">System.Xml 類別中的類型支援</span><span class="sxs-lookup"><span data-stu-id="eb383-175">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)  
- [<span data-ttu-id="eb383-176">使用 XPath 資料模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="eb383-176">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="eb383-177">使用 XPathNavigator 導覽節點集</span><span class="sxs-lookup"><span data-stu-id="eb383-177">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
- [<span data-ttu-id="eb383-178">使用 XPathNavigator 導覽屬性和命名空間節點</span><span class="sxs-lookup"><span data-stu-id="eb383-178">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
- [<span data-ttu-id="eb383-179">使用 XPathNavigator 擷取 XML 資料</span><span class="sxs-lookup"><span data-stu-id="eb383-179">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
