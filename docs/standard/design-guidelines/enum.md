---
title: 列舉設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
ms.openlocfilehash: 3b24bfefd3edb0585e9c6369e9b8151b17151661
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741709"
---
# <a name="enum-design"></a><span data-ttu-id="2f2ac-102">列舉設計</span><span class="sxs-lookup"><span data-stu-id="2f2ac-102">Enum Design</span></span>

<span data-ttu-id="2f2ac-103">列舉是一種特殊的實值型別。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-103">Enums are a special kind of value type.</span></span> <span data-ttu-id="2f2ac-104">列舉有兩種類型：簡單列舉和旗標列舉。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-104">There are two kinds of enums: simple enums and flag enums.</span></span>

<span data-ttu-id="2f2ac-105">簡單列舉代表一組小型封閉的選擇。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-105">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="2f2ac-106">簡單列舉的常見範例是一組色彩。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-106">A common example of the simple enum is a set of colors.</span></span>

<span data-ttu-id="2f2ac-107">旗標列舉是設計用來支援列舉值的位運算。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-107">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="2f2ac-108">旗標列舉的常見範例是選項清單。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-108">A common example of the flags enum is a list of options.</span></span>

<span data-ttu-id="2f2ac-109">✔️確實要使用列舉來表示值集合的強型別參數、屬性和傳回值。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-109">✔️ DO use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>

<span data-ttu-id="2f2ac-110">✔️偏好使用列舉，而不是靜態常數。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-110">✔️ DO favor using an enum instead of static constants.</span></span>

<span data-ttu-id="2f2ac-111">❌ 不要將列舉用於開啟的集合（例如作業系統版本、朋友的名稱等）。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-111">❌ DO NOT use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>

<span data-ttu-id="2f2ac-112">❌ 不提供預定的保留列舉值，供日後使用。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-112">❌ DO NOT provide reserved enum values that are intended for future use.</span></span>

<span data-ttu-id="2f2ac-113">您一律可以在稍後的階段中，直接將值新增至現有的列舉。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-113">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="2f2ac-114">如需將值加入至列舉的詳細資訊，請參閱[將值加入至](#add_value)列舉。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-114">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="2f2ac-115">保留的值只會會污染實際值的集合，而且通常會導致使用者錯誤。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-115">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>

<span data-ttu-id="2f2ac-116">❌ 避免公開只具有一個值的列舉。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-116">❌ AVOID publicly exposing enums with only one value.</span></span>

<span data-ttu-id="2f2ac-117">確保 C Api 未來擴充性的常見作法是將保留參數新增至方法簽章。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-117">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="2f2ac-118">這類保留參數可以用單一預設值來表示為列舉。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-118">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="2f2ac-119">這不應該在受控 Api 中完成。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-119">This should not be done in managed APIs.</span></span> <span data-ttu-id="2f2ac-120">方法多載允許在未來的版本中新增參數。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-120">Method overloading allows adding parameters in future releases.</span></span>

<span data-ttu-id="2f2ac-121">❌ 不包含 enum 中的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-121">❌ DO NOT include sentinel values in enums.</span></span>

<span data-ttu-id="2f2ac-122">雖然它們有時對架構開發人員很有用，但 sentinel 值對架構的使用者會造成混淆。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-122">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="2f2ac-123">它們可用來追蹤列舉的狀態，而不是列舉所表示之集合中的其中一個值。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-123">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>

<span data-ttu-id="2f2ac-124">✔️在簡單列舉上提供零值。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-124">✔️ DO provide a value of zero on simple enums.</span></span>

<span data-ttu-id="2f2ac-125">請考慮呼叫值，例如 "None"。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-125">Consider calling the value something like "None."</span></span> <span data-ttu-id="2f2ac-126">如果這類的值不適用於此特定列舉，則列舉的最常見預設值應指派為零的基礎值。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-126">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>

<span data-ttu-id="2f2ac-127">✔️考慮使用 <xref:System.Int32> （大部分程式設計語言中的預設值）做為列舉的基礎類型，除非下列任何一項為 true：</span><span class="sxs-lookup"><span data-stu-id="2f2ac-127">✔️ CONSIDER using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>

- <span data-ttu-id="2f2ac-128">列舉是旗標列舉，而且您有超過32個旗標，或未來預期會有更多旗標。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-128">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>

- <span data-ttu-id="2f2ac-129">基礎類型必須與 <xref:System.Int32> 不同，以便更容易與非受控程式碼的互通性需要不同大小的列舉。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-129">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>

- <span data-ttu-id="2f2ac-130">較小的基礎類型會導致空間大幅節省。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-130">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="2f2ac-131">如果您預期列舉主要是做為控制流程的引數，則大小不會有太大的差異。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-131">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="2f2ac-132">若有下列情況，節省的大小可能會很明顯：</span><span class="sxs-lookup"><span data-stu-id="2f2ac-132">The size savings might be significant if:</span></span>

  - <span data-ttu-id="2f2ac-133">您預期列舉會當做非常頻繁具現化的結構或類別中的欄位使用。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-133">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>

  - <span data-ttu-id="2f2ac-134">您預期使用者會建立大型陣列或列舉實例的集合。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-134">You expect users to create large arrays or collections of the enum instances.</span></span>

  - <span data-ttu-id="2f2ac-135">您預期會序列化大量的列舉實例。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-135">You expect a large number of instances of the enum to be serialized.</span></span>

<span data-ttu-id="2f2ac-136">針對記憶體中的使用方式，請注意，managed 物件一律 `DWORD`對齊，因此，您在實例中有效地需要多個列舉或其他小型結構來封裝較小的 enum，以便進行差異，因為總實例大小一律會無條件進位到 `DWORD`。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-136">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>

<span data-ttu-id="2f2ac-137">✔️使用名詞或名詞片語來進行名稱旗標列舉，以及使用單數或名詞片語進行簡單列舉。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-137">✔️ DO name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>

<span data-ttu-id="2f2ac-138">❌ 不會直接延伸 <xref:System.Enum?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-138">❌ DO NOT extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>

<span data-ttu-id="2f2ac-139"><xref:System.Enum?displayProperty=nameWithType> 是 CLR 用來建立使用者定義列舉的特殊類型。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-139"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="2f2ac-140">大部分的程式設計語言都會提供程式設計項目，讓您能夠存取這項功能。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-140">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="2f2ac-141">例如，在 `enum` C#關鍵字中，是用來定義列舉型別（enumeration）。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-141">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>

<a name="design"></a>

### <a name="designing-flag-enums"></a><span data-ttu-id="2f2ac-142">設計旗標列舉</span><span class="sxs-lookup"><span data-stu-id="2f2ac-142">Designing Flag Enums</span></span>

<span data-ttu-id="2f2ac-143">✔️請將 <xref:System.FlagsAttribute?displayProperty=nameWithType> 套用至旗標列舉。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-143">✔️ DO apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="2f2ac-144">請勿將此屬性套用至簡單列舉。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-144">Do not apply this attribute to simple enums.</span></span>

<span data-ttu-id="2f2ac-145">✔️在旗標列舉值中使用兩個的乘冪，讓它們可以使用位 OR 運算自由地結合。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-145">✔️ DO use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>

<span data-ttu-id="2f2ac-146">✔️請考慮為常用的旗標組合提供特殊的列舉值。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-146">✔️ CONSIDER providing special enum values for commonly used combinations of flags.</span></span>

<span data-ttu-id="2f2ac-147">位運算是一種先進的概念，而且不應該為簡單的工作所需。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-147">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="2f2ac-148"><xref:System.IO.FileAccess.ReadWrite> 是這種特殊值的範例。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-148"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>

<span data-ttu-id="2f2ac-149">❌ 避免建立旗標列舉，其中某些值的組合無效。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-149">❌ AVOID creating flag enums where certain combinations of values are invalid.</span></span>

<span data-ttu-id="2f2ac-150">❌ 避免使用旗標列舉值零，除非值表示「已清除所有旗標」，而且會適當地命名，如同下一個指導方針所規定。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-150">❌ AVOID using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>

<span data-ttu-id="2f2ac-151">✔️ DO 將旗標列舉的零值命名 `None`。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-151">✔️ DO name the zero value of flag enums `None`.</span></span> <span data-ttu-id="2f2ac-152">針對旗標列舉，此值必須一律表示「已清除所有旗標」。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-152">For a flag enum, the value must always mean "all flags are cleared."</span></span>

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a><span data-ttu-id="2f2ac-153">將值加入至列舉</span><span class="sxs-lookup"><span data-stu-id="2f2ac-153">Adding Value to Enums</span></span>

<span data-ttu-id="2f2ac-154">在您已寄出值之後，您必須將其新增至列舉，這是很常見的情況。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-154">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="2f2ac-155">從現有的 API 傳回新加入的值時，可能會發生應用程式相容性問題，因為撰寫不良的應用程式可能無法正確地處理新的值。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-155">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>

<span data-ttu-id="2f2ac-156">✔️考慮將值加入至列舉，儘管有較小的相容性風險。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-156">✔️ CONSIDER adding values to enums, despite a small compatibility risk.</span></span>

<span data-ttu-id="2f2ac-157">如果您的實際資料是因為新增至列舉而造成的應用程式不相容，請考慮新增新的 API 來傳回新的和舊的值，並取代舊的 API，這應該會繼續只傳回舊的值。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-157">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="2f2ac-158">這可確保您現有的應用程式保持相容。</span><span class="sxs-lookup"><span data-stu-id="2f2ac-158">This will ensure that your existing applications remain compatible.</span></span>

<span data-ttu-id="2f2ac-159">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="2f2ac-159">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="2f2ac-160">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition[ 節錄。](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)*</span><span class="sxs-lookup"><span data-stu-id="2f2ac-160">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="2f2ac-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f2ac-161">See also</span></span>

- [<span data-ttu-id="2f2ac-162">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="2f2ac-162">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="2f2ac-163">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="2f2ac-163">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
