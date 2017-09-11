---
title: "擴充索引子屬性 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyExtensionIndexer
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
caps.latest.revision: 22
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
ms.openlocfilehash: 71c16d3f1b93647154bdead4a85d1117b5f6c463
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="56c12-102">擴充索引子屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56c12-102">Extension Indexer Property (Visual Basic)</span></span>
<span data-ttu-id="56c12-103">提供集合中個別項目的存取。</span><span class="sxs-lookup"><span data-stu-id="56c12-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56c12-104">語法</span><span class="sxs-lookup"><span data-stu-id="56c12-104">Syntax</span></span>  
  
```  
  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="56c12-105">組件</span><span class="sxs-lookup"><span data-stu-id="56c12-105">Parts</span></span>  
  
|<span data-ttu-id="56c12-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="56c12-106">Term</span></span>|<span data-ttu-id="56c12-107">定義</span><span class="sxs-lookup"><span data-stu-id="56c12-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="56c12-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="56c12-108">Required.</span></span> <span data-ttu-id="56c12-109">可查詢的集合。</span><span class="sxs-lookup"><span data-stu-id="56c12-109">A queryable collection.</span></span> <span data-ttu-id="56c12-110">也就是實作<xref:System.Collections.Generic.IEnumerable%601>或<xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601></xref:System.Collections.Generic.IEnumerable%601>集合</span><span class="sxs-lookup"><span data-stu-id="56c12-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="56c12-111">(</span><span class="sxs-lookup"><span data-stu-id="56c12-111">(</span></span>|<span data-ttu-id="56c12-112">必要項。</span><span class="sxs-lookup"><span data-stu-id="56c12-112">Required.</span></span> <span data-ttu-id="56c12-113">代表索引子屬性開始。</span><span class="sxs-lookup"><span data-stu-id="56c12-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="56c12-114">必要項。</span><span class="sxs-lookup"><span data-stu-id="56c12-114">Required.</span></span> <span data-ttu-id="56c12-115">整數運算式，指定集合中項目的以零為起始的位置。</span><span class="sxs-lookup"><span data-stu-id="56c12-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="56c12-116">)</span><span class="sxs-lookup"><span data-stu-id="56c12-116">)</span></span>|<span data-ttu-id="56c12-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="56c12-117">Required.</span></span> <span data-ttu-id="56c12-118">代表索引子屬性的結尾。</span><span class="sxs-lookup"><span data-stu-id="56c12-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="56c12-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="56c12-119">Return Value</span></span>  
 <span data-ttu-id="56c12-120">從集合中指定位置的物件或`Nothing`如果索引超出範圍。</span><span class="sxs-lookup"><span data-stu-id="56c12-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56c12-121">備註</span><span class="sxs-lookup"><span data-stu-id="56c12-121">Remarks</span></span>  
 <span data-ttu-id="56c12-122">擴充索引子屬性可用來存取集合中的個別項目。</span><span class="sxs-lookup"><span data-stu-id="56c12-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="56c12-123">這個索引子屬性通常是 XML 軸屬性的輸出。</span><span class="sxs-lookup"><span data-stu-id="56c12-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="56c12-124">XML 子代和 XML 子代軸屬性傳回的集合傳回<xref:System.Xml.Linq.XElement>物件或屬性值。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="56c12-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="56c12-125">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器會將延伸模組索引子屬性轉換為呼叫`ElementAtOrDefault`方法。</span><span class="sxs-lookup"><span data-stu-id="56c12-125">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts extension indexer properties to calls to the`ElementAtOrDefault` method.</span></span> <span data-ttu-id="56c12-126">不同於陣列索引子，`ElementAtOrDefault`方法會傳回`Nothing`如果索引超出範圍。</span><span class="sxs-lookup"><span data-stu-id="56c12-126">Unlike an array indexer, the`ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="56c12-127">這種行為時，您無法輕易判斷集合中的項目數。</span><span class="sxs-lookup"><span data-stu-id="56c12-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="56c12-128">這個索引子屬性就像延伸模組屬性的集合，實作<xref:System.Collections.Generic.IEnumerable%601>或<xref:System.Linq.IQueryable%601>︰ 集合並沒有索引子或預設屬性時，才使用它。</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="56c12-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="56c12-129">若要存取的集合中的第一個項目值<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XAttribute>物件，您可以使用 XML`Value`屬性。</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="56c12-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="56c12-130">如需詳細資訊，請參閱[XML Value 屬性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)。</span><span class="sxs-lookup"><span data-stu-id="56c12-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="56c12-131">範例</span><span class="sxs-lookup"><span data-stu-id="56c12-131">Example</span></span>  
 <span data-ttu-id="56c12-132">下列範例示範如何使用擴充索引子存取集合中的第二個的子節點<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="56c12-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="56c12-133">使用子代軸屬性，它會取得所有子項目，名為存取集合`phone`中`contact`物件。</span><span class="sxs-lookup"><span data-stu-id="56c12-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 <span data-ttu-id="56c12-134">[!code-vb[VbXMLSamples #&24;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="56c12-134">[!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]</span></span>  
  
 <span data-ttu-id="56c12-135">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="56c12-135">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="56c12-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56c12-136">See Also</span></span>  
 <span data-ttu-id="56c12-137"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="56c12-137"><xref:System.Xml.Linq.XElement></span></span>   
<span data-ttu-id="56c12-138"> [XML 軸屬性](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span><span class="sxs-lookup"><span data-stu-id="56c12-138"> [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span></span>  
<span data-ttu-id="56c12-139"> [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="56c12-139"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="56c12-140"> [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="56c12-140"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="56c12-141"> [XML Value 屬性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)</span><span class="sxs-lookup"><span data-stu-id="56c12-141"> [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)</span></span>
