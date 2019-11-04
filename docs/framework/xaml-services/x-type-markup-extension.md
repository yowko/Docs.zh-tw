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
ms.openlocfilehash: df0b3fe53cb8f284fc6e2d79a9b2cea86318d701
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459909"
---
# <a name="xtype-markup-extension"></a><span data-ttu-id="ccfb3-102">x:Type 標記延伸</span><span class="sxs-lookup"><span data-stu-id="ccfb3-102">x:Type Markup Extension</span></span>
<span data-ttu-id="ccfb3-103">提供 CLR <xref:System.Type> 物件，這是指定之 XAML 類型的基礎類型。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-103">Supplies the CLR <xref:System.Type> object that is the underlying type for a specified XAML type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="ccfb3-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="ccfb3-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Type prefix:typeNameValue}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="ccfb3-105">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="ccfb3-105">XAML Object Element Usage</span></span>  
  
```xaml  
<x:Type TypeName="prefix:typeNameValue"/>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="ccfb3-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="ccfb3-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`prefix`|<span data-ttu-id="ccfb3-107">選擇項。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-107">Optional.</span></span> <span data-ttu-id="ccfb3-108">對應非預設 XAML 命名空間的前置詞。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-108">A prefix that maps a non-default XAML namespace.</span></span> <span data-ttu-id="ccfb3-109">通常不需要指定前置詞。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-109">Specifying a prefix is frequently not necessary.</span></span> <span data-ttu-id="ccfb3-110">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-110">See Remarks.</span></span>|  
|`typeNameValue`|<span data-ttu-id="ccfb3-111">必要項。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-111">Required.</span></span> <span data-ttu-id="ccfb3-112">可解析為目前預設 XAML 命名空間的類型名稱;或者，如果提供 `prefix`，則為指定的對應前置詞。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-112">A type name resolvable to the current default XAML namespace; or the specified mapped prefix if `prefix` is supplied.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccfb3-113">備註</span><span class="sxs-lookup"><span data-stu-id="ccfb3-113">Remarks</span></span>  
 <span data-ttu-id="ccfb3-114">`x:Type` 標記延伸模組與中C#的 `typeof()` 運算子或 Microsoft Visual Basic 中的 `GetType` 運算子具有類似的功能。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-114">The `x:Type` markup extension has a similar function to the `typeof()` operator in C# or the `GetType` operator in Microsoft Visual Basic.</span></span>  
  
 <span data-ttu-id="ccfb3-115">`x:Type` 標記延伸模組會針對接受類型 <xref:System.Type>的屬性，提供 from 字串轉換行為。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-115">The `x:Type` markup extension supplies a from-string conversion behavior for properties that take the type <xref:System.Type>.</span></span> <span data-ttu-id="ccfb3-116">輸入是 XAML 型別。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-116">The input is a XAML type.</span></span> <span data-ttu-id="ccfb3-117">輸入 XAML 型別和輸出 CLR <xref:System.Type> 之間的關聯性是，在根據 XAML 架構內容和內容所提供的 <xref:System.Xaml.XamlType> 服務查閱必要的 <xref:System.Windows.Markup.IXamlTypeResolver> 之後，輸出 <xref:System.Type> 是輸入 <xref:System.Xaml.XamlType>的 <xref:System.Xaml.XamlType.UnderlyingType%2A>。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-117">The relationship between the input XAML type and the output CLR <xref:System.Type> is that the output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input <xref:System.Xaml.XamlType>, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>  
  
 <span data-ttu-id="ccfb3-118">在 .NET Framework XAML 服務中，此標記延伸模組的處理是由 <xref:System.Windows.Markup.TypeExtension> 類別所定義。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-118">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.TypeExtension> class.</span></span>  
  
 <span data-ttu-id="ccfb3-119">在特定架構的執行中，以 <xref:System.Type> 做為值的某些屬性可以直接接受類型的名稱（類型的字串值 `Name`）。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-119">In specific framework implementations, some properties that take <xref:System.Type> as a value can accept the name of the type directly (the string value of the type `Name`).</span></span> <span data-ttu-id="ccfb3-120">不過，執行此行為是一種複雜的案例。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-120">However, implementing this behavior is a complex scenario.</span></span> <span data-ttu-id="ccfb3-121">如需範例，請參閱下面的「WPF 使用注意事項」一節。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-121">For examples, see the "WPF Usage Notes" section that follows.</span></span>  
  
 <span data-ttu-id="ccfb3-122">屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-122">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="ccfb3-123">`x:Type` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 延伸類別的 <xref:System.Windows.Markup.TypeExtension> 值。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-123">The string token provided after the `x:Type` identifier string is assigned as the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> value of the underlying <xref:System.Windows.Markup.TypeExtension> extension class.</span></span> <span data-ttu-id="ccfb3-124">在 .NET Framework XAML 服務（根據 CLR 類型）的預設 XAML 架構內容底下，此屬性的值會是所需類型的 <xref:System.Reflection.MemberInfo.Name%2A>，或是包含該 <xref:System.Reflection.MemberInfo.Name%2A>，前面加上非預設 XAML 命名空間對應的前置詞。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-124">Under the default XAML schema context for .NET Framework XAML Services, which is based on CLR types, the value of this attribute is either the <xref:System.Reflection.MemberInfo.Name%2A> of the desired type, or contains that <xref:System.Reflection.MemberInfo.Name%2A> preceded by a prefix for a non-default XAML namespace mapping.</span></span>  
  
 <span data-ttu-id="ccfb3-125">`x:Type` 標記延伸模組可用於物件元素語法中。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-125">The `x:Type` markup extension can be used in object element syntax.</span></span> <span data-ttu-id="ccfb3-126">在此情況下，必須指定 <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 屬性的值，才能正確地初始化延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-126">In this case, specifying the value of the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> property is required to properly initialize the extension.</span></span>  
  
 <span data-ttu-id="ccfb3-127">`x:Type` 標記延伸也可以當做 verbose 屬性使用;不過，這種用法並不一般： `<object property="{x:Type TypeName=typeNameValue}" .../>`</span><span class="sxs-lookup"><span data-stu-id="ccfb3-127">The `x:Type` markup extension can also be used as a verbose attribute; however this use is not typical: `<object property="{x:Type TypeName=typeNameValue}" .../>`</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="ccfb3-128">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="ccfb3-128">WPF Usage Notes</span></span>  
  
### <a name="default-xaml-namespace-and-type-mapping"></a><span data-ttu-id="ccfb3-129">預設的 XAML 命名空間和類型對應</span><span class="sxs-lookup"><span data-stu-id="ccfb3-129">Default XAML Namespace and Type Mapping</span></span>  
 <span data-ttu-id="ccfb3-130">WPF 程式設計的預設 XAML 命名空間包含一般 XAML 案例所需的大部分 XAML 類型;因此，您通常可以在參考 XAML 類型值時避免前置詞。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-130">The default XAML namespace for WPF programming contains most of the XAML types you need for typical XAML scenarios; therefore, you can often avoid prefixes when referencing XAML type values.</span></span> <span data-ttu-id="ccfb3-131">如果您要從自訂群組件或存在於 WPF 元件中的類型參考，但來自未對應至預設 XAML 命名空間的 CLR 命名空間，則您可能需要對應前置詞。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-131">You might need to map a prefix if you are referencing a type from a custom assembly or for types that exist in a WPF assembly but are from a CLR namespace that was not mapped to the default XAML namespace.</span></span> <span data-ttu-id="ccfb3-132">如需前置詞、XAML 命名空間和對應 CLR 命名空間的詳細資訊，請參閱[WPF xaml 的 Xaml 命名空間和命名空間對應](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-132">For more information about prefixes, XAML namespaces, and mapping CLR namespaces, see [XAML Namespaces and Namespace Mapping for WPF XAML](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>  
  
### <a name="type-properties-that-support-typename-as-string"></a><span data-ttu-id="ccfb3-133">類型支援 Typename as String 的屬性</span><span class="sxs-lookup"><span data-stu-id="ccfb3-133">Type Properties That Support Typename-as-String</span></span>  
 <span data-ttu-id="ccfb3-134">WPF 支援的技術可讓您指定 <xref:System.Type> 類型的某些屬性值，而不需要 `x:Type` 標記延伸使用方式。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-134">WPF supports techniques that enable specifying the value of some properties of type <xref:System.Type> without requiring an `x:Type` markup extension usage.</span></span> <span data-ttu-id="ccfb3-135">相反地，您可以將值指定為名稱為類型的字串。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-135">Instead, you can specify the value as a string that names the type.</span></span> <span data-ttu-id="ccfb3-136"><xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> 和 <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>的範例如下。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-136">Examples of this are <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> and <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ccfb3-137">不是透過型別轉換器或標記延伸來提供此行為的支援。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-137">Support for this behavior is not provided through either type converters or markup extensions.</span></span> <span data-ttu-id="ccfb3-138">相反地，這是透過 <xref:System.Windows.FrameworkElementFactory>實作為延遲的行為。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-138">Instead, this is a deferral behavior implemented through <xref:System.Windows.FrameworkElementFactory>.</span></span>  
  
 <span data-ttu-id="ccfb3-139">Silverlight 支援類似的慣例。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-139">Silverlight supports a similar convention.</span></span> <span data-ttu-id="ccfb3-140">事實上，Silverlight 目前不支援其 XAML 語言支援中的 `{x:Type}`，而且在支援 WPF-Silverlight XAML 遷移的少數情況下，並不接受 `{x:Type}` 的使用方式。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-140">In fact, Silverlight does not currently support `{x:Type}` in its XAML language support, and does not accept `{x:Type}` usages outside of a few circumstances that are intended to support WPF-Silverlight XAML migration.</span></span> <span data-ttu-id="ccfb3-141">因此，typename 字串行為會內建至所有的 Silverlight 原生屬性評估，其中 <xref:System.Type> 為值。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-141">Therefore, the typename-as-string behavior is built-in to all Silverlight native property evaluation where a <xref:System.Type> is the value.</span></span>  
  
## <a name="xaml-2009"></a><span data-ttu-id="ccfb3-142">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="ccfb3-142">XAML 2009</span></span>  
 <span data-ttu-id="ccfb3-143">XAML 2009 提供泛型型別的額外支援，並修改 `x:TypeArguments` 和 `x:Type` 的功能行為，以提供這項支援。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-143">XAML 2009 provides additional support for generic types and modifies the feature behavior of `x:TypeArguments` and `x:Type` to provide this support.</span></span>  
  
- <span data-ttu-id="ccfb3-144">`x:TypeArguments` 和泛型物件具現化的相關聯物件專案，可以位於根以外的元素上。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-144">`x:TypeArguments` and the associated object element for a generic object instantiation can be on elements other than the root.</span></span> <span data-ttu-id="ccfb3-145">如需詳細資訊，請參閱[x:TypeArguments](x-typearguments-directive.md)指示詞的 "XAML 2009" 區段。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-145">For more information, see the "XAML 2009" section of [x:TypeArguments Directive](x-typearguments-directive.md).</span></span>  
  
- <span data-ttu-id="ccfb3-146">XAML 2009 支援在標記中指定泛型型別條件約束的語法。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-146">XAML 2009 supports a syntax for specifying a generic type's constraint in markup.</span></span> <span data-ttu-id="ccfb3-147">這可由 `x:TypeArguments`、`x:Type`或結合這兩個功能使用。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-147">This can be used by `x:TypeArguments`, by `x:Type`, or by the two features in combination.</span></span>  
  
- <span data-ttu-id="ccfb3-148">WPF XAML 在處理 XAML 2009 以進行載入時，也會將這項功能新增至使用類型 <xref:System.Type>之特定架構屬性的隱含類型轉換行為。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-148">WPF XAML implementation when processing XAML 2009 for load also adds this capability to the implicit type conversion behavior for certain framework properties that use type <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="ccfb3-149">在 WPF 中，您可以使用 XAML 2009 功能，但僅適用于鬆散的 XAML （不是以標記編譯的 XAML）。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-149">In WPF, you can use XAML 2009 features but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="ccfb3-150">WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。</span><span class="sxs-lookup"><span data-stu-id="ccfb3-150">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccfb3-151">請參閱</span><span class="sxs-lookup"><span data-stu-id="ccfb3-151">See also</span></span>

- <xref:System.Windows.Style>
- [<span data-ttu-id="ccfb3-152">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="ccfb3-152">Styling and Templating</span></span>](../wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="ccfb3-153">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="ccfb3-153">XAML Overview (WPF)</span></span>](../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="ccfb3-154">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="ccfb3-154">Markup Extensions and WPF XAML</span></span>](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
