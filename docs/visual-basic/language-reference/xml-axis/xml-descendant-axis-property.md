---
title: XML Descendant Axis Property
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
ms.openlocfilehash: 52544619171dbc7034baeb5feb61395d81096387
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400249"
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="ae45c-102">XML 子代軸屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae45c-102">XML Descendant Axis Property (Visual Basic)</span></span>

<span data-ttu-id="ae45c-103">提供下列各項的存取權： <xref:System.Xml.Linq.XElement> 物件、物件 <xref:System.Xml.Linq.XDocument> 、物件的集合 <xref:System.Xml.Linq.XElement> 或物件的集合 <xref:System.Xml.Linq.XDocument> 。</span><span class="sxs-lookup"><span data-stu-id="ae45c-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="ae45c-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae45c-104">Syntax</span></span>

```vb
object...<descendant>
```

## <a name="parts"></a><span data-ttu-id="ae45c-105">組件</span><span class="sxs-lookup"><span data-stu-id="ae45c-105">Parts</span></span>

<span data-ttu-id="ae45c-106">需要 `object`。</span><span class="sxs-lookup"><span data-stu-id="ae45c-106">`object` Required.</span></span> <span data-ttu-id="ae45c-107"><xref:System.Xml.Linq.XElement> 物件、<xref:System.Xml.Linq.XDocument> 物件、<xref:System.Xml.Linq.XElement> 物件集合或 <xref:System.Xml.Linq.XDocument> 物件集合。</span><span class="sxs-lookup"><span data-stu-id="ae45c-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

<span data-ttu-id="ae45c-108">需要 `...<`。</span><span class="sxs-lookup"><span data-stu-id="ae45c-108">`...<` Required.</span></span> <span data-ttu-id="ae45c-109">表示子代軸屬性的開頭。</span><span class="sxs-lookup"><span data-stu-id="ae45c-109">Denotes the start of a descendant axis property.</span></span>

<span data-ttu-id="ae45c-110">需要 `descendant`。</span><span class="sxs-lookup"><span data-stu-id="ae45c-110">`descendant` Required.</span></span> <span data-ttu-id="ae45c-111">要存取的子代節點名稱，格式為 [ `prefix:]name` 。</span><span class="sxs-lookup"><span data-stu-id="ae45c-111">Name of the descendant nodes to access, of the form [`prefix:]name`.</span></span>

|<span data-ttu-id="ae45c-112">部分</span><span class="sxs-lookup"><span data-stu-id="ae45c-112">Part</span></span>|<span data-ttu-id="ae45c-113">描述</span><span class="sxs-lookup"><span data-stu-id="ae45c-113">Description</span></span>|
|----------|-----------------|
|`prefix`|<span data-ttu-id="ae45c-114">選擇性。</span><span class="sxs-lookup"><span data-stu-id="ae45c-114">Optional.</span></span> <span data-ttu-id="ae45c-115">子代節點的 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="ae45c-115">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="ae45c-116">必須是使用語句所定義的全域 XML 命名空間 `Imports` 。</span><span class="sxs-lookup"><span data-stu-id="ae45c-116">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|
|`name`|<span data-ttu-id="ae45c-117">必要。</span><span class="sxs-lookup"><span data-stu-id="ae45c-117">Required.</span></span> <span data-ttu-id="ae45c-118">子代節點的本機名稱。</span><span class="sxs-lookup"><span data-stu-id="ae45c-118">Local name of the descendant node.</span></span> <span data-ttu-id="ae45c-119">請參閱宣告[的 XML 元素和屬性的名稱](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="ae45c-119">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|

<span data-ttu-id="ae45c-120">需要 `>`。</span><span class="sxs-lookup"><span data-stu-id="ae45c-120">`>` Required.</span></span> <span data-ttu-id="ae45c-121">表示子代軸屬性的結尾。</span><span class="sxs-lookup"><span data-stu-id="ae45c-121">Denotes the end of a descendant axis property.</span></span>

## <a name="return-value"></a><span data-ttu-id="ae45c-122">傳回值</span><span class="sxs-lookup"><span data-stu-id="ae45c-122">Return Value</span></span>

<span data-ttu-id="ae45c-123"><xref:System.Xml.Linq.XElement> 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="ae45c-123">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="remarks"></a><span data-ttu-id="ae45c-124">備註</span><span class="sxs-lookup"><span data-stu-id="ae45c-124">Remarks</span></span>

<span data-ttu-id="ae45c-125">您可以使用 XML 子系軸屬性 <xref:System.Xml.Linq.XElement> ，從或物件的名稱 <xref:System.Xml.Linq.XDocument> 或從或物件的集合存取下階節點 <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> 。</span><span class="sxs-lookup"><span data-stu-id="ae45c-125">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="ae45c-126">使用 XML `Value` 屬性來存取所傳回集合中第一個子代節點的值。</span><span class="sxs-lookup"><span data-stu-id="ae45c-126">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="ae45c-127">如需詳細資訊，請參閱[XML Value 屬性](xml-value-property.md)。</span><span class="sxs-lookup"><span data-stu-id="ae45c-127">For more information, see [XML Value Property](xml-value-property.md).</span></span>

<span data-ttu-id="ae45c-128">Visual Basic 編譯器會將子代軸屬性轉換成方法的呼叫 <xref:System.Xml.Linq.XContainer.Descendants%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ae45c-128">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="ae45c-129">XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="ae45c-129">XML Namespaces</span></span>

<span data-ttu-id="ae45c-130">[子代軸] 屬性中的名稱只能使用以語句全域宣告的 XML 命名空間 `Imports` 。</span><span class="sxs-lookup"><span data-stu-id="ae45c-130">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="ae45c-131">它無法使用在 XML 專案常值中本機宣告的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="ae45c-131">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="ae45c-132">如需詳細資訊，請參閱[Imports 語句（XML 命名空間）](../statements/imports-statement-xml-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="ae45c-132">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>

## <a name="example"></a><span data-ttu-id="ae45c-133">範例</span><span class="sxs-lookup"><span data-stu-id="ae45c-133">Example</span></span>

<span data-ttu-id="ae45c-134">下列範例顯示如何存取名為的第一個子系節點值 `name` ，以及從物件命名的所有子系節點的值 `phone` `contacts` 。</span><span class="sxs-lookup"><span data-stu-id="ae45c-134">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

<span data-ttu-id="ae45c-135">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="ae45c-135">This code displays the following text:</span></span>

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a><span data-ttu-id="ae45c-136">範例</span><span class="sxs-lookup"><span data-stu-id="ae45c-136">Example</span></span>

<span data-ttu-id="ae45c-137">下列範例會宣告 `ns` 作為 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="ae45c-137">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="ae45c-138">然後，它會使用命名空間的前置詞來建立 XML 常值，並以限定名稱存取第一個子節點的值 `ns:name` 。</span><span class="sxs-lookup"><span data-stu-id="ae45c-138">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

<span data-ttu-id="ae45c-139">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="ae45c-139">This code displays the following text:</span></span>

`Name: Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="ae45c-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae45c-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="ae45c-141">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="ae45c-141">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="ae45c-142">XML 常值</span><span class="sxs-lookup"><span data-stu-id="ae45c-142">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="ae45c-143">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="ae45c-143">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="ae45c-144">宣告的 XML 項目和屬性的名稱</span><span class="sxs-lookup"><span data-stu-id="ae45c-144">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
