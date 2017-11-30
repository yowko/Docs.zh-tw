---
title: "XML 子代軸屬性 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f3c42b5134b058c010ca4c7a5ee7c24627c65fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="505d3-102">XML 子代軸屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="505d3-102">XML Descendant Axis Property (Visual Basic)</span></span>
<span data-ttu-id="505d3-103">提供下列的下階的存取：<xref:System.Xml.Linq.XElement>物件<xref:System.Xml.Linq.XDocument>物件、 集合<xref:System.Xml.Linq.XElement>物件或集合<xref:System.Xml.Linq.XDocument>物件。</span><span class="sxs-lookup"><span data-stu-id="505d3-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="505d3-104">語法</span><span class="sxs-lookup"><span data-stu-id="505d3-104">Syntax</span></span>  
  
```  
object...<descendant>  
```  
  
## <a name="parts"></a><span data-ttu-id="505d3-105">組件</span><span class="sxs-lookup"><span data-stu-id="505d3-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="505d3-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="505d3-106">Required.</span></span> <span data-ttu-id="505d3-107"><xref:System.Xml.Linq.XElement> 物件、<xref:System.Xml.Linq.XDocument> 物件、<xref:System.Xml.Linq.XElement> 物件集合或 <xref:System.Xml.Linq.XDocument> 物件集合。</span><span class="sxs-lookup"><span data-stu-id="505d3-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
 <span data-ttu-id="505d3-108">...<</span><span class="sxs-lookup"><span data-stu-id="505d3-108">...<</span></span>  
 <span data-ttu-id="505d3-109">必要項。</span><span class="sxs-lookup"><span data-stu-id="505d3-109">Required.</span></span> <span data-ttu-id="505d3-110">代表子代 axis 屬性開始。</span><span class="sxs-lookup"><span data-stu-id="505d3-110">Denotes the start of a descendant axis property.</span></span>  
  
 `descendant`  
 <span data-ttu-id="505d3-111">必要項。</span><span class="sxs-lookup"><span data-stu-id="505d3-111">Required.</span></span> <span data-ttu-id="505d3-112">若要存取，表單的下階節點的名稱 [`prefix``:`]`name`。</span><span class="sxs-lookup"><span data-stu-id="505d3-112">Name of the descendant nodes to access, of the form [`prefix``:`]`name`.</span></span>  
  
|<span data-ttu-id="505d3-113">組件</span><span class="sxs-lookup"><span data-stu-id="505d3-113">Part</span></span>|<span data-ttu-id="505d3-114">說明</span><span class="sxs-lookup"><span data-stu-id="505d3-114">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="505d3-115">選擇項。</span><span class="sxs-lookup"><span data-stu-id="505d3-115">Optional.</span></span> <span data-ttu-id="505d3-116">XML 子代節點的命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="505d3-116">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="505d3-117">必須是定義所使用的全域 XML 命名空間`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="505d3-117">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="505d3-118">必要項。</span><span class="sxs-lookup"><span data-stu-id="505d3-118">Required.</span></span> <span data-ttu-id="505d3-119">下階節點的本機名稱。</span><span class="sxs-lookup"><span data-stu-id="505d3-119">Local name of the descendant node.</span></span> <span data-ttu-id="505d3-120">請參閱[宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="505d3-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="505d3-121">必要項。</span><span class="sxs-lookup"><span data-stu-id="505d3-121">Required.</span></span> <span data-ttu-id="505d3-122">代表子代 axis 屬性結尾。</span><span class="sxs-lookup"><span data-stu-id="505d3-122">Denotes the end of a descendant axis property.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="505d3-123">傳回值</span><span class="sxs-lookup"><span data-stu-id="505d3-123">Return Value</span></span>  
 <span data-ttu-id="505d3-124"><xref:System.Xml.Linq.XElement> 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="505d3-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="505d3-125">備註</span><span class="sxs-lookup"><span data-stu-id="505d3-125">Remarks</span></span>  
 <span data-ttu-id="505d3-126">您可以使用 XML 子代軸屬性來依據名稱，從存取子系節點<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>物件，或從集合<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>物件。</span><span class="sxs-lookup"><span data-stu-id="505d3-126">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="505d3-127">使用 XML`Value`屬性來存取傳回集合中的第一個子系節點的值。</span><span class="sxs-lookup"><span data-stu-id="505d3-127">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="505d3-128">如需詳細資訊，請參閱[XML Value 屬性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)。</span><span class="sxs-lookup"><span data-stu-id="505d3-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="505d3-129">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]編譯器會將子代軸屬性轉換成呼叫<xref:System.Xml.Linq.XContainer.Descendants%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="505d3-129">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="505d3-130">XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="505d3-130">XML Namespaces</span></span>  
 <span data-ttu-id="505d3-131">子代 axis 屬性中的名稱可以使用僅有全域宣告的 XML 命名空間`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="505d3-131">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="505d3-132">它無法使用 XML 元素常值內本機宣告的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="505d3-132">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="505d3-133">如需詳細資訊，請參閱[Imports 陳述式 （XML 命名空間）](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="505d3-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="505d3-134">範例</span><span class="sxs-lookup"><span data-stu-id="505d3-134">Example</span></span>  
 <span data-ttu-id="505d3-135">下列範例示範如何存取名為第一個子系節點的值`name`和所有子系的節點名稱為值`phone`從`contacts`物件。</span><span class="sxs-lookup"><span data-stu-id="505d3-135">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]  
  
 <span data-ttu-id="505d3-136">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="505d3-136">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="505d3-137">範例</span><span class="sxs-lookup"><span data-stu-id="505d3-137">Example</span></span>  
 <span data-ttu-id="505d3-138">下列範例會宣告 `ns` 作為 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="505d3-138">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="505d3-139">然後它會使用命名空間的前置詞來建立 XML 常值，並存取具有限定名稱的第一個子節點的值`ns:name`。</span><span class="sxs-lookup"><span data-stu-id="505d3-139">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]  
  
 <span data-ttu-id="505d3-140">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="505d3-140">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="505d3-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="505d3-141">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="505d3-142">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="505d3-142">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="505d3-143">XML 常值</span><span class="sxs-lookup"><span data-stu-id="505d3-143">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="505d3-144">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="505d3-144">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="505d3-145">宣告的 XML 項目和屬性的名稱</span><span class="sxs-lookup"><span data-stu-id="505d3-145">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
