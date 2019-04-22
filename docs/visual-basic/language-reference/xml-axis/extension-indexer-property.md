---
title: 擴充索引子屬性 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: a02c482db81d9d76752cfe66a292dc57c48b2acb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841243"
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="53c83-102">擴充索引子屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53c83-102">Extension Indexer Property (Visual Basic)</span></span>
<span data-ttu-id="53c83-103">提供集合中個別項目的存取。</span><span class="sxs-lookup"><span data-stu-id="53c83-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53c83-104">語法</span><span class="sxs-lookup"><span data-stu-id="53c83-104">Syntax</span></span>  
  
```  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="53c83-105">組件</span><span class="sxs-lookup"><span data-stu-id="53c83-105">Parts</span></span>  
  
|<span data-ttu-id="53c83-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="53c83-106">Term</span></span>|<span data-ttu-id="53c83-107">定義</span><span class="sxs-lookup"><span data-stu-id="53c83-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="53c83-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="53c83-108">Required.</span></span> <span data-ttu-id="53c83-109">可查詢的集合。</span><span class="sxs-lookup"><span data-stu-id="53c83-109">A queryable collection.</span></span> <span data-ttu-id="53c83-110">也就是集合，實作<xref:System.Collections.Generic.IEnumerable%601>或<xref:System.Linq.IQueryable%601>。</span><span class="sxs-lookup"><span data-stu-id="53c83-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="53c83-111">(</span><span class="sxs-lookup"><span data-stu-id="53c83-111">(</span></span>|<span data-ttu-id="53c83-112">必要項。</span><span class="sxs-lookup"><span data-stu-id="53c83-112">Required.</span></span> <span data-ttu-id="53c83-113">表示索引子屬性的開頭。</span><span class="sxs-lookup"><span data-stu-id="53c83-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="53c83-114">必要項。</span><span class="sxs-lookup"><span data-stu-id="53c83-114">Required.</span></span> <span data-ttu-id="53c83-115">整數運算式，指定集合中項目的以零為起始的位置。</span><span class="sxs-lookup"><span data-stu-id="53c83-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="53c83-116">)</span><span class="sxs-lookup"><span data-stu-id="53c83-116">)</span></span>|<span data-ttu-id="53c83-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="53c83-117">Required.</span></span> <span data-ttu-id="53c83-118">表示索引子屬性的結尾。</span><span class="sxs-lookup"><span data-stu-id="53c83-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="53c83-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="53c83-119">Return Value</span></span>  
 <span data-ttu-id="53c83-120">從指定的位置，集合中的物件或`Nothing`如果索引超出範圍。</span><span class="sxs-lookup"><span data-stu-id="53c83-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53c83-121">備註</span><span class="sxs-lookup"><span data-stu-id="53c83-121">Remarks</span></span>  
 <span data-ttu-id="53c83-122">您可以使用擴充索引子屬性來存取集合中的個別項目。</span><span class="sxs-lookup"><span data-stu-id="53c83-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="53c83-123">這個索引子屬性通常是 XML 軸屬性的輸出。</span><span class="sxs-lookup"><span data-stu-id="53c83-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="53c83-124">XML 子代和 XML 子代 axis 屬性傳回的集合<xref:System.Xml.Linq.XElement>物件或屬性值。</span><span class="sxs-lookup"><span data-stu-id="53c83-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="53c83-125">Visual Basic 編譯器會將呼叫中的擴充索引子屬性`ElementAtOrDefault`方法。</span><span class="sxs-lookup"><span data-stu-id="53c83-125">The Visual Basic compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="53c83-126">不同於陣列索引子`ElementAtOrDefault`方法會傳回`Nothing`如果索引超出範圍。</span><span class="sxs-lookup"><span data-stu-id="53c83-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="53c83-127">當您無法輕易判斷集合中的項目數，則此行為會有所幫助。</span><span class="sxs-lookup"><span data-stu-id="53c83-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="53c83-128">這個索引子屬性就像延伸模組屬性實作的集合<xref:System.Collections.Generic.IEnumerable%601>或<xref:System.Linq.IQueryable%601>： 集合並沒有索引子或預設屬性時，才使用它。</span><span class="sxs-lookup"><span data-stu-id="53c83-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="53c83-129">若要存取的集合中的第一個元素的值<xref:System.Xml.Linq.XElement>或是<xref:System.Xml.Linq.XAttribute>物件，您可以使用 XML`Value`屬性。</span><span class="sxs-lookup"><span data-stu-id="53c83-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="53c83-130">如需詳細資訊，請參閱 < [XML Value 屬性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)。</span><span class="sxs-lookup"><span data-stu-id="53c83-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="53c83-131">範例</span><span class="sxs-lookup"><span data-stu-id="53c83-131">Example</span></span>  
 <span data-ttu-id="53c83-132">下列範例示範如何使用擴充索引子來存取集合中的第二個的子節點<xref:System.Xml.Linq.XElement>物件。</span><span class="sxs-lookup"><span data-stu-id="53c83-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="53c83-133">集合會使用子軸屬性，它會取得所有子項目來存取`phone`在`contact`物件。</span><span class="sxs-lookup"><span data-stu-id="53c83-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 <span data-ttu-id="53c83-134">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="53c83-134">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="53c83-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53c83-135">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="53c83-136">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="53c83-136">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="53c83-137">XML 常值</span><span class="sxs-lookup"><span data-stu-id="53c83-137">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="53c83-138">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="53c83-138">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="53c83-139">XML Value 屬性</span><span class="sxs-lookup"><span data-stu-id="53c83-139">XML Value Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
