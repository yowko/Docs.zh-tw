---
title: 維護名稱/值組-LINQ to XML
description: 瞭解如何使用 LINQ to XML 方法來維護一組名稱/值配對。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 681df91d42f8bdb403dcf6f735104301c4a0c9ba
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552218"
---
# <a name="maintain-name-value-pairs-linq-to-xml"></a><span data-ttu-id="88cc3-103">維護名稱/值組 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="88cc3-103">Maintain name-value pairs (LINQ to XML)</span></span>

<span data-ttu-id="88cc3-104">許多應用程式都必須維護最適合作為成對名稱/值的資訊。</span><span class="sxs-lookup"><span data-stu-id="88cc3-104">Many applications have to maintain information that is best kept as name-value pairs.</span></span> <span data-ttu-id="88cc3-105">這類資訊可能是組態或全域設定的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="88cc3-105">This information might be configuration information or global settings.</span></span> <span data-ttu-id="88cc3-106">LINQ to XML 包含的方法，可讓您輕鬆地維護一組名稱/值配對。</span><span class="sxs-lookup"><span data-stu-id="88cc3-106">LINQ to XML contains methods that make it easy to maintain a set of name-value pairs.</span></span> <span data-ttu-id="88cc3-107">您可以將該資訊保存為屬性或一組子項目。</span><span class="sxs-lookup"><span data-stu-id="88cc3-107">You can either keep the information as attributes or as a set of child elements.</span></span>

<span data-ttu-id="88cc3-108">將資訊保存為屬性或子項目的其中一個差異在於，屬性所擁有的條件約束中，僅能有一個具有項目之特定名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="88cc3-108">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="88cc3-109">這項限制不適用於子項目。</span><span class="sxs-lookup"><span data-stu-id="88cc3-109">This limitation doesn't apply to child elements.</span></span>

## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="88cc3-110">SetAttributeValue 和 SetElementValue</span><span class="sxs-lookup"><span data-stu-id="88cc3-110">SetAttributeValue and SetElementValue</span></span>

<span data-ttu-id="88cc3-111">有助於將名稱/值配對保持在一起的兩個方法為 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 和 <xref:System.Xml.Linq.XElement.SetElementValue%2A> 。</span><span class="sxs-lookup"><span data-stu-id="88cc3-111">The two methods that facilitate keeping name-value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="88cc3-112">這些兩個方法具有類似的語意 (Semantics)。</span><span class="sxs-lookup"><span data-stu-id="88cc3-112">These two methods have similar semantics.</span></span>

<span data-ttu-id="88cc3-113"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 可以加入、修改和移除專案的屬性。</span><span class="sxs-lookup"><span data-stu-id="88cc3-113"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, and remove attributes of an element.</span></span>

- <span data-ttu-id="88cc3-114">如果您 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 使用不存在的屬性名稱進行呼叫，此方法會建立新的屬性，並將它加入至指定的元素。</span><span class="sxs-lookup"><span data-stu-id="88cc3-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that doesn't exist, the method creates a new attribute and adds it to the specified element.</span></span>
- <span data-ttu-id="88cc3-115">如果您呼叫的 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 具有現有屬性的名稱以及某些指定的內容，屬性的內容會取代為指定的內容。</span><span class="sxs-lookup"><span data-stu-id="88cc3-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>
- <span data-ttu-id="88cc3-116">如果您 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 使用現有屬性的名稱來呼叫，並指定 `null` 內容的，則會從其父系中移除該屬性。</span><span class="sxs-lookup"><span data-stu-id="88cc3-116">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify `null` for the content, the attribute is removed from its parent.</span></span>

<span data-ttu-id="88cc3-117"><xref:System.Xml.Linq.XElement.SetElementValue%2A> 可以加入、修改和移除專案的子項目。</span><span class="sxs-lookup"><span data-stu-id="88cc3-117"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, and remove child elements of an element.</span></span>

- <span data-ttu-id="88cc3-118">如果您 <xref:System.Xml.Linq.XElement.SetElementValue%2A> 使用不存在的子專案名稱來呼叫，此方法會建立新的專案，並將其加入至指定的元素。</span><span class="sxs-lookup"><span data-stu-id="88cc3-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that doesn't exist, the method creates a new element and adds it to the specified element.</span></span>
- <span data-ttu-id="88cc3-119">如果您呼叫的 <xref:System.Xml.Linq.XElement.SetElementValue%2A> 具有現有項目的名稱以及某些指定的內容，項目的內容會取代為指定的內容。</span><span class="sxs-lookup"><span data-stu-id="88cc3-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>
- <span data-ttu-id="88cc3-120">如果您使用現有專案的名稱來呼叫 <xref:System.Xml.Linq.XElement.SetElementValue%2A> ，並 `null` 為內容指定，則會從其父系中移除該元素。</span><span class="sxs-lookup"><span data-stu-id="88cc3-120">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify `null` for the content, the element is removed from its parent.</span></span>

## <a name="example-use-setattributevalue-to-create-and-maintain-a-list-of-name-value-pairs"></a><span data-ttu-id="88cc3-121">範例：用 `SetAttributeValue` 來建立及維護成對的名稱/值組清單</span><span class="sxs-lookup"><span data-stu-id="88cc3-121">Example: Use `SetAttributeValue` to create and maintain a list of name-value pairs</span></span>

<span data-ttu-id="88cc3-122">下列範例會建立沒有屬性的項目。</span><span class="sxs-lookup"><span data-stu-id="88cc3-122">The following example creates an element with no attributes.</span></span> <span data-ttu-id="88cc3-123">然後，它會使用 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 方法來建立和維護成對的名稱/值組清單。</span><span class="sxs-lookup"><span data-stu-id="88cc3-123">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name-value pairs.</span></span>

```csharp
// Create an element with no content.
XElement root = new XElement("Root");

// Add a number of name-value pairs as attributes.
root.SetAttributeValue("Top", 22);
root.SetAttributeValue("Left", 20);
root.SetAttributeValue("Bottom", 122);
root.SetAttributeValue("Right", 300);
root.SetAttributeValue("DefaultColor", "Color.Red");
Console.WriteLine(root);

// Replace the value of Top.
root.SetAttributeValue("Top", 10);
Console.WriteLine(root);

// Remove DefaultColor.
root.SetAttributeValue("DefaultColor", null);
Console.WriteLine(root);
```

```vb
' Create an element with no content.
Dim root As XElement = <Root/>

' Add a number of name-value pairs as attributes.
root.SetAttributeValue("Top", 22)
root.SetAttributeValue("Left", 20)
root.SetAttributeValue("Bottom", 122)
root.SetAttributeValue("Right", 300)
root.SetAttributeValue("DefaultColor", "Color.Red")
Console.WriteLine(root)

' Replace the value of Top.
root.SetAttributeValue("Top", 10)
Console.WriteLine(root)

' Remove DefaultColor.
root.SetAttributeValue("DefaultColor", Nothing)
Console.WriteLine(root)
```

<span data-ttu-id="88cc3-124">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="88cc3-124">This example produces the following output:</span></span>

```xml
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />
<Root Top="10" Left="20" Bottom="122" Right="300" />
```

## <a name="example-use-setelementvalue-to-create-and-maintain-a-list-of-name-value-pairs"></a><span data-ttu-id="88cc3-125">範例：用 `SetElementValue` 來建立及維護成對的名稱/值組清單</span><span class="sxs-lookup"><span data-stu-id="88cc3-125">Example: Use `SetElementValue` to create and maintain a list of name-value pairs</span></span>

<span data-ttu-id="88cc3-126">下列範例會建立沒有子項目的項目。</span><span class="sxs-lookup"><span data-stu-id="88cc3-126">The following example creates an element with no child elements.</span></span> <span data-ttu-id="88cc3-127">然後，它會使用 <xref:System.Xml.Linq.XElement.SetElementValue%2A> 方法來建立和維護成對的名稱/值組清單。</span><span class="sxs-lookup"><span data-stu-id="88cc3-127">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name-value pairs.</span></span>

```csharp
// Create an element with no content.
XElement root = new XElement("Root");

// Add a number of name-value pairs as elements.
root.SetElementValue("Top", 22);
root.SetElementValue("Left", 20);
root.SetElementValue("Bottom", 122);
root.SetElementValue("Right", 300);
root.SetElementValue("DefaultColor", "Color.Red");
Console.WriteLine(root);
Console.WriteLine("----");

// Replace the value of Top.
root.SetElementValue("Top", 10);
Console.WriteLine(root);
Console.WriteLine("----");

// Remove DefaultColor.
root.SetElementValue("DefaultColor", null);
Console.WriteLine(root);
```

```vb
' Create an element with no content.
Dim root As XElement = <Root/>

' Add a number of name-value pairs as elements.
root.SetElementValue("Top", 22)
root.SetElementValue("Left", 20)
root.SetElementValue("Bottom", 122)
root.SetElementValue("Right", 300)
root.SetElementValue("DefaultColor", "Color.Red")
Console.WriteLine(root)
Console.WriteLine("----")

' Replace the value of Top.
root.SetElementValue("Top", 10)
Console.WriteLine(root)
Console.WriteLine("----")

' Remove DefaultColor.
root.SetElementValue("DefaultColor", Nothing)
Console.WriteLine(root)
```

<span data-ttu-id="88cc3-128">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="88cc3-128">This example produces the following output:</span></span>

```xml
<Root>
  <Top>22</Top>
  <Left>20</Left>
  <Bottom>122</Bottom>
  <Right>300</Right>
  <DefaultColor>Color.Red</DefaultColor>
</Root>
----
<Root>
  <Top>10</Top>
  <Left>20</Left>
  <Bottom>122</Bottom>
  <Right>300</Right>
  <DefaultColor>Color.Red</DefaultColor>
</Root>
----
<Root>
  <Top>10</Top>
  <Left>20</Left>
  <Bottom>122</Bottom>
  <Right>300</Right>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="88cc3-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88cc3-129">See also</span></span>

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
