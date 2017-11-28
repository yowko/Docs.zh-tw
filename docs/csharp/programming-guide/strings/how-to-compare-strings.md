---
title: "如何：比較字串 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.assetid: e1268e28-ee98-4695-98e9-92280f1c33c0
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4837fa57c962cba841ffcc83c5bd4475a4faff0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compare-strings-c-programming-guide"></a><span data-ttu-id="35546-102">如何：比較字串 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="35546-102">How to: Compare strings (C# Programming Guide)</span></span>

<span data-ttu-id="35546-103">當您比較字串時，您產生的結果會顯示一個字串是大於或小於另一個，或兩個字串相等。</span><span class="sxs-lookup"><span data-stu-id="35546-103">When you compare strings, you are producing a result that says one string is greater than or less than the other, or that the two strings are equal.</span></span> <span data-ttu-id="35546-104">決定結果的規則會隨您執行「序數比較」或「區分文化特性比較」而異。</span><span class="sxs-lookup"><span data-stu-id="35546-104">The rules by which the result is determined are different depending on whether you are performing *ordinal comparison* or *culture-sensitive comparison*.</span></span> <span data-ttu-id="35546-105">特定工作請務必使用正確的比較類型。</span><span class="sxs-lookup"><span data-stu-id="35546-105">It is important to use the correct kind of comparison for the specific task.</span></span>

 <span data-ttu-id="35546-106">當您必須比較或排序兩個字串的值，但不考慮語言慣例時，請使用基本的序數比較。</span><span class="sxs-lookup"><span data-stu-id="35546-106">Use basic ordinal comparisons when you have to compare or sort the values of two strings without regard to linguistic conventions.</span></span> <span data-ttu-id="35546-107">基本的序數比較 (`System.StringComparison.Ordinal`) 會區分大小寫，這表示兩個字串必須逐字元比對："and" 不等於 "And" 或 "AND"。</span><span class="sxs-lookup"><span data-stu-id="35546-107">A basic ordinal comparison (`System.StringComparison.Ordinal`) is case-sensitive, which means that the two strings must match character for character: "and" does not equal "And" or "AND".</span></span> <span data-ttu-id="35546-108">常用的變化是 `System.StringComparison.OrdinalIgnoreCase`，它會比對 "and"、"And" 和 "AND"。</span><span class="sxs-lookup"><span data-stu-id="35546-108">A frequently-used variation is `System.StringComparison.OrdinalIgnoreCase`, which will match "and", "And", and "AND".</span></span> <span data-ttu-id="35546-109">`StringComparison.OrdinalIgnoreCase` 通常用來比較檔案名稱、路徑名稱、網路路徑，以及不會隨使用者電腦的地區設定而變更其值的任何其他字串。</span><span class="sxs-lookup"><span data-stu-id="35546-109">`StringComparison.OrdinalIgnoreCase` is often used to compare file names, path names, network paths, and any other string whose value does not change based on the locale of the user's computer.</span></span> <span data-ttu-id="35546-110">如需詳細資訊，請參閱<xref:System.StringComparison?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="35546-110">For more information, see <xref:System.StringComparison?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="35546-111">區分文化特性比較通常用於比較和排序使用者輸入的字串，因為這些字串的字元和排序慣例可能會隨使用者電腦的地區設定而異。</span><span class="sxs-lookup"><span data-stu-id="35546-111">Culture-sensitive comparisons are typically used to compare and sort strings that are input by end users, because the characters and sorting conventions of these strings might vary depending on the locale of the user's computer.</span></span> <span data-ttu-id="35546-112">即使包含完全相同字元的字串，也可能因目前執行緒的文化特性而改變排序。</span><span class="sxs-lookup"><span data-stu-id="35546-112">Even strings that contain identical characters might sort differently depending on the culture of the current thread.</span></span>

> [!NOTE]
> <span data-ttu-id="35546-113">當您比較字串時，您應該使用明確指定打算執行比較類型的方法。</span><span class="sxs-lookup"><span data-stu-id="35546-113">When you compare strings, you should use the methods that explicitly specify what kind of comparison you intend to perform.</span></span> <span data-ttu-id="35546-114">這可讓程式碼更容易維護及閱讀。</span><span class="sxs-lookup"><span data-stu-id="35546-114">This makes your code much more maintainable and readable.</span></span> <span data-ttu-id="35546-115">可能的話，請使用 <xref:System.String?displayProperty=nameWithType> 和 <xref:System.Array?displayProperty=nameWithType> 類別之方法的多載，而這些類別接受 <xref:System.StringComparison> 列舉參數，以指定要執行的比較類型。</span><span class="sxs-lookup"><span data-stu-id="35546-115">Whenever possible, use the overloads of the methods of the <xref:System.String?displayProperty=nameWithType> and <xref:System.Array?displayProperty=nameWithType> classes that take a <xref:System.StringComparison> enumeration parameter, so that you can specify which type of comparison to perform.</span></span> <span data-ttu-id="35546-116">比較字串時，最好避免使用 `==` 和 `!=` 運算子。</span><span class="sxs-lookup"><span data-stu-id="35546-116">It is best to avoid using the `==` and `!=` operators when you compare strings.</span></span> <span data-ttu-id="35546-117">此外，請避免使用 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> 執行個體方法，因為沒有任何多載接受 <xref:System.StringComparison>。</span><span class="sxs-lookup"><span data-stu-id="35546-117">Also, avoid using the <xref:System.String.CompareTo%2A?displayProperty=nameWithType> instance methods because none of the overloads takes a <xref:System.StringComparison>.</span></span>

## <a name="example"></a><span data-ttu-id="35546-118">範例</span><span class="sxs-lookup"><span data-stu-id="35546-118">Example</span></span>

<span data-ttu-id="35546-119">下例示範如何正確比較不隨使用者電腦的地區設定而變更其值的字串。</span><span class="sxs-lookup"><span data-stu-id="35546-119">The following example shows how to correctly compare strings whose values will not change based on the locale of the user's computer.</span></span> <span data-ttu-id="35546-120">此外，它也會示範 C# 的「字串暫留」功能。</span><span class="sxs-lookup"><span data-stu-id="35546-120">In addition, it also demonstrates the *string interning* feature of C#.</span></span> <span data-ttu-id="35546-121">當程式宣告兩個或多個相同的字串變數時，編譯器會將它們全部儲存在相同的位置。</span><span class="sxs-lookup"><span data-stu-id="35546-121">When a program declares two or more identical string variables, the compiler stores them all in the same location.</span></span> <span data-ttu-id="35546-122">藉由呼叫 <xref:System.Object.ReferenceEquals%2A> 方法，您會看到兩個字串實際上參考記憶體中的相同物件。</span><span class="sxs-lookup"><span data-stu-id="35546-122">By calling the <xref:System.Object.ReferenceEquals%2A> method, you can see that the two strings actually refer to the same object in memory.</span></span> <span data-ttu-id="35546-123">請使用 <xref:System.String.Copy%2A?displayProperty=nameWithType> 方法來避免暫留，如範例中所示。</span><span class="sxs-lookup"><span data-stu-id="35546-123">Use the <xref:System.String.Copy%2A?displayProperty=nameWithType> method to avoid interning, as shown in the example.</span></span>

[!code-csharp[csProgGuideStrings#11](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#11)]

## <a name="example"></a><span data-ttu-id="35546-124">範例</span><span class="sxs-lookup"><span data-stu-id="35546-124">Example</span></span>

<span data-ttu-id="35546-125">下列範例示範如何使用可接受 <xref:System.StringComparison> 列舉的 <xref:System.String?displayProperty=nameWithType> 方法，以慣用方式來比較字串。</span><span class="sxs-lookup"><span data-stu-id="35546-125">The following example shows how to compare strings the preferred way by using the <xref:System.String?displayProperty=nameWithType> methods that take a <xref:System.StringComparison> enumeration.</span></span> <span data-ttu-id="35546-126">請注意，在這裡未使用 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> 執行個體方法，因為沒有任何多載接受 <xref:System.StringComparison>。</span><span class="sxs-lookup"><span data-stu-id="35546-126">Note that the <xref:System.String.CompareTo%2A?displayProperty=nameWithType> instance methods are not used here, because none of the overloads takes a <xref:System.StringComparison>.</span></span>

[!code-csharp[csProgGuideStrings#31](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#31)]

## <a name="example"></a><span data-ttu-id="35546-127">範例</span><span class="sxs-lookup"><span data-stu-id="35546-127">Example</span></span>

<span data-ttu-id="35546-128">下例示範如何使用接受 <xref:System.StringComparer?displayProperty=nameWithType> 參數的靜態 <xref:System.Array> 方法，在陣列中以區分文化特性的方式來排序及搜尋字串。</span><span class="sxs-lookup"><span data-stu-id="35546-128">The following example shows how to sort and search for strings in an array in a culture-sensitive manner by using the static <xref:System.Array> methods that take a <xref:System.StringComparer?displayProperty=nameWithType> parameter.</span></span>

[!code-csharp[csProgGuideStrings#32](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#32)]

<span data-ttu-id="35546-129">項目或索引鍵的類型為 `string` 時，<xref:System.Collections.Hashtable?displayProperty=nameWithType>、<xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> 和 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 這類集合類別具有接受 <xref:System.StringComparer?displayProperty=nameWithType> 參數的建構函式。</span><span class="sxs-lookup"><span data-stu-id="35546-129">Collection classes such as <xref:System.Collections.Hashtable?displayProperty=nameWithType>, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>, and <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> have constructors that take a <xref:System.StringComparer?displayProperty=nameWithType> parameter when the type of the elements or keys is `string`.</span></span> <span data-ttu-id="35546-130">通常應該盡可能使用這些建構函式，並指定 `Ordinal` 或 `OrdinalIgnoreCase`。</span><span class="sxs-lookup"><span data-stu-id="35546-130">In general, you should use these constructors whenever possible, and specify either `Ordinal` or `OrdinalIgnoreCase`.</span></span>

## <a name="see-also"></a><span data-ttu-id="35546-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="35546-131">See also</span></span>
 <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>  
 <xref:System.StringComparer?displayProperty=nameWithType>  
 [<span data-ttu-id="35546-132">字串</span><span class="sxs-lookup"><span data-stu-id="35546-132">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="35546-133">比較字串</span><span class="sxs-lookup"><span data-stu-id="35546-133">Comparing Strings</span></span>](../../../standard/base-types/comparing.md)  
 [<span data-ttu-id="35546-134">全球化和當地語系化應用程式</span><span class="sxs-lookup"><span data-stu-id="35546-134">Globalizing and Localizing Applications</span></span>](/visualstudio/ide/globalizing-and-localizing-applications)