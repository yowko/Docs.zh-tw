---
title: XML Attribute Axis Property
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
ms.openlocfilehash: 109c4b45a5e3ed4e3e4db49687df5cb127a5e0c6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352664"
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="01571-102">XML 屬性軸屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01571-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="01571-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span><span class="sxs-lookup"><span data-stu-id="01571-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01571-104">語法</span><span class="sxs-lookup"><span data-stu-id="01571-104">Syntax</span></span>  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="01571-105">組件</span><span class="sxs-lookup"><span data-stu-id="01571-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="01571-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="01571-106">Required.</span></span> <span data-ttu-id="01571-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span><span class="sxs-lookup"><span data-stu-id="01571-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="01571-108">.@</span><span class="sxs-lookup"><span data-stu-id="01571-108">.@</span></span>  
 <span data-ttu-id="01571-109">必要項。</span><span class="sxs-lookup"><span data-stu-id="01571-109">Required.</span></span> <span data-ttu-id="01571-110">Denotes the start of an attribute axis property.</span><span class="sxs-lookup"><span data-stu-id="01571-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="01571-111">選擇項。</span><span class="sxs-lookup"><span data-stu-id="01571-111">Optional.</span></span> <span data-ttu-id="01571-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="01571-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
 `attribute`  
 <span data-ttu-id="01571-113">必要項。</span><span class="sxs-lookup"><span data-stu-id="01571-113">Required.</span></span> <span data-ttu-id="01571-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span><span class="sxs-lookup"><span data-stu-id="01571-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="01571-115">組件</span><span class="sxs-lookup"><span data-stu-id="01571-115">Part</span></span>|<span data-ttu-id="01571-116">描述</span><span class="sxs-lookup"><span data-stu-id="01571-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="01571-117">選擇項。</span><span class="sxs-lookup"><span data-stu-id="01571-117">Optional.</span></span> <span data-ttu-id="01571-118">XML namespace prefix for the attribute.</span><span class="sxs-lookup"><span data-stu-id="01571-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="01571-119">必須是以 `Imports` 陳述式定義的全域 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="01571-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="01571-120">必要項。</span><span class="sxs-lookup"><span data-stu-id="01571-120">Required.</span></span> <span data-ttu-id="01571-121">Local attribute name.</span><span class="sxs-lookup"><span data-stu-id="01571-121">Local attribute name.</span></span> <span data-ttu-id="01571-122">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="01571-122">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="01571-123">選擇項。</span><span class="sxs-lookup"><span data-stu-id="01571-123">Optional.</span></span> <span data-ttu-id="01571-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="01571-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01571-125">傳回值</span><span class="sxs-lookup"><span data-stu-id="01571-125">Return Value</span></span>  
 <span data-ttu-id="01571-126">A string that contains the value of `attribute`.</span><span class="sxs-lookup"><span data-stu-id="01571-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="01571-127">If the attribute name does not exist, `Nothing` is returned.</span><span class="sxs-lookup"><span data-stu-id="01571-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01571-128">備註</span><span class="sxs-lookup"><span data-stu-id="01571-128">Remarks</span></span>  
 <span data-ttu-id="01571-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span><span class="sxs-lookup"><span data-stu-id="01571-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="01571-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span><span class="sxs-lookup"><span data-stu-id="01571-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="01571-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span><span class="sxs-lookup"><span data-stu-id="01571-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="01571-132">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span><span class="sxs-lookup"><span data-stu-id="01571-132">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span></span> <span data-ttu-id="01571-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span><span class="sxs-lookup"><span data-stu-id="01571-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="01571-134">XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="01571-134">XML Namespaces</span></span>  
 <span data-ttu-id="01571-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span><span class="sxs-lookup"><span data-stu-id="01571-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="01571-136">它不能使用在 XML 項目常值內本機宣告的 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="01571-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="01571-137">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="01571-137">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="01571-138">範例</span><span class="sxs-lookup"><span data-stu-id="01571-138">Example</span></span>  
 <span data-ttu-id="01571-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span><span class="sxs-lookup"><span data-stu-id="01571-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 <span data-ttu-id="01571-140">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="01571-140">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="01571-141">範例</span><span class="sxs-lookup"><span data-stu-id="01571-141">Example</span></span>  
 <span data-ttu-id="01571-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span><span class="sxs-lookup"><span data-stu-id="01571-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="01571-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span><span class="sxs-lookup"><span data-stu-id="01571-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 <span data-ttu-id="01571-144">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="01571-144">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="01571-145">範例</span><span class="sxs-lookup"><span data-stu-id="01571-145">Example</span></span>  
 <span data-ttu-id="01571-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="01571-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span></span>  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 <span data-ttu-id="01571-147">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="01571-147">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="01571-148">範例</span><span class="sxs-lookup"><span data-stu-id="01571-148">Example</span></span>  
 <span data-ttu-id="01571-149">下列範例會宣告 `ns` 作為 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="01571-149">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="01571-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span><span class="sxs-lookup"><span data-stu-id="01571-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 <span data-ttu-id="01571-151">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="01571-151">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="01571-152">請參閱</span><span class="sxs-lookup"><span data-stu-id="01571-152">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="01571-153">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="01571-153">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="01571-154">XML 常值</span><span class="sxs-lookup"><span data-stu-id="01571-154">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="01571-155">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="01571-155">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="01571-156">宣告的 XML 項目和屬性的名稱</span><span class="sxs-lookup"><span data-stu-id="01571-156">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
