---
title: XML 屬性軸屬性 (Visual Basic)
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
ms.openlocfilehash: 9107b946394ab70980e4865364fc1ba9683e2025
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785156"
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="48719-102">XML 屬性軸屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48719-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="48719-103">提供的屬性值存取權<xref:System.Xml.Linq.XElement>物件或集合中的第一個項目<xref:System.Xml.Linq.XElement>物件。</span><span class="sxs-lookup"><span data-stu-id="48719-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48719-104">語法</span><span class="sxs-lookup"><span data-stu-id="48719-104">Syntax</span></span>  
  
```  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="48719-105">組件</span><span class="sxs-lookup"><span data-stu-id="48719-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="48719-106">必要。</span><span class="sxs-lookup"><span data-stu-id="48719-106">Required.</span></span> <span data-ttu-id="48719-107"><xref:System.Xml.Linq.XElement>物件或集合<xref:System.Xml.Linq.XElement>物件。</span><span class="sxs-lookup"><span data-stu-id="48719-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="48719-108">.@</span><span class="sxs-lookup"><span data-stu-id="48719-108">.@</span></span>  
 <span data-ttu-id="48719-109">必要。</span><span class="sxs-lookup"><span data-stu-id="48719-109">Required.</span></span> <span data-ttu-id="48719-110">表示屬性軸屬性的開頭。</span><span class="sxs-lookup"><span data-stu-id="48719-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="48719-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="48719-111">Optional.</span></span> <span data-ttu-id="48719-112">表示屬性名稱的開頭時`attribute`不在 Visual Basic 中是有效的識別項。</span><span class="sxs-lookup"><span data-stu-id="48719-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
 `attribute`  
 <span data-ttu-id="48719-113">必要。</span><span class="sxs-lookup"><span data-stu-id="48719-113">Required.</span></span> <span data-ttu-id="48719-114">若要存取，在表單的屬性名稱的 [`prefix`:]`name`。</span><span class="sxs-lookup"><span data-stu-id="48719-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="48719-115">組件</span><span class="sxs-lookup"><span data-stu-id="48719-115">Part</span></span>|<span data-ttu-id="48719-116">描述</span><span class="sxs-lookup"><span data-stu-id="48719-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="48719-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="48719-117">Optional.</span></span> <span data-ttu-id="48719-118">XML 屬性的命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="48719-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="48719-119">必須是以 `Imports` 陳述式定義的全域 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="48719-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="48719-120">必要。</span><span class="sxs-lookup"><span data-stu-id="48719-120">Required.</span></span> <span data-ttu-id="48719-121">本機屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="48719-121">Local attribute name.</span></span> <span data-ttu-id="48719-122">請參閱[宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="48719-122">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="48719-123">選擇性。</span><span class="sxs-lookup"><span data-stu-id="48719-123">Optional.</span></span> <span data-ttu-id="48719-124">代表屬性名稱的結尾時`attribute`不在 Visual Basic 中是有效的識別項。</span><span class="sxs-lookup"><span data-stu-id="48719-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48719-125">傳回值</span><span class="sxs-lookup"><span data-stu-id="48719-125">Return Value</span></span>  
 <span data-ttu-id="48719-126">字串，包含的值`attribute`。</span><span class="sxs-lookup"><span data-stu-id="48719-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="48719-127">如果屬性名稱不存在，`Nothing`會傳回。</span><span class="sxs-lookup"><span data-stu-id="48719-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48719-128">備註</span><span class="sxs-lookup"><span data-stu-id="48719-128">Remarks</span></span>  
 <span data-ttu-id="48719-129">您可以使用 XML 屬性軸屬性來存取屬性的值，依名稱從<xref:System.Xml.Linq.XElement>物件或從集合中的第一個項目<xref:System.Xml.Linq.XElement>物件。</span><span class="sxs-lookup"><span data-stu-id="48719-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="48719-130">您可以依名稱擷取屬性值，或加入新屬性的項目，藉由指定新名稱，前面加上 @ 識別項。</span><span class="sxs-lookup"><span data-stu-id="48719-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="48719-131">當您參考 XML 屬性使用 @ 識別項，則屬性會傳回值為字串，並不需要明確指定<xref:System.Xml.Linq.XAttribute.Value%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="48719-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="48719-132">與 Visual Basic 識別項的命名規則，不同的 XML 屬性的命名規則。</span><span class="sxs-lookup"><span data-stu-id="48719-132">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span></span> <span data-ttu-id="48719-133">若要存取 XML 屬性具有不是有效的 Visual Basic 識別項的名稱，將名稱括在括弧 (\<和 >)。</span><span class="sxs-lookup"><span data-stu-id="48719-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="48719-134">XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="48719-134">XML Namespaces</span></span>  
 <span data-ttu-id="48719-135">屬性軸屬性 中的名稱可以使用只有 XML 命名空間前置詞使用全域宣告`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="48719-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="48719-136">它不能使用在 XML 項目常值內本機宣告的 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="48719-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="48719-137">如需詳細資訊，請參閱 < [Imports 陳述式 （XML 命名空間）](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="48719-137">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="48719-138">範例</span><span class="sxs-lookup"><span data-stu-id="48719-138">Example</span></span>  
 <span data-ttu-id="48719-139">下列範例示範如何取得名為 XML 屬性的值`type`集合中的 XML 項目會在名為`phone`。</span><span class="sxs-lookup"><span data-stu-id="48719-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]  
  
 <span data-ttu-id="48719-140">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="48719-140">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="48719-141">範例</span><span class="sxs-lookup"><span data-stu-id="48719-141">Example</span></span>  
 <span data-ttu-id="48719-142">下列範例示範如何以宣告方式，XML 中，而且以動態方式加入的執行個體的屬性建立屬性的 XML 項目這兩個<xref:System.Xml.Linq.XElement>物件。</span><span class="sxs-lookup"><span data-stu-id="48719-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="48719-143">`type`屬性會以宣告方式建立和`owner`屬性會動態建立。</span><span class="sxs-lookup"><span data-stu-id="48719-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]  
  
 <span data-ttu-id="48719-144">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="48719-144">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="48719-145">範例</span><span class="sxs-lookup"><span data-stu-id="48719-145">Example</span></span>  
 <span data-ttu-id="48719-146">下列範例使用角括號語法來取得名為 XML 屬性的值`number-type`，這不是在 Visual Basic 中是有效的識別碼。</span><span class="sxs-lookup"><span data-stu-id="48719-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span></span>  
  
 [!code-vb[VbXMLSamples#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]  
  
 <span data-ttu-id="48719-147">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="48719-147">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="48719-148">範例</span><span class="sxs-lookup"><span data-stu-id="48719-148">Example</span></span>  
 <span data-ttu-id="48719-149">下列範例會宣告 `ns` 作為 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="48719-149">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="48719-150">然後它會使用命名空間的前置詞來建立 XML 常值，並存取具有限定名稱的第一個子節點 」`ns:name`"。</span><span class="sxs-lookup"><span data-stu-id="48719-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]  
  
 <span data-ttu-id="48719-151">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="48719-151">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="48719-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48719-152">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="48719-153">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="48719-153">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)  
 [<span data-ttu-id="48719-154">XML 常值</span><span class="sxs-lookup"><span data-stu-id="48719-154">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="48719-155">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="48719-155">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="48719-156">宣告的 XML 項目和屬性的名稱</span><span class="sxs-lookup"><span data-stu-id="48719-156">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
