---
title: "Discard - C# 指南 | Microsoft Docs"
description: "說明 C# 的 discard 支援，這是未指派且可捨棄的變數，並說明 discard 的使用方式。"
keywords: .NET, .NET Core
author: rpetrusha
ms.author: ronpet
ms.date: 07/21/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.translationtype: HT
ms.sourcegitcommit: 6170e096e36f8d054fdfe9cbd8311e6492e32a04
ms.openlocfilehash: 3f8804f9b7522e385b145a9643dec942cc1aab9f
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="discards---c-guide"></a><span data-ttu-id="dcad7-104">Discard - C# 指南</span><span class="sxs-lookup"><span data-stu-id="dcad7-104">Discards - C# Guide</span></span>

<span data-ttu-id="dcad7-105">從 C# 7 開始，C# 支援 discard，這是應用程式程式碼中刻意未使用的暫存虛擬變數。</span><span class="sxs-lookup"><span data-stu-id="dcad7-105">Starting with C# 7, C# supports discards, which are temporary, dummy variables that are intentionally unused in application code.</span></span> <span data-ttu-id="dcad7-106">Discard 相當於未指派的變數，不具有任何值。</span><span class="sxs-lookup"><span data-stu-id="dcad7-106">Discards are equivalent to unassigned variables; they do not have a value.</span></span> <span data-ttu-id="dcad7-107">因為只有一個 discard 變數，而且該變數可能甚至未配置儲存空間，所以 discard 可減少記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="dcad7-107">Because there is only a single discard variable, and that variable may not even be allocated storage, discards can reduce memory allocations.</span></span> <span data-ttu-id="dcad7-108">這些變數讓您的程式碼意圖更清楚，因而提高其可讀性和可維護性。</span><span class="sxs-lookup"><span data-stu-id="dcad7-108">Because they make the intent of your code clear, they enhance its readability and maintainability.</span></span>

<span data-ttu-id="dcad7-109">指定變數為 discard 的方式是在其名稱中指派底線 (`_`)。</span><span class="sxs-lookup"><span data-stu-id="dcad7-109">You indicate that a variable is a discard by assigning it the underscore (`_`) as its name.</span></span> <span data-ttu-id="dcad7-110">例如，下列方法呼叫會傳回 3 元組，其中的第一個和第二個值為 discard：</span><span class="sxs-lookup"><span data-stu-id="dcad7-110">For example, the following method call returns a 3-tuple in which the first and second values are discards:</span></span>

```csharp
(var _, _, area) = city.GetCityInformation(cityName);
```

<span data-ttu-id="dcad7-111">在 C# 7 中，下列內容中的指派支援 discard：</span><span class="sxs-lookup"><span data-stu-id="dcad7-111">In C# 7, discards are supported in assignments in the following contexts:</span></span>

- <span data-ttu-id="dcad7-112">元組和物件[解構](deconstruct.md)。</span><span class="sxs-lookup"><span data-stu-id="dcad7-112">Tuple and object [deconstruction](deconstruct.md).</span></span>
- <span data-ttu-id="dcad7-113">以 [is](language-reference/keywords/is.md) 和 [switch](language-reference/keywords/switch.md) 進行的模式比對。</span><span class="sxs-lookup"><span data-stu-id="dcad7-113">Pattern matching with [is](language-reference/keywords/is.md) and [switch](language-reference/keywords/switch.md).</span></span>
- <span data-ttu-id="dcad7-114">以 `out` 參數進行的方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="dcad7-114">Calls to methods with `out` parameters.</span></span>
- <span data-ttu-id="dcad7-115">範圍內沒有 `_` 時的獨立 `_`。</span><span class="sxs-lookup"><span data-stu-id="dcad7-115">A standalone `_` when no `_` is in scope.</span></span>

<span data-ttu-id="dcad7-116">當 `_` 是有效的捨棄時，嘗試擷取其值或用於指派作業會產生編譯器錯誤 CS0301：「目前內容中不存在名稱 '\_'」。</span><span class="sxs-lookup"><span data-stu-id="dcad7-116">When `_` is a valid discard, attempting to retrieve its value or use it in an assignment operation generates compiler error CS0301, "The name '\_' does not exist in the current context".</span></span> <span data-ttu-id="dcad7-117">這是因為 `_` 未指派值，可能甚至未指派儲存位置。</span><span class="sxs-lookup"><span data-stu-id="dcad7-117">This is because `_` is not assigned a value, and may not even be assigned a storage location.</span></span> <span data-ttu-id="dcad7-118">如果它原本是實際變數，可能無法像上述範例一樣捨棄多個值。</span><span class="sxs-lookup"><span data-stu-id="dcad7-118">If it were an actual variable, you could not discard more than one value, as the previous example did.</span></span>

## <a name="tuple-and-object-deconstruction"></a><span data-ttu-id="dcad7-119">元組和物件解構</span><span class="sxs-lookup"><span data-stu-id="dcad7-119">Tuple and object deconstruction</span></span>

<span data-ttu-id="dcad7-120">當您的應用程式程式碼使用一些元組項目但忽略其他項目時，discard 特別適合用來處理元組。</span><span class="sxs-lookup"><span data-stu-id="dcad7-120">Discards are particularly useful in working with tuples when your application code uses some tuple elements but ignores others.</span></span> <span data-ttu-id="dcad7-121">例如，下列 `QueryCityDataForYears` 方法會傳回 6 元組，其中包含城市名稱、其區碼、年份、該年的城市人口、次年的年份、次年的城市人口。</span><span class="sxs-lookup"><span data-stu-id="dcad7-121">For example, the following `QueryCityDataForYears` method returns a 6-tuple with the name of a city, its area, a year, the city's population for that year, a second year, and the city's population for that second year.</span></span> <span data-ttu-id="dcad7-122">此範例會顯示這兩年之間的人口變化。</span><span class="sxs-lookup"><span data-stu-id="dcad7-122">The example shows the change in population between those two years.</span></span> <span data-ttu-id="dcad7-123">在元組可用的資料中，我們對城市區碼不感興趣，並在設計階段得知城市名稱及兩個日期。</span><span class="sxs-lookup"><span data-stu-id="dcad7-123">Of the data available from the tuple, we're unconcerned with the city area, and we know the city name and the two dates at design-time.</span></span> <span data-ttu-id="dcad7-124">因此，我們只對元組中所儲存的兩個人口值感興趣，而可以將其餘值視為 discard。</span><span class="sxs-lookup"><span data-stu-id="dcad7-124">As a result, we're only interested in the two population values stored in the tuple, and can handle its remaining values as discards.</span></span>  

<span data-ttu-id="dcad7-125">[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]</span><span class="sxs-lookup"><span data-stu-id="dcad7-125">[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]</span></span>

<span data-ttu-id="dcad7-126">如需使用 discard 解構元組的詳細資訊，請參閱[解構元組和其他類型](deconstruct.md#deconstructing-tuple-elements-with-discards)。</span><span class="sxs-lookup"><span data-stu-id="dcad7-126">For more information on deconstructing tuples with discards, see [Deconstructing tuples and other types](deconstruct.md#deconstructing-tuple-elements-with-discards).</span></span>

<span data-ttu-id="dcad7-127">類別、結構或介面的 `Deconstruct` 方法也可讓您從一個物件擷取及解構一組特定的資料。</span><span class="sxs-lookup"><span data-stu-id="dcad7-127">The `Deconstruct` method of a class, structure, or interface also allows you to retrieve and deconstruct a specific set of data from an object.</span></span> <span data-ttu-id="dcad7-128">如果您只想使用部分已解構的值，可以使用 discard。</span><span class="sxs-lookup"><span data-stu-id="dcad7-128">You can use discards when you are interested in working with only a subset of the deconstructed values.</span></span> <span data-ttu-id="dcad7-129">下列範例會將 `Person` 物件解構為四個字串 (名字、姓氏、城市和州/省)，但捨棄姓氏和州/省。</span><span class="sxs-lookup"><span data-stu-id="dcad7-129">Ihe following example deconstructs a `Person` object into four strings (the first and last names, the city, and the state), but discards the last name and the state.</span></span>

<span data-ttu-id="dcad7-130">[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]</span><span class="sxs-lookup"><span data-stu-id="dcad7-130">[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]</span></span>

<span data-ttu-id="dcad7-131">如需使用 discard 解構使用者定義型別的詳細資訊，請參閱[解構元組和其他類型](deconstruct.md#deconstructing-a-user-defined-type-with-discards)。</span><span class="sxs-lookup"><span data-stu-id="dcad7-131">For more information on deconstructing user-defined types with discards, see [Deconstructing tuples and other types](deconstruct.md#deconstructing-a-user-defined-type-with-discards).</span></span>

## <a name="pattern-matching-with-switch-and-is"></a><span data-ttu-id="dcad7-132">以 `switch` 和 `is` 進行的模式比對</span><span class="sxs-lookup"><span data-stu-id="dcad7-132">Pattern matching with `switch` and `is`</span></span>

<span data-ttu-id="dcad7-133">「捨棄模式」可用於以 [is](language-reference/keywords/is.md) 和 [switch](language-reference/keywords/switch.md) 關鍵字進行的模式比對。</span><span class="sxs-lookup"><span data-stu-id="dcad7-133">The *discard pattern* can be used in pattern matching with the [is](language-reference/keywords/is.md) and [switch](language-reference/keywords/switch.md) keywords.</span></span> <span data-ttu-id="dcad7-134">每個運算式一律會比對捨棄模式。</span><span class="sxs-lookup"><span data-stu-id="dcad7-134">Every expression always matches the discard pattern.</span></span>

<span data-ttu-id="dcad7-135">下列範例會定義 `ProvidesFormatInfo` 方法，該方法使用 [is](language-reference/keywords/is.md) 陳述式來判斷物件是否提供 <xref:System.IFormatProvider> 實作，並測試物件是否為 `null`。</span><span class="sxs-lookup"><span data-stu-id="dcad7-135">The following example defines a `ProvidesFormatInfo` method that uses [is](language-reference/keywords/is.md) statements to determine whether an object provides an <xref:System.IFormatProvider> implementation and tests whether the object is `null`.</span></span> <span data-ttu-id="dcad7-136">它也會使用捨棄模式來處理任何其他類型的非 Null 物件。</span><span class="sxs-lookup"><span data-stu-id="dcad7-136">It also uses the discard pattern to handle non-null objects of any other type.</span></span>

<span data-ttu-id="dcad7-137">[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]</span><span class="sxs-lookup"><span data-stu-id="dcad7-137">[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]</span></span>

## <a name="calls-to-methods-with-out-parameters"></a><span data-ttu-id="dcad7-138">以 out 參數進行的方法呼叫</span><span class="sxs-lookup"><span data-stu-id="dcad7-138">Calls to methods with out parameters</span></span>

<span data-ttu-id="dcad7-139">當呼叫 `Deconstruct` 方法解構使用者定義型別 (類別、結構或介面的執行個體) 時，您可以捨棄個別 `out` 引數的值。</span><span class="sxs-lookup"><span data-stu-id="dcad7-139">When calling the `Deconstruct` method to deconstruct a user-defined type (an instance of a class, structure, or interface), you can discard the values of individual `out` arguments.</span></span> <span data-ttu-id="dcad7-140">但當使用 out 參數呼叫任何方法時，您也可以捨棄 `out` 引數的值。</span><span class="sxs-lookup"><span data-stu-id="dcad7-140">But you can also discard the value of `out` arguments when calling any method with an out parameter.</span></span> 

<span data-ttu-id="dcad7-141">下列範例會呼叫 [DateTime.TryParse(String, out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) 方法，以判斷日期的字串表示在目前的文化特性 (culture) 中是否有效。</span><span class="sxs-lookup"><span data-stu-id="dcad7-141">The following example calls the [DateTime.TryParse(String, out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) method to determine whether the string representation of a date is valid in the current culture.</span></span> <span data-ttu-id="dcad7-142">因為此範例只需要驗證日期字串，而不需要將它剖析以擷取日期，所以該方法的 `out` 引數為 discard。</span><span class="sxs-lookup"><span data-stu-id="dcad7-142">Because the example is concerned only with validating the date string and not with parsing it to extract the date, the `out` argument to the method is a discard.</span></span>

<span data-ttu-id="dcad7-143">[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]</span><span class="sxs-lookup"><span data-stu-id="dcad7-143">[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]</span></span>

## <a name="a-standalone-discard"></a><span data-ttu-id="dcad7-144">獨立 discard</span><span class="sxs-lookup"><span data-stu-id="dcad7-144">A standalone discard</span></span>

<span data-ttu-id="dcad7-145">您可以使用獨立 discard，指出您選擇忽略的任何變數。</span><span class="sxs-lookup"><span data-stu-id="dcad7-145">You can use a standalone discard to indicate any variable that you choose to ignore.</span></span> <span data-ttu-id="dcad7-146">下列範例會使用獨立 discard 來忽略非同步作業傳回的 <xref:System.Threading.Tasks.Task> 物件。</span><span class="sxs-lookup"><span data-stu-id="dcad7-146">The following example uses a standalone discard to ignore the <xref:System.Threading.Tasks.Task> object returned by an asynchronous operation.</span></span> <span data-ttu-id="dcad7-147">這會造成在作業即將完成時，隱藏作業所擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="dcad7-147">This has the effect of suppressing the exception that the operation throws as it is about to complete.</span></span>

<span data-ttu-id="dcad7-148">[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]</span><span class="sxs-lookup"><span data-stu-id="dcad7-148">[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]</span></span>

<span data-ttu-id="dcad7-149">請注意，`_` 也是有效的識別項。</span><span class="sxs-lookup"><span data-stu-id="dcad7-149">Note that `_` is also a valid identifier.</span></span> <span data-ttu-id="dcad7-150">在支援的內容之外使用時，`_` 會視為有效的變數，而不是 discard。</span><span class="sxs-lookup"><span data-stu-id="dcad7-150">When used outside of a supported context, `_` is treated not as a discard but as a valid variable.</span></span> <span data-ttu-id="dcad7-151">如果範圍內已有名為 `_` 的識別項，使用 `_` 作為獨立 discard 可能會導致：</span><span class="sxs-lookup"><span data-stu-id="dcad7-151">If an identifier named `_` is already in scope, the use of `_` as a standalone discard can result in:</span></span>

- <span data-ttu-id="dcad7-152">將預定的 dscard 值指派給範圍內的 `_` 變數，而意外修改變數的值。</span><span class="sxs-lookup"><span data-stu-id="dcad7-152">Accidental modification of the value of the in-scope `_` variable by assigning it the value of the intended discard.</span></span> <span data-ttu-id="dcad7-153">例如: </span><span class="sxs-lookup"><span data-stu-id="dcad7-153">For example:</span></span>

   <span data-ttu-id="dcad7-154">[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="dcad7-154">[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]</span></span>
 
- <span data-ttu-id="dcad7-155">違反型別安全的編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="dcad7-155">A compiler error for violating type safety.</span></span> <span data-ttu-id="dcad7-156">例如: </span><span class="sxs-lookup"><span data-stu-id="dcad7-156">For example:</span></span>

   <span data-ttu-id="dcad7-157">[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]</span><span class="sxs-lookup"><span data-stu-id="dcad7-157">[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]</span></span>
 
- <span data-ttu-id="dcad7-158">編譯器錯誤 CS0136：「無法在此範圍宣告名為 '_' 的區域變數或參數，因為該名稱已用於封入區域變數範圍，以定義區域變數或參數」。</span><span class="sxs-lookup"><span data-stu-id="dcad7-158">Compiler error CS0136, "A local or parameter named '_' cannot be declared in this scope because that name is used in an enclosing local scope to define a local or parameter."</span></span> <span data-ttu-id="dcad7-159">例如: </span><span class="sxs-lookup"><span data-stu-id="dcad7-159">For example:</span></span>

   <span data-ttu-id="dcad7-160">[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]</span><span class="sxs-lookup"><span data-stu-id="dcad7-160">[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]</span></span>

## <a name="see-also"></a><span data-ttu-id="dcad7-161">請參閱</span><span class="sxs-lookup"><span data-stu-id="dcad7-161">See also</span></span>
<span data-ttu-id="dcad7-162">[解構元組和其他類型](deconstruct.md) </span><span class="sxs-lookup"><span data-stu-id="dcad7-162">[Deconstructing tuples and other types](deconstruct.md) </span></span>  
<span data-ttu-id="dcad7-163">[`is` 關鍵字](language-reference/keywords/is.md) </span><span class="sxs-lookup"><span data-stu-id="dcad7-163">[`is` keyword](language-reference/keywords/is.md) </span></span>  
[<span data-ttu-id="dcad7-164">`switch` 關鍵字</span><span class="sxs-lookup"><span data-stu-id="dcad7-164">`switch` keyword</span></span>](language-reference/keywords/switch.md)   

