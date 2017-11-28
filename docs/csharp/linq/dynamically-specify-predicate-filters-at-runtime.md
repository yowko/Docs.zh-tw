---
title: "在執行階段動態指定述詞篩選"
description: "如何在執行階段動態指定述詞篩選。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: 06bc594ac1357e7dca6c182fa28310559a79875c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a><span data-ttu-id="0094f-104">在執行階段動態指定述詞篩選</span><span class="sxs-lookup"><span data-stu-id="0094f-104">Dynamically specify predicate filters at runtime</span></span>

<span data-ttu-id="0094f-105">在某些情況下，您要到執行階段才知道在 `where` 子句中必須套用多少述詞至來源項目。</span><span class="sxs-lookup"><span data-stu-id="0094f-105">In some cases you do not know until run time how many predicates you have to apply to source elements in the `where` clause.</span></span> <span data-ttu-id="0094f-106">動態指定多個述詞篩選的其中一個方式是使用 <xref:System.Linq.Enumerable.Contains%2A> 方法，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0094f-106">One way to dynamically specify multiple predicate filters is to use the <xref:System.Linq.Enumerable.Contains%2A> method, as shown in the following example.</span></span> <span data-ttu-id="0094f-107">此範例以兩種方式建構。</span><span class="sxs-lookup"><span data-stu-id="0094f-107">The example is constructed in two ways.</span></span> <span data-ttu-id="0094f-108">首先，篩選程式中所提供的值來執行專案。</span><span class="sxs-lookup"><span data-stu-id="0094f-108">First, the project is run by filtering on values that are provided in the program.</span></span> <span data-ttu-id="0094f-109">然後使用執行階段提供的輸入再次執行專案。</span><span class="sxs-lookup"><span data-stu-id="0094f-109">Then the project is run again by using input provided at run time.</span></span>  
  
## <a name="to-filter-by-using-the-contains-method"></a><span data-ttu-id="0094f-110">使用 Contains 方法篩選</span><span class="sxs-lookup"><span data-stu-id="0094f-110">To filter by using the Contains method</span></span>  
  
1.  <span data-ttu-id="0094f-111">開啟新的主控台應用程式並命名為 `PredicateFilters`。</span><span class="sxs-lookup"><span data-stu-id="0094f-111">Open a new console application and name it `PredicateFilters`.</span></span>  
  
2.  <span data-ttu-id="0094f-112">從[查詢物件集合](query-a-collection-of-objects.md)複製 `StudentClass` 類別，再將它貼入 `Program` 類別下的命名空間 `PredicateFilters`。</span><span class="sxs-lookup"><span data-stu-id="0094f-112">Copy the `StudentClass` class from [Query a collection of objects](query-a-collection-of-objects.md) and paste it into namespace `PredicateFilters` underneath class `Program`.</span></span> <span data-ttu-id="0094f-113">`StudentClass` 提供 `Student` 物件的清單。</span><span class="sxs-lookup"><span data-stu-id="0094f-113">`StudentClass` provides a list of `Student` objects.</span></span>  
  
3.  <span data-ttu-id="0094f-114">以 `StudentClass` 註解 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="0094f-114">Comment out the `Main` method in `StudentClass`.</span></span>  
  
4.  <span data-ttu-id="0094f-115">使用下列程式碼取代 `Program` 類別。</span><span class="sxs-lookup"><span data-stu-id="0094f-115">Replace class `Program` with the following code.</span></span>  
  
     [!code-csharp[csProgGuideLINQ#26](../../../samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]  
  
5.  <span data-ttu-id="0094f-116">將下列行新增至 `ids` 宣告下之 `DynamicPredicates` 類別中的 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="0094f-116">Add the following line to the `Main` method in class `DynamicPredicates`, under the declaration of `ids`.</span></span>  
  
     ```csharp
     QueryById(ids);
     ```

6.  <span data-ttu-id="0094f-117">執行專案。</span><span class="sxs-lookup"><span data-stu-id="0094f-117">Run the project.</span></span>  
  
7.  <span data-ttu-id="0094f-118">主控台視窗會顯示下列輸出：</span><span class="sxs-lookup"><span data-stu-id="0094f-118">The following output is displayed in a console window:</span></span>  
  
     <span data-ttu-id="0094f-119">Garcia: 114</span><span class="sxs-lookup"><span data-stu-id="0094f-119">Garcia: 114</span></span>  
  
     <span data-ttu-id="0094f-120">O'Donnell: 112</span><span class="sxs-lookup"><span data-stu-id="0094f-120">O'Donnell: 112</span></span>  
  
     <span data-ttu-id="0094f-121">Omelchenko: 111</span><span class="sxs-lookup"><span data-stu-id="0094f-121">Omelchenko: 111</span></span>  
  
8.  <span data-ttu-id="0094f-122">下一步是再次執行專案，這次使用在執行階段輸入的輸入，而不是陣列 `ids`。</span><span class="sxs-lookup"><span data-stu-id="0094f-122">The next step is to run the project again, this time by using input entered at run time instead of array `ids`.</span></span> <span data-ttu-id="0094f-123">在 `Main` 方法中，將 `QueryByID(ids)` 變更為 `QueryByID(args)`。</span><span class="sxs-lookup"><span data-stu-id="0094f-123">Change `QueryByID(ids)` to `QueryByID(args)` in the `Main` method.</span></span>  
  
9. <span data-ttu-id="0094f-124">使用命令列引數 `122 117 120 115` 執行專案。</span><span class="sxs-lookup"><span data-stu-id="0094f-124">Run the project with the command line arguments `122 117 120 115`.</span></span> <span data-ttu-id="0094f-125">執行專案時，這些值會變成 `args` 的項目，`Main` 方法的參數。</span><span class="sxs-lookup"><span data-stu-id="0094f-125">When the project is run, those values become elements of `args`, the parameter of the `Main` method..</span></span>  
  
10. <span data-ttu-id="0094f-126">主控台視窗會顯示下列輸出：</span><span class="sxs-lookup"><span data-stu-id="0094f-126">The following output is displayed in a console window:</span></span>  
  
     <span data-ttu-id="0094f-127">Adams: 120</span><span class="sxs-lookup"><span data-stu-id="0094f-127">Adams: 120</span></span>  
  
     <span data-ttu-id="0094f-128">Feng: 117</span><span class="sxs-lookup"><span data-stu-id="0094f-128">Feng: 117</span></span>  
  
     <span data-ttu-id="0094f-129">Garcia: 115</span><span class="sxs-lookup"><span data-stu-id="0094f-129">Garcia: 115</span></span>  
  
     <span data-ttu-id="0094f-130">Tucker: 122</span><span class="sxs-lookup"><span data-stu-id="0094f-130">Tucker: 122</span></span>  
  
## <a name="to-filter-by-using-a-switch-statement"></a><span data-ttu-id="0094f-131">使用 switch 陳述式來篩選</span><span class="sxs-lookup"><span data-stu-id="0094f-131">To filter by using a switch statement</span></span>  
  
1.  <span data-ttu-id="0094f-132">您可以使用 `switch` 陳述式，在預先定義的替代查詢中選取。</span><span class="sxs-lookup"><span data-stu-id="0094f-132">You can use a `switch` statement to select among predetermined alternative queries.</span></span> <span data-ttu-id="0094f-133">在下例中，`studentQuery` 會根據執行階段指定的年級或年份，使用不同的 `where` 子句。</span><span class="sxs-lookup"><span data-stu-id="0094f-133">In the following example, `studentQuery` uses a different `where` clause depending on which grade level, or year, is specified at run time.</span></span>  
  
2.  <span data-ttu-id="0094f-134">將下列方法複製並貼入 `DynamicPredicates` 類別中。</span><span class="sxs-lookup"><span data-stu-id="0094f-134">Copy the following method and paste it into class `DynamicPredicates`.</span></span>  
  
     [!code-csharp[csProgGuideLINQ#27](../../../samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]  
  
3.  <span data-ttu-id="0094f-135">在 `Main` 方法中，使用下列呼叫取代 `QueryByID` 的呼叫，將 `args` 陣列的第一個項目傳送為其引數︰`QueryByYear(args[0])`。</span><span class="sxs-lookup"><span data-stu-id="0094f-135">In the `Main` method, replace the call to `QueryByID` with the following call, which sends the first element from the `args` array as its argument: `QueryByYear(args[0])`.</span></span>  
  
4.  <span data-ttu-id="0094f-136">以 1 到 4 之間整數值的命令列引數執行專案。</span><span class="sxs-lookup"><span data-stu-id="0094f-136">Run the project with a command line argument of an integer value between 1 and 4.</span></span>  
  
 
## <a name="see-also"></a><span data-ttu-id="0094f-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0094f-137">See Also</span></span>  
 [<span data-ttu-id="0094f-138">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="0094f-138">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="0094f-139">where 子句</span><span class="sxs-lookup"><span data-stu-id="0094f-139">where clause</span></span>](../language-reference/keywords/where-clause.md)
