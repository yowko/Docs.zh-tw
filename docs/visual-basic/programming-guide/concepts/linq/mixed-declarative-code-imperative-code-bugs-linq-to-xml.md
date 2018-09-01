---
title: 混合的宣告式程式碼-命令式程式碼 Bug (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f12b1ab4-bb92-4b92-a648-0525e45b3ce7
ms.openlocfilehash: 797866514a2f290a98d1a75e92f850e96d28dabd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43385603"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-visual-basic"></a><span data-ttu-id="a50d7-102">宣告式程式碼/命令式混合程式碼 Bug (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a50d7-102">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="a50d7-103"> 包含各種方法，可讓您直接修改 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="a50d7-103"> contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="a50d7-104">您可以加入項目、刪除項目、變更項目的內容、加入屬性等等。</span><span class="sxs-lookup"><span data-stu-id="a50d7-104">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="a50d7-105">這個程式發展介面所述[修改 XML 樹狀結構 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="a50d7-105">This programming interface is described in [Modifying XML Trees (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span> <span data-ttu-id="a50d7-106">如果您要逐一查看其中一個座標軸 (例如，<xref:System.Xml.Linq.XContainer.Elements%2A>)，而且您要在逐一查看座標軸時修改 XML 樹狀結構，您可以解決一些奇怪的 Bug。</span><span class="sxs-lookup"><span data-stu-id="a50d7-106">If you are iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you are modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>  
  
 <span data-ttu-id="a50d7-107">這種問題有時候稱為「幽靈問題」。</span><span class="sxs-lookup"><span data-stu-id="a50d7-107">This problem is sometimes known as "The Halloween Problem".</span></span>  
  
## <a name="definition-of-the-problem"></a><span data-ttu-id="a50d7-108">問題的定義</span><span class="sxs-lookup"><span data-stu-id="a50d7-108">Definition of the Problem</span></span>  
 <span data-ttu-id="a50d7-109">當您使用可逐一查看集合的 LINQ 撰寫特定程式碼時，您要以宣告式方法撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="a50d7-109">When you write some code using LINQ that iterates through a collection, you are writing code in a declarative style.</span></span> <span data-ttu-id="a50d7-110">這比較類似於描述您要的是「什麼」，而不是您要「如何」完成。</span><span class="sxs-lookup"><span data-stu-id="a50d7-110">It is more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="a50d7-111">如果您撰寫的程式碼可 1) 取得第一個項目、2) 針對某些條件進行測試、3) 加以修改，以及 4) 將其放回清單中，則這會是命令性程式碼。</span><span class="sxs-lookup"><span data-stu-id="a50d7-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="a50d7-112">您是在告訴電腦「如何」進行您要完成的動作。</span><span class="sxs-lookup"><span data-stu-id="a50d7-112">You are telling the computer *how* to do what you want done.</span></span>  
  
 <span data-ttu-id="a50d7-113">在相同的運算中混用這些程式碼樣式就是導致問題發生的原因。</span><span class="sxs-lookup"><span data-stu-id="a50d7-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="a50d7-114">請考慮下列事項：</span><span class="sxs-lookup"><span data-stu-id="a50d7-114">Consider the following:</span></span>  
  
 <span data-ttu-id="a50d7-115">假設您有一個連結的清單，其中包含三個項目 (a、b 和 c)：</span><span class="sxs-lookup"><span data-stu-id="a50d7-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>  
  
 `a -> b -> c`  
  
 <span data-ttu-id="a50d7-116">現在，假設您要移動連結的清單，以加入三個新項目 (a'、b' 和 c')。</span><span class="sxs-lookup"><span data-stu-id="a50d7-116">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="a50d7-117">您希望所產生的連結清單如下所示：</span><span class="sxs-lookup"><span data-stu-id="a50d7-117">You want the resulting linked list to look like this:</span></span>  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 <span data-ttu-id="a50d7-118">因此，您可以撰寫逐一查看清單的程式碼，然後針對每個項目，將新項目加入到清單的後面。</span><span class="sxs-lookup"><span data-stu-id="a50d7-118">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="a50d7-119">結果是，您的程式碼將會先看到 `a` 項目，然後在其後插入 `a'`。</span><span class="sxs-lookup"><span data-stu-id="a50d7-119">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="a50d7-120">現在，您的程式碼將會移到清單中的下一個節點，而這個節點現在是 `a'`！</span><span class="sxs-lookup"><span data-stu-id="a50d7-120">Now, your code will move to the next node in the list, which is now `a'`!</span></span> <span data-ttu-id="a50d7-121">它會將新項目適當地加入到清單 `a''` 中。</span><span class="sxs-lookup"><span data-stu-id="a50d7-121">It happily adds a new item to the list, `a''`.</span></span>  
  
 <span data-ttu-id="a50d7-122">您在現實世界會如何解決這個問題？</span><span class="sxs-lookup"><span data-stu-id="a50d7-122">How would you solve this in the real world?</span></span> <span data-ttu-id="a50d7-123">您可以複製原始的連結清單，然後建立一個全新的清單。</span><span class="sxs-lookup"><span data-stu-id="a50d7-123">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="a50d7-124">或者，如果您要撰寫純命令性程式碼，您可能會找到第一個項目、加入新項目，然後在連結的清單中往前兩次，超過您剛才加入的項目。</span><span class="sxs-lookup"><span data-stu-id="a50d7-124">Or if you are writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>  
  
## <a name="adding-while-iterating"></a><span data-ttu-id="a50d7-125">反覆運算時加入</span><span class="sxs-lookup"><span data-stu-id="a50d7-125">Adding While Iterating</span></span>  
 <span data-ttu-id="a50d7-126">例如，假設您要針對樹狀結構中的每個項目撰寫特定的程式碼，您會想要建立重複的項目：</span><span class="sxs-lookup"><span data-stu-id="a50d7-126">For example, suppose you want to write some code that for every element in a tree, you want to create a duplicate element:</span></span>  
  
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
  
 <span data-ttu-id="a50d7-127">這個程式碼會進入無限的迴圈。</span><span class="sxs-lookup"><span data-stu-id="a50d7-127">This code goes into an infinite loop.</span></span> <span data-ttu-id="a50d7-128">`foreach` 陳述式會逐一查看 `Elements()` 座標軸，並將新的項目加入到 `doc` 項目。</span><span class="sxs-lookup"><span data-stu-id="a50d7-128">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="a50d7-129">它也會透過剛才加入的項目結束反覆運算。</span><span class="sxs-lookup"><span data-stu-id="a50d7-129">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="a50d7-130">而且它會利用迴圈的每次反覆運算配置新物件，因此最終會消耗所有可用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="a50d7-130">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>  
  
 <span data-ttu-id="a50d7-131">您可以使用 <xref:System.Linq.Enumerable.ToList%2A> 標準查詢運算子將集合配置到記憶體，藉以修正這個問題，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a50d7-131">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>  
  
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
  
 <span data-ttu-id="a50d7-132">現在，這個程式碼可以運作了。</span><span class="sxs-lookup"><span data-stu-id="a50d7-132">Now the code works.</span></span> <span data-ttu-id="a50d7-133">所產生的 XML 樹狀結構如下所示：</span><span class="sxs-lookup"><span data-stu-id="a50d7-133">The resulting XML tree is the following:</span></span>  
  
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
  
## <a name="deleting-while-iterating"></a><span data-ttu-id="a50d7-134">反覆運算時刪除</span><span class="sxs-lookup"><span data-stu-id="a50d7-134">Deleting While Iterating</span></span>  
 <span data-ttu-id="a50d7-135">如果您要在特定的層級刪除所有節點，您可能想要撰寫如下的程式碼：</span><span class="sxs-lookup"><span data-stu-id="a50d7-135">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>  
  
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
  
 <span data-ttu-id="a50d7-136">不過，這不會執行您想要的動作。</span><span class="sxs-lookup"><span data-stu-id="a50d7-136">However, this does not do what you want.</span></span> <span data-ttu-id="a50d7-137">在這個情況下，當您移除第一個項目 A 後，該項目就會從根目錄中所包含的 XML 樹狀結構移除，而負責進行反覆運算之 Elements 方法中的程式碼則找不到下一個項目。</span><span class="sxs-lookup"><span data-stu-id="a50d7-137">In this situation, after you have removed the first element, A, it is removed from the XML tree contained in root, and the code in the Elements method that is doing the iterating cannot find the next element.</span></span>  
  
 <span data-ttu-id="a50d7-138">前一個程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="a50d7-138">The preceding code produces the following output:</span></span>  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 <span data-ttu-id="a50d7-139">解決方案為呼叫 <xref:System.Linq.Enumerable.ToList%2A> 來具體化集合，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a50d7-139">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>  
  
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
  
 <span data-ttu-id="a50d7-140">這會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="a50d7-140">This produces the following output:</span></span>  
  
```xml  
<Root />  
```  
  
 <span data-ttu-id="a50d7-141">或者，您可以在父項目上呼叫 <xref:System.Xml.Linq.XElement.RemoveAll%2A>，一起排除反覆運算：</span><span class="sxs-lookup"><span data-stu-id="a50d7-141">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>  
  
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
  
## <a name="why-cant-linq-automatically-handle-this"></a><span data-ttu-id="a50d7-142">為什麼 LINQ 無法自動處理這個情況？</span><span class="sxs-lookup"><span data-stu-id="a50d7-142">Why Can't LINQ Automatically Handle This?</span></span>  
 <span data-ttu-id="a50d7-143">其中一個方法是，一律將所有項目放入記憶體，而不是進行延遲評估。</span><span class="sxs-lookup"><span data-stu-id="a50d7-143">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="a50d7-144">不過，關於效能和記憶體使用率，這將會高度耗費資源。</span><span class="sxs-lookup"><span data-stu-id="a50d7-144">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="a50d7-145">事實上，如果 LINQ 和 (LINQ to XML) 要採取這個方法，在實際的情況下將會失敗。</span><span class="sxs-lookup"><span data-stu-id="a50d7-145">In fact, if LINQ and (LINQ to XML) were to take this approach, it would fail in real-world situations.</span></span>  
  
 <span data-ttu-id="a50d7-146">另一個可能的方法是將特定類型的交易語法放入 LINQ 中，然後讓編譯器嘗試分析程式碼，並判斷是否需要將任何特定集合具體化。</span><span class="sxs-lookup"><span data-stu-id="a50d7-146">Another possible approach would be to put in some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code and determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="a50d7-147">不過，嘗試判斷具有副作用的所有程式碼相當複雜。</span><span class="sxs-lookup"><span data-stu-id="a50d7-147">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="a50d7-148">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="a50d7-148">Consider the following code:</span></span>  
  
```vb  
Dim z = _  
    From e In root.Elements() _  
    Where (TestSomeCondition(e)) _  
    Select DoMyProjection(e)  
```  
  
 <span data-ttu-id="a50d7-149">此類分析程式碼必須分析 TestSomeCondition 和 DoMyProjection 方法，而且這些方法呼叫的所有方法都必須判斷任何程式碼是否有副作用。</span><span class="sxs-lookup"><span data-stu-id="a50d7-149">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="a50d7-150">但是，分析程式碼無法只尋找具有副作用的任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="a50d7-150">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="a50d7-151">在此情況下，此分析程式碼必須僅針對 `root` 的子項目上，具有副作用的程式碼進行選取。</span><span class="sxs-lookup"><span data-stu-id="a50d7-151">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>  
  
 <span data-ttu-id="a50d7-152">LINQ to XML 不會嘗試執行此類分析。</span><span class="sxs-lookup"><span data-stu-id="a50d7-152">LINQ to XML does not attempt to do any such analysis.</span></span>  
  
 <span data-ttu-id="a50d7-153">您可以選擇避免這些問題。</span><span class="sxs-lookup"><span data-stu-id="a50d7-153">It is up to you to avoid these problems.</span></span>  
  
## <a name="guidance"></a><span data-ttu-id="a50d7-154">指引</span><span class="sxs-lookup"><span data-stu-id="a50d7-154">Guidance</span></span>  
 <span data-ttu-id="a50d7-155">首先，請勿混用宣告式與命令性程式碼。</span><span class="sxs-lookup"><span data-stu-id="a50d7-155">First, do not mix declarative and imperative code.</span></span>  
  
 <span data-ttu-id="a50d7-156">即使您完全了解集合的語意以及修改 XML 樹狀結構之方法的語意，如果您要撰寫可避免這些類別之問題的聰明程式碼，您的程式碼未來將需要由其他開發人員維護，而且他們對於這些問題可能不是那麼清楚。</span><span class="sxs-lookup"><span data-stu-id="a50d7-156">Even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree, if you write some clever code that avoids these categories of problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="a50d7-157">如果您混用宣告式與命令性編碼方式，您的程式碼將更不可靠。</span><span class="sxs-lookup"><span data-stu-id="a50d7-157">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  
  
 <span data-ttu-id="a50d7-158">如果您撰寫可具體化集合的程式碼，讓這些問題得以避免，請在程式碼中，以適當的註解方式記錄下來，負責維護的程式設計人員就可以了解這個問題。</span><span class="sxs-lookup"><span data-stu-id="a50d7-158">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>  
  
 <span data-ttu-id="a50d7-159">接著，如果效能和其他考量允許，請只使用宣告式程式碼。</span><span class="sxs-lookup"><span data-stu-id="a50d7-159">Second, if performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="a50d7-160">請勿修改您現有的 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="a50d7-160">Don't modify your existing XML tree.</span></span> <span data-ttu-id="a50d7-161">產生一個新的 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="a50d7-161">Generate a new one.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a50d7-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a50d7-162">See Also</span></span>  
 [<span data-ttu-id="a50d7-163">進階的 LINQ to XML 程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a50d7-163">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
