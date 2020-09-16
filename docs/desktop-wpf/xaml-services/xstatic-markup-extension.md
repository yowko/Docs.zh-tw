---
title: x:Static 標記延伸
ms.date: 03/30/2017
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
ms.openlocfilehash: 634a480b4d7446ed09708f6c91276d1c2f61d4a9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551607"
---
# <a name="xstatic-markup-extension"></a><span data-ttu-id="42da5-102">x:Static 標記延伸</span><span class="sxs-lookup"><span data-stu-id="42da5-102">x:Static Markup Extension</span></span>

<span data-ttu-id="42da5-103">參考 Common Language Specification 中定義的任何靜態傳值程式碼實體， (符合 CLS) 規範的方式。</span><span class="sxs-lookup"><span data-stu-id="42da5-103">References any static by-value code entity that is defined in a Common Language Specification (CLS)–compliant way.</span></span> <span data-ttu-id="42da5-104">所參考的靜態屬性可以用來提供 XAML 中的屬性值。</span><span class="sxs-lookup"><span data-stu-id="42da5-104">The static property that is referenced can be used to provide the value of a property in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="42da5-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="42da5-105">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Static prefix:typeName.staticMemberName}" .../>
```

## <a name="xaml-values"></a><span data-ttu-id="42da5-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="42da5-106">XAML Values</span></span>

| | |
|-|-|
|`prefix`|<span data-ttu-id="42da5-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="42da5-107">Optional.</span></span> <span data-ttu-id="42da5-108">參考對應的非預設 XAML 命名空間的前置詞。</span><span class="sxs-lookup"><span data-stu-id="42da5-108">A prefix that refers to a mapped, non-default XAML namespace.</span></span> <span data-ttu-id="42da5-109">`prefix` 因為您很少參考來自預設 XAML 命名空間的靜態屬性，所以會明確顯示在使用方式中。</span><span class="sxs-lookup"><span data-stu-id="42da5-109">`prefix` is shown explicitly in the usage because you rarely reference static properties that come from a default XAML namespace.</span></span> <span data-ttu-id="42da5-110">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="42da5-110">See Remarks.</span></span>|
|`typeName`|<span data-ttu-id="42da5-111">必要。</span><span class="sxs-lookup"><span data-stu-id="42da5-111">Required.</span></span> <span data-ttu-id="42da5-112">定義所需靜態成員的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="42da5-112">The name of the type that defines the desired static member.</span></span>|
|`staticMemberName`|<span data-ttu-id="42da5-113">必要。</span><span class="sxs-lookup"><span data-stu-id="42da5-113">Required.</span></span> <span data-ttu-id="42da5-114">所需的靜態值成員名稱 (常數、靜態屬性、欄位或列舉值) 。</span><span class="sxs-lookup"><span data-stu-id="42da5-114">The name of the desired static value member (a constant, a static property, a field, or an enumeration value).</span></span>|

## <a name="remarks"></a><span data-ttu-id="42da5-115">備註</span><span class="sxs-lookup"><span data-stu-id="42da5-115">Remarks</span></span>

<span data-ttu-id="42da5-116">參考的程式碼實體必須是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="42da5-116">The code entity that is referenced must be one of the following:</span></span>

- <span data-ttu-id="42da5-117">常數</span><span class="sxs-lookup"><span data-stu-id="42da5-117">A constant</span></span>
- <span data-ttu-id="42da5-118">靜態屬性</span><span class="sxs-lookup"><span data-stu-id="42da5-118">A static property</span></span>
- <span data-ttu-id="42da5-119">欄位</span><span class="sxs-lookup"><span data-stu-id="42da5-119">A field</span></span>
- <span data-ttu-id="42da5-120">列舉值</span><span class="sxs-lookup"><span data-stu-id="42da5-120">An enumeration value</span></span>

<span data-ttu-id="42da5-121">指定任何其他程式碼實體（例如非靜態屬性）時，如果 XAML 經過標記編譯，或 XAML 載入時間剖析例外狀況，則會導致編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="42da5-121">Specifying any other code entity, such as a nonstatic property, causes a compile-time error if the XAML is markup compiled, or a XAML load-time parse exception.</span></span>

<span data-ttu-id="42da5-122">您可以 `x:Static` 參考不在目前 xaml 檔之預設 xaml 命名空間中的靜態欄位或屬性; 不過，這需要前置詞對應。</span><span class="sxs-lookup"><span data-stu-id="42da5-122">You can make `x:Static` references to static fields or properties that are not in the default XAML namespace for the current XAML document; however, this requires a prefix mapping.</span></span> <span data-ttu-id="42da5-123">XAML 命名空間幾乎一律定義在 XAML 檔的根項目上。</span><span class="sxs-lookup"><span data-stu-id="42da5-123">XAML namespaces are almost always defined on the root element of the XAML document.</span></span>

<span data-ttu-id="42da5-124">當使用預設的 XAML 架構內容執行時，.NET XAML 服務及其 XAML 讀取器和 XAML 寫入器可執行靜態屬性的查閱作業。</span><span class="sxs-lookup"><span data-stu-id="42da5-124">The lookup operations for static properties can be performed by .NET XAML Services and its XAML readers and XAML writers, when they are running with the default XAML schema context.</span></span> <span data-ttu-id="42da5-125">這個 XAML 架構內容可以使用 CLR 反映來提供物件圖形結構的必要靜態值。</span><span class="sxs-lookup"><span data-stu-id="42da5-125">This XAML schema context can use CLR reflection to provide the necessary static values for object graph construction.</span></span> <span data-ttu-id="42da5-126">`typeName`您指定的實際上是 xaml 型別名稱，而不是 CLR 型別名稱，但在使用預設的 XAML 架構內容或使用所有現有的 CLR 型 XAML 實架構時，這些基本上是相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="42da5-126">The `typeName` you specify is actually a XAML type name, not a CLR type name, although these are essentially the same name when using the default XAML schema context or when using all existing CLR-based XAML-implementing frameworks.</span></span>

<span data-ttu-id="42da5-127">當您建立的 `x:Static` 參考不是屬性值的型別時，請特別小心。</span><span class="sxs-lookup"><span data-stu-id="42da5-127">Use caution when you make `x:Static` references that are not directly the type of a property's value.</span></span> <span data-ttu-id="42da5-128">在 XAML 處理順序中，提供的標記延伸值不會叫用額外的值轉換。</span><span class="sxs-lookup"><span data-stu-id="42da5-128">In the XAML processing sequence, provided values from a markup extension do not invoke additional value conversion.</span></span> <span data-ttu-id="42da5-129">即使您的 `x:Static` 參考會建立文字字串，且以文字字串為基礎之屬性值的值轉換通常是針對該特定成員或傳回型別的任何成員值來轉換，也是如此。</span><span class="sxs-lookup"><span data-stu-id="42da5-129">This is true even if your `x:Static` reference creates a text string, and a value conversion for attribute values based on text string typically occurs either for that specific member or for any member values of the return type.</span></span>

<span data-ttu-id="42da5-130">屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。</span><span class="sxs-lookup"><span data-stu-id="42da5-130">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="42da5-131">`x:Static` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.Markup.StaticExtension.Member%2A> 延伸類別的 <xref:System.Windows.Markup.StaticExtension> 值。</span><span class="sxs-lookup"><span data-stu-id="42da5-131">The string token provided after the `x:Static` identifier string is assigned as the <xref:System.Windows.Markup.StaticExtension.Member%2A> value of the underlying <xref:System.Windows.Markup.StaticExtension> extension class.</span></span>

<span data-ttu-id="42da5-132">在技術上，有兩個其他的 XAML 用法。</span><span class="sxs-lookup"><span data-stu-id="42da5-132">There are two other XAML usages that are technically possible.</span></span> <span data-ttu-id="42da5-133">不過，這些使用方式較不常見，因為它們是不必要的詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="42da5-133">However, these usages are less common because they are unnecessarily verbose:</span></span>

01. <span data-ttu-id="42da5-134">物件元素語法。</span><span class="sxs-lookup"><span data-stu-id="42da5-134">Object element syntax.</span></span>

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

02. <span data-ttu-id="42da5-135">具有初始化字串之明確成員屬性的屬性語法。</span><span class="sxs-lookup"><span data-stu-id="42da5-135">Attribute syntax with explicit Member property for initialization string.</span></span>

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

<span data-ttu-id="42da5-136">在 .NET XAML 服務執行中，這個標記延伸的處理是由類別所定義 <xref:System.Windows.Markup.StaticExtension> 。</span><span class="sxs-lookup"><span data-stu-id="42da5-136">In .NET XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.StaticExtension> class.</span></span>

<span data-ttu-id="42da5-137">`x:Static` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="42da5-137">`x:Static` is a markup extension.</span></span> <span data-ttu-id="42da5-138">XAML 中的所有標記延伸 `{` `}` 都會在其屬性語法中使用和字元，這是 xaml 處理器辨識標記延伸必須提供值的慣例。</span><span class="sxs-lookup"><span data-stu-id="42da5-138">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must provide a value.</span></span> <span data-ttu-id="42da5-139">如需標記延伸的詳細資訊，請參閱 [Markup Extensions for XAML Overview](markup-extensions-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="42da5-139">For more information about markup extensions, see [Markup Extensions for XAML Overview](markup-extensions-overview.md).</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="42da5-140">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="42da5-140">WPF Usage Notes</span></span>

<span data-ttu-id="42da5-141">您用於 WPF 程式設計的預設 XAML 命名空間不包含許多有用的靜態屬性，而且大部分有用的靜態屬性都有支援，例如可在不需要的情況下，協助使用的類型轉換器 `{x:Static}` 。</span><span class="sxs-lookup"><span data-stu-id="42da5-141">The default XAML namespace you use for WPF programming does not contain many useful static properties, and most of the useful static properties have support such as type converters that facilitate the usage without requiring `{x:Static}` .</span></span> <span data-ttu-id="42da5-142">若為靜態屬性，如果下列其中一個條件成立，您就必須對應 XAML 命名空間的前置詞：</span><span class="sxs-lookup"><span data-stu-id="42da5-142">For static properties, you must map a prefix for a XAML namespace if one of the following is true:</span></span>

- <span data-ttu-id="42da5-143">您參考的類型存在於 WPF 中，但不是 WPF () 的預設 XAML 命名空間的一部分 `http://schemas.microsoft.com/winfx/2006/xaml/presentation` 。</span><span class="sxs-lookup"><span data-stu-id="42da5-143">You are referencing a type that exists in WPF but is not part of the default XAML namespace for WPF (`http://schemas.microsoft.com/winfx/2006/xaml/presentation`).</span></span> <span data-ttu-id="42da5-144">這是相當常見的使用案例 `x:Static` 。</span><span class="sxs-lookup"><span data-stu-id="42da5-144">This is a fairly common scenario for using `x:Static`.</span></span> <span data-ttu-id="42da5-145">例如，您可以使用 `x:Static` 具有 XAML 命名空間對應的參考，以對應到 <xref:System> CLR 命名空間和 mscorlib.dll 元件，以便參考類別的靜態屬性 <xref:System.Environment> 。</span><span class="sxs-lookup"><span data-stu-id="42da5-145">For example, you might use an `x:Static` reference with a XAML namespace mapping to the <xref:System> CLR namespace and mscorlib assembly in order to reference the static properties of the <xref:System.Environment> class.</span></span>

- <span data-ttu-id="42da5-146">您正在從自訂群組件參考型別。</span><span class="sxs-lookup"><span data-stu-id="42da5-146">You are referencing a type from a custom assembly.</span></span>

- <span data-ttu-id="42da5-147">您參考的類型存在於 WPF 元件中，但該類型在 CLR 命名空間中，而該命名空間未對應為 WPF 預設 XAML 命名空間的一部分。</span><span class="sxs-lookup"><span data-stu-id="42da5-147">You are referencing a type that exists in a WPF assembly, but that type is within a CLR namespace that was not mapped to be part of the WPF default XAML namespace.</span></span> <span data-ttu-id="42da5-148">CLR 命名空間與 WPF 的預設 XAML 命名空間的對應是由各種 WPF 元件中的定義所執行 (如需此概念的詳細資訊，請參閱 [WPF xaml 的 Xaml 命名空間和命名空間對應](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml)) 。</span><span class="sxs-lookup"><span data-stu-id="42da5-148">The mapping of CLR namespaces into the default XAML namespace for WPF is performed by definitions in the various WPF assemblies (for more information about this concept, see [XAML Namespaces and Namespace Mapping for WPF XAML](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml)).</span></span> <span data-ttu-id="42da5-149">如果該 CLR 命名空間大部分是由通常不適合 XAML 的類別定義所組成（例如），則可能會存在非對應的 CLR 命名空間 <xref:System.Windows.Threading> 。</span><span class="sxs-lookup"><span data-stu-id="42da5-149">Non-mapped CLR namespaces can exist if that CLR namespace is composed mostly of class definitions that are not typically intended for XAML, such as <xref:System.Windows.Threading>.</span></span>

<span data-ttu-id="42da5-150">如需如何使用 WPF 的前置詞和 XAML 命名空間的詳細資訊，請參閱 [WPF xaml 的 Xaml 命名空間和命名空間對應](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml)。</span><span class="sxs-lookup"><span data-stu-id="42da5-150">For more information on how to use prefixes and XAML namespaces for WPF, see [XAML Namespaces and Namespace Mapping for WPF XAML](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml).</span></span>

## <a name="see-also"></a><span data-ttu-id="42da5-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42da5-151">See also</span></span>

- [<span data-ttu-id="42da5-152">x:Type 標記延伸</span><span class="sxs-lookup"><span data-stu-id="42da5-152">x:Type Markup Extension</span></span>](xtype-markup-extension.md)
- [<span data-ttu-id="42da5-153">從 WPF 移轉至 System.Xaml 的類型</span><span class="sxs-lookup"><span data-stu-id="42da5-153">Types Migrated from WPF to System.Xaml</span></span>](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
