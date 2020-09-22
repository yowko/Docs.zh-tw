---
title: 擴充索引子屬性
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: 23417cd982c2ddf06afce69d9b120ae0737fb87d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866114"
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="2b044-102">擴充索引子屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b044-102">Extension Indexer Property (Visual Basic)</span></span>

<span data-ttu-id="2b044-103">提供集合中個別項目的存取。</span><span class="sxs-lookup"><span data-stu-id="2b044-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b044-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2b044-104">Syntax</span></span>  
  
```vb  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="2b044-105">組件</span><span class="sxs-lookup"><span data-stu-id="2b044-105">Parts</span></span>  
  
|<span data-ttu-id="2b044-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="2b044-106">Term</span></span>|<span data-ttu-id="2b044-107">定義</span><span class="sxs-lookup"><span data-stu-id="2b044-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="2b044-108">必要。</span><span class="sxs-lookup"><span data-stu-id="2b044-108">Required.</span></span> <span data-ttu-id="2b044-109">可查詢的集合。</span><span class="sxs-lookup"><span data-stu-id="2b044-109">A queryable collection.</span></span> <span data-ttu-id="2b044-110">也就是實作為或的 <xref:System.Collections.Generic.IEnumerable%601> 集合 <xref:System.Linq.IQueryable%601> 。</span><span class="sxs-lookup"><span data-stu-id="2b044-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="2b044-111">(</span><span class="sxs-lookup"><span data-stu-id="2b044-111">(</span></span>|<span data-ttu-id="2b044-112">必要。</span><span class="sxs-lookup"><span data-stu-id="2b044-112">Required.</span></span> <span data-ttu-id="2b044-113">表示索引子屬性的開頭。</span><span class="sxs-lookup"><span data-stu-id="2b044-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="2b044-114">必要。</span><span class="sxs-lookup"><span data-stu-id="2b044-114">Required.</span></span> <span data-ttu-id="2b044-115">整數運算式，指定集合元素之以零為基底的位置。</span><span class="sxs-lookup"><span data-stu-id="2b044-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="2b044-116">)</span><span class="sxs-lookup"><span data-stu-id="2b044-116">)</span></span>|<span data-ttu-id="2b044-117">必要。</span><span class="sxs-lookup"><span data-stu-id="2b044-117">Required.</span></span> <span data-ttu-id="2b044-118">表示索引子屬性的結尾。</span><span class="sxs-lookup"><span data-stu-id="2b044-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="2b044-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="2b044-119">Return Value</span></span>  

 <span data-ttu-id="2b044-120">集合中指定位置的物件， `Nothing` 如果索引超出範圍，則為。</span><span class="sxs-lookup"><span data-stu-id="2b044-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b044-121">備註</span><span class="sxs-lookup"><span data-stu-id="2b044-121">Remarks</span></span>  

 <span data-ttu-id="2b044-122">您可以使用擴充索引子屬性來存取集合中的個別元素。</span><span class="sxs-lookup"><span data-stu-id="2b044-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="2b044-123">此索引子屬性通常用於 XML 軸屬性的輸出。</span><span class="sxs-lookup"><span data-stu-id="2b044-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="2b044-124">XML 子系和 XML 子代軸屬性會傳回物件的集合 <xref:System.Xml.Linq.XElement> 或屬性值。</span><span class="sxs-lookup"><span data-stu-id="2b044-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="2b044-125">Visual Basic 編譯器會將擴充索引子屬性轉換成方法的呼叫 `ElementAtOrDefault` 。</span><span class="sxs-lookup"><span data-stu-id="2b044-125">The Visual Basic compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="2b044-126">不同于陣列索引子， `ElementAtOrDefault` 如果索引超出範圍，則此方法會傳回 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="2b044-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="2b044-127">當您無法輕鬆地判斷集合中的專案數目時，這個行為會很有用。</span><span class="sxs-lookup"><span data-stu-id="2b044-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="2b044-128">此索引子屬性就像是執行或的集合的延伸模組屬性 <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> 。只有在集合沒有索引子或預設屬性時，才會使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="2b044-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="2b044-129">若要存取或物件集合中第一個元素的值 <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> ，您可以使用 XML `Value` 屬性。</span><span class="sxs-lookup"><span data-stu-id="2b044-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="2b044-130">如需詳細資訊，請參閱 [XML 值屬性](xml-value-property.md)。</span><span class="sxs-lookup"><span data-stu-id="2b044-130">For more information, see [XML Value Property](xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b044-131">範例</span><span class="sxs-lookup"><span data-stu-id="2b044-131">Example</span></span>  

 <span data-ttu-id="2b044-132">下列範例示範如何使用擴充索引子來存取物件集合中的第二個子節點 <xref:System.Xml.Linq.XElement> 。</span><span class="sxs-lookup"><span data-stu-id="2b044-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="2b044-133">您可以使用子軸屬性來存取集合，該屬性會取得物件中所命名的所有子項目 `phone` `contact` 。</span><span class="sxs-lookup"><span data-stu-id="2b044-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 <span data-ttu-id="2b044-134">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="2b044-134">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="2b044-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b044-135">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="2b044-136">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="2b044-136">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="2b044-137">XML 常值</span><span class="sxs-lookup"><span data-stu-id="2b044-137">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="2b044-138">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="2b044-138">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="2b044-139">XML 值屬性</span><span class="sxs-lookup"><span data-stu-id="2b044-139">XML Value Property</span></span>](xml-value-property.md)
