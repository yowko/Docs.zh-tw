---
title: Discard - C# 指南
description: 說明 C# 的 discard 支援，這是未指派且可捨棄的變數，並說明 discard 的使用方式。
author: rpetrusha
ms.author: ronpet
ms.date: 07/21/2017
ms.openlocfilehash: 761fb69d3bc774975caf63b8aa665f8c19c0430a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143593"
---
# <a name="discards---c-guide"></a><span data-ttu-id="5e084-103">Discard - C# 指南</span><span class="sxs-lookup"><span data-stu-id="5e084-103">Discards - C# Guide</span></span>

<span data-ttu-id="5e084-104">從 C# 7.0 開始，C# 支援 discard，這是應用程式程式碼中刻意未使用的暫存虛擬變數。</span><span class="sxs-lookup"><span data-stu-id="5e084-104">Starting with C# 7.0, C# supports discards, which are temporary, dummy variables that are intentionally unused in application code.</span></span> <span data-ttu-id="5e084-105">Discard 相當於未指派的變數，不具有任何值。</span><span class="sxs-lookup"><span data-stu-id="5e084-105">Discards are equivalent to unassigned variables; they do not have a value.</span></span> <span data-ttu-id="5e084-106">因為只有一個 discard 變數，而且該變數可能甚至未配置儲存空間，所以 discard 可減少記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="5e084-106">Because there is only a single discard variable, and that variable may not even be allocated storage, discards can reduce memory allocations.</span></span> <span data-ttu-id="5e084-107">這些變數讓您的程式碼意圖更清楚，因而提高其可讀性和可維護性。</span><span class="sxs-lookup"><span data-stu-id="5e084-107">Because they make the intent of your code clear, they enhance its readability and maintainability.</span></span>

<span data-ttu-id="5e084-108">指定變數為 discard 的方式是在其名稱中指派底線 (`_`)。</span><span class="sxs-lookup"><span data-stu-id="5e084-108">You indicate that a variable is a discard by assigning it the underscore (`_`) as its name.</span></span> <span data-ttu-id="5e084-109">例如，下列方法呼叫會傳回 3 Tuple，其中第一個和第二個值會被捨棄，而*area* 是先前宣告的變數，要設定為 *GetCityInformation* 所傳回的第三個對應元件：</span><span class="sxs-lookup"><span data-stu-id="5e084-109">For example, the following method call returns a 3-tuple in which the first and second values are discards and *area* is a previously declared variable to be set to the corresponding third component returned by *GetCityInformation*:</span></span>

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

<span data-ttu-id="5e084-110">在 C# 7.0 中，下列內容中的指派支援 discard：</span><span class="sxs-lookup"><span data-stu-id="5e084-110">In C# 7.0, discards are supported in assignments in the following contexts:</span></span>

- <span data-ttu-id="5e084-111">元組和物件[解構](deconstruct.md)。</span><span class="sxs-lookup"><span data-stu-id="5e084-111">Tuple and object [deconstruction](deconstruct.md).</span></span>
- <span data-ttu-id="5e084-112">以 [is](language-reference/keywords/is.md) 和 [switch](language-reference/keywords/switch.md) 進行的模式比對。</span><span class="sxs-lookup"><span data-stu-id="5e084-112">Pattern matching with [is](language-reference/keywords/is.md) and [switch](language-reference/keywords/switch.md).</span></span>
- <span data-ttu-id="5e084-113">以 `out` 參數進行的方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="5e084-113">Calls to methods with `out` parameters.</span></span>
- <span data-ttu-id="5e084-114">範圍內沒有 `_` 時的獨立 `_`。</span><span class="sxs-lookup"><span data-stu-id="5e084-114">A standalone `_` when no `_` is in scope.</span></span>

<span data-ttu-id="5e084-115">當 `_` 是有效的捨棄時，嘗試擷取其值或用於指派作業會產生編譯器錯誤 CS0301：「目前內容中不存在名稱 '\_'」。</span><span class="sxs-lookup"><span data-stu-id="5e084-115">When `_` is a valid discard, attempting to retrieve its value or use it in an assignment operation generates compiler error CS0301, "The name '\_' does not exist in the current context".</span></span> <span data-ttu-id="5e084-116">這是因為 `_` 未指派值，可能甚至未指派儲存位置。</span><span class="sxs-lookup"><span data-stu-id="5e084-116">This is because `_` is not assigned a value, and may not even be assigned a storage location.</span></span> <span data-ttu-id="5e084-117">如果它原本是實際變數，可能無法像上述範例一樣捨棄多個值。</span><span class="sxs-lookup"><span data-stu-id="5e084-117">If it were an actual variable, you could not discard more than one value, as the previous example did.</span></span>

## <a name="tuple-and-object-deconstruction"></a><span data-ttu-id="5e084-118">元組和物件解構</span><span class="sxs-lookup"><span data-stu-id="5e084-118">Tuple and object deconstruction</span></span>

<span data-ttu-id="5e084-119">當您的應用程式程式碼使用一些元組項目但忽略其他項目時，discard 特別適合用來處理元組。</span><span class="sxs-lookup"><span data-stu-id="5e084-119">Discards are particularly useful in working with tuples when your application code uses some tuple elements but ignores others.</span></span> <span data-ttu-id="5e084-120">例如，下列 `QueryCityDataForYears` 方法會傳回 6 元組，其中包含城市名稱、其區碼、年份、該年的城市人口、次年的年份、次年的城市人口。</span><span class="sxs-lookup"><span data-stu-id="5e084-120">For example, the following `QueryCityDataForYears` method returns a 6-tuple with the name of a city, its area, a year, the city's population for that year, a second year, and the city's population for that second year.</span></span> <span data-ttu-id="5e084-121">此範例會顯示這兩年之間的人口變化。</span><span class="sxs-lookup"><span data-stu-id="5e084-121">The example shows the change in population between those two years.</span></span> <span data-ttu-id="5e084-122">在元組可用的資料中，我們對城市區碼不感興趣，並在設計階段得知城市名稱及兩個日期。</span><span class="sxs-lookup"><span data-stu-id="5e084-122">Of the data available from the tuple, we're unconcerned with the city area, and we know the city name and the two dates at design-time.</span></span> <span data-ttu-id="5e084-123">因此，我們只對元組中所儲存的兩個人口值感興趣，而可以將其餘值視為 discard。</span><span class="sxs-lookup"><span data-stu-id="5e084-123">As a result, we're only interested in the two population values stored in the tuple, and can handle its remaining values as discards.</span></span>  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

<span data-ttu-id="5e084-124">如需使用 discard 解構元組的詳細資訊，請參閱[解構元組和其他類型](deconstruct.md#deconstructing-tuple-elements-with-discards)。</span><span class="sxs-lookup"><span data-stu-id="5e084-124">For more information on deconstructing tuples with discards, see [Deconstructing tuples and other types](deconstruct.md#deconstructing-tuple-elements-with-discards).</span></span>

<span data-ttu-id="5e084-125">類別、結構或介面的 `Deconstruct` 方法也可讓您從一個物件擷取及解構一組特定的資料。</span><span class="sxs-lookup"><span data-stu-id="5e084-125">The `Deconstruct` method of a class, structure, or interface also allows you to retrieve and deconstruct a specific set of data from an object.</span></span> <span data-ttu-id="5e084-126">如果您只想使用部分已解構的值，可以使用 discard。</span><span class="sxs-lookup"><span data-stu-id="5e084-126">You can use discards when you are interested in working with only a subset of the deconstructed values.</span></span> <span data-ttu-id="5e084-127">下列範例會將 `Person` 物件解構為四個字串 (名字、姓氏、城市和州/省)，但捨棄姓氏和州/省。</span><span class="sxs-lookup"><span data-stu-id="5e084-127">The following example deconstructs a `Person` object into four strings (the first and last names, the city, and the state), but discards the last name and the state.</span></span>

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]

<span data-ttu-id="5e084-128">如需使用 discard 解構使用者定義型別的詳細資訊，請參閱[解構元組和其他類型](deconstruct.md#deconstructing-a-user-defined-type-with-discards)。</span><span class="sxs-lookup"><span data-stu-id="5e084-128">For more information on deconstructing user-defined types with discards, see [Deconstructing tuples and other types](deconstruct.md#deconstructing-a-user-defined-type-with-discards).</span></span>

## <a name="pattern-matching-with-switch-and-is"></a><span data-ttu-id="5e084-129">以 `switch` 和 `is` 進行的模式比對</span><span class="sxs-lookup"><span data-stu-id="5e084-129">Pattern matching with `switch` and `is`</span></span>

<span data-ttu-id="5e084-130">「捨棄模式」可用於以 [is](language-reference/keywords/is.md) 和 [switch](language-reference/keywords/switch.md) 關鍵字進行的模式比對。</span><span class="sxs-lookup"><span data-stu-id="5e084-130">The *discard pattern* can be used in pattern matching with the [is](language-reference/keywords/is.md) and [switch](language-reference/keywords/switch.md) keywords.</span></span> <span data-ttu-id="5e084-131">每個運算式一律會比對捨棄模式。</span><span class="sxs-lookup"><span data-stu-id="5e084-131">Every expression always matches the discard pattern.</span></span>

<span data-ttu-id="5e084-132">下列範例會定義 `ProvidesFormatInfo` 方法，該方法使用 [is](language-reference/keywords/is.md) 陳述式來判斷物件是否提供 <xref:System.IFormatProvider> 實作，並測試物件是否為 `null`。</span><span class="sxs-lookup"><span data-stu-id="5e084-132">The following example defines a `ProvidesFormatInfo` method that uses [is](language-reference/keywords/is.md) statements to determine whether an object provides an <xref:System.IFormatProvider> implementation and tests whether the object is `null`.</span></span> <span data-ttu-id="5e084-133">它也會使用捨棄模式來處理任何其他類型的非 Null 物件。</span><span class="sxs-lookup"><span data-stu-id="5e084-133">It also uses the discard pattern to handle non-null objects of any other type.</span></span>

[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]

## <a name="calls-to-methods-with-out-parameters"></a><span data-ttu-id="5e084-134">以 out 參數進行的方法呼叫</span><span class="sxs-lookup"><span data-stu-id="5e084-134">Calls to methods with out parameters</span></span>

<span data-ttu-id="5e084-135">當呼叫 `Deconstruct` 方法解構使用者定義型別 (類別、結構或介面的執行個體) 時，您可以捨棄個別 `out` 引數的值。</span><span class="sxs-lookup"><span data-stu-id="5e084-135">When calling the `Deconstruct` method to deconstruct a user-defined type (an instance of a class, structure, or interface), you can discard the values of individual `out` arguments.</span></span> <span data-ttu-id="5e084-136">但當使用 out 參數呼叫任何方法時，您也可以捨棄 `out` 引數的值。</span><span class="sxs-lookup"><span data-stu-id="5e084-136">But you can also discard the value of `out` arguments when calling any method with an out parameter.</span></span>

<span data-ttu-id="5e084-137">下列範例會呼叫 [DateTime.TryParse(String, out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) 方法，以判斷日期的字串表示在目前的文化特性 (culture) 中是否有效。</span><span class="sxs-lookup"><span data-stu-id="5e084-137">The following example calls the [DateTime.TryParse(String, out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) method to determine whether the string representation of a date is valid in the current culture.</span></span> <span data-ttu-id="5e084-138">因為此範例只需要驗證日期字串，而不需要將它剖析以擷取日期，所以該方法的 `out` 引數為 discard。</span><span class="sxs-lookup"><span data-stu-id="5e084-138">Because the example is concerned only with validating the date string and not with parsing it to extract the date, the `out` argument to the method is a discard.</span></span>

[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]

## <a name="a-standalone-discard"></a><span data-ttu-id="5e084-139">獨立 discard</span><span class="sxs-lookup"><span data-stu-id="5e084-139">A standalone discard</span></span>

<span data-ttu-id="5e084-140">您可以使用獨立 discard，指出您選擇忽略的任何變數。</span><span class="sxs-lookup"><span data-stu-id="5e084-140">You can use a standalone discard to indicate any variable that you choose to ignore.</span></span> <span data-ttu-id="5e084-141">下列範例會使用獨立 discard 來忽略非同步作業傳回的 <xref:System.Threading.Tasks.Task> 物件。</span><span class="sxs-lookup"><span data-stu-id="5e084-141">The following example uses a standalone discard to ignore the <xref:System.Threading.Tasks.Task> object returned by an asynchronous operation.</span></span> <span data-ttu-id="5e084-142">這會造成在作業即將完成時，隱藏作業所擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5e084-142">This has the effect of suppressing the exception that the operation throws as it is about to complete.</span></span>

[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]

<span data-ttu-id="5e084-143">請注意，`_` 也是有效的識別項。</span><span class="sxs-lookup"><span data-stu-id="5e084-143">Note that `_` is also a valid identifier.</span></span> <span data-ttu-id="5e084-144">在支援的內容之外使用時，`_` 會視為有效的變數，而不是 discard。</span><span class="sxs-lookup"><span data-stu-id="5e084-144">When used outside of a supported context, `_` is treated not as a discard but as a valid variable.</span></span> <span data-ttu-id="5e084-145">如果範圍內已有名為 `_` 的識別項，使用 `_` 作為獨立 discard 可能會導致：</span><span class="sxs-lookup"><span data-stu-id="5e084-145">If an identifier named `_` is already in scope, the use of `_` as a standalone discard can result in:</span></span>

- <span data-ttu-id="5e084-146">將預定的 dscard 值指派給範圍內的 `_` 變數，而意外修改變數的值。</span><span class="sxs-lookup"><span data-stu-id="5e084-146">Accidental modification of the value of the in-scope `_` variable by assigning it the value of the intended discard.</span></span> <span data-ttu-id="5e084-147">例如：</span><span class="sxs-lookup"><span data-stu-id="5e084-147">For example:</span></span>

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]

- <span data-ttu-id="5e084-148">違反型別安全的編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="5e084-148">A compiler error for violating type safety.</span></span> <span data-ttu-id="5e084-149">例如：</span><span class="sxs-lookup"><span data-stu-id="5e084-149">For example:</span></span>

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]

- <span data-ttu-id="5e084-150">編譯器錯誤 CS0136：「無法在此範圍宣告名為 '\_' 的區域變數或參數，因為該名稱已用於封入區域變數範圍，以定義區域變數或參數」。</span><span class="sxs-lookup"><span data-stu-id="5e084-150">Compiler error CS0136, "A local or parameter named '\_' cannot be declared in this scope because that name is used in an enclosing local scope to define a local or parameter."</span></span> <span data-ttu-id="5e084-151">例如：</span><span class="sxs-lookup"><span data-stu-id="5e084-151">For example:</span></span>

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]

## <a name="see-also"></a><span data-ttu-id="5e084-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e084-152">See also</span></span>

- [<span data-ttu-id="5e084-153">解構 Tuple 和其他型別</span><span class="sxs-lookup"><span data-stu-id="5e084-153">Deconstructing tuples and other types</span></span>](deconstruct.md)
- [<span data-ttu-id="5e084-154">`is` 關鍵字</span><span class="sxs-lookup"><span data-stu-id="5e084-154">`is` keyword</span></span>](language-reference/keywords/is.md)
- [<span data-ttu-id="5e084-155">`switch` 關鍵字</span><span class="sxs-lookup"><span data-stu-id="5e084-155">`switch` keyword</span></span>](language-reference/keywords/switch.md)
