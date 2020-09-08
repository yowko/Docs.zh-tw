---
title: XPath 和 LINQ to XML LINQ to XML 的比較
description: XPath 和 LINQ to XML 查詢都可以查詢 XML 樹狀結構。 本文將比較這兩個選項，並尋找 LINQ to XML 的查詢，這些都是最強大、多用途、更快速、更方便的選擇。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: b98651ffd7e0df0057164f40bedbc43d654d8c81
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552248"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a><span data-ttu-id="3e127-104">XPath 和 LINQ to XML 的比較</span><span class="sxs-lookup"><span data-stu-id="3e127-104">Comparison of XPath and LINQ to XML</span></span>

<span data-ttu-id="3e127-105">XPath 和 LINQ to XML 在某些方面很類似。</span><span class="sxs-lookup"><span data-stu-id="3e127-105">XPath and LINQ to XML are similar in some ways.</span></span> <span data-ttu-id="3e127-106">兩者都可用於查詢 XML 樹狀結構，將此類結果當做項目的集合、屬性的集合、節點的集合，以及項目或屬性的值傳回。</span><span class="sxs-lookup"><span data-stu-id="3e127-106">Both can be used to query an XML tree, returning such results as a collection of elements, a collection of attributes, a collection of nodes, or the value of an element or attribute.</span></span> <span data-ttu-id="3e127-107">不過，這兩個選項之間有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="3e127-107">However, there are significant differences between the two options.</span></span>

## <a name="differences-between-xpath-and-linq-to-xml"></a><span data-ttu-id="3e127-108">XPath 與 LINQ to XML 之間的差異</span><span class="sxs-lookup"><span data-stu-id="3e127-108">Differences between XPath and LINQ to XML</span></span>

<span data-ttu-id="3e127-109">XPath 不允許投影新的類型。</span><span class="sxs-lookup"><span data-stu-id="3e127-109">XPath doesn't allow projection of new types.</span></span> <span data-ttu-id="3e127-110">它只能從樹狀結構傳回節點的集合，而 LINQ to XML 可以執行查詢並評估新圖案中的物件圖形或 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="3e127-110">It can only return collections of nodes from the tree, whereas LINQ to XML can execute a query and project an object graph or an XML tree in a new shape.</span></span> <span data-ttu-id="3e127-111">LINQ to XML 查詢可以比 XPath 運算式更多。</span><span class="sxs-lookup"><span data-stu-id="3e127-111">LINQ to XML queries can do much more than XPath expressions.</span></span>

<span data-ttu-id="3e127-112">XPath 運算式存在於字串內的隔離中。</span><span class="sxs-lookup"><span data-stu-id="3e127-112">XPath expressions exist in isolation within a string.</span></span> <span data-ttu-id="3e127-113">C # 編譯器無法在編譯時期協助剖析 XPath 運算式。</span><span class="sxs-lookup"><span data-stu-id="3e127-113">The C# compiler can't help parse the XPath expression at compile time.</span></span> <span data-ttu-id="3e127-114">相較之下，C# 編譯器會剖析與編譯 LINQ to XML 查詢。</span><span class="sxs-lookup"><span data-stu-id="3e127-114">By contrast, LINQ to XML queries are parsed and compiled by the C# compiler.</span></span> <span data-ttu-id="3e127-115">編譯器可能會攔截許多查詢錯誤。</span><span class="sxs-lookup"><span data-stu-id="3e127-115">The compiler can catch many query errors.</span></span>

<span data-ttu-id="3e127-116">XPath 結果不是強型別。</span><span class="sxs-lookup"><span data-stu-id="3e127-116">XPath results aren't strongly typed.</span></span> <span data-ttu-id="3e127-117">在許多情況下，評估 XPath 運算式的結果是一個物件，而開發人員可以決定適當的類型，並視需要轉換結果。</span><span class="sxs-lookup"><span data-stu-id="3e127-117">In a number of circumstances, the result of evaluating an XPath expression is an object, and it's up to the developer to determine the proper type and cast the result as necessary.</span></span> <span data-ttu-id="3e127-118">相較之下，LINQ to XML 查詢的評估為強型別。</span><span class="sxs-lookup"><span data-stu-id="3e127-118">By contrast, the projections from a LINQ to XML query are strongly typed.</span></span>

## <a name="result-ordering"></a><span data-ttu-id="3e127-119">結果排序</span><span class="sxs-lookup"><span data-stu-id="3e127-119">Result ordering</span></span>

<span data-ttu-id="3e127-120">XPath 1.0 建議事項指出評估 XPath 運算式結果的集合未排序。</span><span class="sxs-lookup"><span data-stu-id="3e127-120">The XPath 1.0 Recommendation states that a collection that's the result of evaluating an XPath expression is unordered.</span></span>

<span data-ttu-id="3e127-121">不過，逐一查看由 LINQ to XML XPath 軸方法傳回的集合時，會以文件順序傳回集合中的節點。</span><span class="sxs-lookup"><span data-stu-id="3e127-121">However, when iterating through a collection returned by a LINQ to XML XPath axis method, the nodes in the collection are returned in document order.</span></span> <span data-ttu-id="3e127-122">即使在存取 XPath 軸 (其中的述詞會根據反向的文件順序表示，例如，`preceding` 和 `preceding-sibling`) 時，也是如此。</span><span class="sxs-lookup"><span data-stu-id="3e127-122">This is the case even when accessing the XPath axes where predicates are expressed in terms of reverse document order, such as `preceding` and `preceding-sibling`.</span></span>

<span data-ttu-id="3e127-123">相較之下，大部分的 LINQ to XML 軸會以檔順序傳回集合。</span><span class="sxs-lookup"><span data-stu-id="3e127-123">By contrast, most of the LINQ to XML axes return collections in document order.</span></span> <span data-ttu-id="3e127-124">但是，其中的兩個 <xref:System.Xml.Linq.XNode.Ancestors%2A> 和會 <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A> 以反向檔順序傳回集合。</span><span class="sxs-lookup"><span data-stu-id="3e127-124">However, two of them, <xref:System.Xml.Linq.XNode.Ancestors%2A> and <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, return collections in reverse document order.</span></span> <span data-ttu-id="3e127-125">下表列舉座標軸，並指出每個軸的收集順序：</span><span class="sxs-lookup"><span data-stu-id="3e127-125">The following table enumerates the axes, and indicates the collection order for each:</span></span>

|<span data-ttu-id="3e127-126">LINQ to XML 軸</span><span class="sxs-lookup"><span data-stu-id="3e127-126">LINQ to XML axis</span></span>|<span data-ttu-id="3e127-127">排序</span><span class="sxs-lookup"><span data-stu-id="3e127-127">Ordering</span></span>|
|----------------------|--------------|
|<span data-ttu-id="3e127-128">XContainer.DescendantNodes</span><span class="sxs-lookup"><span data-stu-id="3e127-128">XContainer.DescendantNodes</span></span>|<span data-ttu-id="3e127-129">文件順序</span><span class="sxs-lookup"><span data-stu-id="3e127-129">Document order</span></span>|
|<span data-ttu-id="3e127-130">XContainer.Descendants</span><span class="sxs-lookup"><span data-stu-id="3e127-130">XContainer.Descendants</span></span>|<span data-ttu-id="3e127-131">文件順序</span><span class="sxs-lookup"><span data-stu-id="3e127-131">Document order</span></span>|
|<span data-ttu-id="3e127-132">XContainer.Elements</span><span class="sxs-lookup"><span data-stu-id="3e127-132">XContainer.Elements</span></span>|<span data-ttu-id="3e127-133">文件順序</span><span class="sxs-lookup"><span data-stu-id="3e127-133">Document order</span></span>|
|<span data-ttu-id="3e127-134">XContainer.Nodes</span><span class="sxs-lookup"><span data-stu-id="3e127-134">XContainer.Nodes</span></span>|<span data-ttu-id="3e127-135">文件順序</span><span class="sxs-lookup"><span data-stu-id="3e127-135">Document order</span></span>|
|<span data-ttu-id="3e127-136">XContainer.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="3e127-136">XContainer.NodesAfterSelf</span></span>|<span data-ttu-id="3e127-137">文件順序</span><span class="sxs-lookup"><span data-stu-id="3e127-137">Document order</span></span>|
|<span data-ttu-id="3e127-138">XContainer.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="3e127-138">XContainer.NodesBeforeSelf</span></span>|<span data-ttu-id="3e127-139">文件順序</span><span class="sxs-lookup"><span data-stu-id="3e127-139">Document order</span></span>|
|<span data-ttu-id="3e127-140">XElement.AncestorsAndSelf</span><span class="sxs-lookup"><span data-stu-id="3e127-140">XElement.AncestorsAndSelf</span></span>|<span data-ttu-id="3e127-141">反向的文件順序</span><span class="sxs-lookup"><span data-stu-id="3e127-141">Reverse document order</span></span>|
|<span data-ttu-id="3e127-142">XElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="3e127-142">XElement.Attributes</span></span>|<span data-ttu-id="3e127-143">文件順序</span><span class="sxs-lookup"><span data-stu-id="3e127-143">Document order</span></span>|
|<span data-ttu-id="3e127-144">XElement.DescendantNodesAndSelf</span><span class="sxs-lookup"><span data-stu-id="3e127-144">XElement.DescendantNodesAndSelf</span></span>|<span data-ttu-id="3e127-145">文件順序</span><span class="sxs-lookup"><span data-stu-id="3e127-145">Document order</span></span>|
|<span data-ttu-id="3e127-146">XElement.DescendantsAndSelf</span><span class="sxs-lookup"><span data-stu-id="3e127-146">XElement.DescendantsAndSelf</span></span>|<span data-ttu-id="3e127-147">文件順序</span><span class="sxs-lookup"><span data-stu-id="3e127-147">Document order</span></span>|
|<span data-ttu-id="3e127-148">XNode.Ancestors</span><span class="sxs-lookup"><span data-stu-id="3e127-148">XNode.Ancestors</span></span>|<span data-ttu-id="3e127-149">反向的文件順序</span><span class="sxs-lookup"><span data-stu-id="3e127-149">Reverse document order</span></span>|
|<span data-ttu-id="3e127-150">XNode.ElementsAfterSelf</span><span class="sxs-lookup"><span data-stu-id="3e127-150">XNode.ElementsAfterSelf</span></span>|<span data-ttu-id="3e127-151">文件順序</span><span class="sxs-lookup"><span data-stu-id="3e127-151">Document order</span></span>|
|<span data-ttu-id="3e127-152">XNode.ElementsBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="3e127-152">XNode.ElementsBeforeSelf</span></span>|<span data-ttu-id="3e127-153">文件順序</span><span class="sxs-lookup"><span data-stu-id="3e127-153">Document order</span></span>|
|<span data-ttu-id="3e127-154">XNode.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="3e127-154">XNode.NodesAfterSelf</span></span>|<span data-ttu-id="3e127-155">文件順序</span><span class="sxs-lookup"><span data-stu-id="3e127-155">Document order</span></span>|
|<span data-ttu-id="3e127-156">XNode.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="3e127-156">XNode.NodesBeforeSelf</span></span>|<span data-ttu-id="3e127-157">文件順序</span><span class="sxs-lookup"><span data-stu-id="3e127-157">Document order</span></span>|

## <a name="positional-predicates"></a><span data-ttu-id="3e127-158">位置述詞</span><span class="sxs-lookup"><span data-stu-id="3e127-158">Positional predicates</span></span>

<span data-ttu-id="3e127-159">在 XPath 運算式中，位置述詞會以檔順序表示許多座標軸，但以反向軸的反向檔順序表示。</span><span class="sxs-lookup"><span data-stu-id="3e127-159">Within an XPath expression, positional predicates are expressed in terms of document order for many axes, but are expressed in reverse document order for reverse axes.</span></span> <span data-ttu-id="3e127-160">反向軸如下： `preceding` 、 `preceding-sibling` 、 `ancestor` 和 `ancestor-or-self` 。</span><span class="sxs-lookup"><span data-stu-id="3e127-160">The reverse axes are: `preceding`, `preceding-sibling`, `ancestor`, and `ancestor-or-self`.</span></span> <span data-ttu-id="3e127-161">例如，XPath 運算式 `preceding-sibling::*[1]` 會傳回正前面的同層級。</span><span class="sxs-lookup"><span data-stu-id="3e127-161">For example, the XPath expression `preceding-sibling::*[1]` returns the immediately preceding sibling.</span></span> <span data-ttu-id="3e127-162">即使最後的結果集會以文件順序呈現，也是如此。</span><span class="sxs-lookup"><span data-stu-id="3e127-162">This is the case even though the final result set is presented in document order.</span></span>

<span data-ttu-id="3e127-163">相較之下，LINQ to XML 中的所有位置性述詞都一律會以座標軸的順序表示。</span><span class="sxs-lookup"><span data-stu-id="3e127-163">By contrast, all positional predicates in LINQ to XML are always expressed in terms of the order of the axis.</span></span> <span data-ttu-id="3e127-164">例如，`anElement.ElementsBeforeSelf().ElementAt(0)` 會傳回所查詢項目之父代的第一個子項目，而非正前面的同層級。</span><span class="sxs-lookup"><span data-stu-id="3e127-164">For example, `anElement.ElementsBeforeSelf().ElementAt(0)` returns the first child element of the parent of the queried element, not the immediate preceding sibling.</span></span> <span data-ttu-id="3e127-165">另一個範例：`anElement.Ancestors().ElementAt(0)` 會傳回父項目。</span><span class="sxs-lookup"><span data-stu-id="3e127-165">Another example: `anElement.Ancestors().ElementAt(0)` returns the parent element.</span></span>

<span data-ttu-id="3e127-166">如果您要在 LINQ to XML 中尋找正前面的項目，您可以撰寫下列運算式：</span><span class="sxs-lookup"><span data-stu-id="3e127-166">If you wanted to find the immediately preceding element in LINQ to XML, you would write the following expression:</span></span>

```csharp
ElementsBeforeSelf().Last()
```

```vb
ElementsBeforeSelf().Last()
```

## <a name="performance-differences"></a><span data-ttu-id="3e127-167">效能差異</span><span class="sxs-lookup"><span data-stu-id="3e127-167">Performance differences</span></span>

<span data-ttu-id="3e127-168">在 LINQ to XML 中使用 XPath 功能的 XPath 查詢將會比 LINQ to XML 查詢慢。</span><span class="sxs-lookup"><span data-stu-id="3e127-168">XPath queries that use the XPath functionality in LINQ to XML will be slower than LINQ to XML queries.</span></span>

## <a name="comparison-of-composition"></a><span data-ttu-id="3e127-169">組合的比較</span><span class="sxs-lookup"><span data-stu-id="3e127-169">Comparison of composition</span></span>

<span data-ttu-id="3e127-170">LINQ to XML 查詢的組合類似于 XPath 運算式的組合，但是語法非常不同。</span><span class="sxs-lookup"><span data-stu-id="3e127-170">Composition of a LINQ to XML query is similar to composition of an XPath expression, but the syntax is very different.</span></span>

<span data-ttu-id="3e127-171">例如，如果您在名為的變數中有一個專案 `customers` ，而您想要在名為的所有子項目底下尋找名為的孫元素 `CompanyName` `Customer` ，您可以撰寫此 XPath 運算式：</span><span class="sxs-lookup"><span data-stu-id="3e127-171">For example, if you have an element in a variable named `customers`, and you want to find a grandchild element named `CompanyName` under all child elements named `Customer`, you would write this XPath expression:</span></span>

```csharp
customers.XPathSelectElements("./Customer/CompanyName")
```

```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

<span data-ttu-id="3e127-172">對等的 LINQ to XML 查詢為：</span><span class="sxs-lookup"><span data-stu-id="3e127-172">The equivalent LINQ to XML query is:</span></span>

```csharp
customers.Elements("Customer").Elements("CompanyName")
```

```vb
customers.Elements("Customer").Elements("CompanyName")
```

<span data-ttu-id="3e127-173">每個 XPath 座標軸都有類似的項目。</span><span class="sxs-lookup"><span data-stu-id="3e127-173">There are similar parallels for each of the XPath axes.</span></span>

|<span data-ttu-id="3e127-174">XPath 座標軸</span><span class="sxs-lookup"><span data-stu-id="3e127-174">XPath axis</span></span>|<span data-ttu-id="3e127-175">LINQ to XML 軸</span><span class="sxs-lookup"><span data-stu-id="3e127-175">LINQ to XML axis</span></span>|
|----------------|----------------------|
|<span data-ttu-id="3e127-176">child (預設軸)</span><span class="sxs-lookup"><span data-stu-id="3e127-176">child (the default axis)</span></span>|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|
|<span data-ttu-id="3e127-177">Parent (..)</span><span class="sxs-lookup"><span data-stu-id="3e127-177">Parent (..)</span></span>|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|
|<span data-ttu-id="3e127-178">attribute 軸 (@)</span><span class="sxs-lookup"><span data-stu-id="3e127-178">attribute axis (@)</span></span>|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="3e127-179">或</span><span class="sxs-lookup"><span data-stu-id="3e127-179">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|
|<span data-ttu-id="3e127-180">ancestor 軸</span><span class="sxs-lookup"><span data-stu-id="3e127-180">ancestor axis</span></span>|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|
|<span data-ttu-id="3e127-181">ancestor-or-self 軸</span><span class="sxs-lookup"><span data-stu-id="3e127-181">ancestor-or-self axis</span></span>|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|
|<span data-ttu-id="3e127-182">descendant 軸 (//)</span><span class="sxs-lookup"><span data-stu-id="3e127-182">descendant axis (//)</span></span>|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="3e127-183">或</span><span class="sxs-lookup"><span data-stu-id="3e127-183">or</span></span><br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|
|<span data-ttu-id="3e127-184">descendant-or-self</span><span class="sxs-lookup"><span data-stu-id="3e127-184">descendant-or-self</span></span>|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="3e127-185">或</span><span class="sxs-lookup"><span data-stu-id="3e127-185">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|
|<span data-ttu-id="3e127-186">following-sibling</span><span class="sxs-lookup"><span data-stu-id="3e127-186">following-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="3e127-187">或</span><span class="sxs-lookup"><span data-stu-id="3e127-187">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|
|<span data-ttu-id="3e127-188">preceding-sibling</span><span class="sxs-lookup"><span data-stu-id="3e127-188">preceding-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="3e127-189">或</span><span class="sxs-lookup"><span data-stu-id="3e127-189">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|
|<span data-ttu-id="3e127-190">following</span><span class="sxs-lookup"><span data-stu-id="3e127-190">following</span></span>|<span data-ttu-id="3e127-191">沒有直接的對等。</span><span class="sxs-lookup"><span data-stu-id="3e127-191">No direct equivalent.</span></span>|
|<span data-ttu-id="3e127-192">preceding</span><span class="sxs-lookup"><span data-stu-id="3e127-192">preceding</span></span>|<span data-ttu-id="3e127-193">沒有直接的對等。</span><span class="sxs-lookup"><span data-stu-id="3e127-193">No direct equivalent.</span></span>|
