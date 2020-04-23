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
ms.openlocfilehash: fb9ee6807135f17fd9e0c799533bba28b369ebe2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072022"
---
# <a name="xstatic-markup-extension"></a><span data-ttu-id="43d0f-102">x:Static 標記延伸</span><span class="sxs-lookup"><span data-stu-id="43d0f-102">x:Static Markup Extension</span></span>

<span data-ttu-id="43d0f-103">引用以通用語言規範 (CLS) 相容方式定義的任何靜態按值代碼實體。</span><span class="sxs-lookup"><span data-stu-id="43d0f-103">References any static by-value code entity that is defined in a Common Language Specification (CLS)–compliant way.</span></span> <span data-ttu-id="43d0f-104">引用的靜態屬性可用於在 XAML 中提供屬性的值。</span><span class="sxs-lookup"><span data-stu-id="43d0f-104">The static property that is referenced can be used to provide the value of a property in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="43d0f-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="43d0f-105">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Static prefix:typeName.staticMemberName}" .../>
```

## <a name="xaml-values"></a><span data-ttu-id="43d0f-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="43d0f-106">XAML Values</span></span>

| | |
|-|-|
|`prefix`|<span data-ttu-id="43d0f-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="43d0f-107">Optional.</span></span> <span data-ttu-id="43d0f-108">指映射的非預設 XAML 命名空間的前置碼。</span><span class="sxs-lookup"><span data-stu-id="43d0f-108">A prefix that refers to a mapped, non-default XAML namespace.</span></span> <span data-ttu-id="43d0f-109">`prefix`在用法中顯式顯示,因為很少引用來自預設 XAML 命名空間的靜態屬性。</span><span class="sxs-lookup"><span data-stu-id="43d0f-109">`prefix` is shown explicitly in the usage because you rarely reference static properties that come from a default XAML namespace.</span></span> <span data-ttu-id="43d0f-110">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="43d0f-110">See Remarks.</span></span>|
|`typeName`|<span data-ttu-id="43d0f-111">必要。</span><span class="sxs-lookup"><span data-stu-id="43d0f-111">Required.</span></span> <span data-ttu-id="43d0f-112">定義所需靜態成員的類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="43d0f-112">The name of the type that defines the desired static member.</span></span>|
|`staticMemberName`|<span data-ttu-id="43d0f-113">必要。</span><span class="sxs-lookup"><span data-stu-id="43d0f-113">Required.</span></span> <span data-ttu-id="43d0f-114">所需靜態值成員(常量、靜態屬性、欄位或枚舉值)的名稱。</span><span class="sxs-lookup"><span data-stu-id="43d0f-114">The name of the desired static value member (a constant, a static property, a field, or an enumeration value).</span></span>|

## <a name="remarks"></a><span data-ttu-id="43d0f-115">備註</span><span class="sxs-lookup"><span data-stu-id="43d0f-115">Remarks</span></span>

<span data-ttu-id="43d0f-116">參考的代碼實體必須是以下類型之一:</span><span class="sxs-lookup"><span data-stu-id="43d0f-116">The code entity that is referenced must be one of the following:</span></span>

- <span data-ttu-id="43d0f-117">常量</span><span class="sxs-lookup"><span data-stu-id="43d0f-117">A constant</span></span>
- <span data-ttu-id="43d0f-118">靜態屬性</span><span class="sxs-lookup"><span data-stu-id="43d0f-118">A static property</span></span>
- <span data-ttu-id="43d0f-119">欄位</span><span class="sxs-lookup"><span data-stu-id="43d0f-119">A field</span></span>
- <span data-ttu-id="43d0f-120">Enlt</span><span class="sxs-lookup"><span data-stu-id="43d0f-120">An enumeration value</span></span>

<span data-ttu-id="43d0f-121">如果編譯了 XAML,或者 XAML 載入時間分析異常,則指定任何其他代碼實體(如非靜態屬性)會導致編譯時錯誤。</span><span class="sxs-lookup"><span data-stu-id="43d0f-121">Specifying any other code entity, such as a nonstatic property, causes a compile-time error if the XAML is markup compiled, or a XAML load-time parse exception.</span></span>

<span data-ttu-id="43d0f-122">您可以`x:Static`參考目前 XAML 文件的預設 XAML 命名空間中未包含的靜態欄位或屬性;但是,這需要首碼映射。</span><span class="sxs-lookup"><span data-stu-id="43d0f-122">You can make `x:Static` references to static fields or properties that are not in the default XAML namespace for the current XAML document; however, this requires a prefix mapping.</span></span> <span data-ttu-id="43d0f-123">XAML 命名空間幾乎總是在 XAML 文件的根元素上定義。</span><span class="sxs-lookup"><span data-stu-id="43d0f-123">XAML namespaces are almost always defined on the root element of the XAML document.</span></span>

<span data-ttu-id="43d0f-124">靜態屬性的尋找操作可以由 .NET XAML 服務及其 XAML 讀取器和 XAML 編寫器執行,當它們使用預設的 XAML 架構上下文運行時。</span><span class="sxs-lookup"><span data-stu-id="43d0f-124">The lookup operations for static properties can be performed by .NET XAML Services and its XAML readers and XAML writers, when they are running with the default XAML schema context.</span></span> <span data-ttu-id="43d0f-125">此 XAML 架構上下文可以使用 CLR 反射為物件圖形建構提供必要的靜態值。</span><span class="sxs-lookup"><span data-stu-id="43d0f-125">This XAML schema context can use CLR reflection to provide the necessary static values for object graph construction.</span></span> <span data-ttu-id="43d0f-126">`typeName`您指定的實際上是一個 XAML 類型名稱,而不是 CLR 類型名稱,儘管在使用預設 XAML 架構上下文或使用所有基於 CLR 的 XAML 實現框架時,這些名稱本質上是相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="43d0f-126">The `typeName` you specify is actually a XAML type name, not a CLR type name, although these are essentially the same name when using the default XAML schema context or when using all existing CLR-based XAML-implementing frameworks.</span></span>

<span data-ttu-id="43d0f-127">當您進行`x:Static`不是屬性值類型的引用時,應小心謹慎。</span><span class="sxs-lookup"><span data-stu-id="43d0f-127">Use caution when you make `x:Static` references that are not directly the type of a property's value.</span></span> <span data-ttu-id="43d0f-128">在 XAML 處理序列中,從標記擴展提供的值不會調用附加值轉換。</span><span class="sxs-lookup"><span data-stu-id="43d0f-128">In the XAML processing sequence, provided values from a markup extension do not invoke additional value conversion.</span></span> <span data-ttu-id="43d0f-129">即使引用`x:Static`創建了文本字串,也是如此,並且通常針對該特定成員或返回類型的任何成員值對基於文本字串的屬性值進行值轉換。</span><span class="sxs-lookup"><span data-stu-id="43d0f-129">This is true even if your `x:Static` reference creates a text string, and a value conversion for attribute values based on text string typically occurs either for that specific member or for any member values of the return type.</span></span>

<span data-ttu-id="43d0f-130">屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。</span><span class="sxs-lookup"><span data-stu-id="43d0f-130">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="43d0f-131">`x:Static` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.Markup.StaticExtension.Member%2A> 延伸類別的 <xref:System.Windows.Markup.StaticExtension> 值。</span><span class="sxs-lookup"><span data-stu-id="43d0f-131">The string token provided after the `x:Static` identifier string is assigned as the <xref:System.Windows.Markup.StaticExtension.Member%2A> value of the underlying <xref:System.Windows.Markup.StaticExtension> extension class.</span></span>

<span data-ttu-id="43d0f-132">技術上可能還有其他兩個 XAML 用法。</span><span class="sxs-lookup"><span data-stu-id="43d0f-132">There are two other XAML usages that are technically possible.</span></span> <span data-ttu-id="43d0f-133">但是,這些用法不太常見,因為它們是不必要的冗長:</span><span class="sxs-lookup"><span data-stu-id="43d0f-133">However, these usages are less common because they are unnecessarily verbose:</span></span>

01. <span data-ttu-id="43d0f-134">物件元素語法。</span><span class="sxs-lookup"><span data-stu-id="43d0f-134">Object element syntax.</span></span>

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

02. <span data-ttu-id="43d0f-135">具有顯式成員屬性的屬性語法,用於初始化字串。</span><span class="sxs-lookup"><span data-stu-id="43d0f-135">Attribute syntax with explicit Member property for initialization string.</span></span>

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

<span data-ttu-id="43d0f-136">在 .NET XAML 服務實現中,此標記擴展<xref:System.Windows.Markup.StaticExtension>的處理由 類定義。</span><span class="sxs-lookup"><span data-stu-id="43d0f-136">In .NET XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.StaticExtension> class.</span></span>

<span data-ttu-id="43d0f-137">`x:Static` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="43d0f-137">`x:Static` is a markup extension.</span></span> <span data-ttu-id="43d0f-138">XAML 中的所有標記擴展在其屬性語法中`{``}`使用和字元,這是 XAML 處理器識別標記擴展必須提供值的約定。</span><span class="sxs-lookup"><span data-stu-id="43d0f-138">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must provide a value.</span></span> <span data-ttu-id="43d0f-139">如需標記延伸的詳細資訊，請參閱 [Markup Extensions for XAML Overview](markup-extensions-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="43d0f-139">For more information about markup extensions, see [Markup Extensions for XAML Overview](markup-extensions-overview.md).</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="43d0f-140">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="43d0f-140">WPF Usage Notes</span></span>

<span data-ttu-id="43d0f-141">用於 WPF 程式設計的預設 XAML 命名空間不包含許多有用的靜態屬性,並且大多數有用的靜態屬性都支援,例如類型轉換`{x:Static}`器,無需即可 方便使用。</span><span class="sxs-lookup"><span data-stu-id="43d0f-141">The default XAML namespace you use for WPF programming does not contain many useful static properties, and most of the useful static properties have support such as type converters that facilitate the usage without requiring `{x:Static}` .</span></span> <span data-ttu-id="43d0f-142">對於靜態屬性,如果以下原因之一為 true,則必須映射 XAML 命名空間的前置字串:</span><span class="sxs-lookup"><span data-stu-id="43d0f-142">For static properties, you must map a prefix for a XAML namespace if one of the following is true:</span></span>

- <span data-ttu-id="43d0f-143">您引用的類型存在於 WPF 中,但不是 WPF ( 的`http://schemas.microsoft.com/winfx/2006/xaml/presentation`預設 XAML 命名空間的一部分)。</span><span class="sxs-lookup"><span data-stu-id="43d0f-143">You are referencing a type that exists in WPF but is not part of the default XAML namespace for WPF (`http://schemas.microsoft.com/winfx/2006/xaml/presentation`).</span></span> <span data-ttu-id="43d0f-144">這是使用`x:Static`的相當常見的方案。</span><span class="sxs-lookup"><span data-stu-id="43d0f-144">This is a fairly common scenario for using `x:Static`.</span></span> <span data-ttu-id="43d0f-145">例如,可以使用具有`x:Static`XAML 命名空間映<xref:System>射到 CLR 命名空間和 mscorlib 程式集的<xref:System.Environment>引用,以便引用類的靜態屬性。</span><span class="sxs-lookup"><span data-stu-id="43d0f-145">For example, you might use an `x:Static` reference with a XAML namespace mapping to the <xref:System> CLR namespace and mscorlib assembly in order to reference the static properties of the <xref:System.Environment> class.</span></span>

- <span data-ttu-id="43d0f-146">您正在引用自訂程式集中的類型。</span><span class="sxs-lookup"><span data-stu-id="43d0f-146">You are referencing a type from a custom assembly.</span></span>

- <span data-ttu-id="43d0f-147">您引用的類型存在於 WPF 程式集中,但該類型位於未映射到 WPF 預設 XAML 命名空間的 CLR 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="43d0f-147">You are referencing a type that exists in a WPF assembly, but that type is within a CLR namespace that was not mapped to be part of the WPF default XAML namespace.</span></span> <span data-ttu-id="43d0f-148">CLR 命名空間映射到 WPF 的預設 XAML 命名空間由各種 WPF 程式集中的定義執行(有關此概念的詳細資訊,請參閱[WPF XAML 的 XAML 命名空間和命名空間映射](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md))。</span><span class="sxs-lookup"><span data-stu-id="43d0f-148">The mapping of CLR namespaces into the default XAML namespace for WPF is performed by definitions in the various WPF assemblies (for more information about this concept, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)).</span></span> <span data-ttu-id="43d0f-149">如果 CLR 命名空間主要由通常不用於 XAML 的類別定義組成,則存在非映射 CLR 命名空間,例如<xref:System.Windows.Threading>。</span><span class="sxs-lookup"><span data-stu-id="43d0f-149">Non-mapped CLR namespaces can exist if that CLR namespace is composed mostly of class definitions that are not typically intended for XAML, such as <xref:System.Windows.Threading>.</span></span>

<span data-ttu-id="43d0f-150">有關如何為 WPF 使用前置碼與 XAML 命名空間的詳細資訊,請參考[WPF XAML 的 XAML 命名空間與命名空間映射](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="43d0f-150">For more information on how to use prefixes and XAML namespaces for WPF, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="43d0f-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43d0f-151">See also</span></span>

- [<span data-ttu-id="43d0f-152">x:Type 標記延伸</span><span class="sxs-lookup"><span data-stu-id="43d0f-152">x:Type Markup Extension</span></span>](xtype-markup-extension.md)
- [<span data-ttu-id="43d0f-153">從 WPF 移轉至 System.Xaml 的類型</span><span class="sxs-lookup"><span data-stu-id="43d0f-153">Types Migrated from WPF to System.Xaml</span></span>](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
