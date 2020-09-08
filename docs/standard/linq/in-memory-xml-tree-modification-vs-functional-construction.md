---
title: 記憶體中 XML 樹狀結構修改與功能結構 LINQ to XML
description: 請參閱修改 XML 樹狀結構的兩種不同方法的範例。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 71f76d12024bb07cf90df2299df14646ae271b47
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552123"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml"></a><span data-ttu-id="949c6-103">記憶體中的 XML 樹狀結構修改與功能結構 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="949c6-103">In-memory XML tree modification vs. functional construction (LINQ to XML)</span></span>

<span data-ttu-id="949c6-104">就地修改 XML 樹狀結構是變更 XML 文件組織結構的傳統方式。</span><span class="sxs-lookup"><span data-stu-id="949c6-104">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="949c6-105">一般的應用程式會將檔載入至資料存放區，例如 DOM 或 LINQ to XML;使用程式設計介面插入或刪除節點，或變更其內容;然後將 XML 儲存至檔案，或透過網路傳輸。</span><span class="sxs-lookup"><span data-stu-id="949c6-105">A typical application loads a document into a data store such as DOM or LINQ to XML; uses a programming interface to insert or delete nodes, or change their content; and then saves the XML to a file or transmits it over a network.</span></span>

<span data-ttu-id="949c6-106">LINQ to XML 啟用在許多案例中有用的另一種方法： *功能結構*。</span><span class="sxs-lookup"><span data-stu-id="949c6-106">LINQ to XML enables another approach that is useful in many scenarios: *functional construction*.</span></span> <span data-ttu-id="949c6-107">功能結構會將修改資料視為轉換的問題，而不是資料存放區的詳細管理。</span><span class="sxs-lookup"><span data-stu-id="949c6-107">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="949c6-108">如果您可以表示資料，並將其有效地從一個表單轉換到另一個表單，結果會與您取得一個資料存放區，然後以相同的方式管理該資料存放區取得其他組織結構相同。</span><span class="sxs-lookup"><span data-stu-id="949c6-108">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="949c6-109">功能結構方法的關鍵在於將查詢結果傳遞到 <xref:System.Xml.Linq.XDocument> 和 <xref:System.Xml.Linq.XElement> 建構函式。</span><span class="sxs-lookup"><span data-stu-id="949c6-109">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>

<span data-ttu-id="949c6-110">在許多情況下，您可以在運算元據存放區所需的時間內撰寫轉換程式碼，而產生的程式碼會更穩定且更容易維護。</span><span class="sxs-lookup"><span data-stu-id="949c6-110">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and the resulting code is more robust and easier to maintain.</span></span> <span data-ttu-id="949c6-111">在這些情況下，即使轉換方法可能需要更多處理能力，也是修改資料的有效方式。</span><span class="sxs-lookup"><span data-stu-id="949c6-111">In these cases, even though the transformational approach can take more processing power, it's a more effective way to modify data.</span></span> <span data-ttu-id="949c6-112">如果開發人員熟悉功能性方法，在許多情況下產生的程式碼會更容易瞭解，而且很容易就能找到修改樹狀結構每個部分的程式碼。</span><span class="sxs-lookup"><span data-stu-id="949c6-112">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand, and it's easy to find the code that modifies each part of the tree.</span></span>

<span data-ttu-id="949c6-113">對許多 DOM 程式設計師來說，您修改 XML 樹狀結構的方法比較熟悉，而使用功能性方法撰寫的程式碼可能看起來不熟悉該方法的開發人員。</span><span class="sxs-lookup"><span data-stu-id="949c6-113">The approach where you modify an XML tree in place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="949c6-114">如果您必須針對大型 XML 樹狀結構進行小小的修改，您就地修改樹狀結構的方法在大部分的情況下，將會需要較少的 CPU 時間。</span><span class="sxs-lookup"><span data-stu-id="949c6-114">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>

<span data-ttu-id="949c6-115">本文提供這兩種方法的範例。</span><span class="sxs-lookup"><span data-stu-id="949c6-115">This article provides examples of both approaches.</span></span> <span data-ttu-id="949c6-116">假設您想要修改下列簡單的 XML 檔，讓屬性成為元素：</span><span class="sxs-lookup"><span data-stu-id="949c6-116">Suppose you want to modify the following simple XML document so that the attributes become elements:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Root Data1="123" Data2="456">
  <Child1>Content</Child1>
</Root>
```

<span data-ttu-id="949c6-117">下列範例中的第一個範例會使用傳統的就地修改方法，而第二個範例會使用功能結構方法。</span><span class="sxs-lookup"><span data-stu-id="949c6-117">The first of the following examples uses the traditional in-place modification approach, and the second uses the functional construction approach.</span></span>

## <a name="example-transform-attributes-into-elements-with-the-traditional-in-place-approach"></a><span data-ttu-id="949c6-118">範例：使用傳統的就地方法將屬性轉換成元素</span><span class="sxs-lookup"><span data-stu-id="949c6-118">Example: Transform attributes into elements with the traditional in-place approach</span></span>

<span data-ttu-id="949c6-119">您可以撰寫特定的程序性程式碼以便從屬性建立項目，然後刪除該屬性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="949c6-119">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>

```csharp
XElement root = XElement.Load("Data.xml");
foreach (XAttribute att in root.Attributes()) {
    root.Add(new XElement(att.Name, (string)att));
}
root.Attributes().Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
For Each att As XAttribute In root.Attributes()
    root.Add(New XElement(att.Name, att.Value))
Next
root.Attributes().Remove()
Console.WriteLine(root)
```

<span data-ttu-id="949c6-120">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="949c6-120">This example produces the following output:</span></span>

```xml
<Root>
  <Child1>Content</Child1>
  <Data1>123</Data1>
  <Data2>456</Data2>
</Root>
```

## <a name="example-transform-attributes-into-elements-with-the-functional-construction-approach"></a><span data-ttu-id="949c6-121">範例：使用功能結構方法將屬性轉換成元素</span><span class="sxs-lookup"><span data-stu-id="949c6-121">Example: Transform attributes into elements with the functional construction approach</span></span>

<span data-ttu-id="949c6-122">相較之下，功能性方法是由程式碼組成，以形成新的樹狀結構、挑選和選擇來源樹狀結構中的專案和屬性，以及在新增至新樹狀結構時適當地轉換它們。</span><span class="sxs-lookup"><span data-stu-id="949c6-122">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they're added to the new tree.</span></span>

```csharp
XElement root = XElement.Load("Data.xml");
XElement newTree = new XElement("Root",
    root.Element("Child1"),
    from att in root.Attributes()
    select new XElement(att.Name, (string)att)
);
Console.WriteLine(newTree);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim newTree As XElement = _
    <Root>
        <%= root.<Child1> %>
        <%= From att In root.Attributes() _
            Select New XElement(att.Name, att.Value) %>
    </Root>
Console.WriteLine(newTree)
```

<span data-ttu-id="949c6-123">這個範例會與第一個範例輸出相同的 XML。</span><span class="sxs-lookup"><span data-stu-id="949c6-123">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="949c6-124">但是請注意，您實際上可以用功能性方法查看所產生的新 XML 結構。</span><span class="sxs-lookup"><span data-stu-id="949c6-124">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="949c6-125">您可以查看 `Root` 項目的建立、從來源樹狀結構提取 `Child1` 項目的程式碼，以及將屬性從來源樹狀結構轉換到新樹狀結構中的項目之程式碼。</span><span class="sxs-lookup"><span data-stu-id="949c6-125">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>

<span data-ttu-id="949c6-126">在此情況下，此功能範例的長度不會比第一個範例還簡單。</span><span class="sxs-lookup"><span data-stu-id="949c6-126">The functional example in this case is neither shorter nor simpler than the first example.</span></span> <span data-ttu-id="949c6-127">但是，如果您對 XML 樹狀結構進行了許多變更，則程式化方法會變得相當複雜，而且有點遲鈍。</span><span class="sxs-lookup"><span data-stu-id="949c6-127">However, if you have many changes to make to an XML tree, the procedural approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="949c6-128">相反地，使用功能性方法時，您仍然可以在適當地內嵌查詢和運算式，只形成所需的 XML，以便在所需的內容中提取。</span><span class="sxs-lookup"><span data-stu-id="949c6-128">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="949c6-129">功能性方法會產生容易維護的程式碼。</span><span class="sxs-lookup"><span data-stu-id="949c6-129">The functional approach yields code that is easier to maintain.</span></span>

<span data-ttu-id="949c6-130">請注意，在這個情況下，功能性方法可能不會實際與樹狀結構管理方法一起執行。</span><span class="sxs-lookup"><span data-stu-id="949c6-130">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="949c6-131">主要的問題是，功能性方法會建立更多短期的物件。</span><span class="sxs-lookup"><span data-stu-id="949c6-131">The main issue is that the functional approach creates more short-lived objects.</span></span> <span data-ttu-id="949c6-132">不過，如果使用功能性方法能讓程式設計人員的產能更大，進行取捨是有效的方法。</span><span class="sxs-lookup"><span data-stu-id="949c6-132">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>

<span data-ttu-id="949c6-133">這是非常簡單的範例，但是它有助於顯示兩種方法間的觀點差異。</span><span class="sxs-lookup"><span data-stu-id="949c6-133">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="949c6-134">功能性方法在轉換大型 XML 文件時，會產生較大的產能。</span><span class="sxs-lookup"><span data-stu-id="949c6-134">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>
