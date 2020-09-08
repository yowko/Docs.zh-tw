---
title: 混合的宣告式/命令式程式碼 bug-LINQ to XML
description: 瞭解如何辨識和避免程式碼逐一查看進行變更時可能發生的問題。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 280bb62d15ff28d1fd09ca2d0c52c0a0c36d7282
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552217"
---
# <a name="mixed-declarativeimperative-code-bugs-linq-to-xml"></a><span data-ttu-id="0bc5a-103">混合的宣告式/命令式程式碼 bug (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="0bc5a-103">Mixed declarative/imperative code bugs (LINQ to XML)</span></span>

<span data-ttu-id="0bc5a-104">LINQ to XML 包含各種可讓您直接修改 XML 樹狀結構的方法。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-104">LINQ to XML contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="0bc5a-105">您可以加入項目、刪除項目、變更項目的內容、加入屬性等等。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-105">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="0bc5a-106">[修改 XML 樹狀](in-memory-xml-tree-modification-vs-functional-construction.md)結構中會說明這個程式設計介面。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-106">This programming interface is described in [Modify XML trees](in-memory-xml-tree-modification-vs-functional-construction.md).</span></span> <span data-ttu-id="0bc5a-107">如果您正在逐一查看其中一個軸（例如）， <xref:System.Xml.Linq.XContainer.Elements%2A> 而且您要在逐一查看軸時修改 XML 樹狀結構，最後可能會出現一些奇怪的錯誤。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-107">If you're iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you're modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>

<span data-ttu-id="0bc5a-108">這種問題有時候稱為「幽靈問題」。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-108">This problem is sometimes known as "The Halloween Problem".</span></span>

<span data-ttu-id="0bc5a-109">當您使用可逐一查看集合的 LINQ 撰寫一些程式碼時，就是以宣告式樣式撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-109">When you write some code using LINQ that iterates through a collection, you're writing code in a declarative style.</span></span> <span data-ttu-id="0bc5a-110">它比較類似于描述您想要的 *內容* ，而不是您想要 *如何* 完成。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-110">It's more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="0bc5a-111">如果您撰寫的程式碼可 1) 取得第一個項目、2) 針對某些條件進行測試、3) 加以修改，以及 4) 將其放回清單中，則這會是命令性程式碼。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="0bc5a-112">您會告訴電腦 *如何* 執行您想要的動作。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-112">You're telling the computer *how* to do what you want done.</span></span>

<span data-ttu-id="0bc5a-113">在相同的運算中混用這些程式碼樣式就是導致問題發生的原因。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="0bc5a-114">請考慮下列事項：</span><span class="sxs-lookup"><span data-stu-id="0bc5a-114">Consider the following:</span></span>

<span data-ttu-id="0bc5a-115">假設您有一個連結的清單，其中包含三個項目 (a、b 和 c)：</span><span class="sxs-lookup"><span data-stu-id="0bc5a-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>

> <span data-ttu-id="0bc5a-116">a-> b-> c</span><span class="sxs-lookup"><span data-stu-id="0bc5a-116">a -> b -> c</span></span>

<span data-ttu-id="0bc5a-117">現在，假設您要移動連結的清單，以加入三個新項目 (a'、b' 和 c')。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-117">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="0bc5a-118">您希望所產生的連結清單如下所示：</span><span class="sxs-lookup"><span data-stu-id="0bc5a-118">You want the resulting linked list to look like this:</span></span>

 > <span data-ttu-id="0bc5a-119">a-> a '-> b-> b '-> c-> c '</span><span class="sxs-lookup"><span data-stu-id="0bc5a-119">a -> a' -> b -> b' -> c -> c'</span></span>

<span data-ttu-id="0bc5a-120">因此，您可以撰寫逐一查看清單的程式碼，然後針對每個項目，將新項目加入到清單的後面。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-120">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="0bc5a-121">結果是，您的程式碼將會先看到 `a` 項目，然後在其後插入 `a'`。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-121">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="0bc5a-122">現在，您的程式碼會移至清單中的下一個節點（現在 `a'` ），因此它會在清單中加入新的專案到清單中！</span><span class="sxs-lookup"><span data-stu-id="0bc5a-122">Now, your code will move to the next node in the list, which is now `a'`, so it adds a new item between a' and b to the list!</span></span>

<span data-ttu-id="0bc5a-123">您要如何解決這個問題？</span><span class="sxs-lookup"><span data-stu-id="0bc5a-123">How would you solve this?</span></span> <span data-ttu-id="0bc5a-124">您可以複製原始的連結清單，然後建立一個全新的清單。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-124">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="0bc5a-125">或者，如果您要撰寫單純的命令式程式碼，您可能會發現第一個專案，加入新的專案，然後在連結清單中前進兩次，然後在您剛加入的元素上前進。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-125">Or if you're writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>

## <a name="example-adding-while-iterating"></a><span data-ttu-id="0bc5a-126">範例：反覆運算時加入</span><span class="sxs-lookup"><span data-stu-id="0bc5a-126">Example: Adding while iterating</span></span>

<span data-ttu-id="0bc5a-127">例如，假設您想要撰寫程式碼，以在樹狀結構中建立每個元素的重複專案：</span><span class="sxs-lookup"><span data-stu-id="0bc5a-127">For example, suppose you want to write code to create a duplicate of every element in a tree:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements())
    root.Add(new XElement(e.Name, (string)e));
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements()
    root.Add(New XElement(e.Name, e.Value))
Next
```

<span data-ttu-id="0bc5a-128">這個程式碼會進入無限的迴圈。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-128">This code goes into an infinite loop.</span></span> <span data-ttu-id="0bc5a-129">`foreach` 陳述式會逐一查看 `Elements()` 座標軸，並將新的項目加入到 `doc` 項目。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-129">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="0bc5a-130">它也會透過剛才加入的項目結束反覆運算。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-130">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="0bc5a-131">而且它會利用迴圈的每次反覆運算配置新物件，因此最終會消耗所有可用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-131">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>

<span data-ttu-id="0bc5a-132">您可以使用 <xref:System.Linq.Enumerable.ToList%2A> 標準查詢運算子將集合配置到記憶體，藉以修正這個問題，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0bc5a-132">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements().ToList())
    root.Add(new XElement(e.Name, (string)e));
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements().ToList()
    root.Add(New XElement(e.Name, e.Value))
Next
Console.WriteLine(root)
```

<span data-ttu-id="0bc5a-133">現在，這個程式碼可以運作了。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-133">Now the code works.</span></span> <span data-ttu-id="0bc5a-134">所產生的 XML 樹狀結構如下所示：</span><span class="sxs-lookup"><span data-stu-id="0bc5a-134">The resulting XML tree is the following:</span></span>

```xml
<Root>
  <A>1</A>
  <B>2</B>
  <C>3</C>
  <A>1</A>
  <B>2</B>
  <C>3</C>
</Root>
```

## <a name="example-deleting-while-iterating"></a><span data-ttu-id="0bc5a-135">範例：反覆運算時刪除</span><span class="sxs-lookup"><span data-stu-id="0bc5a-135">Example: Deleting while iterating</span></span>

<span data-ttu-id="0bc5a-136">如果您要在特定的層級刪除所有節點，您可能想要撰寫如下的程式碼：</span><span class="sxs-lookup"><span data-stu-id="0bc5a-136">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements())
    e.Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements()
    e.Remove()
Next
Console.WriteLine(root)
```

<span data-ttu-id="0bc5a-137">不過，這並不是您想要的。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-137">However, this doesn't do what you want.</span></span> <span data-ttu-id="0bc5a-138">在這種情況下，當您移除第一個專案（A）之後，它會從根目錄中包含的 XML 樹狀結構中移除，而 Elements 方法中執行反覆運算的程式碼則找不到下一個元素。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-138">In this situation, after you've removed the first element, A, it's removed from the XML tree contained in root, and the code in the Elements method that does the iterating can't find the next element.</span></span>

<span data-ttu-id="0bc5a-139">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="0bc5a-139">This example produces the following output:</span></span>

```xml
<Root>
  <B>2</B>
  <C>3</C>
</Root>
```

<span data-ttu-id="0bc5a-140">解決方案為呼叫 <xref:System.Linq.Enumerable.ToList%2A> 來具體化集合，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0bc5a-140">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements().ToList())
    e.Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements().ToList()
    e.Remove()
Next
Console.WriteLine(root)
```

<span data-ttu-id="0bc5a-141">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="0bc5a-141">This example produces the following output:</span></span>

```xml
<Root />
```

<span data-ttu-id="0bc5a-142">或者，您可以在父項目上呼叫 <xref:System.Xml.Linq.XElement.RemoveAll%2A>，一起排除反覆運算：</span><span class="sxs-lookup"><span data-stu-id="0bc5a-142">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
root.RemoveAll();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
root.RemoveAll()
Console.WriteLine(root)
```

## <a name="example-why-linq-cant-automatically-handle-these-issues"></a><span data-ttu-id="0bc5a-143">範例：為什麼 LINQ 無法自動處理這些問題</span><span class="sxs-lookup"><span data-stu-id="0bc5a-143">Example: Why LINQ can't automatically handle these issues</span></span>

<span data-ttu-id="0bc5a-144">其中一個方法是，一律將所有項目放入記憶體，而不是進行延遲評估。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-144">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="0bc5a-145">不過，關於效能和記憶體使用率，這將會高度耗費資源。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-145">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="0bc5a-146">事實上，如果 LINQ 和 LINQ to XML 是採用這種方法，在真實世界的情況下會失敗。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-146">In fact, if LINQ, and LINQ to XML, were to take this approach, it would fail in real-world situations.</span></span>

<span data-ttu-id="0bc5a-147">另一個可能的方法是將某種形式的交易語法放到 LINQ 中，並讓編譯器嘗試分析程式碼，以判斷是否需要具體化任何特定的集合。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-147">Another possible approach would be to put some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code to determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="0bc5a-148">不過，嘗試判斷具有副作用的所有程式碼相當複雜。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-148">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="0bc5a-149">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="0bc5a-149">Consider the following code:</span></span>

```csharp
var z =
    from e in root.Elements()
    where TestSomeCondition(e)
    select DoMyProjection(e);
```

```vb
Dim z = _
    From e In root.Elements() _
    Where (TestSomeCondition(e)) _
    Select DoMyProjection(e)
```

<span data-ttu-id="0bc5a-150">此類分析程式碼必須分析 TestSomeCondition 和 DoMyProjection 方法，而且這些方法呼叫的所有方法都必須判斷任何程式碼是否有副作用。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-150">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="0bc5a-151">但是，分析程式碼無法只尋找具有副作用的任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-151">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="0bc5a-152">在此情況下，此分析程式碼必須僅針對 `root` 的子項目上，具有副作用的程式碼進行選取。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-152">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>

<span data-ttu-id="0bc5a-153">LINQ to XML 不會嘗試進行任何這類的分析。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-153">LINQ to XML doesn't attempt to do any such analysis.</span></span> <span data-ttu-id="0bc5a-154">您可以自行避免這些問題。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-154">It's up to you to avoid these problems.</span></span>

## <a name="example-use-declarative-code-to-generate-a-new-xml-tree-rather-than-modify-the-existing-tree"></a><span data-ttu-id="0bc5a-155">範例：使用宣告式程式碼產生新的 XML 樹狀結構，而不是修改現有的樹狀結構</span><span class="sxs-lookup"><span data-stu-id="0bc5a-155">Example: Use declarative code to generate a new XML tree rather than modify the existing tree</span></span>

<span data-ttu-id="0bc5a-156">若要避免這類問題，請不要混用宣告式和命令式程式碼，即使您知道集合的語義以及修改 XML 樹狀結構的方法的語法也是一樣。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-156">To avoid such problems, don't mix declarative and imperative code, even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree.</span></span> <span data-ttu-id="0bc5a-157">如果您撰寫可避免問題的程式碼，則您的程式碼未來將需要由其他開發人員維護，而這些程式碼可能不會對問題造成任何清楚的解決。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-157">If you write code that avoids problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="0bc5a-158">如果您混用宣告式與命令性編碼方式，您的程式碼將更不可靠。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-158">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  <span data-ttu-id="0bc5a-159">如果您撰寫可具體化集合的程式碼，讓這些問題得以避免，請在程式碼中，以適當的註解方式記錄下來，負責維護的程式設計人員就可以了解這個問題。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-159">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>

<span data-ttu-id="0bc5a-160">如果效能和其他考慮允許，請只使用宣告式程式碼。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-160">If performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="0bc5a-161">請勿修改您現有的 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="0bc5a-161">Don't modify your existing XML tree.</span></span> <span data-ttu-id="0bc5a-162">請改為產生一個新的，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0bc5a-162">Instead, generate a new one as shown in the following example:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
XElement newRoot = new XElement("Root",
    root.Elements(),
    root.Elements()
);
Console.WriteLine(newRoot);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
Dim newRoot As XElement = New XElement("Root", _
    root.Elements(), root.Elements())
Console.WriteLine(newRoot)
```
