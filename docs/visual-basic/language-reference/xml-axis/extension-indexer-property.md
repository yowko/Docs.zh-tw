---
title: "擴充索引子屬性 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 99d14b6e54a59ffc904a9e786c22498d23ee8ab6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="d0052-102">擴充索引子屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0052-102">Extension Indexer Property (Visual Basic)</span></span>
<span data-ttu-id="d0052-103">提供集合中個別項目的存取。</span><span class="sxs-lookup"><span data-stu-id="d0052-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0052-104">語法</span><span class="sxs-lookup"><span data-stu-id="d0052-104">Syntax</span></span>  
  
```  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="d0052-105">組件</span><span class="sxs-lookup"><span data-stu-id="d0052-105">Parts</span></span>  
  
|<span data-ttu-id="d0052-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="d0052-106">Term</span></span>|<span data-ttu-id="d0052-107">定義</span><span class="sxs-lookup"><span data-stu-id="d0052-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="d0052-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="d0052-108">Required.</span></span> <span data-ttu-id="d0052-109">可查詢的集合。</span><span class="sxs-lookup"><span data-stu-id="d0052-109">A queryable collection.</span></span> <span data-ttu-id="d0052-110">也就是集合中實作<xref:System.Collections.Generic.IEnumerable%601>或<xref:System.Linq.IQueryable%601>。</span><span class="sxs-lookup"><span data-stu-id="d0052-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="d0052-111">(</span><span class="sxs-lookup"><span data-stu-id="d0052-111">(</span></span>|<span data-ttu-id="d0052-112">必要項。</span><span class="sxs-lookup"><span data-stu-id="d0052-112">Required.</span></span> <span data-ttu-id="d0052-113">代表索引子屬性開始。</span><span class="sxs-lookup"><span data-stu-id="d0052-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="d0052-114">必要項。</span><span class="sxs-lookup"><span data-stu-id="d0052-114">Required.</span></span> <span data-ttu-id="d0052-115">整數運算式，指定集合中項目的以零為起始的位置。</span><span class="sxs-lookup"><span data-stu-id="d0052-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="d0052-116">)</span><span class="sxs-lookup"><span data-stu-id="d0052-116">)</span></span>|<span data-ttu-id="d0052-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="d0052-117">Required.</span></span> <span data-ttu-id="d0052-118">代表索引子屬性的結尾。</span><span class="sxs-lookup"><span data-stu-id="d0052-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="d0052-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="d0052-119">Return Value</span></span>  
 <span data-ttu-id="d0052-120">從集合中指定位置的物件或`Nothing`如果索引超出範圍。</span><span class="sxs-lookup"><span data-stu-id="d0052-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0052-121">備註</span><span class="sxs-lookup"><span data-stu-id="d0052-121">Remarks</span></span>  
 <span data-ttu-id="d0052-122">擴充索引子屬性可用來存取集合中的個別項目。</span><span class="sxs-lookup"><span data-stu-id="d0052-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="d0052-123">XML 軸屬性的輸出通常會用於這個索引子屬性。</span><span class="sxs-lookup"><span data-stu-id="d0052-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="d0052-124">XML 子代和 XML 子代軸屬性傳回的集合<xref:System.Xml.Linq.XElement>物件或屬性值。</span><span class="sxs-lookup"><span data-stu-id="d0052-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="d0052-125">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]編譯器會將擴充功能索引子屬性轉換成呼叫`ElementAtOrDefault`方法。</span><span class="sxs-lookup"><span data-stu-id="d0052-125">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="d0052-126">不同於陣列索引子，`ElementAtOrDefault`方法會傳回`Nothing`如果索引超出範圍。</span><span class="sxs-lookup"><span data-stu-id="d0052-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="d0052-127">這種行為時，您無法輕鬆地判斷集合中的項目數。</span><span class="sxs-lookup"><span data-stu-id="d0052-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="d0052-128">這個索引子屬性就延伸模組屬性的集合，實作像是<xref:System.Collections.Generic.IEnumerable%601>或<xref:System.Linq.IQueryable%601>： 集合沒有索引子或預設屬性時，才使用它。</span><span class="sxs-lookup"><span data-stu-id="d0052-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="d0052-129">若要存取之集合中的第一個元素的值<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XAttribute>物件，您可以使用 XML`Value`屬性。</span><span class="sxs-lookup"><span data-stu-id="d0052-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="d0052-130">如需詳細資訊，請參閱[XML Value 屬性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)。</span><span class="sxs-lookup"><span data-stu-id="d0052-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0052-131">範例</span><span class="sxs-lookup"><span data-stu-id="d0052-131">Example</span></span>  
 <span data-ttu-id="d0052-132">下列範例示範如何使用來存取集合中的第二個的子節點的擴充索引子<xref:System.Xml.Linq.XElement>物件。</span><span class="sxs-lookup"><span data-stu-id="d0052-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="d0052-133">使用子軸屬性，就會取得所有子項目，名為存取集合`phone`中`contact`物件。</span><span class="sxs-lookup"><span data-stu-id="d0052-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]  
  
 <span data-ttu-id="d0052-134">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="d0052-134">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="d0052-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0052-135">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="d0052-136">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="d0052-136">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="d0052-137">XML 常值</span><span class="sxs-lookup"><span data-stu-id="d0052-137">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="d0052-138">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="d0052-138">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="d0052-139">XML Value 屬性</span><span class="sxs-lookup"><span data-stu-id="d0052-139">XML Value Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
