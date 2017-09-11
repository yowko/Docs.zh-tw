---
title: "XML 子代軸屬性 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyDescendantsAxis
dev_langs:
- VB
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
ms.openlocfilehash: e84a8bb989ebbed57595ebf93cef620027a04328
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="98955-102">XML 子代軸屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98955-102">XML Descendant Axis Property (Visual Basic)</span></span>
<span data-ttu-id="98955-103">可讓您存取下列的下階︰<xref:System.Xml.Linq.XElement>物件，<xref:System.Xml.Linq.XDocument>物件、 集合<xref:System.Xml.Linq.XElement>物件或一系列<xref:System.Xml.Linq.XDocument>物件。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="98955-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98955-104">語法</span><span class="sxs-lookup"><span data-stu-id="98955-104">Syntax</span></span>  
  
```  
  
object...<descendant>  
```  
  
## <a name="parts"></a><span data-ttu-id="98955-105">組件</span><span class="sxs-lookup"><span data-stu-id="98955-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="98955-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="98955-106">Required.</span></span> <span data-ttu-id="98955-107"><xref:System.Xml.Linq.XElement>物件，<xref:System.Xml.Linq.XDocument>物件、 集合<xref:System.Xml.Linq.XElement>物件或一系列<xref:System.Xml.Linq.XDocument>物件。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="98955-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
 <span data-ttu-id="98955-108">...<</span><span class="sxs-lookup"><span data-stu-id="98955-108">...<</span></span>  
 <span data-ttu-id="98955-109">必要項。</span><span class="sxs-lookup"><span data-stu-id="98955-109">Required.</span></span> <span data-ttu-id="98955-110">代表子代軸屬性開始。</span><span class="sxs-lookup"><span data-stu-id="98955-110">Denotes the start of a descendant axis property.</span></span>  
  
 `descendant`  
 <span data-ttu-id="98955-111">必要項。</span><span class="sxs-lookup"><span data-stu-id="98955-111">Required.</span></span> <span data-ttu-id="98955-112">若要存取，表單的下階節點的名稱 [`prefix``:`]`name`。</span><span class="sxs-lookup"><span data-stu-id="98955-112">Name of the descendant nodes to access, of the form [`prefix``:`]`name`.</span></span>  
  
|<span data-ttu-id="98955-113">組件</span><span class="sxs-lookup"><span data-stu-id="98955-113">Part</span></span>|<span data-ttu-id="98955-114">描述</span><span class="sxs-lookup"><span data-stu-id="98955-114">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="98955-115">選擇項。</span><span class="sxs-lookup"><span data-stu-id="98955-115">Optional.</span></span> <span data-ttu-id="98955-116">XML 子代節點的命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="98955-116">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="98955-117">必須是全域的 XML 命名空間定義使用`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="98955-117">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="98955-118">必要項。</span><span class="sxs-lookup"><span data-stu-id="98955-118">Required.</span></span> <span data-ttu-id="98955-119">子系節點的本機名稱。</span><span class="sxs-lookup"><span data-stu-id="98955-119">Local name of the descendant node.</span></span> <span data-ttu-id="98955-120">請參閱[宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="98955-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="98955-121">必要項。</span><span class="sxs-lookup"><span data-stu-id="98955-121">Required.</span></span> <span data-ttu-id="98955-122">代表子代軸屬性的結尾。</span><span class="sxs-lookup"><span data-stu-id="98955-122">Denotes the end of a descendant axis property.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98955-123">傳回值</span><span class="sxs-lookup"><span data-stu-id="98955-123">Return Value</span></span>  
 <span data-ttu-id="98955-124">一系列<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="98955-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98955-125">備註</span><span class="sxs-lookup"><span data-stu-id="98955-125">Remarks</span></span>  
 <span data-ttu-id="98955-126">您可以使用 XML 子代軸屬性存取子系節點，依名稱從<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>物件，或從一堆<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>物件。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="98955-126">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="98955-127">使用 XML`Value`屬性來存取所傳回集合中的第一個子系節點的值。</span><span class="sxs-lookup"><span data-stu-id="98955-127">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="98955-128">如需詳細資訊，請參閱[XML Value 屬性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)。</span><span class="sxs-lookup"><span data-stu-id="98955-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="98955-129">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器將子代軸屬性轉換成呼叫<xref:System.Xml.Linq.XContainer.Descendants%2A>方法。</xref:System.Xml.Linq.XContainer.Descendants%2A></span><span class="sxs-lookup"><span data-stu-id="98955-129">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="98955-130">XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="98955-130">XML Namespaces</span></span>  
 <span data-ttu-id="98955-131">子代 axis 屬性中的名稱可以使用僅與全域宣告的 XML 命名空間`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="98955-131">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="98955-132">它不能使用 XML 項目常值內本機宣告的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="98955-132">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="98955-133">如需詳細資訊，請參閱[Imports 陳述式 （XML 命名空間）](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="98955-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="98955-134">範例</span><span class="sxs-lookup"><span data-stu-id="98955-134">Example</span></span>  
 <span data-ttu-id="98955-135">下列範例示範如何存取名為第一個子系節點的值`name`和值的所有子系的節點，名為`phone`從`contacts`物件。</span><span class="sxs-lookup"><span data-stu-id="98955-135">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>  
  
 <span data-ttu-id="98955-136">[!code-vb[VbXMLSamples #&25;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="98955-136">[!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]</span></span>  
  
 <span data-ttu-id="98955-137">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="98955-137">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="98955-138">範例</span><span class="sxs-lookup"><span data-stu-id="98955-138">Example</span></span>  
 <span data-ttu-id="98955-139">下列範例會宣告 `ns` 作為 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="98955-139">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="98955-140">然後它會使用命名空間的前置詞來建立 XML 常值，並存取具有限定名稱的第一個子節點的值`ns:name`。</span><span class="sxs-lookup"><span data-stu-id="98955-140">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>  
  
 <span data-ttu-id="98955-141">[!code-vb[VbXMLSamples #&26;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="98955-141">[!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]</span></span>  
  
 <span data-ttu-id="98955-142">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="98955-142">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="98955-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98955-143">See Also</span></span>  
 <span data-ttu-id="98955-144"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="98955-144"><xref:System.Xml.Linq.XElement></span></span>   
<span data-ttu-id="98955-145"> [XML 軸屬性](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span><span class="sxs-lookup"><span data-stu-id="98955-145"> [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span></span>  
<span data-ttu-id="98955-146"> [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="98955-146"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="98955-147"> [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="98955-147"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="98955-148"> [宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="98955-148"> [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)</span></span>
