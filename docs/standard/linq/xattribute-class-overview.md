---
title: System.xml.linq.xattribute> 類別總覽
description: System.xml.linq.xattribute> 類別代表 XML 屬性。 使用 LINQ to XML 中的屬性類似于使用元素。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: deab6e8dd9695a442cd362401aec8b68cdbf218f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552114"
---
# <a name="xattribute-class-overview"></a><span data-ttu-id="88f3f-104">System.xml.linq.xattribute> 類別總覽</span><span class="sxs-lookup"><span data-stu-id="88f3f-104">XAttribute class overview</span></span>

<span data-ttu-id="88f3f-105">屬性是與專案相關聯的成對名稱/值。</span><span class="sxs-lookup"><span data-stu-id="88f3f-105">Attributes are name-value pairs that are associated with an element.</span></span> <span data-ttu-id="88f3f-106"><xref:System.Xml.Linq.XAttribute> 類別表示 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="88f3f-106">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>

<span data-ttu-id="88f3f-107">使用 LINQ to XML 中的屬性類似于使用元素。</span><span class="sxs-lookup"><span data-stu-id="88f3f-107">Working with attributes in LINQ to XML is similar to working with elements.</span></span> <span data-ttu-id="88f3f-108">其建構函式類似。</span><span class="sxs-lookup"><span data-stu-id="88f3f-108">Their constructors are similar.</span></span> <span data-ttu-id="88f3f-109">您用來擷取其集合的方法也類似。</span><span class="sxs-lookup"><span data-stu-id="88f3f-109">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="88f3f-110">屬性集合的 LINQ 查詢運算式看起來類似于元素集合的 LINQ 查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="88f3f-110">A LINQ query expression for a collection of attributes looks similar to a LINQ query expression for a collection of elements.</span></span>

<span data-ttu-id="88f3f-111">系統會保留將屬性加入到項目的順序。</span><span class="sxs-lookup"><span data-stu-id="88f3f-111">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="88f3f-112">也就是說，當您逐一查看屬性時，您會看到加入這些屬性的相同順序。</span><span class="sxs-lookup"><span data-stu-id="88f3f-112">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>

## <a name="the-xattribute-constructor"></a><span data-ttu-id="88f3f-113">System.xml.linq.xattribute> 函式</span><span class="sxs-lookup"><span data-stu-id="88f3f-113">The XAttribute constructor</span></span>

<span data-ttu-id="88f3f-114">下列類別的函式 <xref:System.Xml.Linq.XAttribute> 是您最常使用的類別：</span><span class="sxs-lookup"><span data-stu-id="88f3f-114">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you'll most commonly use:</span></span>

|<span data-ttu-id="88f3f-115">建構函式</span><span class="sxs-lookup"><span data-stu-id="88f3f-115">Constructor</span></span>|<span data-ttu-id="88f3f-116">描述</span><span class="sxs-lookup"><span data-stu-id="88f3f-116">Description</span></span>|
|-----------------|-----------------|
|`XAttribute(XName name, object content)`|<span data-ttu-id="88f3f-117">建立 <xref:System.Xml.Linq.XAttribute> 物件。</span><span class="sxs-lookup"><span data-stu-id="88f3f-117">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="88f3f-118">`name` 引數會指定屬性的名稱；`content` 會指定屬性的內容。</span><span class="sxs-lookup"><span data-stu-id="88f3f-118">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|

## <a name="example-create-an-element-with-an-attribute"></a><span data-ttu-id="88f3f-119">範例：建立具有屬性的元素</span><span class="sxs-lookup"><span data-stu-id="88f3f-119">Example: Create an element with an attribute</span></span>

<span data-ttu-id="88f3f-120">下列範例顯示建立包含屬性之元素的一般工作。</span><span class="sxs-lookup"><span data-stu-id="88f3f-120">The following example shows the common task of creating an element that contains an attribute.</span></span>

```csharp
XElement phone = new XElement("Phone",
    new XAttribute("Type", "Home"),
    "555-555-5555");
Console.WriteLine(phone);
```

```vb
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>
Console.WriteLine(phone)
```

<span data-ttu-id="88f3f-121">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="88f3f-121">This example produces the following output:</span></span>

```xml
<Phone Type="Home">555-555-5555</Phone>
```

## <a name="example-functional-construction-of-attributes"></a><span data-ttu-id="88f3f-122">範例：屬性的功能結構</span><span class="sxs-lookup"><span data-stu-id="88f3f-122">Example: Functional construction of attributes</span></span>

<span data-ttu-id="88f3f-123">您可以 <xref:System.Xml.Linq.XAttribute> 使用物件的結構，以內嵌方式建立物件 <xref:System.Xml.Linq.XElement> ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="88f3f-123">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as shown in the following example:</span></span>

```csharp
XElement c = new XElement("Customers",
    new XElement("Customer",
        new XElement("Name", "John Doe"),
        new XElement("PhoneNumbers",
            new XElement("Phone",
                new XAttribute("type", "home"),
                "555-555-5555"),
            new XElement("Phone",
                new XAttribute("type", "work"),
                "666-666-6666")
        )
    )
);
Console.WriteLine(c);
```

```vb
Dim c As XElement = _
    <Customers>
        <Customer>
            <Name>John Doe</Name>
            <PhoneNumbers>
                <Phone type="home">555-555-5555</Phone>
                <Phone type="work">666-666-6666</Phone>
            </PhoneNumbers>
        </Customer>
    </Customers>
Console.WriteLine(c)
```

<span data-ttu-id="88f3f-124">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="88f3f-124">This example produces the following output:</span></span>

```xml
<Customers>
  <Customer>
    <Name>John Doe</Name>
    <PhoneNumbers>
      <Phone type="home">555-555-5555</Phone>
      <Phone type="work">666-666-6666</Phone>
    </PhoneNumbers>
  </Customer>
</Customers>
```

## <a name="attributes-arent-nodes"></a><span data-ttu-id="88f3f-125">屬性不是節點</span><span class="sxs-lookup"><span data-stu-id="88f3f-125">Attributes aren't nodes</span></span>

<span data-ttu-id="88f3f-126">屬性和項目有一些差異。</span><span class="sxs-lookup"><span data-stu-id="88f3f-126">There are some differences between attributes and elements.</span></span> <span data-ttu-id="88f3f-127"><xref:System.Xml.Linq.XAttribute> 物件不是 XML 樹狀結構中的節點。</span><span class="sxs-lookup"><span data-stu-id="88f3f-127"><xref:System.Xml.Linq.XAttribute> objects aren't nodes in the XML tree.</span></span> <span data-ttu-id="88f3f-128">它們是與 XML 元素相關聯的名稱/值配對。</span><span class="sxs-lookup"><span data-stu-id="88f3f-128">They're name-value pairs associated with an XML element.</span></span> <span data-ttu-id="88f3f-129">相較於文件物件模型 (DOM)，這在反映 XML 的結構時，更為接近。</span><span class="sxs-lookup"><span data-stu-id="88f3f-129">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="88f3f-130">雖然 <xref:System.Xml.Linq.XAttribute> 物件實際上不是 XML 樹狀結構中的節點，但使用物件的方式類似于使用 <xref:System.Xml.Linq.XAttribute> <xref:System.Xml.Linq.XElement> 物件。</span><span class="sxs-lookup"><span data-stu-id="88f3f-130">Although <xref:System.Xml.Linq.XAttribute> objects aren't actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>

<span data-ttu-id="88f3f-131">這個區別只有對於撰寫可在節點層級使用 XML 樹狀結構之程式碼的開發人員特別重要。</span><span class="sxs-lookup"><span data-stu-id="88f3f-131">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="88f3f-132">許多開發人員都不在意這種差異。</span><span class="sxs-lookup"><span data-stu-id="88f3f-132">Many developers won't be concerned with this distinction.</span></span>

## <a name="see-also"></a><span data-ttu-id="88f3f-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88f3f-133">See also</span></span>

- [<span data-ttu-id="88f3f-134">LINQ to XML 總覽</span><span class="sxs-lookup"><span data-stu-id="88f3f-134">LINQ to XML overview</span></span>](linq-xml-overview.md)
