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
author: KrzysztofCwalina
ms.openlocfilehash: c0645ba1179c4c6fd961b871b3061cd51174f427
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669091"
---
# <a name="enum-design"></a><span data-ttu-id="e8a74-102">列舉設計</span><span class="sxs-lookup"><span data-stu-id="e8a74-102">Enum Design</span></span>
<span data-ttu-id="e8a74-103">列舉都是一種特殊的實值型別。</span><span class="sxs-lookup"><span data-stu-id="e8a74-103">Enums are a special kind of value type.</span></span> <span data-ttu-id="e8a74-104">有兩種類型的列舉： 簡單列舉和旗標的列舉。</span><span class="sxs-lookup"><span data-stu-id="e8a74-104">There are two kinds of enums: simple enums and flag enums.</span></span>  
  
 <span data-ttu-id="e8a74-105">簡單列舉代表封閉的少量的選擇。</span><span class="sxs-lookup"><span data-stu-id="e8a74-105">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="e8a74-106">簡單列舉的常見範例是一組色彩。</span><span class="sxs-lookup"><span data-stu-id="e8a74-106">A common example of the simple enum is a set of colors.</span></span>  
  
 <span data-ttu-id="e8a74-107">旗標列舉被設計來支援列舉值的位元運算。</span><span class="sxs-lookup"><span data-stu-id="e8a74-107">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="e8a74-108">旗標列舉的常見範例是選項的清單。</span><span class="sxs-lookup"><span data-stu-id="e8a74-108">A common example of the flags enum is a list of options.</span></span>  
  
 <span data-ttu-id="e8a74-109">**✓ DO** 列舉使用強型別參數、 屬性和傳回值，表示一組值。</span><span class="sxs-lookup"><span data-stu-id="e8a74-109">**✓ DO** use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>  
  
 <span data-ttu-id="e8a74-110">**✓ DO** 偏好使用列舉，而不靜態的常數。</span><span class="sxs-lookup"><span data-stu-id="e8a74-110">**✓ DO** favor using an enum instead of static constants.</span></span>  
  
 <span data-ttu-id="e8a74-111">**X DO NOT** 列舉用於開啟設定 （例如作業系統版本、 您的朋友、 等等的名稱。）。</span><span class="sxs-lookup"><span data-stu-id="e8a74-111">**X DO NOT** use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>  
  
 <span data-ttu-id="e8a74-112">**X DO NOT** 提供保留的列舉值是要供未來使用。</span><span class="sxs-lookup"><span data-stu-id="e8a74-112">**X DO NOT** provide reserved enum values that are intended for future use.</span></span>  
  
 <span data-ttu-id="e8a74-113">您一律只可以加入至現有的列舉的值，在稍後的階段。</span><span class="sxs-lookup"><span data-stu-id="e8a74-113">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="e8a74-114">請參閱[新增的值，以列舉](#add_value)如需詳細資訊將值加入至列舉。</span><span class="sxs-lookup"><span data-stu-id="e8a74-114">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="e8a74-115">保留的值只會干擾的一組真實的值，並通常會導致使用者錯誤。</span><span class="sxs-lookup"><span data-stu-id="e8a74-115">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>  
  
 <span data-ttu-id="e8a74-116">**X AVOID** 公開僅有一個值的列舉。</span><span class="sxs-lookup"><span data-stu-id="e8a74-116">**X AVOID** publicly exposing enums with only one value.</span></span>  
  
 <span data-ttu-id="e8a74-117">確保未來的擴充性的 C Api 的常見作法是將保留的參數新增至方法簽章。</span><span class="sxs-lookup"><span data-stu-id="e8a74-117">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="e8a74-118">這類保留的參數可以表示為單一的預設值的列舉。</span><span class="sxs-lookup"><span data-stu-id="e8a74-118">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="e8a74-119">這不應該在受管理的 Api。</span><span class="sxs-lookup"><span data-stu-id="e8a74-119">This should not be done in managed APIs.</span></span> <span data-ttu-id="e8a74-120">方法多載，可讓新增參數在未來的版本。</span><span class="sxs-lookup"><span data-stu-id="e8a74-120">Method overloading allows adding parameters in future releases.</span></span>  
  
 <span data-ttu-id="e8a74-121">**X DO NOT** sentinel 值包含在列舉中。</span><span class="sxs-lookup"><span data-stu-id="e8a74-121">**X DO NOT** include sentinel values in enums.</span></span>  
  
 <span data-ttu-id="e8a74-122">雖然它們有時會很有幫助架構開發人員，sentinel 值會是令人困惑的 framework 的使用者。</span><span class="sxs-lookup"><span data-stu-id="e8a74-122">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="e8a74-123">它們用來追蹤狀態的列舉，而不是其中一個值是從列舉所表示的集合。</span><span class="sxs-lookup"><span data-stu-id="e8a74-123">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>  
  
 <span data-ttu-id="e8a74-124">**✓ DO** 提供簡單列舉上零的值。</span><span class="sxs-lookup"><span data-stu-id="e8a74-124">**✓ DO** provide a value of zero on simple enums.</span></span>  
  
 <span data-ttu-id="e8a74-125">請考慮呼叫值類似"None"。</span><span class="sxs-lookup"><span data-stu-id="e8a74-125">Consider calling the value something like "None."</span></span> <span data-ttu-id="e8a74-126">如果這類值不適用於這個特定的列舉，最常見的預設值，列舉應該指派基礎值為零。</span><span class="sxs-lookup"><span data-stu-id="e8a74-126">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>  
  
 <span data-ttu-id="e8a74-127">**✓ CONSIDER** 使用 <xref:System.Int32> （大部分的程式設計語言中的預設值） 列舉的基礎類型為除非有下列情況：</span><span class="sxs-lookup"><span data-stu-id="e8a74-127">**✓ CONSIDER** using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>  
  
- <span data-ttu-id="e8a74-128">列舉是旗標列舉，而且您有 32 個以上的旗標，或希望有更多在未來。</span><span class="sxs-lookup"><span data-stu-id="e8a74-128">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>  
  
- <span data-ttu-id="e8a74-129">基礎類型必須是不同於<xref:System.Int32>更容易與預期不同大小列舉的 unmanaged 程式碼的互通性。</span><span class="sxs-lookup"><span data-stu-id="e8a74-129">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>  
  
- <span data-ttu-id="e8a74-130">較小的基礎類型會導致大量節省空間。</span><span class="sxs-lookup"><span data-stu-id="e8a74-130">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="e8a74-131">如果您預期的列舉，主要是做為控制流程的引數，則大小會將些許差異。</span><span class="sxs-lookup"><span data-stu-id="e8a74-131">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="e8a74-132">節省大小可能會很大如果：</span><span class="sxs-lookup"><span data-stu-id="e8a74-132">The size savings might be significant if:</span></span>  
  
    - <span data-ttu-id="e8a74-133">您預期的列舉，用於經常執行個體化的結構或類別中的欄位。</span><span class="sxs-lookup"><span data-stu-id="e8a74-133">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>  
  
    - <span data-ttu-id="e8a74-134">您預期使用者建立大型陣列或集合的列舉執行個體。</span><span class="sxs-lookup"><span data-stu-id="e8a74-134">You expect users to create large arrays or collections of the enum instances.</span></span>  
  
    - <span data-ttu-id="e8a74-135">您預期大量的列舉，可序列化的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e8a74-135">You expect a large number of instances of the enum to be serialized.</span></span>  
  
 <span data-ttu-id="e8a74-136">記憶體使用量，請留意，受管理的物件都`DWORD`-對齊，因此您實際上需要多個列舉或其他封裝具有較小的列舉，而以深遠的影響，因為總執行個體的大小一律為執行個體中的小型結構要無條件進位至`DWORD`。</span><span class="sxs-lookup"><span data-stu-id="e8a74-136">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>  
  
 <span data-ttu-id="e8a74-137">**✓ DO** 命名為旗標列舉的複數名詞或名詞片語，並使用單數名詞或名詞片語的簡單列舉。</span><span class="sxs-lookup"><span data-stu-id="e8a74-137">**✓ DO** name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="e8a74-138">**X DO NOT** 擴充 <xref:System.Enum?displayProperty=nameWithType> 直接。</span><span class="sxs-lookup"><span data-stu-id="e8a74-138">**X DO NOT** extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>  
  
 <span data-ttu-id="e8a74-139"><xref:System.Enum?displayProperty=nameWithType> 是一種特殊類型用於由 CLR 建立使用者定義的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="e8a74-139"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="e8a74-140">大部分的程式設計語言提供這項功能可讓您存取的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="e8a74-140">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="e8a74-141">例如，在 C#`enum`關鍵字用以定義列舉類型。</span><span class="sxs-lookup"><span data-stu-id="e8a74-141">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a><span data-ttu-id="e8a74-142">設計的旗標列舉</span><span class="sxs-lookup"><span data-stu-id="e8a74-142">Designing Flag Enums</span></span>  
 <span data-ttu-id="e8a74-143">**✓ DO** 套用 <xref:System.FlagsAttribute?displayProperty=nameWithType> 用於旗標列舉。</span><span class="sxs-lookup"><span data-stu-id="e8a74-143">**✓ DO** apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="e8a74-144">不套用這個屬性用於簡單的列舉。</span><span class="sxs-lookup"><span data-stu-id="e8a74-144">Do not apply this attribute to simple enums.</span></span>  
  
 <span data-ttu-id="e8a74-145">**✓ DO** 使用的 2 乘冪的旗標列舉值，因此也可以自由地結合使用位元 OR 運算。</span><span class="sxs-lookup"><span data-stu-id="e8a74-145">**✓ DO** use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>  
  
 <span data-ttu-id="e8a74-146">**✓ CONSIDER** 常提供的特殊的列舉值使用的旗標的組合。</span><span class="sxs-lookup"><span data-stu-id="e8a74-146">**✓ CONSIDER** providing special enum values for commonly used combinations of flags.</span></span>  
  
 <span data-ttu-id="e8a74-147">位元運算是進階的概念，而且應該不需要簡單的工作。</span><span class="sxs-lookup"><span data-stu-id="e8a74-147">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="e8a74-148"><xref:System.IO.FileAccess.ReadWrite> 是特殊值的範例。</span><span class="sxs-lookup"><span data-stu-id="e8a74-148"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>  
  
 <span data-ttu-id="e8a74-149">**X AVOID** 建立旗標列舉，其中某些值的組合會無效。</span><span class="sxs-lookup"><span data-stu-id="e8a74-149">**X AVOID** creating flag enums where certain combinations of values are invalid.</span></span>  
  
 <span data-ttu-id="e8a74-150">**X AVOID** 使用旗標為零的列舉值，除非值代表 「 清除所有旗標 」 且命名為適當的 下一步的指導方針所述。</span><span class="sxs-lookup"><span data-stu-id="e8a74-150">**X AVOID** using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>  
  
 <span data-ttu-id="e8a74-151">**✓ DO** 將零值的旗標列舉 `None`。</span><span class="sxs-lookup"><span data-stu-id="e8a74-151">**✓ DO** name the zero value of flag enums `None`.</span></span> <span data-ttu-id="e8a74-152">對於旗標列舉值必須一律表示 「 清除所有旗標 」。</span><span class="sxs-lookup"><span data-stu-id="e8a74-152">For a flag enum, the value must always mean "all flags are cleared."</span></span>  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a><span data-ttu-id="e8a74-153">將值加入至列舉</span><span class="sxs-lookup"><span data-stu-id="e8a74-153">Adding Value to Enums</span></span>  
 <span data-ttu-id="e8a74-154">它是很常見發現您需要將值加入至列舉，您有已出貨之後。</span><span class="sxs-lookup"><span data-stu-id="e8a74-154">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="e8a74-155">沒有潛在的應用程式相容性問題時新增的值會傳回從現有的 API，因為撰寫不夠周全的應用程式可能會正確處理新的值。</span><span class="sxs-lookup"><span data-stu-id="e8a74-155">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>  
  
 <span data-ttu-id="e8a74-156">**✓ CONSIDER** 將值加入至忽略小型的相容性風險的列舉。</span><span class="sxs-lookup"><span data-stu-id="e8a74-156">**✓ CONSIDER** adding values to enums, despite a small compatibility risk.</span></span>  
  
 <span data-ttu-id="e8a74-157">如果您有關於列舉的新增項目所造成的應用程式不相容的實際資料，請考慮新增，則傳回新的和舊值的新 API，並取代舊版的 API 應該會繼續傳回舊的值。</span><span class="sxs-lookup"><span data-stu-id="e8a74-157">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="e8a74-158">這可確保您現有的應用程式保持相容。</span><span class="sxs-lookup"><span data-stu-id="e8a74-158">This will ensure that your existing applications remain compatible.</span></span>  
  
 <span data-ttu-id="e8a74-159">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="e8a74-159">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e8a74-160">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="e8a74-160">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8a74-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8a74-161">See also</span></span>

- [<span data-ttu-id="e8a74-162">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="e8a74-162">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="e8a74-163">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="e8a74-163">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
