---
title: '在 c # 中建立 XML 樹狀結構-LINQ to XML'
description: '您可以使用 LINQ to XML System.xml.linq.xelement> 和 System.xml.linq.xattribute> 的函式，以 c # 建立 XML 樹狀結構，也可以讓程式碼類似于基礎 XML 的結構。'
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 97bf40d84f40eabf6fa84f10bf4febb7697b10f5
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552773"
---
# <a name="create-xml-trees-in-c-linq-to-xml"></a><span data-ttu-id="eb2b2-103">在 c # 中建立 XML 樹狀結構 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="eb2b2-103">Create XML trees in C# (LINQ to XML)</span></span>

<span data-ttu-id="eb2b2-104">本文提供如何在 c # 中建立 XML 樹狀結構的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-104">This article provides information about creating XML trees in C#.</span></span>

<span data-ttu-id="eb2b2-105">如需使用 LINQ 查詢結果作為內容的詳細資訊 <xref:System.Xml.Linq.XElement> ，請參閱 [功能性結構](functional-construction.md)。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-105">For information about using the results of LINQ queries as the content for an <xref:System.Xml.Linq.XElement>, see [Functional construction](functional-construction.md).</span></span>

## <a name="construct-elements"></a><span data-ttu-id="eb2b2-106">結構元素</span><span class="sxs-lookup"><span data-stu-id="eb2b2-106">Construct elements</span></span>

<span data-ttu-id="eb2b2-107"><xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XAttribute> 建構函式的簽章可讓您傳遞項目或屬性的內容，當做建構函式的引數。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-107">The signatures of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors let you pass the contents of the element or attribute as arguments to the constructor.</span></span> <span data-ttu-id="eb2b2-108">由於其中一個建構函式採用多個引數，因此，您可以傳遞任何數目的子項目。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-108">Because one of the constructors takes a variable number of arguments, you can pass any number of child elements.</span></span> <span data-ttu-id="eb2b2-109">當然，這些子項目中的每個子項目都可以包含其自己的子項目。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-109">Of course, each of those child elements can contain their own child elements.</span></span> <span data-ttu-id="eb2b2-110">對於任何項目，您可以加入任何數目的屬性。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-110">For any element, you can add any number of attributes.</span></span>

<span data-ttu-id="eb2b2-111">加入 <xref:System.Xml.Linq.XNode> (包括 <xref:System.Xml.Linq.XElement>) 或 <xref:System.Xml.Linq.XAttribute> 物件時，如果新內容沒有父代，這些物件只會附加到 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-111">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="eb2b2-112">如果新內容已經成為父代，或是其他 XML 樹狀的一部分，則會複製新內容，而且新複製的內容會附加到 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-112">If the new content already is parented, and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span> <span data-ttu-id="eb2b2-113">本文的最後一個範例將示範這項功能。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-113">The last example in this article demonstrates this.</span></span>

<span data-ttu-id="eb2b2-114">若要建立 `contacts` <xref:System.Xml.Linq.XElement> ，您可以使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="eb2b2-114">To create a `contacts` <xref:System.Xml.Linq.XElement>, you could use the following code:</span></span>

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
```

<span data-ttu-id="eb2b2-115">如果縮排正確，建構 <xref:System.Xml.Linq.XElement> 物件的程式碼會非常接近基礎 XML 的結構。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-115">If indented properly, the code to construct <xref:System.Xml.Linq.XElement> objects closely resembles the structure of the underlying XML.</span></span>

## <a name="xelement-constructors"></a><span data-ttu-id="eb2b2-116">XElement 建構函式</span><span class="sxs-lookup"><span data-stu-id="eb2b2-116">XElement constructors</span></span>

<span data-ttu-id="eb2b2-117"><xref:System.Xml.Linq.XElement> 類別會將下列建構函式用於功能結構。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-117">The <xref:System.Xml.Linq.XElement> class uses the following constructors for functional construction.</span></span> <span data-ttu-id="eb2b2-118">請注意，有一些其他的函式 <xref:System.Xml.Linq.XElement> ，但因為它們不是用於功能結構，所以不會在這裡列出。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-118">Note that there are some other constructors for <xref:System.Xml.Linq.XElement>, but because they're not used for functional construction they're not listed here.</span></span>

|<span data-ttu-id="eb2b2-119">建構函式</span><span class="sxs-lookup"><span data-stu-id="eb2b2-119">Constructor</span></span>|<span data-ttu-id="eb2b2-120">描述</span><span class="sxs-lookup"><span data-stu-id="eb2b2-120">Description</span></span>|
|-----------------|-----------------|
|`XElement(XName name, object content)`|<span data-ttu-id="eb2b2-121">建立 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-121">Creates an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="eb2b2-122">`name` 參數會指定項目的名稱；`content` 會指定項目的內容。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-122">The `name` parameter specifies the name of the element; `content` specifies the content of the element.</span></span>|
|`XElement(XName name)`|<span data-ttu-id="eb2b2-123">在將其 <xref:System.Xml.Linq.XElement> 初始化為指定之名稱的情況下，建立 <xref:System.Xml.Linq.XName>。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-123">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span>|
|`XElement(XName name, params object[] content)`|<span data-ttu-id="eb2b2-124">在將其 <xref:System.Xml.Linq.XElement> 初始化為指定之名稱的情況下，建立 <xref:System.Xml.Linq.XName>。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-124">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span> <span data-ttu-id="eb2b2-125">系統會從參數清單的內容建立屬性和/或子項目。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-125">The attributes and/or child elements are created from the contents of the parameter list.</span></span>|

<span data-ttu-id="eb2b2-126">`content` 參數非常有彈性。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-126">The `content` parameter is extremely flexible.</span></span> <span data-ttu-id="eb2b2-127">它支援任何屬於有效子系的物件類型 <xref:System.Xml.Linq.XElement> 。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-127">It supports any type of object that's a valid child of an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="eb2b2-128">下列規則適用於傳入此參數的不同型別物件：</span><span class="sxs-lookup"><span data-stu-id="eb2b2-128">The following rules apply to different types of objects passed in this parameter:</span></span>

- <span data-ttu-id="eb2b2-129">字串當做文字內容加入。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-129">A string is added as text content.</span></span>
- <span data-ttu-id="eb2b2-130"><xref:System.Xml.Linq.XElement> 當做子項目加入。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-130">An <xref:System.Xml.Linq.XElement> is added as a child element.</span></span>
- <span data-ttu-id="eb2b2-131"><xref:System.Xml.Linq.XAttribute> 當做屬性加入。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-131">An <xref:System.Xml.Linq.XAttribute> is added as an attribute.</span></span>
- <span data-ttu-id="eb2b2-132"><xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment> 或 <xref:System.Xml.Linq.XText> 當做子內容加入。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-132">An <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, or <xref:System.Xml.Linq.XText> is added as child content.</span></span>
- <span data-ttu-id="eb2b2-133">系統會列舉 <xref:System.Collections.IEnumerable>，並將這些規則遞迴地套用到結果。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-133">An <xref:System.Collections.IEnumerable> is enumerated, and these rules are applied recursively to the results.</span></span>
- <span data-ttu-id="eb2b2-134">若是其他任何型別，則會呼叫其 `ToString` 方法，並將結果當做文字內容加入。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-134">For any other type, its `ToString` method is called and the result is added as text content.</span></span>

## <a name="example-create-an-xelement-with-content"></a><span data-ttu-id="eb2b2-135">範例：建立具有內容的 System.xml.linq.xelement></span><span class="sxs-lookup"><span data-stu-id="eb2b2-135">Example: Create an XElement with content</span></span>

<span data-ttu-id="eb2b2-136">您可以建立包含具有單一方法呼叫之簡單內容的 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-136">You can create an <xref:System.Xml.Linq.XElement> that contains simple content with a single method call.</span></span> <span data-ttu-id="eb2b2-137">如果要這樣做，請將內容指定為第二個參數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="eb2b2-137">To do this, specify the content as the second parameter, as follows:</span></span>

```csharp
XElement n = new XElement("Customer", "Adventure Works");
Console.WriteLine(n);
```

<span data-ttu-id="eb2b2-138">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="eb2b2-138">This example produces the following output:</span></span>

```xml
<Customer>Adventure Works</Customer>
```

<span data-ttu-id="eb2b2-139">您可以傳遞任何型別的物件當做內容。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-139">You can pass any type of object as the content.</span></span> <span data-ttu-id="eb2b2-140">例如，下列程式碼會建立包含浮點數的項目當做內容：</span><span class="sxs-lookup"><span data-stu-id="eb2b2-140">For example, the following code creates an element that contains a floating point number as content:</span></span>

```csharp
XElement n = new XElement("Cost", 324.50);
Console.WriteLine(n);
```

<span data-ttu-id="eb2b2-141">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="eb2b2-141">This example produces the following output:</span></span>

```xml
<Cost>324.5</Cost>
```

<span data-ttu-id="eb2b2-142">浮點數為 Boxed 而且會傳入建構函式。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-142">The floating point number is boxed and passed in to the constructor.</span></span> <span data-ttu-id="eb2b2-143">Boxed 數字會轉換為字串，並當做項目的內容使用。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-143">The boxed number is converted to a string and used as the content of the element.</span></span>

## <a name="example-create-an-xelement-with-a-child-element"></a><span data-ttu-id="eb2b2-144">範例：建立具有子項目的 System.xml.linq.xelement></span><span class="sxs-lookup"><span data-stu-id="eb2b2-144">Example: Create an XElement with a child element</span></span>

<span data-ttu-id="eb2b2-145">如果您要針對內容引數傳遞 <xref:System.Xml.Linq.XElement> 類別的執行個體，建構函式會建立包含子項目的項目：</span><span class="sxs-lookup"><span data-stu-id="eb2b2-145">If you pass an instance of the <xref:System.Xml.Linq.XElement> class for the content argument, the constructor creates an element with a child element:</span></span>

```csharp
XElement shippingUnit = new XElement("ShippingUnit",
    new XElement("Cost", 324.50)
);
Console.WriteLine(shippingUnit);
```

<span data-ttu-id="eb2b2-146">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="eb2b2-146">This example produces the following output:</span></span>

```xml
<ShippingUnit>
  <Cost>324.5</Cost>
</ShippingUnit>
```

## <a name="example-create-an-xelement-with-multiple-child-elements"></a><span data-ttu-id="eb2b2-147">範例：建立具有多個子項目的 System.xml.linq.xelement></span><span class="sxs-lookup"><span data-stu-id="eb2b2-147">Example: Create an XElement with multiple child elements</span></span>

<span data-ttu-id="eb2b2-148">您可以針對內容傳入多個 <xref:System.Xml.Linq.XElement> 物件。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-148">You can pass in a number of <xref:System.Xml.Linq.XElement> objects for the content.</span></span> <span data-ttu-id="eb2b2-149">每個 <xref:System.Xml.Linq.XElement> 物件都會當做子項目包含在內。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-149">Each of the <xref:System.Xml.Linq.XElement> objects is included as a child element.</span></span>

```csharp
XElement address = new XElement("Address",
    new XElement("Street1", "123 Main St"),
    new XElement("City", "Mercer Island"),
    new XElement("State", "WA"),
    new XElement("Postal", "68042")
);
Console.WriteLine(address);
```

<span data-ttu-id="eb2b2-150">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="eb2b2-150">This example produces the following output:</span></span>

```xml
<Address>
  <Street1>123 Main St</Street1>
  <City>Mercer Island</City>
  <State>WA</State>
  <Postal>68042</Postal>
</Address>
```

<span data-ttu-id="eb2b2-151">藉由擴充先前的範例，您可以建立整個 XML 樹狀結構，如下所示：</span><span class="sxs-lookup"><span data-stu-id="eb2b2-151">By extending the previous example, you can create an entire XML tree, as follows:</span></span>

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
Console.WriteLine(contacts);
```

<span data-ttu-id="eb2b2-152">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="eb2b2-152">This example produces the following output:</span></span>

```xml
<Contacts>
  <Contact>
    <Name>Patrick Hines</Name>
    <Phone>206-555-0144</Phone>
    <Address>
      <Street1>123 Main St</Street1>
      <City>Mercer Island</City>
      <State>WA</State>
      <Postal>68042</Postal>
    </Address>
  </Contact>
</Contacts>
```

## <a name="example-create-an-xelement-with-an-xattribute"></a><span data-ttu-id="eb2b2-153">範例：使用 System.xml.linq.xattribute> 建立 System.xml.linq.xelement></span><span class="sxs-lookup"><span data-stu-id="eb2b2-153">Example: Create an XElement with an XAttribute</span></span>

<span data-ttu-id="eb2b2-154">如果您針對內容引數傳遞 <xref:System.Xml.Linq.XAttribute> 類別的執行個體，建構函式會建立具有屬性的元素：</span><span class="sxs-lookup"><span data-stu-id="eb2b2-154">If you pass an instance of the <xref:System.Xml.Linq.XAttribute> class for the content argument, the constructor creates an element with an attribute:</span></span>

```csharp
XElement phone = new XElement("Phone",
    new XAttribute("Type", "Home"),
    "555-555-5555");
Console.WriteLine(phone);
```

<span data-ttu-id="eb2b2-155">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="eb2b2-155">This example produces the following output:</span></span>

```xml
<Phone Type="Home">555-555-5555</Phone>
```

## <a name="example-create-an-empty-element"></a><span data-ttu-id="eb2b2-156">範例：建立空白元素</span><span class="sxs-lookup"><span data-stu-id="eb2b2-156">Example: Create an empty element</span></span>

<span data-ttu-id="eb2b2-157">若要建立空的 <xref:System.Xml.Linq.XElement> ，請不要將任何內容傳遞至該函式。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-157">To create an empty <xref:System.Xml.Linq.XElement>, don't pass any content to the constructor.</span></span> <span data-ttu-id="eb2b2-158">下列範例會建立空項目：</span><span class="sxs-lookup"><span data-stu-id="eb2b2-158">The following example creates an empty element:</span></span>

```csharp
XElement n = new XElement("Customer");
Console.WriteLine(n);
```

<span data-ttu-id="eb2b2-159">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="eb2b2-159">This example produces the following output:</span></span>

```xml
<Customer />
```

## <a name="example-attach-vs-clone"></a><span data-ttu-id="eb2b2-160">範例：附加與複製</span><span class="sxs-lookup"><span data-stu-id="eb2b2-160">Example: Attach vs. clone</span></span>

<span data-ttu-id="eb2b2-161">如先前所述，加入 <xref:System.Xml.Linq.XNode> (包括 <xref:System.Xml.Linq.XElement>) 或 <xref:System.Xml.Linq.XAttribute> 物件時，如果新內容沒有父代，這些物件只會附加到 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-161">As mentioned previously, when adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="eb2b2-162">如果新內容已經成為父代，或是其他 XML 樹狀的一部分，則會複製新內容，而且新複製的內容會附加到 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="eb2b2-162">If the new content already is parented and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>

<span data-ttu-id="eb2b2-163">下列範例將示範當您將父元素加入至樹狀結構，以及將沒有父代的專案加入樹狀結構時的行為：</span><span class="sxs-lookup"><span data-stu-id="eb2b2-163">The following example demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree:</span></span>

```csharp
// Create a tree with a child element.
XElement xmlTree1 = new XElement("Root",
    new XElement("Child1", 1)
);

// Create an element that's not parented.
XElement child2 = new XElement("Child2", 2);

// Create a tree and add Child1 and Child2 to it.
XElement xmlTree2 = new XElement("Root",
    xmlTree1.Element("Child1"),
    child2
);

// Compare Child1 identity.
Console.WriteLine("Child1 was {0}",
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?
    "attached" : "cloned");

// Compare Child2 identity.
Console.WriteLine("Child2 was {0}",
    child2 == xmlTree2.Element("Child2") ?
    "attached" : "cloned");

// This example produces the following output:
//    Child1 was cloned
//    Child2 was attached
```

## <a name="see-also"></a><span data-ttu-id="eb2b2-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb2b2-164">See also</span></span>

- [<span data-ttu-id="eb2b2-165">功能結構</span><span class="sxs-lookup"><span data-stu-id="eb2b2-165">Functional construction</span></span>](functional-construction.md)
