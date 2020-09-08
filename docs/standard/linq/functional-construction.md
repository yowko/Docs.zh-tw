---
title: 功能結構-LINQ to XML
description: LINQ to XML 提供功能結構，可讓您在單一語句中建立 XML 樹狀結構。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: bcdc153d7f60cfb165dcb741d62b6af5c07a148a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552165"
---
# <a name="functional-construction-linq-to-xml"></a><span data-ttu-id="ea508-103">功能結構 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="ea508-103">Functional construction (LINQ to XML)</span></span>

<span data-ttu-id="ea508-104">LINQ to XML 提供了一種強大的方式來建立稱為「 *功能結構*」的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="ea508-104">LINQ to XML provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="ea508-105">功能結構可讓您在單一語句中建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="ea508-105">Functional construction enables you to create an XML tree in a single statement.</span></span>

<span data-ttu-id="ea508-106">在功能結構中使用 LINQ to XML 程式設計介面的幾個主要功能：</span><span class="sxs-lookup"><span data-stu-id="ea508-106">Several key features of the LINQ to XML programming interface are used in functional construction:</span></span>

- <span data-ttu-id="ea508-107"><xref:System.Xml.Linq.XElement> 建構函式會針對內容採用各種引數類型。</span><span class="sxs-lookup"><span data-stu-id="ea508-107">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="ea508-108">例如，您可以傳遞變成子項目的其他 <xref:System.Xml.Linq.XElement> 物件。</span><span class="sxs-lookup"><span data-stu-id="ea508-108">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="ea508-109">您可以傳遞變成項目屬性的 <xref:System.Xml.Linq.XAttribute> 物件。</span><span class="sxs-lookup"><span data-stu-id="ea508-109">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="ea508-110">或者，您可以傳遞轉換成字串的其他類物件型，然後變成項目的文字內容。</span><span class="sxs-lookup"><span data-stu-id="ea508-110">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>
- <span data-ttu-id="ea508-111"><xref:System.Xml.Linq.XElement> 建構函式會採用 `params` 類型的 <xref:System.Object> 陣列，讓您可以將任何數目的物件傳遞到建構函式。</span><span class="sxs-lookup"><span data-stu-id="ea508-111">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="ea508-112">這可讓您建立包含複雜內容的項目。</span><span class="sxs-lookup"><span data-stu-id="ea508-112">This enables you to create an element that has complex content.</span></span>
- <span data-ttu-id="ea508-113">如果物件實作 <xref:System.Collections.Generic.IEnumerable%601>，系統列舉物件中的集合，並加入集合中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="ea508-113">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="ea508-114">如果集合包含 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 物件，系統會個別加入集合中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="ea508-114">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="ea508-115">這點很重要，因為它可讓您將 LINQ 查詢的結果傳遞給函式。</span><span class="sxs-lookup"><span data-stu-id="ea508-115">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>

## <a name="example-create-an-xml-tree"></a><span data-ttu-id="ea508-116">範例：建立 XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="ea508-116">Example: Create an XML tree</span></span>

<span data-ttu-id="ea508-117">您可以使用功能結構來撰寫程式碼，以建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="ea508-117">You can use functional construction to write code to create an XML tree.</span></span> <span data-ttu-id="ea508-118">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="ea508-118">The following is an example:</span></span>

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

## <a name="example-create-an-xml-tree-using-linq-query-results"></a><span data-ttu-id="ea508-119">範例：使用 LINQ 查詢結果建立 XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="ea508-119">Example: Create an XML tree using LINQ query results</span></span>

<span data-ttu-id="ea508-120">當您建立 XML 樹狀結構時，這些功能也可讓您撰寫使用 LINQ 查詢結果的程式碼，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ea508-120">These features also enable you to write code that uses the results of LINQ queries when you create an XML tree, as in the following example:</span></span>

```csharp
XElement srcTree = new XElement("Root",
    new XElement("Element", 1),
    new XElement("Element", 2),
    new XElement("Element", 3),
    new XElement("Element", 4),
    new XElement("Element", 5)
);
XElement xmlTree = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    from el in srcTree.Elements()
    where (int)el > 2
    select el
);
Console.WriteLine(xmlTree);
```

<span data-ttu-id="ea508-121">在 Visual Basic 中，您可以使用 XML 常值來完成相同的動作：</span><span class="sxs-lookup"><span data-stu-id="ea508-121">In Visual Basic, the same thing is accomplished with XML literals:</span></span>

```vb
Dim srcTree As XElement = _
    <Root>
        <Element>1</Element>
        <Element>2</Element>
        <Element>3</Element>
        <Element>4</Element>
        <Element>5</Element>
    </Root>
Dim xmlTree As XElement = _
    <Root>
        <Child>1</Child>
        <Child>2</Child>
        <%= From el In srcTree.Elements() _
            Where CInt(el) > 2 _
            Select el %>
    </Root>
Console.WriteLine(xmlTree)
```

<span data-ttu-id="ea508-122">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="ea508-122">This example produces the following output:</span></span>

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Element>3</Element>
  <Element>4</Element>
  <Element>5</Element>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="ea508-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea508-123">See also</span></span>

- [<span data-ttu-id="ea508-124">在 C 中建立 XML 樹狀結構#</span><span class="sxs-lookup"><span data-stu-id="ea508-124">Create XML Trees in C#</span></span>](create-xml-trees.md)
- [<span data-ttu-id="ea508-125">Visual Basic 中的 XML 常值</span><span class="sxs-lookup"><span data-stu-id="ea508-125">XML literals in Visual Basic</span></span>](xml-literals.md)
