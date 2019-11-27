---
title: Ref 傳回值
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: 2d2a302a899fbde549161469f281d3e580bcb71f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352542"
---
# <a name="support-for-reference-return-values-visual-basic"></a><span data-ttu-id="060b2-102">支援參考傳回值（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="060b2-102">Support for reference return values (Visual Basic)</span></span>

<span data-ttu-id="060b2-103">從C# 7.0 開始， C#語言支援參考傳回*值*。</span><span class="sxs-lookup"><span data-stu-id="060b2-103">Starting with C# 7.0, the C# language supports *reference return values*.</span></span> <span data-ttu-id="060b2-104">瞭解參考傳回值的其中一種方式是，它們與以傳址方式傳遞至方法的引數相反。</span><span class="sxs-lookup"><span data-stu-id="060b2-104">One way to understand reference return values is that they are the opposite of arguments that are passed by reference to a method.</span></span> <span data-ttu-id="060b2-105">當修改以傳址方式傳遞的引數時，變更會反映在呼叫端的變數值中。</span><span class="sxs-lookup"><span data-stu-id="060b2-105">When an argument passed by reference is modified, the changes are reflected in value of the variable on the caller.</span></span> <span data-ttu-id="060b2-106">當方法提供參考傳回值給呼叫端時，呼叫端對參考傳回值所做的修改會反映在被呼叫的方法資料中。</span><span class="sxs-lookup"><span data-stu-id="060b2-106">When an method provides a reference return value to a caller, modifications made to the reference return value by the caller are reflected in the called method's data.</span></span>

<span data-ttu-id="060b2-107">Visual Basic 不允許您撰寫具有參考傳回值的方法，但它可讓您使用參考傳回值。</span><span class="sxs-lookup"><span data-stu-id="060b2-107">Visual Basic does not allow you to author methods with reference return values, but it does allow you to consume reference return values.</span></span> <span data-ttu-id="060b2-108">換句話說，您可以呼叫具有參考傳回值的方法，並修改該傳回值，而參考傳回值的變更會反映在被呼叫的方法資料中。</span><span class="sxs-lookup"><span data-stu-id="060b2-108">In other words, you can call a method with a reference return value and modify that return value, and changes to the reference return value are reflected in the called method's data.</span></span>

## <a name="modifying-the-ref-return-value-directly"></a><span data-ttu-id="060b2-109">直接修改 ref 傳回值</span><span class="sxs-lookup"><span data-stu-id="060b2-109">Modifying the ref return value directly</span></span>

<span data-ttu-id="060b2-110">對於一律成功且沒有 `ByRef` 參數的方法，您可以直接修改參考傳回值。</span><span class="sxs-lookup"><span data-stu-id="060b2-110">For methods that always succeed and have no `ByRef` parameters, you can modify the reference return value directly.</span></span> <span data-ttu-id="060b2-111">若要這麼做，您可以將新值指派給傳回參考傳回值的運算式。</span><span class="sxs-lookup"><span data-stu-id="060b2-111">You do this by assigning the new value to the expressions that returns the reference return value.</span></span>

<span data-ttu-id="060b2-112">下列C#範例會定義會遞增內部值，並將其傳回為參考傳回值的 `NumericValue.IncrementValue` 方法。</span><span class="sxs-lookup"><span data-stu-id="060b2-112">The following C# example defines a `NumericValue.IncrementValue` method that increments an internal value and returns it as a reference return value.</span></span>

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

<span data-ttu-id="060b2-113">然後，下列 Visual Basic 範例中的呼叫者會修改參考傳回值。</span><span class="sxs-lookup"><span data-stu-id="060b2-113">The reference return value is then modified by the caller in the following Visual Basic example.</span></span> <span data-ttu-id="060b2-114">請注意，具有 `NumericValue.IncrementValue` 方法呼叫的行會不會將值指派給方法。</span><span class="sxs-lookup"><span data-stu-id="060b2-114">Note that the line with the `NumericValue.IncrementValue` method call does not assign a value to the method.</span></span> <span data-ttu-id="060b2-115">相反地，它會將值指派給方法所傳回的參考傳回值。</span><span class="sxs-lookup"><span data-stu-id="060b2-115">Instead, it assigns a value to the reference return value returned by the method.</span></span>

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a><span data-ttu-id="060b2-116">使用 helper 方法</span><span class="sxs-lookup"><span data-stu-id="060b2-116">Using a helper method</span></span>

<span data-ttu-id="060b2-117">在其他情況下，直接修改方法呼叫的參考傳回值可能不一定是理想的做法。</span><span class="sxs-lookup"><span data-stu-id="060b2-117">In other cases, modifying the reference return value of a method call directly may not always be desirable.</span></span> <span data-ttu-id="060b2-118">例如，傳回字串的搜尋方法可能不一定會找到相符的結果。</span><span class="sxs-lookup"><span data-stu-id="060b2-118">For example, a search method that returns a string may not always find a match.</span></span> <span data-ttu-id="060b2-119">在這種情況下，您只想要在搜尋成功時修改參考傳回值。</span><span class="sxs-lookup"><span data-stu-id="060b2-119">In that case, you want to modify the reference return value only if the search is successful.</span></span>

<span data-ttu-id="060b2-120">下列C#範例說明此案例。</span><span class="sxs-lookup"><span data-stu-id="060b2-120">The following C# example illustrates this scenario.</span></span> <span data-ttu-id="060b2-121">它會定義以C#撰寫的 `Sentence` 類別，其中包含 `FindNext` 方法，可在以指定子字串開頭的句子中尋找下一個單字。</span><span class="sxs-lookup"><span data-stu-id="060b2-121">It defines a `Sentence` class written in C# includes a `FindNext` method that finds the next word in a sentence that begins with a specified substring.</span></span> <span data-ttu-id="060b2-122">字串會以參考傳回值傳回，而參考所傳遞至方法的 `Boolean` 變數會指出搜尋是否成功。</span><span class="sxs-lookup"><span data-stu-id="060b2-122">The string is returned as a reference return value, and a `Boolean` variable passed by reference to the method indicates whether the search was successful.</span></span> <span data-ttu-id="060b2-123">參考傳回值表示呼叫端不能唯讀取傳回的值。他或她也可以修改它，這項修改會反映在 `Sentence` 類別內部所包含的資料中。</span><span class="sxs-lookup"><span data-stu-id="060b2-123">The reference return value indicates that the caller can not only read the returned value; he or she can also modify it, and that modification is reflected in the data contained internally in the `Sentence` class.</span></span>

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

<span data-ttu-id="060b2-124">在此情況下，直接修改參考傳回值並不可靠，因為方法呼叫可能會找不到相符的結果，並傳回句子中的第一個單字。</span><span class="sxs-lookup"><span data-stu-id="060b2-124">Directly modifying the reference return value in this case is not reliable, since the method call may fail to find a match and return the first word in the sentence.</span></span> <span data-ttu-id="060b2-125">在這種情況下，呼叫端不會不慎修改句子的第一個單字。</span><span class="sxs-lookup"><span data-stu-id="060b2-125">In that case, the caller will inadvertently modify the first word of the sentence.</span></span> <span data-ttu-id="060b2-126">這可能是因為呼叫端傳回 `null` （或 Visual Basic 中 `Nothing`）而導致的。</span><span class="sxs-lookup"><span data-stu-id="060b2-126">This could be prevented by the caller returning a `null` (or `Nothing` in Visual Basic).</span></span> <span data-ttu-id="060b2-127">但是在這種情況下，嘗試修改值 `Nothing` 的字串會擲回 <xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="060b2-127">But in that case, attempting to modify a string whose value is `Nothing` throws a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="060b2-128">如果呼叫端也可以防止傳回 <xref:System.String.Empty?displayProperty=nameWithType>，但這需要呼叫者定義其值為 <xref:System.String.Empty?displayProperty=nameWithType>的字串變數。</span><span class="sxs-lookup"><span data-stu-id="060b2-128">If could also be prevented by the caller returning <xref:System.String.Empty?displayProperty=nameWithType>, but this requires that the caller define a string variable whose value is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span> <span data-ttu-id="060b2-129">雖然呼叫者可以修改該字串，但修改本身沒有任何用途，因為修改過的字串與 `Sentence` 類別所儲存之句子中的單字沒有任何關聯性。</span><span class="sxs-lookup"><span data-stu-id="060b2-129">While the caller can modify that string, the modification itself serves no purpose, since the modified string has no relationship to the words in the sentence stored by the `Sentence` class.</span></span>

<span data-ttu-id="060b2-130">處理這種情況的最佳方式，就是將參考傳回值傳遞至 helper 方法。</span><span class="sxs-lookup"><span data-stu-id="060b2-130">The best way to handle this scenario is to pass the reference return value by reference to a helper method.</span></span> <span data-ttu-id="060b2-131">Helper 方法接著會包含邏輯，以判斷方法呼叫是否成功，如果有的話，則會修改參考傳回值。</span><span class="sxs-lookup"><span data-stu-id="060b2-131">The helper method then contains the logic to determine whether the method call succeeded and, if it did, to modify the reference return value.</span></span> <span data-ttu-id="060b2-132">下列範例提供可能的執行方式。</span><span class="sxs-lookup"><span data-stu-id="060b2-132">The following example provides a possible implementation.</span></span>

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a><span data-ttu-id="060b2-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="060b2-133">See also</span></span>

- [<span data-ttu-id="060b2-134">依值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="060b2-134">Passing arguments by value and by reference</span></span>](passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="060b2-135">Visual Basic 中的程序</span><span class="sxs-lookup"><span data-stu-id="060b2-135">Procedures in Visual Basic</span></span>](index.md)
