---
title: "dynamic (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- dynamic_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- dynamic [C#]
- dynamic keyword [C#]
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
caps.latest.revision: 25
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
ms.openlocfilehash: b68a6ef4dc3dda01638b9bb84db58ba77214f490
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="dynamic-c-reference"></a><span data-ttu-id="99f57-102">dynamic (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="99f57-102">dynamic (C# Reference)</span></span>
<span data-ttu-id="99f57-103">`dynamic` 類型可讓發生它的作業略過編譯時期類型檢查。</span><span class="sxs-lookup"><span data-stu-id="99f57-103">The `dynamic` type enables the operations in which it occurs to bypass compile-time type checking.</span></span> <span data-ttu-id="99f57-104">相反地，這些作業會在執行階段解決。</span><span class="sxs-lookup"><span data-stu-id="99f57-104">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="99f57-105">`dynamic` 類型會簡化 Office Automation API 這類 COM API 的存取、IronPython 程式庫這類動態 API 的存取，以及 HTML 文件物件模型 (DOM) 的存取。</span><span class="sxs-lookup"><span data-stu-id="99f57-105">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, and also to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>  
  
 <span data-ttu-id="99f57-106">在大多數情況下，`dynamic` 類型的行為與 `object` 類型類似。</span><span class="sxs-lookup"><span data-stu-id="99f57-106">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="99f57-107">不過，不會解決包含 `dynamic` 類型之運算式的作業，或編譯器不會對其進行類型檢查。</span><span class="sxs-lookup"><span data-stu-id="99f57-107">However, operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="99f57-108">編譯器會將作業資訊封裝在一起，而且稍後在執行階段會使用這項資訊來評估作業。</span><span class="sxs-lookup"><span data-stu-id="99f57-108">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="99f57-109">在此程序期間，會將 `dynamic` 類型的變數編譯為 `object` 類型的變數。</span><span class="sxs-lookup"><span data-stu-id="99f57-109">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="99f57-110">因此，`dynamic` 類型只存在於編譯時期，而非執行階段。</span><span class="sxs-lookup"><span data-stu-id="99f57-110">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>  
  
 <span data-ttu-id="99f57-111">下列範例會對照 `dynamic` 類型的變數與 `object` 類型的變數。</span><span class="sxs-lookup"><span data-stu-id="99f57-111">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="99f57-112">若要在編譯時期驗證每個變數的類型，請將滑鼠指標放在 `WriteLine` 陳述式中的 `dyn` 或 `obj` 上方。</span><span class="sxs-lookup"><span data-stu-id="99f57-112">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="99f57-113">IntelliSense 會顯示「動態」來表示 `dyn`，並顯示「物件」來表示 `obj`。</span><span class="sxs-lookup"><span data-stu-id="99f57-113">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>  
  
 <span data-ttu-id="99f57-114">[!code-cs[csrefKeywordsTypes#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="99f57-114">[!code-cs[csrefKeywordsTypes#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_1.cs)]</span></span>  
  
 <span data-ttu-id="99f57-115">`WriteLine` 陳述式會顯示執行階段類型 `dyn` 和 `obj`。</span><span class="sxs-lookup"><span data-stu-id="99f57-115">The `WriteLine` statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="99f57-116">此時，兩者都有相同的類型：整數。</span><span class="sxs-lookup"><span data-stu-id="99f57-116">At that point, both have the same type, integer.</span></span> <span data-ttu-id="99f57-117">會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="99f57-117">The following output is produced:</span></span>  
  
 `System.Int32`  
  
 `System.Int32`  
  
 <span data-ttu-id="99f57-118">若要查看 `dyn` 與 `obj` 在編譯時期的差異，請在上述範例的宣告與 `WriteLine` 陳述式之間新增下列兩行。</span><span class="sxs-lookup"><span data-stu-id="99f57-118">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>  
  
```csharp  
dyn = dyn + 3;  
obj = obj + 3;  
```  
  
 <span data-ttu-id="99f57-119">嘗試新增運算式 `obj + 3` 中的整數和物件時報告編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="99f57-119">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="99f57-120">不過，不會回報 `dyn + 3` 的錯誤。</span><span class="sxs-lookup"><span data-stu-id="99f57-120">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="99f57-121">在編譯時期不會檢查包含 `dyn` 的運算式，因為 `dyn` 的類型是 `dynamic`。</span><span class="sxs-lookup"><span data-stu-id="99f57-121">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>  
  
## <a name="context"></a><span data-ttu-id="99f57-122">內容</span><span class="sxs-lookup"><span data-stu-id="99f57-122">Context</span></span>  
 <span data-ttu-id="99f57-123">在下列情況下，`dynamic` 關鍵字可能會直接出現，或作為建構類型的元件︰</span><span class="sxs-lookup"><span data-stu-id="99f57-123">The `dynamic` keyword can appear directly or as a component of a constructed type in the following situations:</span></span>  
  
-   <span data-ttu-id="99f57-124">在宣告中，作為屬性、欄位、索引子、參數、傳回值、區域變數或類型條件約束的類型。</span><span class="sxs-lookup"><span data-stu-id="99f57-124">In declarations, as the type of a property, field, indexer, parameter, return value, local variable, or type constraint.</span></span> <span data-ttu-id="99f57-125">下列類別定義在數個不同宣告中使用 `dynamic`。</span><span class="sxs-lookup"><span data-stu-id="99f57-125">The following class definition uses `dynamic` in several different declarations.</span></span>  
  
     <span data-ttu-id="99f57-126">[!code-cs[csrefKeywordsTypes#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="99f57-126">[!code-cs[csrefKeywordsTypes#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_2.cs)]</span></span>  
  
-   <span data-ttu-id="99f57-127">在明確類型轉換中，作為轉換的目標類型。</span><span class="sxs-lookup"><span data-stu-id="99f57-127">In explicit type conversions, as the target type of a conversion.</span></span>  
  
     <span data-ttu-id="99f57-128">[!code-cs[csrefKeywordsTypes#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="99f57-128">[!code-cs[csrefKeywordsTypes#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_3.cs)]</span></span>  
  
-   <span data-ttu-id="99f57-129">在任何內容中，其中類型作為值 (例如 `is` 運算子或 `as` 運算子右側) 或作為部分建構類型之 `typeof` 的引數。</span><span class="sxs-lookup"><span data-stu-id="99f57-129">In any context where types serve as values, such as on the right side of an `is` operator or an `as` operator, or as the argument to `typeof` as part of a constructed type.</span></span> <span data-ttu-id="99f57-130">例如，`dynamic` 可以用於下列運算式中。</span><span class="sxs-lookup"><span data-stu-id="99f57-130">For example, `dynamic` can be used in the following expressions.</span></span>  
  
     <span data-ttu-id="99f57-131">[!code-cs[csrefKeywordsTypes#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="99f57-131">[!code-cs[csrefKeywordsTypes#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_4.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="99f57-132">範例</span><span class="sxs-lookup"><span data-stu-id="99f57-132">Example</span></span>  
 <span data-ttu-id="99f57-133">下列範例會在數個宣告中使用 `dynamic`。</span><span class="sxs-lookup"><span data-stu-id="99f57-133">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="99f57-134">`Main` 方法也會對照編譯時期類型檢查與執行階段類型檢查。</span><span class="sxs-lookup"><span data-stu-id="99f57-134">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>  
  
 <span data-ttu-id="99f57-135">[!code-cs[csrefKeywordsTypes#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="99f57-135">[!code-cs[csrefKeywordsTypes#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_5.cs)]</span></span>  
  
 <span data-ttu-id="99f57-136">如需詳細資訊和範例，請參閱[使用動態類型](../../../csharp/programming-guide/types/using-type-dynamic.md)。</span><span class="sxs-lookup"><span data-stu-id="99f57-136">For more information and examples, see [Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99f57-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99f57-137">See Also</span></span>  
 <span data-ttu-id="99f57-138"><xref:System.Dynamic.ExpandoObject?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="99f57-138"><xref:System.Dynamic.ExpandoObject?displayProperty=fullName></span></span>   
 <span data-ttu-id="99f57-139"><xref:System.Dynamic.DynamicObject?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="99f57-139"><xref:System.Dynamic.DynamicObject?displayProperty=fullName></span></span>   
 <span data-ttu-id="99f57-140">[使用動態類型](../../../csharp/programming-guide/types/using-type-dynamic.md) </span><span class="sxs-lookup"><span data-stu-id="99f57-140">[Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md) </span></span>  
 <span data-ttu-id="99f57-141">[object](../../../csharp/language-reference/keywords/object.md) </span><span class="sxs-lookup"><span data-stu-id="99f57-141">[object](../../../csharp/language-reference/keywords/object.md) </span></span>  
 <span data-ttu-id="99f57-142">[is](../../../csharp/language-reference/keywords/is.md) </span><span class="sxs-lookup"><span data-stu-id="99f57-142">[is](../../../csharp/language-reference/keywords/is.md) </span></span>  
 <span data-ttu-id="99f57-143">[as](../../../csharp/language-reference/keywords/as.md) </span><span class="sxs-lookup"><span data-stu-id="99f57-143">[as](../../../csharp/language-reference/keywords/as.md) </span></span>  
 <span data-ttu-id="99f57-144">[typeof](../../../csharp/language-reference/keywords/typeof.md) </span><span class="sxs-lookup"><span data-stu-id="99f57-144">[typeof](../../../csharp/language-reference/keywords/typeof.md) </span></span>  
 <span data-ttu-id="99f57-145">[如何：使用 as 和 is 運算子進行安全轉換](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md) </span><span class="sxs-lookup"><span data-stu-id="99f57-145">[How to: Safely Cast by Using as and is Operators](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md) </span></span>  
 [<span data-ttu-id="99f57-146">逐步解說：建立和使用動態物件</span><span class="sxs-lookup"><span data-stu-id="99f57-146">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)

