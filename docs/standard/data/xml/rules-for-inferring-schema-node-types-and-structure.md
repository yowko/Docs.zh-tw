---
title: 推斷結構描述節點型別與結構的規則
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d74ce896-717d-4871-8fd9-b070e2f53cb0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1593f703f1f8b4465b46d3b22b763d35c582744
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="rules-for-inferring-schema-node-types-and-structure"></a><span data-ttu-id="0bff5-102">推斷結構描述節點型別與結構的規則</span><span class="sxs-lookup"><span data-stu-id="0bff5-102">Rules for Inferring Schema Node Types and Structure</span></span>
<span data-ttu-id="0bff5-103">本主題說明結構描述推斷程序如何將 XML 文件中所發現的節點型別轉譯為 XML 結構描述定義語言 (XSD) 結構。</span><span class="sxs-lookup"><span data-stu-id="0bff5-103">This topic describes how the schema inference process translates the node types in an XML document to an XML Schema definition language (XSD) structure.</span></span>  
  
## <a name="element-inference-rules"></a><span data-ttu-id="0bff5-104">項目推斷規則</span><span class="sxs-lookup"><span data-stu-id="0bff5-104">Element Inference Rules</span></span>  
 <span data-ttu-id="0bff5-105">本節將說明項目宣告的推斷規則。</span><span class="sxs-lookup"><span data-stu-id="0bff5-105">This section describes the inference rules for element declarations.</span></span> <span data-ttu-id="0bff5-106">有八種項目宣告的結構會進行推斷：</span><span class="sxs-lookup"><span data-stu-id="0bff5-106">There are eight structures of element declarations that will be inferred:</span></span>  
  
1.  <span data-ttu-id="0bff5-107">簡單型別項目</span><span class="sxs-lookup"><span data-stu-id="0bff5-107">Element of simple type</span></span>  
  
2.  <span data-ttu-id="0bff5-108">空白項目</span><span class="sxs-lookup"><span data-stu-id="0bff5-108">Empty element</span></span>  
  
3.  <span data-ttu-id="0bff5-109">具有屬性的空白項目</span><span class="sxs-lookup"><span data-stu-id="0bff5-109">Empty element with attributes</span></span>  
  
4.  <span data-ttu-id="0bff5-110">具有屬性與簡單內容的項目</span><span class="sxs-lookup"><span data-stu-id="0bff5-110">Element with attributes and simple content</span></span>  
  
5.  <span data-ttu-id="0bff5-111">具有項目子系序列的項目</span><span class="sxs-lookup"><span data-stu-id="0bff5-111">Element with a sequence of child elements</span></span>  
  
6.  <span data-ttu-id="0bff5-112">具有項目子系與屬性序列的項目</span><span class="sxs-lookup"><span data-stu-id="0bff5-112">Element with a sequence of child elements and attributes</span></span>  
  
7.  <span data-ttu-id="0bff5-113">具有項目子系選擇序列的項目</span><span class="sxs-lookup"><span data-stu-id="0bff5-113">Element with a sequence of choices of child elements</span></span>  
  
8.  <span data-ttu-id="0bff5-114">具有項目子系與屬性選擇序列的項目</span><span class="sxs-lookup"><span data-stu-id="0bff5-114">Element with a sequence of choices of child elements and attributes</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0bff5-115">所有 `complexType` 宣告都會被推斷為匿名型別。</span><span class="sxs-lookup"><span data-stu-id="0bff5-115">All `complexType` declarations are inferred as anonymous types.</span></span> <span data-ttu-id="0bff5-116">唯一會進行推斷的全域項目為根項目；其他項目都是區域項目。</span><span class="sxs-lookup"><span data-stu-id="0bff5-116">The only global element inferred is the root element; all other elements are local.</span></span>  
  
 <span data-ttu-id="0bff5-117">如需結構描述推斷程序的詳細資訊，請參閱[從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)。</span><span class="sxs-lookup"><span data-stu-id="0bff5-117">For more information about the schema inference process, see [Inferring Schemas from XML Documents](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).</span></span>  
  
### <a name="simple-typed-element"></a><span data-ttu-id="0bff5-118">簡單型別項目</span><span class="sxs-lookup"><span data-stu-id="0bff5-118">Simple Typed Element</span></span>  
 <span data-ttu-id="0bff5-119">下表顯示對 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> 方法的 XML 輸入及產生的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="0bff5-119">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="0bff5-120">粗體的項目表示針對簡單型別項目所推斷的結構描述。</span><span class="sxs-lookup"><span data-stu-id="0bff5-120">The bolded element shows the schema inferred for the simple type element.</span></span>  
  
 <span data-ttu-id="0bff5-121">如需結構描述推斷程序的詳細資訊，請參閱[從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)。</span><span class="sxs-lookup"><span data-stu-id="0bff5-121">For more information about the schema inference process, see [Inferring Schemas from XML Documents](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="0bff5-122">XML</span><span class="sxs-lookup"><span data-stu-id="0bff5-122">XML</span></span>|<span data-ttu-id="0bff5-123">結構描述</span><span class="sxs-lookup"><span data-stu-id="0bff5-123">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>text</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root" type="xs:string" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element"></a><span data-ttu-id="0bff5-124">空元素</span><span class="sxs-lookup"><span data-stu-id="0bff5-124">Empty Element</span></span>  
 <span data-ttu-id="0bff5-125">下表顯示對 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> 方法的 XML 輸入及產生的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="0bff5-125">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="0bff5-126">粗體的項目表示針對空白項目所推斷的結構描述。</span><span class="sxs-lookup"><span data-stu-id="0bff5-126">The bolded element shows the schema inferred for the empty element.</span></span>  
  
 <span data-ttu-id="0bff5-127">如需結構描述推斷程序的詳細資訊，請參閱[從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)。</span><span class="sxs-lookup"><span data-stu-id="0bff5-127">For more information about the schema inference process, see [Inferring Schemas from XML Documents](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="0bff5-128">XML</span><span class="sxs-lookup"><span data-stu-id="0bff5-128">XML</span></span>|<span data-ttu-id="0bff5-129">結構描述</span><span class="sxs-lookup"><span data-stu-id="0bff5-129">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element-with-attributes"></a><span data-ttu-id="0bff5-130">具有屬性的空白項目</span><span class="sxs-lookup"><span data-stu-id="0bff5-130">Empty Element with Attributes</span></span>  
 <span data-ttu-id="0bff5-131">下表顯示對 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> 方法的 XML 輸入及產生的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="0bff5-131">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="0bff5-132">粗體的項目表示針對具有屬性的空白項目所推斷的結構描述。</span><span class="sxs-lookup"><span data-stu-id="0bff5-132">The bolded elements show the schema inferred for the empty element with attributes.</span></span>  
  
 <span data-ttu-id="0bff5-133">如需結構描述推斷程序的詳細資訊，請參閱[從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)。</span><span class="sxs-lookup"><span data-stu-id="0bff5-133">For more information about the schema inference process, see [Inferring Schemas from XML Documents](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="0bff5-134">XML</span><span class="sxs-lookup"><span data-stu-id="0bff5-134">XML</span></span>|<span data-ttu-id="0bff5-135">結構描述</span><span class="sxs-lookup"><span data-stu-id="0bff5-135">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty attribute1="text"/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-attributes-and-simple-content"></a><span data-ttu-id="0bff5-136">具有屬性與簡單內容的項目</span><span class="sxs-lookup"><span data-stu-id="0bff5-136">Element with Attributes and Simple Content</span></span>  
 <span data-ttu-id="0bff5-137">下表顯示對 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> 方法的 XML 輸入及產生的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="0bff5-137">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="0bff5-138">粗體的項目表示針對具有屬性與簡單內容的項目所推斷的結構描述。</span><span class="sxs-lookup"><span data-stu-id="0bff5-138">The bolded elements show the schema inferred for an element with attributes and simple content.</span></span>  
  
 <span data-ttu-id="0bff5-139">如需結構描述推斷程序的詳細資訊，請參閱[從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)。</span><span class="sxs-lookup"><span data-stu-id="0bff5-139">For more information about the schema inference process, see [Inferring Schemas from XML Documents](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="0bff5-140">XML</span><span class="sxs-lookup"><span data-stu-id="0bff5-140">XML</span></span>|<span data-ttu-id="0bff5-141">結構描述</span><span class="sxs-lookup"><span data-stu-id="0bff5-141">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">value</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:simpleContent>`<br /><br /> `<xs:extension base="xs:string">`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:extension>`<br /><br /> `</xs:simpleContent>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements"></a><span data-ttu-id="0bff5-142">具有項目子系序列的項目</span><span class="sxs-lookup"><span data-stu-id="0bff5-142">Element with a Sequence of Child Elements</span></span>  
 <span data-ttu-id="0bff5-143">下表顯示對 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> 方法的 XML 輸入及產生的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="0bff5-143">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="0bff5-144">粗體的項目表示針對具有項目子系序列的項目所推斷的結構描述。</span><span class="sxs-lookup"><span data-stu-id="0bff5-144">The bolded elements show the schema inferred for an element with a sequence of child elements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0bff5-145">即使某個項目只有一個項目子系，仍會被視為序列。</span><span class="sxs-lookup"><span data-stu-id="0bff5-145">Even if an element has only one child element, it is still treated as a sequence.</span></span>  
  
 <span data-ttu-id="0bff5-146">如需結構描述推斷程序的詳細資訊，請參閱[從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)。</span><span class="sxs-lookup"><span data-stu-id="0bff5-146">For more information about the schema inference process, see [Inferring Schemas from XML Documents](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="0bff5-147">XML</span><span class="sxs-lookup"><span data-stu-id="0bff5-147">XML</span></span>|<span data-ttu-id="0bff5-148">結構描述</span><span class="sxs-lookup"><span data-stu-id="0bff5-148">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement" />`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements-and-attributes"></a><span data-ttu-id="0bff5-149">具有項目子系與屬性序列的項目</span><span class="sxs-lookup"><span data-stu-id="0bff5-149">Element with a Sequence of Child Elements and Attributes</span></span>  
 <span data-ttu-id="0bff5-150">下表顯示對 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> 方法的 XML 輸入及產生的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="0bff5-150">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="0bff5-151">粗體的項目表示針對具有項目子系與屬性序列的項目所推斷的結構描述。</span><span class="sxs-lookup"><span data-stu-id="0bff5-151">The bolded elements show the schema inferred for an element with a sequence of child elements and attributes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0bff5-152">即使某個項目只有一個項目子系，仍會被視為序列。</span><span class="sxs-lookup"><span data-stu-id="0bff5-152">Even if an element has only one child element, it is still treated as a sequence.</span></span>  
  
 <span data-ttu-id="0bff5-153">如需結構描述推斷程序的詳細資訊，請參閱[從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)。</span><span class="sxs-lookup"><span data-stu-id="0bff5-153">For more information about the schema inference process, see [Inferring Schemas from XML Documents](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="0bff5-154">XML</span><span class="sxs-lookup"><span data-stu-id="0bff5-154">XML</span></span>|<span data-ttu-id="0bff5-155">結構描述</span><span class="sxs-lookup"><span data-stu-id="0bff5-155">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choices-of-child-elements"></a><span data-ttu-id="0bff5-156">具有項目子系選擇序列的項目</span><span class="sxs-lookup"><span data-stu-id="0bff5-156">Element with a Sequence and Choices of Child Elements</span></span>  
 <span data-ttu-id="0bff5-157">下表顯示對 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> 方法的 XML 輸入及產生的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="0bff5-157">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="0bff5-158">粗體的項目表示針對具有項目子系選擇序列的項目所推斷的結構描述。</span><span class="sxs-lookup"><span data-stu-id="0bff5-158">The bolded elements show the schema inferred for an element with a sequence and choice of child elements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0bff5-159">在推斷的結構描述中，`maxOccurs` 項目的 `xs:choice` 屬性會設為 `"unbounded"`。</span><span class="sxs-lookup"><span data-stu-id="0bff5-159">The `maxOccurs` attribute of the `xs:choice` element is set to `"unbounded"` in the inferred schema.</span></span>  
  
 <span data-ttu-id="0bff5-160">如需結構描述推斷程序的詳細資訊，請參閱[從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)。</span><span class="sxs-lookup"><span data-stu-id="0bff5-160">For more information about the schema inference process, see [Inferring Schemas from XML Documents](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="0bff5-161">XML</span><span class="sxs-lookup"><span data-stu-id="0bff5-161">XML</span></span>|<span data-ttu-id="0bff5-162">結構描述</span><span class="sxs-lookup"><span data-stu-id="0bff5-162">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choice-of-child-elements-and-attributes"></a><span data-ttu-id="0bff5-163">具有項目子系與屬性之序列與選擇的項目</span><span class="sxs-lookup"><span data-stu-id="0bff5-163">Element with a Sequence and Choice of Child Elements and Attributes</span></span>  
 <span data-ttu-id="0bff5-164">下表顯示對 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> 方法的 XML 輸入及產生的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="0bff5-164">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="0bff5-165">粗體的項目表示針對具有項目子系與屬性之序列與選擇的項目所推斷的結構描述。</span><span class="sxs-lookup"><span data-stu-id="0bff5-165">The bolded elements show the schema inferred for an element with a sequence and choice of child elements and attributes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0bff5-166">在推斷的結構描述中，`maxOccurs` 項目的 `xs:choice` 屬性會設為 `"unbounded"`。</span><span class="sxs-lookup"><span data-stu-id="0bff5-166">The `maxOccurs` attribute of the `xs:choice` element is set to `"unbounded"` in the inferred schema.</span></span>  
  
 <span data-ttu-id="0bff5-167">如需結構描述推斷程序的詳細資訊，請參閱[從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)。</span><span class="sxs-lookup"><span data-stu-id="0bff5-167">For more information about the schema inference process, see [Inferring Schemas from XML Documents](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="0bff5-168">XML</span><span class="sxs-lookup"><span data-stu-id="0bff5-168">XML</span></span>|<span data-ttu-id="0bff5-169">結構描述</span><span class="sxs-lookup"><span data-stu-id="0bff5-169">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="attribute-processing"></a><span data-ttu-id="0bff5-170">屬性處理</span><span class="sxs-lookup"><span data-stu-id="0bff5-170">Attribute Processing</span></span>  
 <span data-ttu-id="0bff5-171">每當在節點中發現新的屬性時，該屬性就會以 `use="required"` 加入節點的推斷定義中。</span><span class="sxs-lookup"><span data-stu-id="0bff5-171">Whenever a new attribute is encountered within a node, it is added to the inferred definition of the node with `use="required"`.</span></span> <span data-ttu-id="0bff5-172">下次在執行個體中發現相同的節點時，推斷程序就會比較目前執行個體的屬性與已推斷的屬性。</span><span class="sxs-lookup"><span data-stu-id="0bff5-172">The next time the same node is found in the instance, the inference process will compare attributes of the current instance with the ones already inferred.</span></span> <span data-ttu-id="0bff5-173">若執行個體中缺少某些已推斷的屬性，`use="optional"` 就會加入屬性定義中。</span><span class="sxs-lookup"><span data-stu-id="0bff5-173">If some of the already inferred ones are missing in the instance, `use="optional"` is added to the attribute definition.</span></span> <span data-ttu-id="0bff5-174">新屬性會以 `use="optional"` 加入現有的宣告中。</span><span class="sxs-lookup"><span data-stu-id="0bff5-174">New attributes are added to existing declarations with `use="optional"`.</span></span>  
  
### <a name="occurrence-constraints"></a><span data-ttu-id="0bff5-175">出現條件約束</span><span class="sxs-lookup"><span data-stu-id="0bff5-175">Occurrence Constraints</span></span>  
 <span data-ttu-id="0bff5-176">在結構描述推斷程序中，會針對結構描述的推斷元件產生 `minOccurs` 和 `maxOccurs` 屬性，其值為 `"0"` 或 `"1"`，以及 `"1"` 或 `"unbounded"`。</span><span class="sxs-lookup"><span data-stu-id="0bff5-176">During the schema inference process, the `minOccurs` and `maxOccurs` attributes are generated, for inferred components of a schema, with the values `"0"` or `"1"` and `"1"` or `"unbounded"`.</span></span> <span data-ttu-id="0bff5-177">`"1"` 和 `"unbounded"` 這兩個值，必須在 `"0"` 與 `"1"` 這兩個值無法驗證 XML 文件時，才會使用 (例如，若 `MinOccurs="0"` 無法精確說明某個項目，才會使用 `minOccurs="1"`)。</span><span class="sxs-lookup"><span data-stu-id="0bff5-177">The values `"1"` and `"unbounded"` are used only when the values `"0"` and `"1"` cannot validate the XML document (for example, if `MinOccurs="0"` does not accurately describe an element, `minOccurs="1"` is used).</span></span>  
  
### <a name="mixed-content"></a><span data-ttu-id="0bff5-178">混合內容</span><span class="sxs-lookup"><span data-stu-id="0bff5-178">Mixed Content</span></span>  
 <span data-ttu-id="0bff5-179">若項目中含有混合內容 (例如文字與項目相互穿插)，則會針對已推斷的複雜型別定義產生 `mixed="true"` 屬性。</span><span class="sxs-lookup"><span data-stu-id="0bff5-179">If an element contains mixed content (for example text interspersed with elements), the `mixed="true"` attribute is generated for the inferred complex type definition.</span></span>  
  
## <a name="other-node-type-inference-rules"></a><span data-ttu-id="0bff5-180">其他節點型別推斷規則</span><span class="sxs-lookup"><span data-stu-id="0bff5-180">Other Node Type Inference Rules</span></span>  
 <span data-ttu-id="0bff5-181">下表所說明的推斷規則，可用來處理指示、註解、實體參考、CDATA、文件型別與命名空間節點。</span><span class="sxs-lookup"><span data-stu-id="0bff5-181">The following table describes the inference rules for processing instruction, comment, entity reference, CDATA, document type, and namespace nodes.</span></span>  
  
|<span data-ttu-id="0bff5-182">節點類型</span><span class="sxs-lookup"><span data-stu-id="0bff5-182">Node Type</span></span>|<span data-ttu-id="0bff5-183">轉譯</span><span class="sxs-lookup"><span data-stu-id="0bff5-183">Translation</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0bff5-184">處理指示</span><span class="sxs-lookup"><span data-stu-id="0bff5-184">Processing instruction</span></span>|<span data-ttu-id="0bff5-185">忽略。</span><span class="sxs-lookup"><span data-stu-id="0bff5-185">Ignored.</span></span>|  
|<span data-ttu-id="0bff5-186">註解</span><span class="sxs-lookup"><span data-stu-id="0bff5-186">Comment</span></span>|<span data-ttu-id="0bff5-187">忽略。</span><span class="sxs-lookup"><span data-stu-id="0bff5-187">Ignored.</span></span>|  
|<span data-ttu-id="0bff5-188">實體參考</span><span class="sxs-lookup"><span data-stu-id="0bff5-188">Entity reference</span></span>|<span data-ttu-id="0bff5-189"><xref:System.Xml.Schema.XmlSchemaInference> 類別不處理實體參考。</span><span class="sxs-lookup"><span data-stu-id="0bff5-189">The <xref:System.Xml.Schema.XmlSchemaInference> class does not handle entity references.</span></span> <span data-ttu-id="0bff5-190">若 XML 文件中含有實體參考，您必須使用可擴充實體的讀取器。</span><span class="sxs-lookup"><span data-stu-id="0bff5-190">If an XML document contains entity references, you need to use a reader that expands the entities.</span></span> <span data-ttu-id="0bff5-191">例如，您可以將 <xref:System.Xml.XmlTextReader> 傳遞為參數，並將其 <xref:System.Xml.XmlTextReader.EntityHandling%2A> 屬性設定為 <xref:System.Xml.EntityHandling.ExpandEntities>。</span><span class="sxs-lookup"><span data-stu-id="0bff5-191">For example, you can pass an <xref:System.Xml.XmlTextReader> with the <xref:System.Xml.XmlTextReader.EntityHandling%2A> property set to <xref:System.Xml.EntityHandling.ExpandEntities> as a parameter.</span></span> <span data-ttu-id="0bff5-192">若發現實體參考，但讀取器並未擴充實體，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0bff5-192">If entity references are encountered and the reader does not expand entities, an exception is throw.</span></span>|  
|<span data-ttu-id="0bff5-193">CDATA</span><span class="sxs-lookup"><span data-stu-id="0bff5-193">CDATA</span></span>|<span data-ttu-id="0bff5-194">XML 文件中的任何 `<![CDATA[ … ]]` 區段都會被推斷為 `xs:string`。</span><span class="sxs-lookup"><span data-stu-id="0bff5-194">Any `<![CDATA[ … ]]` sections in an XML document will be inferred as `xs:string`.</span></span>|  
|<span data-ttu-id="0bff5-195">文件型別</span><span class="sxs-lookup"><span data-stu-id="0bff5-195">Document type</span></span>|<span data-ttu-id="0bff5-196">忽略。</span><span class="sxs-lookup"><span data-stu-id="0bff5-196">Ignored.</span></span>|  
|<span data-ttu-id="0bff5-197">命名空間</span><span class="sxs-lookup"><span data-stu-id="0bff5-197">Namespaces</span></span>|<span data-ttu-id="0bff5-198">忽略。</span><span class="sxs-lookup"><span data-stu-id="0bff5-198">Ignored.</span></span>|  
  
 <span data-ttu-id="0bff5-199">如需結構描述推斷程序的詳細資訊，請參閱[從 XML 文件推斷結構描述](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)。</span><span class="sxs-lookup"><span data-stu-id="0bff5-199">For more information about the schema inference process, see [Inferring Schemas from XML Documents](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bff5-200">請參閱</span><span class="sxs-lookup"><span data-stu-id="0bff5-200">See Also</span></span>  
 <xref:System.Xml.Schema.XmlSchemaInference>  
 [<span data-ttu-id="0bff5-201">XML 結構描述物件模型 (SOM)</span><span class="sxs-lookup"><span data-stu-id="0bff5-201">XML Schema Object Model (SOM)</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 [<span data-ttu-id="0bff5-202">推斷 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="0bff5-202">Inferring an XML Schema</span></span>](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 [<span data-ttu-id="0bff5-203">從 XML 文件推斷結構描述</span><span class="sxs-lookup"><span data-stu-id="0bff5-203">Inferring Schemas from XML Documents</span></span>](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)  
 [<span data-ttu-id="0bff5-204">推斷簡單類型的規則</span><span class="sxs-lookup"><span data-stu-id="0bff5-204">Rules for Inferring Simple Types</span></span>](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)
