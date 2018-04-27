---
title: XML 子代軸屬性 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1dc5fe1addb089f3de9b4d5054f34a578b491fb0
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="9dc7b-102">XML 子代軸屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9dc7b-102">XML Descendant Axis Property (Visual Basic)</span></span>
<span data-ttu-id="9dc7b-103">提供下列的下階的存取：<xref:System.Xml.Linq.XElement>物件<xref:System.Xml.Linq.XDocument>物件、 集合<xref:System.Xml.Linq.XElement>物件或集合<xref:System.Xml.Linq.XDocument>物件。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dc7b-104">語法</span><span class="sxs-lookup"><span data-stu-id="9dc7b-104">Syntax</span></span>  
  
```  
object...<descendant>  
```  
  
## <a name="parts"></a><span data-ttu-id="9dc7b-105">組件</span><span class="sxs-lookup"><span data-stu-id="9dc7b-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="9dc7b-106">必要。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-106">Required.</span></span> <span data-ttu-id="9dc7b-107"><xref:System.Xml.Linq.XElement> 物件、<xref:System.Xml.Linq.XDocument> 物件、<xref:System.Xml.Linq.XElement> 物件集合或 <xref:System.Xml.Linq.XDocument> 物件集合。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
 <span data-ttu-id="9dc7b-108">...<</span><span class="sxs-lookup"><span data-stu-id="9dc7b-108">...<</span></span>  
 <span data-ttu-id="9dc7b-109">必要。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-109">Required.</span></span> <span data-ttu-id="9dc7b-110">代表子代 axis 屬性開始。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-110">Denotes the start of a descendant axis property.</span></span>  
  
 `descendant`  
 <span data-ttu-id="9dc7b-111">必要。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-111">Required.</span></span> <span data-ttu-id="9dc7b-112">若要存取，表單的下階節點的名稱 [`prefix``:`]`name`。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-112">Name of the descendant nodes to access, of the form [`prefix``:`]`name`.</span></span>  
  
|<span data-ttu-id="9dc7b-113">組件</span><span class="sxs-lookup"><span data-stu-id="9dc7b-113">Part</span></span>|<span data-ttu-id="9dc7b-114">描述</span><span class="sxs-lookup"><span data-stu-id="9dc7b-114">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="9dc7b-115">選擇性。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-115">Optional.</span></span> <span data-ttu-id="9dc7b-116">XML 子代節點的命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-116">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="9dc7b-117">必須是定義所使用的全域 XML 命名空間`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-117">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="9dc7b-118">必要。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-118">Required.</span></span> <span data-ttu-id="9dc7b-119">下階節點的本機名稱。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-119">Local name of the descendant node.</span></span> <span data-ttu-id="9dc7b-120">請參閱[宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="9dc7b-121">必要。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-121">Required.</span></span> <span data-ttu-id="9dc7b-122">代表子代 axis 屬性結尾。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-122">Denotes the end of a descendant axis property.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9dc7b-123">傳回值</span><span class="sxs-lookup"><span data-stu-id="9dc7b-123">Return Value</span></span>  
 <span data-ttu-id="9dc7b-124"><xref:System.Xml.Linq.XElement> 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9dc7b-125">備註</span><span class="sxs-lookup"><span data-stu-id="9dc7b-125">Remarks</span></span>  
 <span data-ttu-id="9dc7b-126">您可以使用 XML 子代軸屬性來依據名稱，從存取子系節點<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>物件，或從集合<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>物件。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-126">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="9dc7b-127">使用 XML`Value`屬性來存取傳回集合中的第一個子系節點的值。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-127">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="9dc7b-128">如需詳細資訊，請參閱[XML Value 屬性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="9dc7b-129">Visual Basic 編譯器將子代軸屬性轉換成呼叫<xref:System.Xml.Linq.XContainer.Descendants%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-129">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="9dc7b-130">XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="9dc7b-130">XML Namespaces</span></span>  
 <span data-ttu-id="9dc7b-131">子代 axis 屬性中的名稱可以使用僅有全域宣告的 XML 命名空間`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-131">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="9dc7b-132">它無法使用 XML 元素常值內本機宣告的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-132">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="9dc7b-133">如需詳細資訊，請參閱[Imports 陳述式 （XML 命名空間）](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9dc7b-134">範例</span><span class="sxs-lookup"><span data-stu-id="9dc7b-134">Example</span></span>  
 <span data-ttu-id="9dc7b-135">下列範例示範如何存取名為第一個子系節點的值`name`和所有子系的節點名稱為值`phone`從`contacts`物件。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-135">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]  
  
 <span data-ttu-id="9dc7b-136">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="9dc7b-136">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="9dc7b-137">範例</span><span class="sxs-lookup"><span data-stu-id="9dc7b-137">Example</span></span>  
 <span data-ttu-id="9dc7b-138">下列範例會宣告 `ns` 作為 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-138">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="9dc7b-139">然後它會使用命名空間的前置詞來建立 XML 常值，並存取具有限定名稱的第一個子節點的值`ns:name`。</span><span class="sxs-lookup"><span data-stu-id="9dc7b-139">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]  
  
 <span data-ttu-id="9dc7b-140">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="9dc7b-140">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="9dc7b-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9dc7b-141">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="9dc7b-142">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="9dc7b-142">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="9dc7b-143">XML 常值</span><span class="sxs-lookup"><span data-stu-id="9dc7b-143">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="9dc7b-144">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="9dc7b-144">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="9dc7b-145">宣告的 XML 項目和屬性的名稱</span><span class="sxs-lookup"><span data-stu-id="9dc7b-145">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
