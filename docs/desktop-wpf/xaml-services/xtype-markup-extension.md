---
title: x:Type 標記延伸
ms.date: 03/30/2017
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
ms.openlocfilehash: 00e6684f6ad1eb8d96f72f49bd5e0d211c8166c3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559066"
---
# <a name="xtype-markup-extension"></a><span data-ttu-id="5e1b3-102">x:Type 標記延伸</span><span class="sxs-lookup"><span data-stu-id="5e1b3-102">x:Type Markup Extension</span></span>

<span data-ttu-id="5e1b3-103">提供 CLR <xref:System.Type> 物件，該物件為指定之 XAML 型別的基礎型別。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-103">Supplies the CLR <xref:System.Type> object that is the underlying type for a specified XAML type.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="5e1b3-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="5e1b3-104">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Type prefix:typeNameValue}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="5e1b3-105">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="5e1b3-105">XAML Object Element Usage</span></span>

```xaml
<x:Type TypeName="prefix:typeNameValue"/>
```

## <a name="xaml-values"></a><span data-ttu-id="5e1b3-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="5e1b3-106">XAML Values</span></span>

|||
|-|-|
|`prefix`|<span data-ttu-id="5e1b3-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-107">Optional.</span></span> <span data-ttu-id="5e1b3-108">對應非預設 XAML 命名空間的前置詞。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-108">A prefix that maps a non-default XAML namespace.</span></span> <span data-ttu-id="5e1b3-109">通常不需要指定前置詞。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-109">Specifying a prefix is frequently not necessary.</span></span> <span data-ttu-id="5e1b3-110">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-110">See Remarks.</span></span>|
|`typeNameValue`|<span data-ttu-id="5e1b3-111">必要。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-111">Required.</span></span> <span data-ttu-id="5e1b3-112">可解析為目前預設 XAML 命名空間的類型名稱;如果提供，則為指定的對應前置詞 `prefix` 。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-112">A type name resolvable to the current default XAML namespace; or the specified mapped prefix if `prefix` is supplied.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5e1b3-113">備註</span><span class="sxs-lookup"><span data-stu-id="5e1b3-113">Remarks</span></span>

<span data-ttu-id="5e1b3-114">`x:Type`標記延伸與 `typeof()` c # 中的運算子或 Microsoft Visual Basic 中的運算子具有類似的函數 `GetType` 。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-114">The `x:Type` markup extension has a similar function to the `typeof()` operator in C# or the `GetType` operator in Microsoft Visual Basic.</span></span>

<span data-ttu-id="5e1b3-115">`x:Type`標記延伸針對採用型別的屬性，提供字串轉換行為 <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-115">The `x:Type` markup extension supplies a from-string conversion behavior for properties that take the type <xref:System.Type>.</span></span> <span data-ttu-id="5e1b3-116">輸入是 XAML 類型。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-116">The input is a XAML type.</span></span> <span data-ttu-id="5e1b3-117">輸入 XAML 型別和輸出 CLR 之間的關聯性 <xref:System.Type> <xref:System.Type> <xref:System.Xaml.XamlType.UnderlyingType%2A> <xref:System.Xaml.XamlType> ，是 <xref:System.Xaml.XamlType> 根據 XAML 架構內容和內容所提供的服務，在查閱必要時，輸出是輸入的 <xref:System.Windows.Markup.IXamlTypeResolver> 。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-117">The relationship between the input XAML type and the output CLR <xref:System.Type> is that the output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input <xref:System.Xaml.XamlType>, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>

<span data-ttu-id="5e1b3-118">在 .NET XAML 服務中，此標記延伸的處理是由類別所定義 <xref:System.Windows.Markup.TypeExtension> 。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-118">In .NET XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.TypeExtension> class.</span></span>

<span data-ttu-id="5e1b3-119">在特定的架構執行中，某些做 <xref:System.Type> 為值的屬性可以直接 (類型) 的字串值來接受型別的名稱 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-119">In specific framework implementations, some properties that take <xref:System.Type> as a value can accept the name of the type directly (the string value of the type `Name`).</span></span> <span data-ttu-id="5e1b3-120">不過，執行此行為是很複雜的案例。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-120">However, implementing this behavior is a complex scenario.</span></span> <span data-ttu-id="5e1b3-121">如需範例，請參閱後面的「WPF 使用注意事項」一節。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-121">For examples, see the "WPF Usage Notes" section that follows.</span></span>

<span data-ttu-id="5e1b3-122">屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-122">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="5e1b3-123">`x:Type` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 延伸類別的 <xref:System.Windows.Markup.TypeExtension> 值。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-123">The string token provided after the `x:Type` identifier string is assigned as the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> value of the underlying <xref:System.Windows.Markup.TypeExtension> extension class.</span></span> <span data-ttu-id="5e1b3-124">在 .NET XAML 服務的預設 XAML 架構內容（以 CLR 型別為基礎）下，此屬性的值為所 <xref:System.Reflection.MemberInfo.Name%2A> 需類型的，或包含在 <xref:System.Reflection.MemberInfo.Name%2A> 非預設 XAML 命名空間對應的前置詞前面。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-124">Under the default XAML schema context for .NET XAML Services, which is based on CLR types, the value of this attribute is either the <xref:System.Reflection.MemberInfo.Name%2A> of the desired type, or contains that <xref:System.Reflection.MemberInfo.Name%2A> preceded by a prefix for a non-default XAML namespace mapping.</span></span>

<span data-ttu-id="5e1b3-125">`x:Type`標記延伸可用於物件元素語法中。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-125">The `x:Type` markup extension can be used in object element syntax.</span></span> <span data-ttu-id="5e1b3-126">在此情況下，必須指定屬性的值， <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 才能正確地初始化延伸模組。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-126">In this case, specifying the value of the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> property is required to properly initialize the extension.</span></span>

<span data-ttu-id="5e1b3-127">`x:Type`標記延伸也可以用來做為詳細資訊屬性; 不過，這種使用方式並不常見：`<object property="{x:Type TypeName=typeNameValue}" .../>`</span><span class="sxs-lookup"><span data-stu-id="5e1b3-127">The `x:Type` markup extension can also be used as a verbose attribute; however this use is not typical: `<object property="{x:Type TypeName=typeNameValue}" .../>`</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="5e1b3-128">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="5e1b3-128">WPF Usage Notes</span></span>

### <a name="default-xaml-namespace-and-type-mapping"></a><span data-ttu-id="5e1b3-129">預設 XAML 命名空間和類型對應</span><span class="sxs-lookup"><span data-stu-id="5e1b3-129">Default XAML Namespace and Type Mapping</span></span>

<span data-ttu-id="5e1b3-130">WPF 程式設計的預設 XAML 命名空間包含您一般 XAML 案例所需的大部分 XAML 類型;因此，在參考 XAML 類型值時，您通常可以避免前置詞。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-130">The default XAML namespace for WPF programming contains most of the XAML types you need for typical XAML scenarios; therefore, you can often avoid prefixes when referencing XAML type values.</span></span> <span data-ttu-id="5e1b3-131">如果您是從自訂群組件或存在於 WPF 元件中的類型，而不是來自未對應至預設 XAML 命名空間的 CLR 命名空間，則您可能需要對應前置詞。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-131">You might need to map a prefix if you are referencing a type from a custom assembly or for types that exist in a WPF assembly but are from a CLR namespace that was not mapped to the default XAML namespace.</span></span> <span data-ttu-id="5e1b3-132">如需首碼、XAML 命名空間和對應 CLR 命名空間的詳細資訊，請參閱 [WPF xaml 的 Xaml 命名空間和命名空間對應](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml)。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-132">For more information about prefixes, XAML namespaces, and mapping CLR namespaces, see [XAML Namespaces and Namespace Mapping for WPF XAML](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml).</span></span>

### <a name="type-properties-that-support-typename-as-string"></a><span data-ttu-id="5e1b3-133">支援 Typename as 字串的型別屬性</span><span class="sxs-lookup"><span data-stu-id="5e1b3-133">Type Properties That Support Typename-as-String</span></span>

<span data-ttu-id="5e1b3-134">WPF 支援的技巧可讓您指定類型的某些屬性值， <xref:System.Type> 而不需要 `x:Type` 標記延伸使用方式。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-134">WPF supports techniques that enable specifying the value of some properties of type <xref:System.Type> without requiring an `x:Type` markup extension usage.</span></span> <span data-ttu-id="5e1b3-135">相反地，您可以將此值指定為為該類型命名的字串。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-135">Instead, you can specify the value as a string that names the type.</span></span> <span data-ttu-id="5e1b3-136">這是和的 <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> 範例 <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-136">Examples of this are <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> and <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5e1b3-137">無法透過類型轉換器或標記延伸來提供此行為的支援。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-137">Support for this behavior is not provided through either type converters or markup extensions.</span></span> <span data-ttu-id="5e1b3-138">相反地，這是透過執行的延遲行為 <xref:System.Windows.FrameworkElementFactory> 。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-138">Instead, this is a deferral behavior implemented through <xref:System.Windows.FrameworkElementFactory>.</span></span>

<span data-ttu-id="5e1b3-139">Silverlight 支援類似的慣例。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-139">Silverlight supports a similar convention.</span></span> <span data-ttu-id="5e1b3-140">事實上，Silverlight 目前並不支援 `{x:Type}` 它的 XAML 語言支援，而且在 `{x:Type}` 某些情況下不接受使用 WPF Silverlight XAML 遷移的使用方式。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-140">In fact, Silverlight does not currently support `{x:Type}` in its XAML language support, and does not accept `{x:Type}` usages outside of a few circumstances that are intended to support WPF-Silverlight XAML migration.</span></span> <span data-ttu-id="5e1b3-141">因此，typename 即字串行為內建于所有 Silverlight 原生屬性評估中，其中 <xref:System.Type> 是值。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-141">Therefore, the typename-as-string behavior is built-in to all Silverlight native property evaluation where a <xref:System.Type> is the value.</span></span>

## <a name="xaml-2009"></a><span data-ttu-id="5e1b3-142">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="5e1b3-142">XAML 2009</span></span>

<span data-ttu-id="5e1b3-143">XAML 2009 提供對泛型型別的其他支援，並修改和的功能行為， `x:TypeArguments` `x:Type` 以提供這項支援。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-143">XAML 2009 provides additional support for generic types and modifies the feature behavior of `x:TypeArguments` and `x:Type` to provide this support.</span></span>

- <span data-ttu-id="5e1b3-144">`x:TypeArguments` 而且，泛型物件具現化的相關物件專案可以在根以外的元素上。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-144">`x:TypeArguments` and the associated object element for a generic object instantiation can be on elements other than the root.</span></span> <span data-ttu-id="5e1b3-145">如需詳細資訊，請參閱 [x:TypeArguments](xtypearguments-directive.md)指示詞的 "XAML 2009" 一節。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-145">For more information, see the "XAML 2009" section of [x:TypeArguments Directive](xtypearguments-directive.md).</span></span>

- <span data-ttu-id="5e1b3-146">XAML 2009 支援在標記中指定泛型型別條件約束的語法。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-146">XAML 2009 supports a syntax for specifying a generic type's constraint in markup.</span></span> <span data-ttu-id="5e1b3-147">這可由下列 `x:TypeArguments` `x:Type` 兩個功能的組合使用。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-147">This can be used by `x:TypeArguments`, by `x:Type`, or by the two features in combination.</span></span>

- <span data-ttu-id="5e1b3-148">處理適用于載入的 XAML 2009 時，WPF XAML 會將這項功能新增至使用類型之特定架構屬性的隱含類型轉換行為 <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-148">WPF XAML implementation when processing XAML 2009 for load also adds this capability to the implicit type conversion behavior for certain framework properties that use type <xref:System.Type>.</span></span>

<span data-ttu-id="5e1b3-149">在 WPF 中，您可以使用 XAML 2009 功能，但僅適用于不是標記編譯) 的鬆散 XAML (XAML。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-149">In WPF, you can use XAML 2009 features but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="5e1b3-150">WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。</span><span class="sxs-lookup"><span data-stu-id="5e1b3-150">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e1b3-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e1b3-151">See also</span></span>

- <xref:System.Windows.Style>
- [<span data-ttu-id="5e1b3-152">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="5e1b3-152">Styling and Templating</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="5e1b3-153">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="5e1b3-153">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
- [<span data-ttu-id="5e1b3-154">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="5e1b3-154">Markup Extensions and WPF XAML</span></span>](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
