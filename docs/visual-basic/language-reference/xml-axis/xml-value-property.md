---
title: "XML Value 屬性 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6c52ac09e209d6e3f0cfd877a071cbbe3ab96f18
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="f7e14-102">XML Value 屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7e14-102">XML Value Property (Visual Basic)</span></span>
<span data-ttu-id="f7e14-103">提供存取集合的第一個元素的值<xref:System.Xml.Linq.XElement>物件。</span><span class="sxs-lookup"><span data-stu-id="f7e14-103">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7e14-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7e14-104">Syntax</span></span>  
  
```  
object.Value  
```  
  
## <a name="parts"></a><span data-ttu-id="f7e14-105">組件</span><span class="sxs-lookup"><span data-stu-id="f7e14-105">Parts</span></span>  
  
|<span data-ttu-id="f7e14-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="f7e14-106">Term</span></span>|<span data-ttu-id="f7e14-107">定義</span><span class="sxs-lookup"><span data-stu-id="f7e14-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="f7e14-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="f7e14-108">Required.</span></span> <span data-ttu-id="f7e14-109"><xref:System.Xml.Linq.XElement> 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="f7e14-109">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="f7e14-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="f7e14-110">Return Value</span></span>  
 <span data-ttu-id="f7e14-111">A `String` ，其中包含集合的第一個項目值或`Nothing`如果集合是空的。</span><span class="sxs-lookup"><span data-stu-id="f7e14-111">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7e14-112">備註</span><span class="sxs-lookup"><span data-stu-id="f7e14-112">Remarks</span></span>  
 <span data-ttu-id="f7e14-113"><xref:System.Xml.Linq.XElement.Value%2A>屬性可讓您輕鬆地存取集合中的第一個元素的值<xref:System.Xml.Linq.XElement>物件。</span><span class="sxs-lookup"><span data-stu-id="f7e14-113">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="f7e14-114">這個屬性會先檢查集合是否包含至少一個物件。</span><span class="sxs-lookup"><span data-stu-id="f7e14-114">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="f7e14-115">如果集合是空的則這個屬性會傳回`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="f7e14-115">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="f7e14-116">否則，這個屬性會傳回的值<xref:System.Xml.Linq.XElement.Value%2A>集合中的第一個元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="f7e14-116">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7e14-117">當您存取 XML 屬性使用的值 ' @' 屬性值會傳回做為識別項， `String` ，您不需要明確指定<xref:System.Xml.Linq.XAttribute.Value%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="f7e14-117">When you access the value of an XML attribute using the '@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="f7e14-118">若要存取集合中的其他項目，您可以使用 XML 擴充索引子屬性。</span><span class="sxs-lookup"><span data-stu-id="f7e14-118">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="f7e14-119">如需詳細資訊，請參閱[擴充索引子屬性](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)。</span><span class="sxs-lookup"><span data-stu-id="f7e14-119">For more information, see [Extension Indexer Property](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="f7e14-120">繼承</span><span class="sxs-lookup"><span data-stu-id="f7e14-120">Inheritance</span></span>  
 <span data-ttu-id="f7e14-121">大部分的使用者不需要實作<xref:System.Collections.Generic.IEnumerable%601>，因此可以忽略此區段。</span><span class="sxs-lookup"><span data-stu-id="f7e14-121">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>  
  
 <span data-ttu-id="f7e14-122"><xref:System.Xml.Linq.XElement.Value%2A>屬性是實作的型別擴充功能屬性`IEnumerable(Of XElement)`。</span><span class="sxs-lookup"><span data-stu-id="f7e14-122">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="f7e14-123">這個延伸模組屬性的繫結會使用類似的繫結的擴充方法： 如果類型實作其中一個介面，但會定義具有名稱"Value"的屬性，該屬性優先於擴充功能屬性。</span><span class="sxs-lookup"><span data-stu-id="f7e14-123">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="f7e14-124">換句話說，這<xref:System.Xml.Linq.XElement.Value%2A>屬性，可以藉由實作類別中定義新的屬性覆寫`IEnumerable(Of XElement)`。</span><span class="sxs-lookup"><span data-stu-id="f7e14-124">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7e14-125">範例</span><span class="sxs-lookup"><span data-stu-id="f7e14-125">Example</span></span>  
 <span data-ttu-id="f7e14-126">下列範例示範如何使用<xref:System.Xml.Linq.XElement.Value%2A>屬性來存取集合中的第一個節點<xref:System.Xml.Linq.XElement>物件。</span><span class="sxs-lookup"><span data-stu-id="f7e14-126">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="f7e14-127">此範例會取得名為的所有子節點的集合中使用子軸屬性`phone`處於`contact`物件。</span><span class="sxs-lookup"><span data-stu-id="f7e14-127">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_1.vb)]  
  
 <span data-ttu-id="f7e14-128">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="f7e14-128">This code displays the following text:</span></span>  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="f7e14-129">範例</span><span class="sxs-lookup"><span data-stu-id="f7e14-129">Example</span></span>  
 <span data-ttu-id="f7e14-130">下列範例示範如何從集合中取得 XML 屬性的值<xref:System.Xml.Linq.XAttribute>物件。</span><span class="sxs-lookup"><span data-stu-id="f7e14-130">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="f7e14-131">此範例會顯示的值中使用屬性軸屬性`type`屬性的所有`phone`項目。</span><span class="sxs-lookup"><span data-stu-id="f7e14-131">The example uses the attribute axis property to display the value of the `type` attribute for all of the the `phone` elements.</span></span>  
  
 [!code-vb[VbXMLSamples#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_2.vb)]  
  
 <span data-ttu-id="f7e14-132">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="f7e14-132">This code displays the following text:</span></span>  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a><span data-ttu-id="f7e14-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7e14-133">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="f7e14-134">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="f7e14-134">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="f7e14-135">XML 常值</span><span class="sxs-lookup"><span data-stu-id="f7e14-135">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="f7e14-136">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="f7e14-136">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="f7e14-137">擴充方法</span><span class="sxs-lookup"><span data-stu-id="f7e14-137">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [<span data-ttu-id="f7e14-138">擴充索引子屬性</span><span class="sxs-lookup"><span data-stu-id="f7e14-138">Extension Indexer Property</span></span>](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)  
 [<span data-ttu-id="f7e14-139">XML 子代軸屬性</span><span class="sxs-lookup"><span data-stu-id="f7e14-139">XML Child Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [<span data-ttu-id="f7e14-140">XML 屬性 (Attribute) 軸屬性 (Property)</span><span class="sxs-lookup"><span data-stu-id="f7e14-140">XML Attribute Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
