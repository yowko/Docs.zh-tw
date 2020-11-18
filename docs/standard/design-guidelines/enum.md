---
title: 列舉設計
description: 列舉的設計，這是一種特殊的實值型別。 簡單列舉會保存小型的封閉選項組。 旗標列舉支援列舉值的位運算。
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
ms.openlocfilehash: a2e19197b114daa2a0956a6fc87231a6a81de916
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821355"
---
# <a name="enum-design"></a><span data-ttu-id="87ad0-105">列舉設計</span><span class="sxs-lookup"><span data-stu-id="87ad0-105">Enum Design</span></span>

<span data-ttu-id="87ad0-106">列舉是一種特殊類型的實值型別。</span><span class="sxs-lookup"><span data-stu-id="87ad0-106">Enums are a special kind of value type.</span></span> <span data-ttu-id="87ad0-107">列舉有兩種：簡單列舉和旗標列舉。</span><span class="sxs-lookup"><span data-stu-id="87ad0-107">There are two kinds of enums: simple enums and flag enums.</span></span>

<span data-ttu-id="87ad0-108">簡單列舉代表小型封閉的選項組。</span><span class="sxs-lookup"><span data-stu-id="87ad0-108">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="87ad0-109">簡單列舉的常見範例是一組色彩。</span><span class="sxs-lookup"><span data-stu-id="87ad0-109">A common example of the simple enum is a set of colors.</span></span>

<span data-ttu-id="87ad0-110">旗標列舉是設計用來支援列舉值的位運算。</span><span class="sxs-lookup"><span data-stu-id="87ad0-110">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="87ad0-111">旗標列舉的常見範例是選項清單。</span><span class="sxs-lookup"><span data-stu-id="87ad0-111">A common example of the flags enum is a list of options.</span></span>

<span data-ttu-id="87ad0-112">✔️請使用列舉來表示值集合的強型別參數、屬性和傳回值。</span><span class="sxs-lookup"><span data-stu-id="87ad0-112">✔️ DO use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>

<span data-ttu-id="87ad0-113">✔️會偏好使用列舉，而不是靜態常數。</span><span class="sxs-lookup"><span data-stu-id="87ad0-113">✔️ DO favor using an enum instead of static constants.</span></span>

<span data-ttu-id="87ad0-114">❌ 請勿將列舉用於開放集 (例如作業系統版本、朋友名稱等 ) 。</span><span class="sxs-lookup"><span data-stu-id="87ad0-114">❌ DO NOT use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>

<span data-ttu-id="87ad0-115">❌ 請勿提供預定的列舉值供日後使用。</span><span class="sxs-lookup"><span data-stu-id="87ad0-115">❌ DO NOT provide reserved enum values that are intended for future use.</span></span>

<span data-ttu-id="87ad0-116">您一律可以在稍後的階段中，直接將值加入至現有的列舉。</span><span class="sxs-lookup"><span data-stu-id="87ad0-116">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="87ad0-117">如需將值加入至列舉的詳細資訊，請參閱 [將值加入至](#add_value) 列舉。</span><span class="sxs-lookup"><span data-stu-id="87ad0-117">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="87ad0-118">保留值只是會污染實際值的集合，而且通常會導致使用者錯誤。</span><span class="sxs-lookup"><span data-stu-id="87ad0-118">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>

<span data-ttu-id="87ad0-119">❌ 避免公開只具有一個值的列舉。</span><span class="sxs-lookup"><span data-stu-id="87ad0-119">❌ AVOID publicly exposing enums with only one value.</span></span>

<span data-ttu-id="87ad0-120">確保 C Api 未來擴充性的常見做法是將保留參數新增至方法簽章。</span><span class="sxs-lookup"><span data-stu-id="87ad0-120">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="87ad0-121">這類保留的參數可表示為具有單一預設值的列舉。</span><span class="sxs-lookup"><span data-stu-id="87ad0-121">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="87ad0-122">這不應該在受控 Api 中完成。</span><span class="sxs-lookup"><span data-stu-id="87ad0-122">This should not be done in managed APIs.</span></span> <span data-ttu-id="87ad0-123">方法多載可讓您在未來的版本中加入參數。</span><span class="sxs-lookup"><span data-stu-id="87ad0-123">Method overloading allows adding parameters in future releases.</span></span>

<span data-ttu-id="87ad0-124">❌ 請勿將 sentinel 值包含在列舉中。</span><span class="sxs-lookup"><span data-stu-id="87ad0-124">❌ DO NOT include sentinel values in enums.</span></span>

<span data-ttu-id="87ad0-125">雖然它們有時對架構開發人員很有説明，但 sentinel 值對架構的使用者感到混淆。</span><span class="sxs-lookup"><span data-stu-id="87ad0-125">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="87ad0-126">它們可用來追蹤列舉的狀態，而不是列舉所表示之集合中的其中一個值。</span><span class="sxs-lookup"><span data-stu-id="87ad0-126">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>

<span data-ttu-id="87ad0-127">✔️在簡單列舉上提供值為零。</span><span class="sxs-lookup"><span data-stu-id="87ad0-127">✔️ DO provide a value of zero on simple enums.</span></span>

<span data-ttu-id="87ad0-128">請考慮呼叫值，例如「無」。</span><span class="sxs-lookup"><span data-stu-id="87ad0-128">Consider calling the value something like "None."</span></span> <span data-ttu-id="87ad0-129">如果這類的值不適用於此特定列舉，則列舉的最常見預設值應指派為零的基礎值。</span><span class="sxs-lookup"><span data-stu-id="87ad0-129">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>

<span data-ttu-id="87ad0-130">✔️考慮使用 <xref:System.Int32> (大部分程式設計語言中的預設值，) 作為列舉的基礎類型，除非下列任何條件成立：</span><span class="sxs-lookup"><span data-stu-id="87ad0-130">✔️ CONSIDER using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>

- <span data-ttu-id="87ad0-131">列舉是旗標列舉，而您有超過32個旗標，或預期未來會有更多的旗標。</span><span class="sxs-lookup"><span data-stu-id="87ad0-131">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>

- <span data-ttu-id="87ad0-132">基礎類型必須不同于 <xref:System.Int32> ，以便與非受控程式碼的互通性需要不同大小的列舉。</span><span class="sxs-lookup"><span data-stu-id="87ad0-132">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>

- <span data-ttu-id="87ad0-133">較小的基礎類型會大幅節省空間。</span><span class="sxs-lookup"><span data-stu-id="87ad0-133">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="87ad0-134">如果您預期列舉主要是用來做為控制流程的引數，則大小會有很大的差異。</span><span class="sxs-lookup"><span data-stu-id="87ad0-134">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="87ad0-135">如果有下列情況，節省的大小可能很大：</span><span class="sxs-lookup"><span data-stu-id="87ad0-135">The size savings might be significant if:</span></span>

  - <span data-ttu-id="87ad0-136">您預期列舉是用來做為極常具現化之結構或類別中的欄位。</span><span class="sxs-lookup"><span data-stu-id="87ad0-136">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>

  - <span data-ttu-id="87ad0-137">您希望使用者能夠建立大型陣列或列舉實例的集合。</span><span class="sxs-lookup"><span data-stu-id="87ad0-137">You expect users to create large arrays or collections of the enum instances.</span></span>

  - <span data-ttu-id="87ad0-138">您預期要序列化的列舉實例數量很多。</span><span class="sxs-lookup"><span data-stu-id="87ad0-138">You expect a large number of instances of the enum to be serialized.</span></span>

<span data-ttu-id="87ad0-139">針對記憶體中的使用方式，請注意，managed 物件永遠保持 `DWORD` 一致，因此，您實際上需要在實例中使用多個列舉或其他小型結構來封裝較小的列舉，以使其成為差異，因為實例大小總計一律會無條件進位至 `DWORD` 。</span><span class="sxs-lookup"><span data-stu-id="87ad0-139">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>

<span data-ttu-id="87ad0-140">✔️使用複數名詞或名詞片語，以及具有單數名詞或名詞片語的簡單列舉進行名稱旗標列舉。</span><span class="sxs-lookup"><span data-stu-id="87ad0-140">✔️ DO name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>

<span data-ttu-id="87ad0-141">❌ 請勿直接延伸 <xref:System.Enum?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="87ad0-141">❌ DO NOT extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>

<span data-ttu-id="87ad0-142"><xref:System.Enum?displayProperty=nameWithType> 這是 CLR 用來建立使用者定義列舉的特殊類型。</span><span class="sxs-lookup"><span data-stu-id="87ad0-142"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="87ad0-143">大部分的程式設計語言都會提供程式設計項目，讓您能夠存取這項功能。</span><span class="sxs-lookup"><span data-stu-id="87ad0-143">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="87ad0-144">例如，在 c # 中， `enum` 關鍵字是用來定義列舉。</span><span class="sxs-lookup"><span data-stu-id="87ad0-144">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>

<a name="design"></a>

### <a name="designing-flag-enums"></a><span data-ttu-id="87ad0-145">設計旗標列舉</span><span class="sxs-lookup"><span data-stu-id="87ad0-145">Designing Flag Enums</span></span>

<span data-ttu-id="87ad0-146">✔️將套用 <xref:System.FlagsAttribute?displayProperty=nameWithType> 至旗標列舉。</span><span class="sxs-lookup"><span data-stu-id="87ad0-146">✔️ DO apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="87ad0-147">請勿將此屬性套用至簡單列舉。</span><span class="sxs-lookup"><span data-stu-id="87ad0-147">Do not apply this attribute to simple enums.</span></span>

<span data-ttu-id="87ad0-148">✔️會使用兩個旗標列舉值的乘冪，以便使用位 OR 運算自由地結合。</span><span class="sxs-lookup"><span data-stu-id="87ad0-148">✔️ DO use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>

<span data-ttu-id="87ad0-149">✔️考慮為常用的旗標組合提供特殊的列舉值。</span><span class="sxs-lookup"><span data-stu-id="87ad0-149">✔️ CONSIDER providing special enum values for commonly used combinations of flags.</span></span>

<span data-ttu-id="87ad0-150">位運算是先進的概念，簡單的工作則不需要。</span><span class="sxs-lookup"><span data-stu-id="87ad0-150">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="87ad0-151"><xref:System.IO.FileAccess.ReadWrite> 這是這類特殊值的範例。</span><span class="sxs-lookup"><span data-stu-id="87ad0-151"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>

<span data-ttu-id="87ad0-152">❌ 避免建立旗標列舉，其中某些值的組合無效。</span><span class="sxs-lookup"><span data-stu-id="87ad0-152">❌ AVOID creating flag enums where certain combinations of values are invalid.</span></span>

<span data-ttu-id="87ad0-153">❌ 請避免使用旗標列舉值零，除非此值代表「所有旗標已清除」，並且依照下一個指導方針的規定適當命名。</span><span class="sxs-lookup"><span data-stu-id="87ad0-153">❌ AVOID using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>

<span data-ttu-id="87ad0-154">✔️請將旗標列舉的值命名為零 `None` 。</span><span class="sxs-lookup"><span data-stu-id="87ad0-154">✔️ DO name the zero value of flag enums `None`.</span></span> <span data-ttu-id="87ad0-155">針對旗標列舉，此值必須一律表示「所有旗標已清除」。</span><span class="sxs-lookup"><span data-stu-id="87ad0-155">For a flag enum, the value must always mean "all flags are cleared."</span></span>

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a><span data-ttu-id="87ad0-156">將值新增至列舉</span><span class="sxs-lookup"><span data-stu-id="87ad0-156">Adding Value to Enums</span></span>

<span data-ttu-id="87ad0-157">很常見的情況是，您必須在將值傳送至列舉之後，將其加入至列舉。</span><span class="sxs-lookup"><span data-stu-id="87ad0-157">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="87ad0-158">從現有的 API 傳回新加入的值時，可能會發生應用程式相容性問題，因為寫入不良的應用程式可能無法正確地處理新值。</span><span class="sxs-lookup"><span data-stu-id="87ad0-158">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>

<span data-ttu-id="87ad0-159">✔️考慮將值新增至列舉（儘管有較小的相容性風險）。</span><span class="sxs-lookup"><span data-stu-id="87ad0-159">✔️ CONSIDER adding values to enums, despite a small compatibility risk.</span></span>

<span data-ttu-id="87ad0-160">如果您有關于新增至列舉的應用程式不相容的實際資料，請考慮加入新的 API，以傳回新的和舊的值，並取代舊的 API，這應該只會繼續傳回舊的值。</span><span class="sxs-lookup"><span data-stu-id="87ad0-160">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="87ad0-161">這可確保您現有的應用程式保持相容。</span><span class="sxs-lookup"><span data-stu-id="87ad0-161">This will ensure that your existing applications remain compatible.</span></span>

<span data-ttu-id="87ad0-162">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="87ad0-162">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="87ad0-163">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="87ad0-163">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="87ad0-164">請參閱</span><span class="sxs-lookup"><span data-stu-id="87ad0-164">See also</span></span>

- [<span data-ttu-id="87ad0-165">型別設計方針</span><span class="sxs-lookup"><span data-stu-id="87ad0-165">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="87ad0-166">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="87ad0-166">Framework Design Guidelines</span></span>](index.md)
