---
title: 列舉設計
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 544f617ca3a352814504125d7a61d70db5a81566
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579245"
---
# <a name="enum-design"></a><span data-ttu-id="fe135-102">列舉設計</span><span class="sxs-lookup"><span data-stu-id="fe135-102">Enum Design</span></span>
<span data-ttu-id="fe135-103">列舉是特殊類型的實值型別。</span><span class="sxs-lookup"><span data-stu-id="fe135-103">Enums are a special kind of value type.</span></span> <span data-ttu-id="fe135-104">有兩種類型的列舉： 簡單列舉和旗標的列舉。</span><span class="sxs-lookup"><span data-stu-id="fe135-104">There are two kinds of enums: simple enums and flag enums.</span></span>  
  
 <span data-ttu-id="fe135-105">簡單列舉代表少量已關閉的選項。</span><span class="sxs-lookup"><span data-stu-id="fe135-105">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="fe135-106">簡單列舉的常見範例是一組色彩。</span><span class="sxs-lookup"><span data-stu-id="fe135-106">A common example of the simple enum is a set of colors.</span></span>  
  
 <span data-ttu-id="fe135-107">旗標列舉的設計支援的列舉值的位元運算。</span><span class="sxs-lookup"><span data-stu-id="fe135-107">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="fe135-108">旗標列舉的常見範例是一串選項。</span><span class="sxs-lookup"><span data-stu-id="fe135-108">A common example of the flags enum is a list of options.</span></span>  
  
 <span data-ttu-id="fe135-109">**✓ DO** 列舉使用強型別參數、 屬性和傳回值，表示一組值。</span><span class="sxs-lookup"><span data-stu-id="fe135-109">**✓ DO** use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>  
  
 <span data-ttu-id="fe135-110">**✓ DO** 偏好使用列舉，而不靜態的常數。</span><span class="sxs-lookup"><span data-stu-id="fe135-110">**✓ DO** favor using an enum instead of static constants.</span></span>  
  
 <span data-ttu-id="fe135-111">**X DO NOT** 列舉用於開啟設定 （例如作業系統版本、 您的朋友、 等等的名稱。）。</span><span class="sxs-lookup"><span data-stu-id="fe135-111">**X DO NOT** use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>  
  
 <span data-ttu-id="fe135-112">**X DO NOT** 提供保留的列舉值是要供未來使用。</span><span class="sxs-lookup"><span data-stu-id="fe135-112">**X DO NOT** provide reserved enum values that are intended for future use.</span></span>  
  
 <span data-ttu-id="fe135-113">您一律只可以在稍後階段，將值加入至現有的列舉。</span><span class="sxs-lookup"><span data-stu-id="fe135-113">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="fe135-114">請參閱[加入值，以列舉](#add_value)如需有關將值加入至列舉。</span><span class="sxs-lookup"><span data-stu-id="fe135-114">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="fe135-115">保留的值只會干擾實際值的集合，而且通常會導致使用者的錯誤。</span><span class="sxs-lookup"><span data-stu-id="fe135-115">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>  
  
 <span data-ttu-id="fe135-116">**X AVOID** 公開僅有一個值的列舉。</span><span class="sxs-lookup"><span data-stu-id="fe135-116">**X AVOID** publicly exposing enums with only one value.</span></span>  
  
 <span data-ttu-id="fe135-117">為確保未來的 C 應用程式開發介面的擴充性常見的作法是將保留的參數加入方法簽章。</span><span class="sxs-lookup"><span data-stu-id="fe135-117">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="fe135-118">這種保留的參數可能會以單一的預設值的列舉。</span><span class="sxs-lookup"><span data-stu-id="fe135-118">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="fe135-119">這不應該在受管理的應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="fe135-119">This should not be done in managed APIs.</span></span> <span data-ttu-id="fe135-120">方法多載，可新增參數在未來的版本。</span><span class="sxs-lookup"><span data-stu-id="fe135-120">Method overloading allows adding parameters in future releases.</span></span>  
  
 <span data-ttu-id="fe135-121">**X DO NOT** sentinel 值包含在列舉中。</span><span class="sxs-lookup"><span data-stu-id="fe135-121">**X DO NOT** include sentinel values in enums.</span></span>  
  
 <span data-ttu-id="fe135-122">雖然有時候很有幫助 framework 開發人員，sentinel 值會是架構的使用者造成混淆。</span><span class="sxs-lookup"><span data-stu-id="fe135-122">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="fe135-123">它們可用來從列舉所表示的集追蹤狀態的列舉，而不是正在執行其中一個值。</span><span class="sxs-lookup"><span data-stu-id="fe135-123">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>  
  
 <span data-ttu-id="fe135-124">**✓ DO** 提供簡單列舉上零的值。</span><span class="sxs-lookup"><span data-stu-id="fe135-124">**✓ DO** provide a value of zero on simple enums.</span></span>  
  
 <span data-ttu-id="fe135-125">請考慮呼叫值類似"None"。</span><span class="sxs-lookup"><span data-stu-id="fe135-125">Consider calling the value something like "None."</span></span> <span data-ttu-id="fe135-126">如果這類值不適合這個特定的列舉，最常見的預設值的列舉應該指派基礎值為零。</span><span class="sxs-lookup"><span data-stu-id="fe135-126">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>  
  
 <span data-ttu-id="fe135-127">**✓ CONSIDER** 使用 <xref:System.Int32> （大部分的程式設計語言中的預設值） 列舉的基礎類型為除非有下列情況：</span><span class="sxs-lookup"><span data-stu-id="fe135-127">**✓ CONSIDER** using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>  
  
-   <span data-ttu-id="fe135-128">列舉是旗標列舉，而且您有 32 個以上的旗標，或希望有更多的未來。</span><span class="sxs-lookup"><span data-stu-id="fe135-128">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>  
  
-   <span data-ttu-id="fe135-129">基礎類型必須是不同於<xref:System.Int32>更容易與預期不同大小列舉的 unmanaged 程式碼的互通性。</span><span class="sxs-lookup"><span data-stu-id="fe135-129">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>  
  
-   <span data-ttu-id="fe135-130">較小的基礎類型會導致大幅節省空間。</span><span class="sxs-lookup"><span data-stu-id="fe135-130">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="fe135-131">如果您預期的列舉，主要是做為控制流程的引數時，大小會使只有些微的差異。</span><span class="sxs-lookup"><span data-stu-id="fe135-131">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="fe135-132">節省大小可能會很大如果：</span><span class="sxs-lookup"><span data-stu-id="fe135-132">The size savings might be significant if:</span></span>  
  
    -   <span data-ttu-id="fe135-133">您預期要做為經常執行個體化的結構或類別中的欄位列舉。</span><span class="sxs-lookup"><span data-stu-id="fe135-133">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>  
  
    -   <span data-ttu-id="fe135-134">您預期使用者建立大型陣列或集合的列舉執行個體。</span><span class="sxs-lookup"><span data-stu-id="fe135-134">You expect users to create large arrays or collections of the enum instances.</span></span>  
  
    -   <span data-ttu-id="fe135-135">您預期大量列舉来序列化的執行個體。</span><span class="sxs-lookup"><span data-stu-id="fe135-135">You expect a large number of instances of the enum to be serialized.</span></span>  
  
 <span data-ttu-id="fe135-136">對於記憶體使用方式，請留意，受管理的物件都`DWORD`-讓您有效地需要多個列舉或執行個體的總執行個體大小一律是因為，為了有所差別，封裝具有較小的列舉中的其他小結構對齊要無條件進位至`DWORD`。</span><span class="sxs-lookup"><span data-stu-id="fe135-136">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>  
  
 <span data-ttu-id="fe135-137">**✓ DO** 命名為旗標列舉的複數名詞或名詞片語，並使用單數名詞或名詞片語的簡單列舉。</span><span class="sxs-lookup"><span data-stu-id="fe135-137">**✓ DO** name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="fe135-138">**X DO NOT** 擴充 <xref:System.Enum?displayProperty=nameWithType> 直接。</span><span class="sxs-lookup"><span data-stu-id="fe135-138">**X DO NOT** extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>  
  
 <span data-ttu-id="fe135-139"><xref:System.Enum?displayProperty=nameWithType> 一種特殊類型正由 CLR 建立使用者定義的列舉。</span><span class="sxs-lookup"><span data-stu-id="fe135-139"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="fe135-140">大部分的程式設計語言提供可讓您存取這項功能的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="fe135-140">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="fe135-141">例如，在 C#`enum`關鍵字用來定義列舉型別。</span><span class="sxs-lookup"><span data-stu-id="fe135-141">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a><span data-ttu-id="fe135-142">設計旗標列舉</span><span class="sxs-lookup"><span data-stu-id="fe135-142">Designing Flag Enums</span></span>  
 <span data-ttu-id="fe135-143">**✓ DO** 套用 <xref:System.FlagsAttribute?displayProperty=nameWithType> 用於旗標列舉。</span><span class="sxs-lookup"><span data-stu-id="fe135-143">**✓ DO** apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="fe135-144">並不適用此屬性至簡單列舉。</span><span class="sxs-lookup"><span data-stu-id="fe135-144">Do not apply this attribute to simple enums.</span></span>  
  
 <span data-ttu-id="fe135-145">**✓ DO** 使用的 2 乘冪的旗標列舉值，因此也可以自由地結合使用位元 OR 運算。</span><span class="sxs-lookup"><span data-stu-id="fe135-145">**✓ DO** use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>  
  
 <span data-ttu-id="fe135-146">**✓ CONSIDER** 常提供的特殊的列舉值使用的旗標的組合。</span><span class="sxs-lookup"><span data-stu-id="fe135-146">**✓ CONSIDER** providing special enum values for commonly used combinations of flags.</span></span>  
  
 <span data-ttu-id="fe135-147">位元運算是一種進階的概念，而且應該不需要簡單的工作。</span><span class="sxs-lookup"><span data-stu-id="fe135-147">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="fe135-148"><xref:System.IO.FileAccess.ReadWrite> 是特殊值的範例。</span><span class="sxs-lookup"><span data-stu-id="fe135-148"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>  
  
 <span data-ttu-id="fe135-149">**X AVOID** 建立旗標列舉，其中某些值的組合會無效。</span><span class="sxs-lookup"><span data-stu-id="fe135-149">**X AVOID** creating flag enums where certain combinations of values are invalid.</span></span>  
  
 <span data-ttu-id="fe135-150">**X AVOID** 使用旗標為零的列舉值，除非值代表 「 清除所有旗標 」 且命名為適當的 下一步的指導方針所述。</span><span class="sxs-lookup"><span data-stu-id="fe135-150">**X AVOID** using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>  
  
 <span data-ttu-id="fe135-151">**✓ DO** 將零值的旗標列舉 `None`。</span><span class="sxs-lookup"><span data-stu-id="fe135-151">**✓ DO** name the zero value of flag enums `None`.</span></span> <span data-ttu-id="fe135-152">旗標列舉的值必須一律表示 「 清除所有旗標 」。</span><span class="sxs-lookup"><span data-stu-id="fe135-152">For a flag enum, the value must always mean "all flags are cleared."</span></span>  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a><span data-ttu-id="fe135-153">將值加入至列舉</span><span class="sxs-lookup"><span data-stu-id="fe135-153">Adding Value to Enums</span></span>  
 <span data-ttu-id="fe135-154">它是很常見發現您需要將值加入至列舉之後您有已出貨。</span><span class="sxs-lookup"><span data-stu-id="fe135-154">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="fe135-155">潛在的應用程式相容性問題時沒有新增的值會傳回從現有的 API，因為撰寫不夠周全的應用程式可能會正確處理新的值。</span><span class="sxs-lookup"><span data-stu-id="fe135-155">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>  
  
 <span data-ttu-id="fe135-156">**✓ CONSIDER** 將值加入至忽略小型的相容性風險的列舉。</span><span class="sxs-lookup"><span data-stu-id="fe135-156">**✓ CONSIDER** adding values to enums, despite a small compatibility risk.</span></span>  
  
 <span data-ttu-id="fe135-157">如果您有關於列舉新增的項目所造成的應用程式不相容的實際資料，請考慮加入新的 API 傳回全新和舊的值，並已被取代的舊的 API，應該會繼續傳回舊的值。</span><span class="sxs-lookup"><span data-stu-id="fe135-157">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="fe135-158">這可確保現有的應用程式保持相容。</span><span class="sxs-lookup"><span data-stu-id="fe135-158">This will ensure that your existing applications remain compatible.</span></span>  
  
 <span data-ttu-id="fe135-159">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="fe135-159">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="fe135-160">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="fe135-160">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe135-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe135-161">See Also</span></span>  
 [<span data-ttu-id="fe135-162">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="fe135-162">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="fe135-163">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="fe135-163">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
