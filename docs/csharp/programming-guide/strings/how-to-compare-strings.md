---
title: "如何：比較字串 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.assetid: e1268e28-ee98-4695-98e9-92280f1c33c0
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 494b9ef1a1e6c8958dd3df2edb44debf32690eeb
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-compare-strings-c-programming-guide"></a><span data-ttu-id="45f56-102">如何：比較字串 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="45f56-102">How to: Compare Strings (C# Programming Guide)</span></span>
<span data-ttu-id="45f56-103">當您比較字串時，您產生的結果會顯示一個字串是大於或小於另一個，或兩個字串相等。</span><span class="sxs-lookup"><span data-stu-id="45f56-103">When you compare strings, you are producing a result that says one string is greater than or less than the other, or that the two strings are equal.</span></span> <span data-ttu-id="45f56-104">決定結果的規則會隨您執行「序數比較」或「區分文化特性比較」而異。</span><span class="sxs-lookup"><span data-stu-id="45f56-104">The rules by which the result is determined are different depending on whether you are performing *ordinal comparison* or *culture-sensitive comparison*.</span></span> <span data-ttu-id="45f56-105">特定工作請務必使用正確的比較類型。</span><span class="sxs-lookup"><span data-stu-id="45f56-105">It is important to use the correct kind of comparison for the specific task.</span></span>  
  
 <span data-ttu-id="45f56-106">當您必須比較或排序兩個字串的值，但不考慮語言慣例時，請使用基本的序數比較。</span><span class="sxs-lookup"><span data-stu-id="45f56-106">Use basic ordinal comparisons when you have to compare or sort the values of two strings without regard to linguistic conventions.</span></span> <span data-ttu-id="45f56-107">基本的序數比較 (`System.StringComparison.Ordinal`) 會區分大小寫，這表示兩個字串必須逐字元比對："and" 不等於 "And" 或 "AND"。</span><span class="sxs-lookup"><span data-stu-id="45f56-107">A basic ordinal comparison (`System.StringComparison.Ordinal`) is case-sensitive, which means that the two strings must match character for character: "and" does not equal "And" or "AND".</span></span> <span data-ttu-id="45f56-108">常用的變化是 `System.StringComparison.OrdinalIgnoreCase`，它會比對 "and"、"And" 和 "AND"。</span><span class="sxs-lookup"><span data-stu-id="45f56-108">A frequently-used variation is `System.StringComparison.OrdinalIgnoreCase`, which will match "and", "And", and "AND".</span></span> <span data-ttu-id="45f56-109">`StringComparison.OrdinalIgnoreCase` 通常用來比較檔案名稱、路徑名稱、網路路徑，以及不會隨使用者電腦的地區設定而變更其值的任何其他字串。</span><span class="sxs-lookup"><span data-stu-id="45f56-109">`StringComparison.OrdinalIgnoreCase` is often used to compare file names, path names, network paths, and any other string whose value does not change based on the locale of the user's computer.</span></span> <span data-ttu-id="45f56-110">如需詳細資訊，請參閱<xref:System.StringComparison?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="45f56-110">For more information, see <xref:System.StringComparison?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="45f56-111">區分文化特性比較通常用於比較和排序使用者輸入的字串，因為這些字串的字元和排序慣例可能會隨使用者電腦的地區設定而異。</span><span class="sxs-lookup"><span data-stu-id="45f56-111">Culture-sensitive comparisons are typically used to compare and sort strings that are input by end users, because the characters and sorting conventions of these strings might vary depending on the locale of the user's computer.</span></span> <span data-ttu-id="45f56-112">即使包含完全相同字元的字串，也可能因目前執行緒的文化特性而改變排序。</span><span class="sxs-lookup"><span data-stu-id="45f56-112">Even strings that contain identical characters might sort differently depending on the culture of the current thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45f56-113">當您比較字串時，您應該使用明確指定打算執行比較類型的方法。</span><span class="sxs-lookup"><span data-stu-id="45f56-113">When you compare strings, you should use the methods that explicitly specify what kind of comparison you intend to perform.</span></span> <span data-ttu-id="45f56-114">這可讓程式碼更容易維護及閱讀。</span><span class="sxs-lookup"><span data-stu-id="45f56-114">This makes your code much more maintainable and readable.</span></span> <span data-ttu-id="45f56-115">可能的話，請使用 <xref:System.String?displayProperty=fullName> 和 <xref:System.Array?displayProperty=fullName> 類別之方法的多載，而這些類別接受 <xref:System.StringComparison> 列舉參數，以指定要執行的比較類型。</span><span class="sxs-lookup"><span data-stu-id="45f56-115">Whenever possible, use the overloads of the methods of the <xref:System.String?displayProperty=fullName> and <xref:System.Array?displayProperty=fullName> classes that take a <xref:System.StringComparison> enumeration parameter, so that you can specify which type of comparison to perform.</span></span> <span data-ttu-id="45f56-116">比較字串時，最好避免使用 `==` 和 `!=` 運算子。</span><span class="sxs-lookup"><span data-stu-id="45f56-116">It is best to avoid using the `==` and `!=` operators when you compare strings.</span></span> <span data-ttu-id="45f56-117">此外，請避免使用 <xref:System.String.CompareTo%2A?displayProperty=fullName> 執行個體方法，因為沒有任何多載接受 <xref:System.StringComparison>。</span><span class="sxs-lookup"><span data-stu-id="45f56-117">Also, avoid using the <xref:System.String.CompareTo%2A?displayProperty=fullName> instance methods because none of the overloads takes a <xref:System.StringComparison>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45f56-118">範例</span><span class="sxs-lookup"><span data-stu-id="45f56-118">Example</span></span>  
 <span data-ttu-id="45f56-119">下例示範如何正確比較不隨使用者電腦的地區設定而變更其值的字串。</span><span class="sxs-lookup"><span data-stu-id="45f56-119">The following example shows how to correctly compare strings whose values will not change based on the locale of the user's computer.</span></span> <span data-ttu-id="45f56-120">此外，它也會示範 C# 的「字串暫留」功能。</span><span class="sxs-lookup"><span data-stu-id="45f56-120">In addition, it also demonstrates the *string interning* feature of C#.</span></span> <span data-ttu-id="45f56-121">當程式宣告兩個或多個相同的字串變數時，編譯器會將它們全部儲存在相同的位置。</span><span class="sxs-lookup"><span data-stu-id="45f56-121">When a program declares two or more identical string variables, the compiler stores them all in the same location.</span></span> <span data-ttu-id="45f56-122">藉由呼叫 <xref:System.Object.ReferenceEquals%2A> 方法，您會看到兩個字串實際上參考記憶體中的相同物件。</span><span class="sxs-lookup"><span data-stu-id="45f56-122">By calling the <xref:System.Object.ReferenceEquals%2A> method, you can see that the two strings actually refer to the same object in memory.</span></span> <span data-ttu-id="45f56-123">請使用 <xref:System.String.Copy%2A?displayProperty=fullName> 方法來避免暫留，如範例中所示。</span><span class="sxs-lookup"><span data-stu-id="45f56-123">Use the <xref:System.String.Copy%2A?displayProperty=fullName> method to avoid interning, as shown in the example.</span></span>  
  
 <span data-ttu-id="45f56-124">[!code-cs[csProgGuideStrings#11](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="45f56-124">[!code-cs[csProgGuideStrings#11](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="45f56-125">範例</span><span class="sxs-lookup"><span data-stu-id="45f56-125">Example</span></span>  
 <span data-ttu-id="45f56-126">下列範例示範如何使用可接受 <xref:System.StringComparison> 列舉的 <xref:System.String?displayProperty=fullName> 方法，以慣用方式來比較字串。</span><span class="sxs-lookup"><span data-stu-id="45f56-126">The following example shows how to compare strings the preferred way by using the <xref:System.String?displayProperty=fullName> methods that take a <xref:System.StringComparison> enumeration.</span></span> <span data-ttu-id="45f56-127">請注意，在這裡未使用 <xref:System.String.CompareTo%2A?displayProperty=fullName> 執行個體方法，因為沒有任何多載接受 <xref:System.StringComparison>。</span><span class="sxs-lookup"><span data-stu-id="45f56-127">Note that the <xref:System.String.CompareTo%2A?displayProperty=fullName> instance methods are not used here, because none of the overloads takes a <xref:System.StringComparison>.</span></span>  
  
 <span data-ttu-id="45f56-128">[!code-cs[csProgGuideStrings#31](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="45f56-128">[!code-cs[csProgGuideStrings#31](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="45f56-129">範例</span><span class="sxs-lookup"><span data-stu-id="45f56-129">Example</span></span>  
 <span data-ttu-id="45f56-130">下例示範如何使用接受 <xref:System.StringComparer?displayProperty=fullName> 參數的靜態 <xref:System.Array> 方法，在陣列中以區分文化特性的方式來排序及搜尋字串。</span><span class="sxs-lookup"><span data-stu-id="45f56-130">The following example shows how to sort and search for strings in an array in a culture-sensitive manner by using the static <xref:System.Array> methods that take a <xref:System.StringComparer?displayProperty=fullName> parameter.</span></span>  
  
 <span data-ttu-id="45f56-131">[!code-cs[csProgGuideStrings#32](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="45f56-131">[!code-cs[csProgGuideStrings#32](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_3.cs)]</span></span>  
  
 <span data-ttu-id="45f56-132">項目或索引鍵的類型為 `string` 時，<xref:System.Collections.Hashtable?displayProperty=fullName>、<xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> 和 <xref:System.Collections.Generic.List%601?displayProperty=fullName> 這類集合類別具有接受 <xref:System.StringComparer?displayProperty=fullName> 參數的建構函式。</span><span class="sxs-lookup"><span data-stu-id="45f56-132">Collection classes such as <xref:System.Collections.Hashtable?displayProperty=fullName>, <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>, and <xref:System.Collections.Generic.List%601?displayProperty=fullName> have constructors that take a <xref:System.StringComparer?displayProperty=fullName> parameter when the type of the elements or keys is `string`.</span></span> <span data-ttu-id="45f56-133">通常應該盡可能使用這些建構函式，並指定 `Ordinal` 或 `OrdinalIgnoreCase`。</span><span class="sxs-lookup"><span data-stu-id="45f56-133">In general, you should use these constructors whenever possible, and specify either `Ordinal` or `OrdinalIgnoreCase`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45f56-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45f56-134">See Also</span></span>  
 <span data-ttu-id="45f56-135"><xref:System.Globalization.CultureInfo?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="45f56-135"><xref:System.Globalization.CultureInfo?displayProperty=fullName></span></span>   
 <span data-ttu-id="45f56-136"><xref:System.StringComparer?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="45f56-136"><xref:System.StringComparer?displayProperty=fullName></span></span>   
 <span data-ttu-id="45f56-137">[字串](../../../csharp/programming-guide/strings/index.md) </span><span class="sxs-lookup"><span data-stu-id="45f56-137">[Strings](../../../csharp/programming-guide/strings/index.md) </span></span>  
 <span data-ttu-id="45f56-138">[比較字串](../../../standard/base-types/comparing.md) </span><span class="sxs-lookup"><span data-stu-id="45f56-138">[Comparing Strings](../../../standard/base-types/comparing.md) </span></span>  
 [<span data-ttu-id="45f56-139">全球化和當地語系化應用程式</span><span class="sxs-lookup"><span data-stu-id="45f56-139">Globalizing and Localizing Applications</span></span>](/visualstudio/ide/globalizing-and-localizing-applications)

