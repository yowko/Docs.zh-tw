---
title: XML 子代軸屬性 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyChildAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
ms.openlocfilehash: 1407a3315d8971895b70893af9d85c8bb428c3be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603856"
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="839ea-102">XML 子代軸屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="839ea-102">XML Child Axis Property (Visual Basic)</span></span>
<span data-ttu-id="839ea-103">提供下列任一項目之子系的存取：<xref:System.Xml.Linq.XElement> 物件、<xref:System.Xml.Linq.XDocument> 物件、<xref:System.Xml.Linq.XElement> 物件的集合，或是 <xref:System.Xml.Linq.XDocument> 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="839ea-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="839ea-104">語法</span><span class="sxs-lookup"><span data-stu-id="839ea-104">Syntax</span></span>  
  
```  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="839ea-105">組件</span><span class="sxs-lookup"><span data-stu-id="839ea-105">Parts</span></span>  
  
|<span data-ttu-id="839ea-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="839ea-106">Term</span></span>|<span data-ttu-id="839ea-107">定義</span><span class="sxs-lookup"><span data-stu-id="839ea-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="839ea-108">必要。</span><span class="sxs-lookup"><span data-stu-id="839ea-108">Required.</span></span> <span data-ttu-id="839ea-109"><xref:System.Xml.Linq.XElement> 物件、<xref:System.Xml.Linq.XDocument> 物件、<xref:System.Xml.Linq.XElement> 物件集合或 <xref:System.Xml.Linq.XDocument> 物件集合。</span><span class="sxs-lookup"><span data-stu-id="839ea-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="839ea-110">.<</span><span class="sxs-lookup"><span data-stu-id="839ea-110">.<</span></span>|<span data-ttu-id="839ea-111">必要。</span><span class="sxs-lookup"><span data-stu-id="839ea-111">Required.</span></span> <span data-ttu-id="839ea-112">代表子軸屬性的開頭。</span><span class="sxs-lookup"><span data-stu-id="839ea-112">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="839ea-113">必要。</span><span class="sxs-lookup"><span data-stu-id="839ea-113">Required.</span></span> <span data-ttu-id="839ea-114">若要存取，表單的子節點的名稱 [`prefix``:`]`name`。</span><span class="sxs-lookup"><span data-stu-id="839ea-114">Name of the child nodes to access, of the form [`prefix``:`]`name`.</span></span><br /><br /> <span data-ttu-id="839ea-115">-   `Prefix` 選擇性的。</span><span class="sxs-lookup"><span data-stu-id="839ea-115">-   `Prefix` - Optional.</span></span> <span data-ttu-id="839ea-116">子節點的 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="839ea-116">XML namespace prefix for the child node.</span></span> <span data-ttu-id="839ea-117">必須是以 `Imports` 陳述式定義的全域 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="839ea-117">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="839ea-118">-   `Name` -必要。</span><span class="sxs-lookup"><span data-stu-id="839ea-118">-   `Name` - Required.</span></span> <span data-ttu-id="839ea-119">本機子節點名稱。</span><span class="sxs-lookup"><span data-stu-id="839ea-119">Local child node name.</span></span> <span data-ttu-id="839ea-120">請參閱[宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="839ea-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="839ea-121">必要。</span><span class="sxs-lookup"><span data-stu-id="839ea-121">Required.</span></span> <span data-ttu-id="839ea-122">代表子軸屬性的結尾。</span><span class="sxs-lookup"><span data-stu-id="839ea-122">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="839ea-123">傳回值</span><span class="sxs-lookup"><span data-stu-id="839ea-123">Return Value</span></span>  
 <span data-ttu-id="839ea-124"><xref:System.Xml.Linq.XElement> 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="839ea-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="839ea-125">備註</span><span class="sxs-lookup"><span data-stu-id="839ea-125">Remarks</span></span>  
 <span data-ttu-id="839ea-126">您可以使用 XML 子軸屬性，從 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 物件，或從 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 物件集合依據名稱存取子節點。</span><span class="sxs-lookup"><span data-stu-id="839ea-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="839ea-127">使用 XML `Value` 屬性來存取傳回的集合中第一個子節點的值。</span><span class="sxs-lookup"><span data-stu-id="839ea-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="839ea-128">如需詳細資訊，請參閱[XML Value 屬性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)。</span><span class="sxs-lookup"><span data-stu-id="839ea-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="839ea-129">Visual Basic 編譯器會將子軸屬性轉換成呼叫<xref:System.Xml.Linq.XContainer.Elements%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="839ea-129">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="839ea-130">XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="839ea-130">XML Namespaces</span></span>  
 <span data-ttu-id="839ea-131">子軸屬性中的名稱只可以使用以 `Imports` 陳述式全域宣告的 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="839ea-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="839ea-132">它不能使用在 XML 項目常值內本機宣告的 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="839ea-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="839ea-133">如需詳細資訊，請參閱[Imports 陳述式 （XML 命名空間）](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="839ea-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="839ea-134">範例</span><span class="sxs-lookup"><span data-stu-id="839ea-134">Example</span></span>  
 <span data-ttu-id="839ea-135">下列範例示範如何從 `contact` 物件存取名為 `phone` 的子節點。</span><span class="sxs-lookup"><span data-stu-id="839ea-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_1.vb)]  
  
 <span data-ttu-id="839ea-136">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="839ea-136">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="839ea-137">範例</span><span class="sxs-lookup"><span data-stu-id="839ea-137">Example</span></span>  
 <span data-ttu-id="839ea-138">下列範例示範如何從 `contacts` 物件的 `contact` 子軸屬性傳回的集合存取名為 `phone` 的子節點。</span><span class="sxs-lookup"><span data-stu-id="839ea-138">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_2.vb)]  
  
 <span data-ttu-id="839ea-139">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="839ea-139">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="839ea-140">範例</span><span class="sxs-lookup"><span data-stu-id="839ea-140">Example</span></span>  
 <span data-ttu-id="839ea-141">下列範例會宣告 `ns` 作為 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="839ea-141">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="839ea-142">然後它會使用命名空間的前置詞來建立 XML 常值，以及存取完整名稱為 `ns:name` 的第一個子節點。</span><span class="sxs-lookup"><span data-stu-id="839ea-142">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_3.vb)]  
  
 <span data-ttu-id="839ea-143">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="839ea-143">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="839ea-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="839ea-144">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="839ea-145">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="839ea-145">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="839ea-146">XML 常值</span><span class="sxs-lookup"><span data-stu-id="839ea-146">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="839ea-147">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="839ea-147">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="839ea-148">宣告的 XML 項目和屬性的名稱</span><span class="sxs-lookup"><span data-stu-id="839ea-148">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
