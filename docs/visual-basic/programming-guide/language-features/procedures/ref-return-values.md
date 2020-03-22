---
title: 參考傳回值
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: f2a92c584dbb12a322e28435d797fa4d7c2f6dbb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186929"
---
# <a name="support-for-reference-return-values-visual-basic"></a><span data-ttu-id="76180-102">支援參考傳回值（可視基本值）</span><span class="sxs-lookup"><span data-stu-id="76180-102">Support for reference return values (Visual Basic)</span></span>

<span data-ttu-id="76180-103">從 C# 7.0 開始，C# 語言支援*參考傳回值*。</span><span class="sxs-lookup"><span data-stu-id="76180-103">Starting with C# 7.0, the C# language supports *reference return values*.</span></span> <span data-ttu-id="76180-104">理解引用傳回值的一種方法是，它們是通過引用傳遞給方法的參數的相反。</span><span class="sxs-lookup"><span data-stu-id="76180-104">One way to understand reference return values is that they are the opposite of arguments that are passed by reference to a method.</span></span> <span data-ttu-id="76180-105">修改引用傳遞的參數時，更改將反映在調用方上的變數的值中。</span><span class="sxs-lookup"><span data-stu-id="76180-105">When an argument passed by reference is modified, the changes are reflected in value of the variable on the caller.</span></span> <span data-ttu-id="76180-106">當方法向調用方提供引用傳回值時，調用方對引用傳回值所做的修改將反映在被呼叫者法的資料中。</span><span class="sxs-lookup"><span data-stu-id="76180-106">When an method provides a reference return value to a caller, modifications made to the reference return value by the caller are reflected in the called method's data.</span></span>

<span data-ttu-id="76180-107">Visual Basic 不允許使用引用傳回值編寫方法，但它確實允許您使用引用傳回值。</span><span class="sxs-lookup"><span data-stu-id="76180-107">Visual Basic does not allow you to author methods with reference return values, but it does allow you to consume reference return values.</span></span> <span data-ttu-id="76180-108">換句話說，可以調用具有引用傳回值的方法並修改該傳回值，對引用傳回值的更改將反映在被調用的方法的資料中。</span><span class="sxs-lookup"><span data-stu-id="76180-108">In other words, you can call a method with a reference return value and modify that return value, and changes to the reference return value are reflected in the called method's data.</span></span>

## <a name="modifying-the-ref-return-value-directly"></a><span data-ttu-id="76180-109">直接修改 ref 傳回值</span><span class="sxs-lookup"><span data-stu-id="76180-109">Modifying the ref return value directly</span></span>

<span data-ttu-id="76180-110">對於始終成功且沒有`ByRef`參數的方法，可以直接修改引用傳回值。</span><span class="sxs-lookup"><span data-stu-id="76180-110">For methods that always succeed and have no `ByRef` parameters, you can modify the reference return value directly.</span></span> <span data-ttu-id="76180-111">為此，通過將新值分配給返回引用傳回值的運算式。</span><span class="sxs-lookup"><span data-stu-id="76180-111">You do this by assigning the new value to the expressions that returns the reference return value.</span></span>

<span data-ttu-id="76180-112">下面的 C# 示例定義了一`NumericValue.IncrementValue`個方法，該方法將內部值遞增並返回為引用傳回值。</span><span class="sxs-lookup"><span data-stu-id="76180-112">The following C# example defines a `NumericValue.IncrementValue` method that increments an internal value and returns it as a reference return value.</span></span>

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

<span data-ttu-id="76180-113">然後，調用方在以下 Visual Basic 示例中修改引用傳回值。</span><span class="sxs-lookup"><span data-stu-id="76180-113">The reference return value is then modified by the caller in the following Visual Basic example.</span></span> <span data-ttu-id="76180-114">請注意，使用 方法調用`NumericValue.IncrementValue`的行不會為 方法分配值。</span><span class="sxs-lookup"><span data-stu-id="76180-114">Note that the line with the `NumericValue.IncrementValue` method call does not assign a value to the method.</span></span> <span data-ttu-id="76180-115">相反，它將值分配給方法返回的引用傳回值。</span><span class="sxs-lookup"><span data-stu-id="76180-115">Instead, it assigns a value to the reference return value returned by the method.</span></span>

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a><span data-ttu-id="76180-116">使用説明器方法</span><span class="sxs-lookup"><span data-stu-id="76180-116">Using a helper method</span></span>

<span data-ttu-id="76180-117">在其他情況下，直接修改方法調用的引用傳回值可能並不總是可取的。</span><span class="sxs-lookup"><span data-stu-id="76180-117">In other cases, modifying the reference return value of a method call directly may not always be desirable.</span></span> <span data-ttu-id="76180-118">例如，返回字串的搜索方法可能並不總是找到匹配項。</span><span class="sxs-lookup"><span data-stu-id="76180-118">For example, a search method that returns a string may not always find a match.</span></span> <span data-ttu-id="76180-119">在這種情況下，僅當搜索成功時，才要修改引用傳回值。</span><span class="sxs-lookup"><span data-stu-id="76180-119">In that case, you want to modify the reference return value only if the search is successful.</span></span>

<span data-ttu-id="76180-120">以下 C# 示例說明了此方案。</span><span class="sxs-lookup"><span data-stu-id="76180-120">The following C# example illustrates this scenario.</span></span> <span data-ttu-id="76180-121">它定義用`Sentence`C# 編寫的類包括一`FindNext`個方法，該方法在以指定的子字串開頭的句子中查找下一個單詞。</span><span class="sxs-lookup"><span data-stu-id="76180-121">It defines a `Sentence` class written in C# includes a `FindNext` method that finds the next word in a sentence that begins with a specified substring.</span></span> <span data-ttu-id="76180-122">字串會以參考傳回值傳回，而參考所傳遞至方法的 `Boolean` 變數會指出搜尋是否成功。</span><span class="sxs-lookup"><span data-stu-id="76180-122">The string is returned as a reference return value, and a `Boolean` variable passed by reference to the method indicates whether the search was successful.</span></span> <span data-ttu-id="76180-123">引用傳回值指示除了讀取返回的值外，調用方還可以修改它，並且該修改反映在`Sentence`類內部包含的資料中。</span><span class="sxs-lookup"><span data-stu-id="76180-123">The reference return value indicates that in addition to reading the returned value, the caller can also modify it, and that modification is reflected in the data contained internally in the `Sentence` class.</span></span>

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

<span data-ttu-id="76180-124">在這種情況下，直接修改引用傳回值不可靠，因為方法調用可能無法找到匹配項並返回句子中的第一個單詞。</span><span class="sxs-lookup"><span data-stu-id="76180-124">Directly modifying the reference return value in this case is not reliable, since the method call may fail to find a match and return the first word in the sentence.</span></span> <span data-ttu-id="76180-125">在這種情況下，調用方將無意中修改句子的第一個單詞。</span><span class="sxs-lookup"><span data-stu-id="76180-125">In that case, the caller will inadvertently modify the first word of the sentence.</span></span> <span data-ttu-id="76180-126">調用方返回 （`null`或`Nothing`視覺基本值） 可以防止這種情況。</span><span class="sxs-lookup"><span data-stu-id="76180-126">This could be prevented by the caller returning a `null` (or `Nothing` in Visual Basic).</span></span> <span data-ttu-id="76180-127">但是在這種情況下，嘗試修改其值為`Nothing`的字串將引發 。 <xref:System.NullReferenceException></span><span class="sxs-lookup"><span data-stu-id="76180-127">But in that case, attempting to modify a string whose value is `Nothing` throws a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="76180-128">如果調用方也可以阻止 返回<xref:System.String.Empty?displayProperty=nameWithType>，但這需要調用方定義其值為<xref:System.String.Empty?displayProperty=nameWithType>的字串變數。</span><span class="sxs-lookup"><span data-stu-id="76180-128">If could also be prevented by the caller returning <xref:System.String.Empty?displayProperty=nameWithType>, but this requires that the caller define a string variable whose value is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span> <span data-ttu-id="76180-129">雖然調用方可以修改該字串，但修改本身沒有用處，因為修改後的字串與`Sentence`類存儲的句子中的單詞沒有關系。</span><span class="sxs-lookup"><span data-stu-id="76180-129">While the caller can modify that string, the modification itself serves no purpose, since the modified string has no relationship to the words in the sentence stored by the `Sentence` class.</span></span>

<span data-ttu-id="76180-130">處理此方案的最佳方法是通過引用説明器方法傳遞引用傳回值。</span><span class="sxs-lookup"><span data-stu-id="76180-130">The best way to handle this scenario is to pass the reference return value by reference to a helper method.</span></span> <span data-ttu-id="76180-131">然後，説明器方法包含邏輯，以確定方法調用是否成功，如果成功，則修改引用傳回值。</span><span class="sxs-lookup"><span data-stu-id="76180-131">The helper method then contains the logic to determine whether the method call succeeded and, if it did, to modify the reference return value.</span></span> <span data-ttu-id="76180-132">下面的示例提供了一個可能的實現。</span><span class="sxs-lookup"><span data-stu-id="76180-132">The following example provides a possible implementation.</span></span>

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a><span data-ttu-id="76180-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76180-133">See also</span></span>

- [<span data-ttu-id="76180-134">按值和引用傳遞參數</span><span class="sxs-lookup"><span data-stu-id="76180-134">Passing arguments by value and by reference</span></span>](passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="76180-135">Visual Basic 中的程序</span><span class="sxs-lookup"><span data-stu-id="76180-135">Procedures in Visual Basic</span></span>](index.md)
