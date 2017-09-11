---
title: "XML 屬性軸屬性 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyAttributeAxis
dev_langs:
- VB
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a3c327f4448287bcf6c45b9b6e26a1ef9ba13c16
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="f3243-102">XML 屬性軸屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3243-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="f3243-103">提供的屬性值的存取<xref:System.Xml.Linq.XElement>物件或集合中的第一個元素<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="f3243-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3243-104">語法</span><span class="sxs-lookup"><span data-stu-id="f3243-104">Syntax</span></span>  
  
```  
  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="f3243-105">組件</span><span class="sxs-lookup"><span data-stu-id="f3243-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="f3243-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="f3243-106">Required.</span></span> <span data-ttu-id="f3243-107"><xref:System.Xml.Linq.XElement>物件或集合的<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="f3243-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="f3243-108">.@</span><span class="sxs-lookup"><span data-stu-id="f3243-108">.@</span></span>  
 <span data-ttu-id="f3243-109">必要項。</span><span class="sxs-lookup"><span data-stu-id="f3243-109">Required.</span></span> <span data-ttu-id="f3243-110">代表屬性軸屬性開始。</span><span class="sxs-lookup"><span data-stu-id="f3243-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="f3243-111">選擇項。</span><span class="sxs-lookup"><span data-stu-id="f3243-111">Optional.</span></span> <span data-ttu-id="f3243-112">表示屬性名稱的開頭時`attribute`不是有效的識別項中[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f3243-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 `attribute`  
 <span data-ttu-id="f3243-113">必要項。</span><span class="sxs-lookup"><span data-stu-id="f3243-113">Required.</span></span> <span data-ttu-id="f3243-114">若要存取，表單的屬性名稱的 [`prefix`:]`name`。</span><span class="sxs-lookup"><span data-stu-id="f3243-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="f3243-115">組件</span><span class="sxs-lookup"><span data-stu-id="f3243-115">Part</span></span>|<span data-ttu-id="f3243-116">描述</span><span class="sxs-lookup"><span data-stu-id="f3243-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="f3243-117">選擇項。</span><span class="sxs-lookup"><span data-stu-id="f3243-117">Optional.</span></span> <span data-ttu-id="f3243-118">屬性的 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="f3243-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="f3243-119">必須是以 `Imports` 陳述式定義的全域 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="f3243-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="f3243-120">必要項。</span><span class="sxs-lookup"><span data-stu-id="f3243-120">Required.</span></span> <span data-ttu-id="f3243-121">本機屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="f3243-121">Local attribute name.</span></span> <span data-ttu-id="f3243-122">請參閱[宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="f3243-122">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="f3243-123">選擇項。</span><span class="sxs-lookup"><span data-stu-id="f3243-123">Optional.</span></span> <span data-ttu-id="f3243-124">代表屬性名稱的結尾時`attribute`不是有效的識別項中[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f3243-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3243-125">傳回值</span><span class="sxs-lookup"><span data-stu-id="f3243-125">Return Value</span></span>  
 <span data-ttu-id="f3243-126">字串，包含的值`attribute`。</span><span class="sxs-lookup"><span data-stu-id="f3243-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="f3243-127">如果屬性名稱不存在，`Nothing`會傳回。</span><span class="sxs-lookup"><span data-stu-id="f3243-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3243-128">備註</span><span class="sxs-lookup"><span data-stu-id="f3243-128">Remarks</span></span>  
 <span data-ttu-id="f3243-129">您可以使用 XML 屬性軸屬性來存取屬性的值依名稱從<xref:System.Xml.Linq.XElement>物件或從集合中的第一個項目<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="f3243-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="f3243-130">您可以依名稱擷取屬性值，或加入新屬性的項目，藉由指定新的名稱前面加上 @ 識別項。</span><span class="sxs-lookup"><span data-stu-id="f3243-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="f3243-131">當您參考 XML 屬性使用 @ 識別項，以字串傳回屬性值，您不需要明確指定<xref:System.Xml.Linq.XAttribute.Value%2A>屬性。</xref:System.Xml.Linq.XAttribute.Value%2A></span><span class="sxs-lookup"><span data-stu-id="f3243-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="f3243-132">XML 屬性的命名規則不同的命名規則[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]識別項。</span><span class="sxs-lookup"><span data-stu-id="f3243-132">The naming rules for XML attributes differ from the naming rules for [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] identifiers.</span></span> <span data-ttu-id="f3243-133">若要存取 XML 屬性具有不是有效的 Visual Basic 識別項的名稱，將名稱以角括弧 (\<和 >)。</span><span class="sxs-lookup"><span data-stu-id="f3243-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="f3243-134">XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="f3243-134">XML Namespaces</span></span>  
 <span data-ttu-id="f3243-135">屬性軸屬性中的名稱可以使用只有 XML 命名空間前置詞使用全域宣告`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f3243-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="f3243-136">它不能使用在 XML 項目常值內本機宣告的 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="f3243-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="f3243-137">如需詳細資訊，請參閱[Imports 陳述式 （XML 命名空間）](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="f3243-137">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3243-138">範例</span><span class="sxs-lookup"><span data-stu-id="f3243-138">Example</span></span>  
 <span data-ttu-id="f3243-139">下列範例示範如何取得名為 XML 屬性的值`type`集合中的 XML 項目命名為`phone`。</span><span class="sxs-lookup"><span data-stu-id="f3243-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 <span data-ttu-id="f3243-140">[!code-vb[VbXMLSamples #&12;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f3243-140">[!code-vb[VbXMLSamples#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]</span></span>  
  
 <span data-ttu-id="f3243-141">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="f3243-141">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="f3243-142">範例</span><span class="sxs-lookup"><span data-stu-id="f3243-142">Example</span></span>  
 <span data-ttu-id="f3243-143">下列範例示範如何以宣告方式，做為一部分的 xml，並以動態方式將屬性加入至執行個體建立的 XML 項目這兩個屬性<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="f3243-143">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="f3243-144">`type`屬性以宣告方式建立和`owne`r 屬性會動態建立。</span><span class="sxs-lookup"><span data-stu-id="f3243-144">The `type` attribute is created declaratively and the `owne`r attribute is created dynamically.</span></span>  
  
 <span data-ttu-id="f3243-145">[!code-vb[VbXMLSamples #&44;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="f3243-145">[!code-vb[VbXMLSamples#44](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]</span></span>  
  
 <span data-ttu-id="f3243-146">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="f3243-146">This code displays the following text:</span></span>  
  
```  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="f3243-147">範例</span><span class="sxs-lookup"><span data-stu-id="f3243-147">Example</span></span>  
 <span data-ttu-id="f3243-148">下列範例使用角括號語法，來取得名為 XML 屬性的值`number-type`，這不是有效的識別項中[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f3243-148">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 <span data-ttu-id="f3243-149">[!code-vb[VbXMLSamples #&13;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="f3243-149">[!code-vb[VbXMLSamples#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]</span></span>  
  
 <span data-ttu-id="f3243-150">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="f3243-150">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="f3243-151">範例</span><span class="sxs-lookup"><span data-stu-id="f3243-151">Example</span></span>  
 <span data-ttu-id="f3243-152">下列範例會宣告 `ns` 作為 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="f3243-152">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="f3243-153">然後它會使用命名空間的前置詞來建立 XML 常值和存取具有限定名稱的第一個子節點 」`ns:name`」。</span><span class="sxs-lookup"><span data-stu-id="f3243-153">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 <span data-ttu-id="f3243-154">[!code-vb[VbXMLSamples #&14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="f3243-154">[!code-vb[VbXMLSamples#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]</span></span>  
  
 <span data-ttu-id="f3243-155">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="f3243-155">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="f3243-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3243-156">See Also</span></span>  
 <span data-ttu-id="f3243-157"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="f3243-157"><xref:System.Xml.Linq.XElement></span></span>   
<span data-ttu-id="f3243-158"> [XML 軸屬性](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span><span class="sxs-lookup"><span data-stu-id="f3243-158"> [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span></span>  
<span data-ttu-id="f3243-159"> [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="f3243-159"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="f3243-160"> [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="f3243-160"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="f3243-161"> [宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="f3243-161"> [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)</span></span>
