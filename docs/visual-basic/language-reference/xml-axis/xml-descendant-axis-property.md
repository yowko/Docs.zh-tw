---
title: XML 子代軸屬性 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Basic]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: bc1dff6dc3b580079087f370212b7d3acd30e4fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938667"
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="89124-102">XML 子代軸屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89124-102">XML Descendant Axis Property (Visual Basic)</span></span>

<span data-ttu-id="89124-103">可讓您存取下列的下階：<xref:System.Xml.Linq.XElement>物件，<xref:System.Xml.Linq.XDocument>物件、 集合<xref:System.Xml.Linq.XElement>物件或集合<xref:System.Xml.Linq.XDocument>物件。</span><span class="sxs-lookup"><span data-stu-id="89124-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="89124-104">語法</span><span class="sxs-lookup"><span data-stu-id="89124-104">Syntax</span></span>

```
object...<descendant>
```

## <a name="parts"></a><span data-ttu-id="89124-105">組件</span><span class="sxs-lookup"><span data-stu-id="89124-105">Parts</span></span>

<span data-ttu-id="89124-106">`object` 必要項。</span><span class="sxs-lookup"><span data-stu-id="89124-106">`object` Required.</span></span> <span data-ttu-id="89124-107"><xref:System.Xml.Linq.XElement> 物件、<xref:System.Xml.Linq.XDocument> 物件、<xref:System.Xml.Linq.XElement> 物件集合或 <xref:System.Xml.Linq.XDocument> 物件集合。</span><span class="sxs-lookup"><span data-stu-id="89124-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

<span data-ttu-id="89124-108">`...<` 必要項。</span><span class="sxs-lookup"><span data-stu-id="89124-108">`...<` Required.</span></span> <span data-ttu-id="89124-109">表示子系軸屬性的開頭。</span><span class="sxs-lookup"><span data-stu-id="89124-109">Denotes the start of a descendant axis property.</span></span>

<span data-ttu-id="89124-110">`descendant` 必要項。</span><span class="sxs-lookup"><span data-stu-id="89124-110">`descendant` Required.</span></span> <span data-ttu-id="89124-111">若要存取，在表單的子系節點的名稱 [`prefix:]name`。</span><span class="sxs-lookup"><span data-stu-id="89124-111">Name of the descendant nodes to access, of the form [`prefix:]name`.</span></span>

|<span data-ttu-id="89124-112">組件</span><span class="sxs-lookup"><span data-stu-id="89124-112">Part</span></span>|<span data-ttu-id="89124-113">描述</span><span class="sxs-lookup"><span data-stu-id="89124-113">Description</span></span>|
|----------|-----------------|
|`prefix`|<span data-ttu-id="89124-114">選擇性。</span><span class="sxs-lookup"><span data-stu-id="89124-114">Optional.</span></span> <span data-ttu-id="89124-115">子代節點的 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="89124-115">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="89124-116">必須是全域的 XML 命名空間定義使用`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="89124-116">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|
|`name`|<span data-ttu-id="89124-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="89124-117">Required.</span></span> <span data-ttu-id="89124-118">子系節點的本機名稱。</span><span class="sxs-lookup"><span data-stu-id="89124-118">Local name of the descendant node.</span></span> <span data-ttu-id="89124-119">請參閱[宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="89124-119">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|

<span data-ttu-id="89124-120">`>` 必要項。</span><span class="sxs-lookup"><span data-stu-id="89124-120">`>` Required.</span></span> <span data-ttu-id="89124-121">代表子系軸屬性的結尾。</span><span class="sxs-lookup"><span data-stu-id="89124-121">Denotes the end of a descendant axis property.</span></span>

## <a name="return-value"></a><span data-ttu-id="89124-122">傳回值</span><span class="sxs-lookup"><span data-stu-id="89124-122">Return Value</span></span>

<span data-ttu-id="89124-123"><xref:System.Xml.Linq.XElement> 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="89124-123">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="remarks"></a><span data-ttu-id="89124-124">備註</span><span class="sxs-lookup"><span data-stu-id="89124-124">Remarks</span></span>

<span data-ttu-id="89124-125">您可以使用 XML 子代軸屬性存取子系節點，依名稱從<xref:System.Xml.Linq.XElement>或是<xref:System.Xml.Linq.XDocument>物件，或從集合<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>物件。</span><span class="sxs-lookup"><span data-stu-id="89124-125">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="89124-126">使用 XML`Value`屬性來存取傳回之集合中的第一個子系節點的值。</span><span class="sxs-lookup"><span data-stu-id="89124-126">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="89124-127">如需詳細資訊，請參閱 < [XML Value 屬性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)。</span><span class="sxs-lookup"><span data-stu-id="89124-127">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>

<span data-ttu-id="89124-128">Visual Basic 編譯器會將子系軸屬性轉換成呼叫<xref:System.Xml.Linq.XContainer.Descendants%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="89124-128">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="89124-129">XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="89124-129">XML Namespaces</span></span>

<span data-ttu-id="89124-130">子代 axis 屬性中的名稱可以使用僅有全域宣告的 XML 命名空間`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="89124-130">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="89124-131">它不能使用 XML 元素常值內本機宣告的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="89124-131">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="89124-132">如需詳細資訊，請參閱 < [Imports 陳述式 （XML 命名空間）](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="89124-132">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>

## <a name="example"></a><span data-ttu-id="89124-133">範例</span><span class="sxs-lookup"><span data-stu-id="89124-133">Example</span></span>

<span data-ttu-id="89124-134">下列範例示範如何存取名為第一個子系節點的值`name`和名為所有的子代節點的值`phone`從`contacts`物件。</span><span class="sxs-lookup"><span data-stu-id="89124-134">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

<span data-ttu-id="89124-135">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="89124-135">This code displays the following text:</span></span>

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a><span data-ttu-id="89124-136">範例</span><span class="sxs-lookup"><span data-stu-id="89124-136">Example</span></span>

<span data-ttu-id="89124-137">下列範例會宣告 `ns` 作為 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="89124-137">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="89124-138">然後它會使用命名空間的前置詞來建立 XML 常值，並存取具有限定名稱的第一個子節點的值`ns:name`。</span><span class="sxs-lookup"><span data-stu-id="89124-138">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

<span data-ttu-id="89124-139">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="89124-139">This code displays the following text:</span></span>

`Name: Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="89124-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89124-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="89124-141">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="89124-141">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="89124-142">XML 常值</span><span class="sxs-lookup"><span data-stu-id="89124-142">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="89124-143">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="89124-143">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="89124-144">宣告的 XML 項目和屬性的名稱</span><span class="sxs-lookup"><span data-stu-id="89124-144">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
