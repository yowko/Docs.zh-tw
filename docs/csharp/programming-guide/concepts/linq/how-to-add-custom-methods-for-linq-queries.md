---
title: '如何新增 LINQ 查詢的自訂方法 (c # ) '
description: '瞭解如何 <T> 在 c # 中將擴充方法加入至 IEnumerable 介面，以擴充 LINQ 查詢的語法。'
ms.date: 08/26/2020
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: 768882fce40a2fc6e018f24c8928341e7c65bc4b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89122421"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a><span data-ttu-id="5111f-103">如何新增 LINQ 查詢的自訂方法 (c # ) </span><span class="sxs-lookup"><span data-stu-id="5111f-103">How to add custom methods for LINQ queries (C#)</span></span>

<span data-ttu-id="5111f-104">您可以藉由將擴充方法加入至介面，來擴充您用於 LINQ 查詢的方法集合 <xref:System.Collections.Generic.IEnumerable%601> 。</span><span class="sxs-lookup"><span data-stu-id="5111f-104">You extend the set of methods that you use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="5111f-105">例如，除了標準平均或最大作業之外，您還可以建立自訂匯總方法來計算值序列中的單一值。</span><span class="sxs-lookup"><span data-stu-id="5111f-105">For example, in addition to the standard average or maximum operations, you create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="5111f-106">您也會建立一個方法，以做為自訂篩選或一系列值的特定資料轉換，並傳回新的序列。</span><span class="sxs-lookup"><span data-stu-id="5111f-106">You also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="5111f-107">這類方法的範例包括 <xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Reverse%2A>。</span><span class="sxs-lookup"><span data-stu-id="5111f-107">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="5111f-108">當您延伸 <xref:System.Collections.Generic.IEnumerable%601> 介面時，可將自訂方法套用至任何可列舉的集合。</span><span class="sxs-lookup"><span data-stu-id="5111f-108">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="5111f-109">如需詳細資訊，請參閱[擴充方法](../../classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="5111f-109">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="5111f-110">新增匯總方法</span><span class="sxs-lookup"><span data-stu-id="5111f-110">Adding an aggregate method</span></span>

<span data-ttu-id="5111f-111">彙總方法會計算一組值的單一值。</span><span class="sxs-lookup"><span data-stu-id="5111f-111">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="5111f-112">LINQ 提供數種彙總方法，包括 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Min%2A> 和 <xref:System.Linq.Enumerable.Max%2A>。</span><span class="sxs-lookup"><span data-stu-id="5111f-112">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="5111f-113">您可將擴充方法新增至 <xref:System.Collections.Generic.IEnumerable%601> 介面，建立自己的彙總方法。</span><span class="sxs-lookup"><span data-stu-id="5111f-113">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="5111f-114">下列程式碼範例示範如何建立呼叫 `Median` 的擴充方法，來計算一系列類型為 `double` 的中位數。</span><span class="sxs-lookup"><span data-stu-id="5111f-114">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="LinqExtensionClass":::

<span data-ttu-id="5111f-115">您可以使用從 <xref:System.Collections.Generic.IEnumerable%601> 介面呼叫其他彙總方法同樣的方式，為任何可列舉集合呼叫此擴充方法。</span><span class="sxs-lookup"><span data-stu-id="5111f-115">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="5111f-116">下列程式碼範例示範如何使用 `Median` 方法處理 `double` 類型的陣列。</span><span class="sxs-lookup"><span data-stu-id="5111f-116">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

:::code language="csharp" source="./snippets/Program.cs" ID="MedianUsage":::

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="5111f-117">多載彙總方法以接受各種類型</span><span class="sxs-lookup"><span data-stu-id="5111f-117">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="5111f-118">您可以多載自己的彙總方法，讓它接受各種類型的序列。</span><span class="sxs-lookup"><span data-stu-id="5111f-118">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="5111f-119">標準方法是為每種類型建立多載。</span><span class="sxs-lookup"><span data-stu-id="5111f-119">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="5111f-120">另一種方法是建立採用泛型型別的多載，使用委派將它轉換成特定的類型。</span><span class="sxs-lookup"><span data-stu-id="5111f-120">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="5111f-121">您也可以結合這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="5111f-121">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="5111f-122">為每種類型建立多載</span><span class="sxs-lookup"><span data-stu-id="5111f-122">To create an overload for each type</span></span>

<span data-ttu-id="5111f-123">您可以為想要支援的每種類型建立特定的多載。</span><span class="sxs-lookup"><span data-stu-id="5111f-123">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="5111f-124">下列程式碼範例示範適合 `int` 類型之 `Median` 方法的多載。</span><span class="sxs-lookup"><span data-stu-id="5111f-124">The following code example shows an overload of the `Median` method for the `int` type.</span></span>

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="IntOverload":::

<span data-ttu-id="5111f-125">您現在可以呼叫 `integer` 和 `double` 類型的 `Median` 多載，如下列程式碼所示︰</span><span class="sxs-lookup"><span data-stu-id="5111f-125">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

:::code language="csharp" source="./snippets/Program.cs" ID="OverloadUsage":::

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="5111f-126">建立一般多載</span><span class="sxs-lookup"><span data-stu-id="5111f-126">To create a generic overload</span></span>

<span data-ttu-id="5111f-127">您也可以建立接受一系列泛型物件的多載。</span><span class="sxs-lookup"><span data-stu-id="5111f-127">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="5111f-128">這個多載會接受委派作為參數，並使用它將泛型型別物件的序列轉換成特定的類型。</span><span class="sxs-lookup"><span data-stu-id="5111f-128">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="5111f-129">下列程式碼顯示 `Median` 方法的多載，接受 <xref:System.Func%602> 委派為參數。</span><span class="sxs-lookup"><span data-stu-id="5111f-129">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="5111f-130">這個委派會接受泛型型別 T 的物件，並傳回 `double` 類型的物件。</span><span class="sxs-lookup"><span data-stu-id="5111f-130">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="GenericOverload":::

<span data-ttu-id="5111f-131">您現在可以針對一系列的類型物件呼叫 `Median` 方法。</span><span class="sxs-lookup"><span data-stu-id="5111f-131">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="5111f-132">如果類型沒有自己的方法多載，則您必須傳遞委派參數。</span><span class="sxs-lookup"><span data-stu-id="5111f-132">If the type doesn't have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="5111f-133">在 C# 中，您可以針對此目的使用 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="5111f-133">In C#, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="5111f-134">另僅限 Visual Basic，如果您使用 `Aggregate` 或 `Group By` 子句而不是方法呼叫，您可以傳遞此子句範圍內的任何值或運算式。</span><span class="sxs-lookup"><span data-stu-id="5111f-134">Also, in Visual Basic only, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="5111f-135">下列程式碼範例示範如何呼叫 `Median` 方法，處理整數陣列及字串陣列。</span><span class="sxs-lookup"><span data-stu-id="5111f-135">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="5111f-136">針對字串，會計算陣列字串長度的中間值。</span><span class="sxs-lookup"><span data-stu-id="5111f-136">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="5111f-137">此範例會示範如何將 <xref:System.Func%602> 委派參數傳遞至每個案例的 `Median` 方法。</span><span class="sxs-lookup"><span data-stu-id="5111f-137">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

:::code language="csharp" source="./snippets/Program.cs" ID="GenericUsage":::

## <a name="adding-a-method-that-returns-a-sequence"></a><span data-ttu-id="5111f-138">加入傳回序列的方法</span><span class="sxs-lookup"><span data-stu-id="5111f-138">Adding a method that returns a sequence</span></span>

<span data-ttu-id="5111f-139">您可以使用傳回一系列值的自訂查詢方法來延伸 <xref:System.Collections.Generic.IEnumerable%601> 介面。</span><span class="sxs-lookup"><span data-stu-id="5111f-139">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="5111f-140">在此情況下，方法必須傳回型別 <xref:System.Collections.Generic.IEnumerable%601> 的集合。</span><span class="sxs-lookup"><span data-stu-id="5111f-140">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="5111f-141">此等方法可用來將篩選條件或資料轉換套用至一系列的值。</span><span class="sxs-lookup"><span data-stu-id="5111f-141">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="5111f-142">下例示範如何建立名為 `AlternateElements` 的擴充方法，傳回集合中的每隔個項目，從第一個項目開始。</span><span class="sxs-lookup"><span data-stu-id="5111f-142">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="SequenceElement":::

<span data-ttu-id="5111f-143">您可為任何可列舉集合呼叫此擴充方法，就和您從 <xref:System.Collections.Generic.IEnumerable%601> 介面呼叫其他方法一樣，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="5111f-143">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

:::code language="csharp" source="./snippets/Program.cs" ID="SequenceUsage":::

## <a name="see-also"></a><span data-ttu-id="5111f-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5111f-144">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="5111f-145">擴充方法</span><span class="sxs-lookup"><span data-stu-id="5111f-145">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
