---
title: XML Value 屬性 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 46f81e39686da30270cd67edeb4c9f2d43e048b3
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592011"
---
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="cf746-102">XML Value 屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf746-102">XML Value Property (Visual Basic)</span></span>

<span data-ttu-id="cf746-103">提供對 <xref:System.Xml.Linq.XElement> 物件集合中第一個元素的值的存取。</span><span class="sxs-lookup"><span data-stu-id="cf746-103">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="cf746-104">語法</span><span class="sxs-lookup"><span data-stu-id="cf746-104">Syntax</span></span>

```vb
object.Value
```

## <a name="parts"></a><span data-ttu-id="cf746-105">組件</span><span class="sxs-lookup"><span data-stu-id="cf746-105">Parts</span></span>

|<span data-ttu-id="cf746-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="cf746-106">Term</span></span>|<span data-ttu-id="cf746-107">定義</span><span class="sxs-lookup"><span data-stu-id="cf746-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="cf746-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="cf746-108">Required.</span></span> <span data-ttu-id="cf746-109"><xref:System.Xml.Linq.XElement> 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="cf746-109">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  

## <a name="return-value"></a><span data-ttu-id="cf746-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="cf746-110">Return Value</span></span>

 <span data-ttu-id="cf746-111">@No__t-0，其中包含集合中第一個元素的值，如果集合是空的，則為 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="cf746-111">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>

## <a name="remarks"></a><span data-ttu-id="cf746-112">備註</span><span class="sxs-lookup"><span data-stu-id="cf746-112">Remarks</span></span>

 <span data-ttu-id="cf746-113">@No__t-0 屬性可讓您輕鬆地存取 @no__t 1 物件集合中第一個元素的值。</span><span class="sxs-lookup"><span data-stu-id="cf746-113">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="cf746-114">這個屬性會先檢查集合是否至少包含一個物件。</span><span class="sxs-lookup"><span data-stu-id="cf746-114">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="cf746-115">如果集合是空的，則這個屬性會傳回 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="cf746-115">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="cf746-116">否則，這個屬性會傳回集合中第一個元素的 <xref:System.Xml.Linq.XElement.Value%2A> 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="cf746-116">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>

> [!NOTE]
> <span data-ttu-id="cf746-117">當您使用 ' \@ ' 識別碼來存取 XML 屬性的值時，會以 `String` 的形式傳回屬性值，而您不需要明確指定 <xref:System.Xml.Linq.XAttribute.Value%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="cf746-117">When you access the value of an XML attribute using the '\@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>

 <span data-ttu-id="cf746-118">若要存取集合中的其他元素，您可以使用 XML 延伸模組索引子屬性。</span><span class="sxs-lookup"><span data-stu-id="cf746-118">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="cf746-119">如需詳細資訊，請參閱[擴充索引子屬性](extension-indexer-property.md)。</span><span class="sxs-lookup"><span data-stu-id="cf746-119">For more information, see [Extension Indexer Property](extension-indexer-property.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="cf746-120">繼承</span><span class="sxs-lookup"><span data-stu-id="cf746-120">Inheritance</span></span>

 <span data-ttu-id="cf746-121">大部分的使用者都不需要執行 <xref:System.Collections.Generic.IEnumerable%601>，因此可以忽略此區段。</span><span class="sxs-lookup"><span data-stu-id="cf746-121">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>

 <span data-ttu-id="cf746-122">@No__t-0 屬性是實 `IEnumerable(Of XElement)` 之類型的擴充屬性。</span><span class="sxs-lookup"><span data-stu-id="cf746-122">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="cf746-123">此延伸模組屬性的系結就像是擴充方法的系結：如果型別會實作為其中一個介面，並定義一個名稱為 "Value" 的屬性，則該屬性的優先順序高於擴充屬性。</span><span class="sxs-lookup"><span data-stu-id="cf746-123">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="cf746-124">換句話說，這個 <xref:System.Xml.Linq.XElement.Value%2A> 屬性可以藉由在執行 `IEnumerable(Of XElement)` 的類別中定義新的屬性來覆寫。</span><span class="sxs-lookup"><span data-stu-id="cf746-124">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>

## <a name="example"></a><span data-ttu-id="cf746-125">範例</span><span class="sxs-lookup"><span data-stu-id="cf746-125">Example</span></span>

 <span data-ttu-id="cf746-126">下列範例顯示如何使用 <xref:System.Xml.Linq.XElement.Value%2A> 屬性來存取 @no__t 1 物件集合中的第一個節點。</span><span class="sxs-lookup"><span data-stu-id="cf746-126">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="cf746-127">此範例會使用 [子軸] 屬性來取得 `contact` 物件中名為 `phone` 之所有子節點的集合。</span><span class="sxs-lookup"><span data-stu-id="cf746-127">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>

 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]

 <span data-ttu-id="cf746-128">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="cf746-128">This code displays the following text:</span></span>

 `Phone number: 206-555-0144`

## <a name="example"></a><span data-ttu-id="cf746-129">範例</span><span class="sxs-lookup"><span data-stu-id="cf746-129">Example</span></span>

 <span data-ttu-id="cf746-130">下列範例示範如何從 <xref:System.Xml.Linq.XAttribute> 個物件的集合中取得 XML 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="cf746-130">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="cf746-131">此範例會使用 [屬性軸] 屬性來顯示所有 `phone` 元素的 `type` 屬性值。</span><span class="sxs-lookup"><span data-stu-id="cf746-131">The example uses the attribute axis property to display the value of the `type` attribute for all of the `phone` elements.</span></span>

 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]

 <span data-ttu-id="cf746-132">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="cf746-132">This code displays the following text:</span></span>

 ```console
 home
 work
```

## <a name="see-also"></a><span data-ttu-id="cf746-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf746-133">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="cf746-134">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="cf746-134">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="cf746-135">XML 常值</span><span class="sxs-lookup"><span data-stu-id="cf746-135">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="cf746-136">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="cf746-136">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="cf746-137">擴充方法</span><span class="sxs-lookup"><span data-stu-id="cf746-137">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="cf746-138">擴充索引子屬性</span><span class="sxs-lookup"><span data-stu-id="cf746-138">Extension Indexer Property</span></span>](extension-indexer-property.md)
- [<span data-ttu-id="cf746-139">XML 子代軸屬性</span><span class="sxs-lookup"><span data-stu-id="cf746-139">XML Child Axis Property</span></span>](xml-child-axis-property.md)
- [<span data-ttu-id="cf746-140">XML 屬性 (Attribute) 軸屬性 (Property)</span><span class="sxs-lookup"><span data-stu-id="cf746-140">XML Attribute Axis Property</span></span>](xml-attribute-axis-property.md)
