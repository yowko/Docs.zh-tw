---
title: 在執行階段動態指定述詞篩選條件 (C# 中的 LINQ)
description: 了解如何使用 C# 中的 LINQ 在執行階段動態指定述詞篩選條件。
ms.date: 12/1/2016
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: ece5940edd615f30acab06a429de300e27811a66
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50038483"
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a><span data-ttu-id="28911-103">在執行階段動態指定述詞篩選</span><span class="sxs-lookup"><span data-stu-id="28911-103">Dynamically specify predicate filters at runtime</span></span>

<span data-ttu-id="28911-104">在某些情況下，您要到執行階段才知道在 `where` 子句中必須套用多少述詞至來源元素。</span><span class="sxs-lookup"><span data-stu-id="28911-104">In some cases, you don't know until run time how many predicates you have to apply to source elements in the `where` clause.</span></span> <span data-ttu-id="28911-105">動態指定多個述詞篩選的其中一個方式是使用 <xref:System.Linq.Enumerable.Contains%2A> 方法，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="28911-105">One way to dynamically specify multiple predicate filters is to use the <xref:System.Linq.Enumerable.Contains%2A> method, as shown in the following example.</span></span> <span data-ttu-id="28911-106">此範例以兩種方式建構。</span><span class="sxs-lookup"><span data-stu-id="28911-106">The example is constructed in two ways.</span></span> <span data-ttu-id="28911-107">首先，篩選程式中所提供的值來執行專案。</span><span class="sxs-lookup"><span data-stu-id="28911-107">First, the project is run by filtering on values that are provided in the program.</span></span> <span data-ttu-id="28911-108">然後使用執行階段提供的輸入再次執行專案。</span><span class="sxs-lookup"><span data-stu-id="28911-108">Then the project is run again by using input provided at run time.</span></span>

## <a name="to-filter-by-using-the-contains-method"></a><span data-ttu-id="28911-109">使用 Contains 方法篩選</span><span class="sxs-lookup"><span data-stu-id="28911-109">To filter by using the Contains method</span></span>

1. <span data-ttu-id="28911-110">開啟新的主控台應用程式並命名為 `PredicateFilters`。</span><span class="sxs-lookup"><span data-stu-id="28911-110">Open a new console application and name it `PredicateFilters`.</span></span>

2. <span data-ttu-id="28911-111">從[查詢物件集合](query-a-collection-of-objects.md)複製 `StudentClass` 類別，再將它貼入 `Program` 類別下的命名空間 `PredicateFilters`。</span><span class="sxs-lookup"><span data-stu-id="28911-111">Copy the `StudentClass` class from [Query a collection of objects](query-a-collection-of-objects.md) and paste it into namespace `PredicateFilters` underneath class `Program`.</span></span> <span data-ttu-id="28911-112">`StudentClass` 提供 `Student` 物件的清單。</span><span class="sxs-lookup"><span data-stu-id="28911-112">`StudentClass` provides a list of `Student` objects.</span></span>

3. <span data-ttu-id="28911-113">以 `StudentClass` 註解 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="28911-113">Comment out the `Main` method in `StudentClass`.</span></span>

4. <span data-ttu-id="28911-114">使用下列程式碼取代 `Program` 類別：</span><span class="sxs-lookup"><span data-stu-id="28911-114">Replace class `Program` with the following code:</span></span>

     [!code-csharp[csProgGuideLINQ#26](~/samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]

5. <span data-ttu-id="28911-115">將下列行新增至 `ids` 宣告下之 `DynamicPredicates` 類別中的 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="28911-115">Add the following line to the `Main` method in class `DynamicPredicates`, under the declaration of `ids`.</span></span>

     ```csharp
     QueryById(ids);
     ```

6. <span data-ttu-id="28911-116">執行專案。</span><span class="sxs-lookup"><span data-stu-id="28911-116">Run the project.</span></span>

7. <span data-ttu-id="28911-117">主控台視窗會顯示下列輸出：</span><span class="sxs-lookup"><span data-stu-id="28911-117">The following output is displayed in a console window:</span></span>

     <span data-ttu-id="28911-118">Garcia: 114</span><span class="sxs-lookup"><span data-stu-id="28911-118">Garcia: 114</span></span>

     <span data-ttu-id="28911-119">O'Donnell: 112</span><span class="sxs-lookup"><span data-stu-id="28911-119">O'Donnell: 112</span></span>

     <span data-ttu-id="28911-120">Omelchenko: 111</span><span class="sxs-lookup"><span data-stu-id="28911-120">Omelchenko: 111</span></span>

8. <span data-ttu-id="28911-121">下一步是再次執行專案，這次使用在執行階段輸入的輸入，而不是陣列 `ids`。</span><span class="sxs-lookup"><span data-stu-id="28911-121">The next step is to run the project again, this time by using input entered at run time instead of array `ids`.</span></span> <span data-ttu-id="28911-122">在 `Main` 方法中，將 `QueryByID(ids)` 變更為 `QueryByID(args)`。</span><span class="sxs-lookup"><span data-stu-id="28911-122">Change `QueryByID(ids)` to `QueryByID(args)` in the `Main` method.</span></span>

9. <span data-ttu-id="28911-123">使用命令列引數 `122 117 120 115` 執行專案。</span><span class="sxs-lookup"><span data-stu-id="28911-123">Run the project with the command line arguments `122 117 120 115`.</span></span> <span data-ttu-id="28911-124">執行專案時，這些值會變成 `args` 的元素，`Main` 方法的參數。</span><span class="sxs-lookup"><span data-stu-id="28911-124">When the project is run, those values become elements of `args`, the parameter of the `Main` method.</span></span>

10. <span data-ttu-id="28911-125">主控台視窗會顯示下列輸出：</span><span class="sxs-lookup"><span data-stu-id="28911-125">The following output is displayed in a console window:</span></span>

     <span data-ttu-id="28911-126">Adams: 120</span><span class="sxs-lookup"><span data-stu-id="28911-126">Adams: 120</span></span>

     <span data-ttu-id="28911-127">Feng: 117</span><span class="sxs-lookup"><span data-stu-id="28911-127">Feng: 117</span></span>

     <span data-ttu-id="28911-128">Garcia: 115</span><span class="sxs-lookup"><span data-stu-id="28911-128">Garcia: 115</span></span>

     <span data-ttu-id="28911-129">Tucker: 122</span><span class="sxs-lookup"><span data-stu-id="28911-129">Tucker: 122</span></span>

## <a name="to-filter-by-using-a-switch-statement"></a><span data-ttu-id="28911-130">使用 switch 陳述式來篩選</span><span class="sxs-lookup"><span data-stu-id="28911-130">To filter by using a switch statement</span></span>

1. <span data-ttu-id="28911-131">您可以使用 `switch` 陳述式，在預先定義的替代查詢中選取。</span><span class="sxs-lookup"><span data-stu-id="28911-131">You can use a `switch` statement to select among predetermined alternative queries.</span></span> <span data-ttu-id="28911-132">在下列範例中，`studentQuery` 會根據執行階段指定的年級或年份，使用不同的 `where` 子句。</span><span class="sxs-lookup"><span data-stu-id="28911-132">In the following example, `studentQuery` uses a different `where` clause depending on which grade level, or year, is specified at run time.</span></span>

2. <span data-ttu-id="28911-133">將下列方法複製並貼入 `DynamicPredicates` 類別中。</span><span class="sxs-lookup"><span data-stu-id="28911-133">Copy the following method and paste it into class `DynamicPredicates`.</span></span>

     [!code-csharp[csProgGuideLINQ#27](~/samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]

3. <span data-ttu-id="28911-134">在 `Main` 方法中，使用下列呼叫取代 `QueryByID` 的呼叫，將 `args` 陣列的第一個元素傳送為其引數︰`QueryByYear(args[0])`。</span><span class="sxs-lookup"><span data-stu-id="28911-134">In the `Main` method, replace the call to `QueryByID` with the following call, which sends the first element from the `args` array as its argument: `QueryByYear(args[0])`.</span></span>

4. <span data-ttu-id="28911-135">以 1 到 4 之間整數值的命令列引數執行專案。</span><span class="sxs-lookup"><span data-stu-id="28911-135">Run the project with a command line argument of an integer value between 1 and 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="28911-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28911-136">See also</span></span>

- [<span data-ttu-id="28911-137">Language-Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="28911-137">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="28911-138">where 子句</span><span class="sxs-lookup"><span data-stu-id="28911-138">where clause</span></span>](../language-reference/keywords/where-clause.md)
