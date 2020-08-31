---
title: 如何：新增 LINQ 查詢的自訂方法
ms.date: 08/28/2020
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
ms.openlocfilehash: 7d38a45263135fa10dc53dc0d09b8129838e78e6
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89117775"
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a><span data-ttu-id="38a66-102">如何：新增 LINQ 查詢的自訂方法 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="38a66-102">How to: Add custom methods for LINQ queries (Visual Basic)</span></span>

<span data-ttu-id="38a66-103">您可以藉由將擴充方法加入至介面，來擴充您用於 LINQ 查詢的方法集合 <xref:System.Collections.Generic.IEnumerable%601> 。</span><span class="sxs-lookup"><span data-stu-id="38a66-103">You extend the set of methods that you use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="38a66-104">例如，除了標準平均或最大作業之外，您還可以建立自訂匯總方法來計算值序列中的單一值。</span><span class="sxs-lookup"><span data-stu-id="38a66-104">For example, in addition to the standard average or maximum operations, you create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="38a66-105">您也會建立一個方法，以做為自訂篩選或一系列值的特定資料轉換，並傳回新的序列。</span><span class="sxs-lookup"><span data-stu-id="38a66-105">You also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="38a66-106">這類方法的範例包括 <xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Reverse%2A>。</span><span class="sxs-lookup"><span data-stu-id="38a66-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="38a66-107">當您延伸 <xref:System.Collections.Generic.IEnumerable%601> 介面時，可將自訂方法套用至任何可列舉的集合。</span><span class="sxs-lookup"><span data-stu-id="38a66-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="38a66-108">如需詳細資訊，請參閱[擴充方法](../../language-features/procedures/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="38a66-108">For more information, see [Extension Methods](../../language-features/procedures/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="38a66-109">新增匯總方法</span><span class="sxs-lookup"><span data-stu-id="38a66-109">Adding an aggregate method</span></span>

<span data-ttu-id="38a66-110">彙總方法會計算一組值的單一值。</span><span class="sxs-lookup"><span data-stu-id="38a66-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="38a66-111">LINQ 提供數種彙總方法，包括 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Min%2A> 和 <xref:System.Linq.Enumerable.Max%2A>。</span><span class="sxs-lookup"><span data-stu-id="38a66-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="38a66-112">您可將擴充方法新增至 <xref:System.Collections.Generic.IEnumerable%601> 介面，建立自己的彙總方法。</span><span class="sxs-lookup"><span data-stu-id="38a66-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="38a66-113">下列程式碼範例示範如何建立呼叫 `Median` 的擴充方法，來計算一系列類型為 `double` 的中位數。</span><span class="sxs-lookup"><span data-stu-id="38a66-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

:::code language="vb" source="./snippets/LinqExtension.vb" :::

<span data-ttu-id="38a66-114">您可以使用從 <xref:System.Collections.Generic.IEnumerable%601> 介面呼叫其他彙總方法同樣的方式，為任何可列舉集合呼叫此擴充方法。</span><span class="sxs-lookup"><span data-stu-id="38a66-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

> [!NOTE]
> <span data-ttu-id="38a66-115">在 Visual Basic 中，您可以針對或子句使用方法呼叫或標準查詢語法 `Aggregate` `Group By` 。</span><span class="sxs-lookup"><span data-stu-id="38a66-115">In Visual Basic, you can either use a method call or standard query syntax for the `Aggregate` or `Group By` clause.</span></span> <span data-ttu-id="38a66-116">如需詳細資訊，請參閱 [Aggregate 子句](../../../language-reference/queries/aggregate-clause.md) 和 [group by 子句](../../../language-reference/queries/group-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="38a66-116">For more information, see [Aggregate Clause](../../../language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../language-reference/queries/group-by-clause.md).</span></span>

<span data-ttu-id="38a66-117">下列程式碼範例示範如何使用 `Median` 方法處理 `double` 類型的陣列。</span><span class="sxs-lookup"><span data-stu-id="38a66-117">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

:::code language="vb" source="./snippets/Program.vb" ID="MedianUsage":::

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="38a66-118">多載匯總方法以接受各種類型</span><span class="sxs-lookup"><span data-stu-id="38a66-118">Overloading an aggregate method to accept various types</span></span>

<span data-ttu-id="38a66-119">您可以多載自己的彙總方法，讓它接受各種類型的序列。</span><span class="sxs-lookup"><span data-stu-id="38a66-119">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="38a66-120">標準方法是為每種類型建立多載。</span><span class="sxs-lookup"><span data-stu-id="38a66-120">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="38a66-121">另一種方法是建立採用泛型型別的多載，使用委派將它轉換成特定的類型。</span><span class="sxs-lookup"><span data-stu-id="38a66-121">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="38a66-122">您也可以結合這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="38a66-122">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="38a66-123">為每種類型建立多載</span><span class="sxs-lookup"><span data-stu-id="38a66-123">To create an overload for each type</span></span>

<span data-ttu-id="38a66-124">您可以為想要支援的每種類型建立特定的多載。</span><span class="sxs-lookup"><span data-stu-id="38a66-124">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="38a66-125">下列程式碼範例示範適合 `integer` 類型之 `Median` 方法的多載。</span><span class="sxs-lookup"><span data-stu-id="38a66-125">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

:::code language="vb" source="./snippets/OtherExtensions.vb" ID="IntOverload":::

<span data-ttu-id="38a66-126">您現在可以呼叫 `integer` 和 `double` 類型的 `Median` 多載，如下列程式碼所示︰</span><span class="sxs-lookup"><span data-stu-id="38a66-126">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

:::code language="vb" source="./snippets/Program.vb" ID="OverloadUsage":::

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="38a66-127">建立一般多載</span><span class="sxs-lookup"><span data-stu-id="38a66-127">To create a generic overload</span></span>

<span data-ttu-id="38a66-128">您也可以建立接受一系列泛型物件的多載。</span><span class="sxs-lookup"><span data-stu-id="38a66-128">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="38a66-129">這個多載會接受委派作為參數，並使用它將泛型型別物件的序列轉換成特定的類型。</span><span class="sxs-lookup"><span data-stu-id="38a66-129">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="38a66-130">下列程式碼顯示 `Median` 方法的多載，接受 <xref:System.Func%602> 委派為參數。</span><span class="sxs-lookup"><span data-stu-id="38a66-130">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="38a66-131">這個委派會採用泛型型別的物件 `T` ，並傳回型別的物件 `double` 。</span><span class="sxs-lookup"><span data-stu-id="38a66-131">This delegate takes an object of generic type `T` and returns an object of type `double`.</span></span>

:::code language="vb" source="./snippets/OtherExtensions.vb" ID="GenericOverload":::

<span data-ttu-id="38a66-132">您現在可以針對一系列的類型物件呼叫 `Median` 方法。</span><span class="sxs-lookup"><span data-stu-id="38a66-132">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="38a66-133">如果類型沒有自己的方法多載，您就必須傳遞委派參數。</span><span class="sxs-lookup"><span data-stu-id="38a66-133">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="38a66-134">在 Visual Basic 中，您可以針對此用途使用 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="38a66-134">In Visual Basic, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="38a66-135">此外，如果您使用 `Aggregate` 或 `Group By` 子句，而不是方法呼叫，您可以傳遞此子句範圍內的任何值或運算式。</span><span class="sxs-lookup"><span data-stu-id="38a66-135">Also, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="38a66-136">下列程式碼範例示範如何呼叫 `Median` 方法，處理整數陣列及字串陣列。</span><span class="sxs-lookup"><span data-stu-id="38a66-136">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="38a66-137">針對字串，會計算陣列字串長度的中間值。</span><span class="sxs-lookup"><span data-stu-id="38a66-137">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="38a66-138">此範例會示範如何將 <xref:System.Func%602> 委派參數傳遞至每個案例的 `Median` 方法。</span><span class="sxs-lookup"><span data-stu-id="38a66-138">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

:::code language="vb" source="./snippets/Program.vb" ID="GenericUsage":::

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="38a66-139">新增傳回集合的方法</span><span class="sxs-lookup"><span data-stu-id="38a66-139">Adding a method that returns a collection</span></span>

<span data-ttu-id="38a66-140">您可以使用傳回一系列值的自訂查詢方法來延伸 <xref:System.Collections.Generic.IEnumerable%601> 介面。</span><span class="sxs-lookup"><span data-stu-id="38a66-140">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="38a66-141">在此情況下，方法必須傳回型別 <xref:System.Collections.Generic.IEnumerable%601> 的集合。</span><span class="sxs-lookup"><span data-stu-id="38a66-141">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="38a66-142">此等方法可用來將篩選條件或資料轉換套用至一系列的值。</span><span class="sxs-lookup"><span data-stu-id="38a66-142">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="38a66-143">下例示範如何建立名為 `AlternateElements` 的擴充方法，傳回集合中的每隔個項目，從第一個項目開始。</span><span class="sxs-lookup"><span data-stu-id="38a66-143">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

:::code language="vb" source="./snippets/OtherExtensions.vb" ID="SequenceElement":::

<span data-ttu-id="38a66-144">您可為任何可列舉集合呼叫此擴充方法，就和您從 <xref:System.Collections.Generic.IEnumerable%601> 介面呼叫其他方法一樣，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="38a66-144">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

:::code language="vb" source="./snippets/Program.vb" ID="SequenceUsage":::

## <a name="see-also"></a><span data-ttu-id="38a66-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38a66-145">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="38a66-146">擴充方法</span><span class="sxs-lookup"><span data-stu-id="38a66-146">Extension Methods</span></span>](../../language-features/procedures/extension-methods.md)
