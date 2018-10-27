---
title: Ref 傳回值 (Visual Basic)
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: ba649c4beaf3ec70a8c118f823fe8f25651a05a7
ms.sourcegitcommit: 4621e67f69e7a9503ea93313ff60d69683207889
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2018
ms.locfileid: "49995135"
---
# <a name="support-for-reference-return-values-visual-basic"></a><span data-ttu-id="87c8f-102">支援參考傳回值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87c8f-102">Support for reference return values (Visual Basic)</span></span>

<span data-ttu-id="87c8f-103">開頭為C#7.0 中，C#語言支援*參考傳回值*。</span><span class="sxs-lookup"><span data-stu-id="87c8f-103">Starting with C# 7.0, the C# language supports *reference return values*.</span></span> <span data-ttu-id="87c8f-104">若要了解參考傳回值的方法之一是它們是相反的由參考傳遞至方法的引數。</span><span class="sxs-lookup"><span data-stu-id="87c8f-104">One way to understand reference return values is that they are the opposite of arguments that are passed by reference to a method.</span></span> <span data-ttu-id="87c8f-105">修改參考所傳遞的引數時，所做的變更會反映在變數的值，呼叫端上。</span><span class="sxs-lookup"><span data-stu-id="87c8f-105">When an argument passed by reference is modified, the changes are reflected in value of the variable on the caller.</span></span> <span data-ttu-id="87c8f-106">當方法呼叫端提供參考傳回值時，將參考傳回值對呼叫端所作的修改會反映在呼叫的方法的資料。</span><span class="sxs-lookup"><span data-stu-id="87c8f-106">When an method provides a reference return value to a caller, modifications made to the reference return value by the caller are reflected in the called method's data.</span></span>

<span data-ttu-id="87c8f-107">Visual Basic 不允許您撰寫方法，以參考傳回值，但能讓您使用參考傳回值。</span><span class="sxs-lookup"><span data-stu-id="87c8f-107">Visual Basic does not allow you to author methods with reference return values, but it does allow you to consume reference return values.</span></span> <span data-ttu-id="87c8f-108">換句話說，您可以呼叫具有參考傳回值的方法，並修改該傳回值，並將參考傳回值的變更會反映在呼叫的方法的資料。</span><span class="sxs-lookup"><span data-stu-id="87c8f-108">In other words, you can call a method with a reference return value and modify that return value, and changes to the reference return value are reflected in the called method's data.</span></span>

## <a name="modifying-the-ref-return-value-directly"></a><span data-ttu-id="87c8f-109">直接修改 ref 傳回值</span><span class="sxs-lookup"><span data-stu-id="87c8f-109">Modifying the ref return value directly</span></span>

<span data-ttu-id="87c8f-110">方法永遠成功，而且沒有任何`ByRef`參數，您可以直接修改參考傳回值。</span><span class="sxs-lookup"><span data-stu-id="87c8f-110">For methods that always succeed and have no `ByRef` parameters, you can modify the reference return value directly.</span></span> <span data-ttu-id="87c8f-111">您可以將新的值指派給傳回的參考傳回值的運算式。</span><span class="sxs-lookup"><span data-stu-id="87c8f-111">You do this by assigning the new value to the expressions that returns the reference return value.</span></span> 

<span data-ttu-id="87c8f-112">下列C#範例會定義`NumericValue.IncrementValue`方法遞增內部的值並將其傳回做為參考傳回值。</span><span class="sxs-lookup"><span data-stu-id="87c8f-112">The following C# example defines a `NumericValue.IncrementValue` method that increments an internal value and returns it as a reference return value.</span></span> 

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

<span data-ttu-id="87c8f-113">參考傳回值，然後修改下列 Visual Basic 範例中的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="87c8f-113">The reference return value is then modified by the caller in the following Visual Basic example.</span></span> <span data-ttu-id="87c8f-114">請注意，該程式行使用`NumericValue.IncrementValue`方法呼叫不會將值指派給方法。</span><span class="sxs-lookup"><span data-stu-id="87c8f-114">Note that the line with the `NumericValue.IncrementValue` method call does not assign a value to the method.</span></span> <span data-ttu-id="87c8f-115">相反地，它會指派值給方法所傳回的參考傳回值。</span><span class="sxs-lookup"><span data-stu-id="87c8f-115">Instead, it assigns a value to the reference return value returned by the method.</span></span>

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a><span data-ttu-id="87c8f-116">使用 helper 方法</span><span class="sxs-lookup"><span data-stu-id="87c8f-116">Using a helper method</span></span>

<span data-ttu-id="87c8f-117">在其他情況下，直接修改參考傳回值的方法呼叫不一定需要。</span><span class="sxs-lookup"><span data-stu-id="87c8f-117">In other cases, modifying the reference return value of a method call directly may not always be desirable.</span></span> <span data-ttu-id="87c8f-118">比方說，傳回的字串搜尋方法，可能不會永遠發現相符項目。</span><span class="sxs-lookup"><span data-stu-id="87c8f-118">For example, a search method that returns a string may not always find a match.</span></span> <span data-ttu-id="87c8f-119">在此情況下，您想要修改參考傳回值，只有當搜尋已成功。</span><span class="sxs-lookup"><span data-stu-id="87c8f-119">In that case, you want to modify the reference return value only if the search is successful.</span></span>

<span data-ttu-id="87c8f-120">下列C#範例說明此案例。</span><span class="sxs-lookup"><span data-stu-id="87c8f-120">The following C# example illustrates this scenario.</span></span> <span data-ttu-id="87c8f-121">它會定義`Sentence`撰寫的類別C#包含`FindNext`方法，可在句子開頭為指定的子字串中尋找下一個字。</span><span class="sxs-lookup"><span data-stu-id="87c8f-121">It defines a `Sentence` class written in C# includes a `FindNext` method that finds the next word in a sentence that begins with a specified substring.</span></span> <span data-ttu-id="87c8f-122">字串會以參考傳回值傳回，而參考所傳遞至方法的 `Boolean` 變數會指出搜尋是否成功。</span><span class="sxs-lookup"><span data-stu-id="87c8f-122">The string is returned as a reference return value, and a `Boolean` variable passed by reference to the method indicates whether the search was successful.</span></span> <span data-ttu-id="87c8f-123">將參考傳回值會指出，呼叫端不只可以讀取傳回的值;他或她還可以修改它，而且該修改會反映在內部中包含的資料`Sentence`類別。</span><span class="sxs-lookup"><span data-stu-id="87c8f-123">The reference return value indicates that the caller can not only read the returned value; he or she can also modify it, and that modification is reflected in the data contained internally in the `Sentence` class.</span></span>

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

<span data-ttu-id="87c8f-124">直接修改參考傳回值在此情況下不可靠，因為在方法呼叫可能會失敗，以尋找相符項目並傳回句子中的第一個字。</span><span class="sxs-lookup"><span data-stu-id="87c8f-124">Directly modifying the reference return value in this case is not reliable, since the method call may fail to find a match and return the first word in the sentence.</span></span> <span data-ttu-id="87c8f-125">在此情況下，呼叫端會不小心修改第一個字的句子。</span><span class="sxs-lookup"><span data-stu-id="87c8f-125">In that case, the caller will inadvertently modify the first word of the sentence.</span></span> <span data-ttu-id="87c8f-126">這可能導致傳回呼叫端`null`(或`Nothing`Visual Basic 中)。</span><span class="sxs-lookup"><span data-stu-id="87c8f-126">This could be prevented by the caller returning a `null` (or `Nothing` in Visual Basic).</span></span> <span data-ttu-id="87c8f-127">但在此情況下，嘗試修改的字串，其值是`Nothing`會擲回<xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="87c8f-127">But in that case, attempting to modify a string whose value is `Nothing` throws a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="87c8f-128">如果也無法阻止傳回呼叫端<xref:System.String.Empty?displayProperty=nameWithType>，但這需要呼叫端定義其值的字串變數<xref:System.String.Empty?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="87c8f-128">If could also be prevented by the caller returning <xref:System.String.Empty?displayProperty=nameWithType>, but this requires that the caller define a string variable whose value is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span> <span data-ttu-id="87c8f-129">雖然呼叫者可以修改該字串，本身的修改毫無意義可言，因為修改的字串文字並沒有關聯性中所儲存的句子`Sentence`類別。</span><span class="sxs-lookup"><span data-stu-id="87c8f-129">While the caller can modify that string, the modification itself serves no purpose, since the modified string has no relationship to the words in the sentence stored by the `Sentence` class.</span></span>

<span data-ttu-id="87c8f-130">若要解決這種情況，最好是將參考傳回值傳址方式傳遞的 helper 方法。</span><span class="sxs-lookup"><span data-stu-id="87c8f-130">The best way to handle this scenario is to pass the reference return value by reference to a helper method.</span></span> <span data-ttu-id="87c8f-131">Helper 方法則會包含邏輯，以判斷是否方法呼叫成功，如果有，修改參考傳回值。</span><span class="sxs-lookup"><span data-stu-id="87c8f-131">The helper method then contains the logic to determine whether the method call succeeded and, if it did, to modify the reference return value.</span></span> <span data-ttu-id="87c8f-132">下列範例會提供可能的實作。</span><span class="sxs-lookup"><span data-stu-id="87c8f-132">The following example provides a possible implementation.</span></span>

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a><span data-ttu-id="87c8f-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87c8f-133">See also</span></span>

<span data-ttu-id="87c8f-134">[值和傳參考方式傳遞引數](passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="87c8f-134">[Passing arguments by value and by reference](passing-arguments-by-value-and-by-reference.md) </span></span>  
[<span data-ttu-id="87c8f-135">Visual Basic 中的程序</span><span class="sxs-lookup"><span data-stu-id="87c8f-135">Procedures in Visual Basic</span></span>](index.md)   


