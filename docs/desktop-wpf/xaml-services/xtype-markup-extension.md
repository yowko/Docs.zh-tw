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
ms.openlocfilehash: f75d4e30dc41bbce995e466466c96c1a2830949b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071357"
---
# <a name="xtype-markup-extension"></a><span data-ttu-id="1790f-102">x:Type 標記延伸</span><span class="sxs-lookup"><span data-stu-id="1790f-102">x:Type Markup Extension</span></span>

<span data-ttu-id="1790f-103">提供 CLR<xref:System.Type>物件,該物件是指定 XAML 類型的基礎類型。</span><span class="sxs-lookup"><span data-stu-id="1790f-103">Supplies the CLR <xref:System.Type> object that is the underlying type for a specified XAML type.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="1790f-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="1790f-104">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Type prefix:typeNameValue}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="1790f-105">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="1790f-105">XAML Object Element Usage</span></span>

```xaml
<x:Type TypeName="prefix:typeNameValue"/>
```

## <a name="xaml-values"></a><span data-ttu-id="1790f-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="1790f-106">XAML Values</span></span>

|||
|-|-|
|`prefix`|<span data-ttu-id="1790f-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="1790f-107">Optional.</span></span> <span data-ttu-id="1790f-108">映射非預設 XAML 命名空間的前置碼。</span><span class="sxs-lookup"><span data-stu-id="1790f-108">A prefix that maps a non-default XAML namespace.</span></span> <span data-ttu-id="1790f-109">通常不需要指定首碼。</span><span class="sxs-lookup"><span data-stu-id="1790f-109">Specifying a prefix is frequently not necessary.</span></span> <span data-ttu-id="1790f-110">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="1790f-110">See Remarks.</span></span>|
|`typeNameValue`|<span data-ttu-id="1790f-111">必要。</span><span class="sxs-lookup"><span data-stu-id="1790f-111">Required.</span></span> <span data-ttu-id="1790f-112">可解析為當前預設 XAML 命名空間的類型名稱;或指定的映射前置首(如果`prefix`提供)。</span><span class="sxs-lookup"><span data-stu-id="1790f-112">A type name resolvable to the current default XAML namespace; or the specified mapped prefix if `prefix` is supplied.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1790f-113">備註</span><span class="sxs-lookup"><span data-stu-id="1790f-113">Remarks</span></span>

<span data-ttu-id="1790f-114">標記`x:Type`延伸具有與 C# 中的`typeof()`運算元或 Microsoft Visual `GetType` Basic 中的運算符類似的功能。</span><span class="sxs-lookup"><span data-stu-id="1790f-114">The `x:Type` markup extension has a similar function to the `typeof()` operator in C# or the `GetType` operator in Microsoft Visual Basic.</span></span>

<span data-ttu-id="1790f-115">標記`x:Type`擴展為採用<xref:System.Type>類型的屬性提供從字串轉換行為。</span><span class="sxs-lookup"><span data-stu-id="1790f-115">The `x:Type` markup extension supplies a from-string conversion behavior for properties that take the type <xref:System.Type>.</span></span> <span data-ttu-id="1790f-116">輸入是 XAML 類型。</span><span class="sxs-lookup"><span data-stu-id="1790f-116">The input is a XAML type.</span></span> <span data-ttu-id="1790f-117">輸入<xref:System.Type>XAML 類型和輸出 CLR<xref:System.Type>之間的關係<xref:System.Xaml.XamlType.UnderlyingType%2A><xref:System.Xaml.XamlType>是輸出 是輸入的輸出,在<xref:System.Xaml.XamlType>根據 XAML 架構 上下文和<xref:System.Windows.Markup.IXamlTypeResolver>上下文提供的服務查找必要的結果後。</span><span class="sxs-lookup"><span data-stu-id="1790f-117">The relationship between the input XAML type and the output CLR <xref:System.Type> is that the output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input <xref:System.Xaml.XamlType>, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>

<span data-ttu-id="1790f-118">在 .NET XAML 服務中,此標記擴展<xref:System.Windows.Markup.TypeExtension>的處理由 類定義。</span><span class="sxs-lookup"><span data-stu-id="1790f-118">In .NET XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.TypeExtension> class.</span></span>

<span data-ttu-id="1790f-119">在特定框架實現中,某些作為<xref:System.Type>值的屬性可以直接接受類型的名稱(類型的`Name`字串值)。</span><span class="sxs-lookup"><span data-stu-id="1790f-119">In specific framework implementations, some properties that take <xref:System.Type> as a value can accept the name of the type directly (the string value of the type `Name`).</span></span> <span data-ttu-id="1790f-120">但是,實現此行為是一個複雜的方案。</span><span class="sxs-lookup"><span data-stu-id="1790f-120">However, implementing this behavior is a complex scenario.</span></span> <span data-ttu-id="1790f-121">有關示例,請參閱後面的「WPF 使用說明」 部分。</span><span class="sxs-lookup"><span data-stu-id="1790f-121">For examples, see the "WPF Usage Notes" section that follows.</span></span>

<span data-ttu-id="1790f-122">屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。</span><span class="sxs-lookup"><span data-stu-id="1790f-122">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="1790f-123">`x:Type` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 延伸類別的 <xref:System.Windows.Markup.TypeExtension> 值。</span><span class="sxs-lookup"><span data-stu-id="1790f-123">The string token provided after the `x:Type` identifier string is assigned as the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> value of the underlying <xref:System.Windows.Markup.TypeExtension> extension class.</span></span> <span data-ttu-id="1790f-124">在基於 CLR 類型的 .NET XAML 服務的預設 XAML 架構上下文<xref:System.Reflection.MemberInfo.Name%2A>中,此屬性的值<xref:System.Reflection.MemberInfo.Name%2A>是所需類型的,或者包含非預設 XAML 命名空間映射的前置碼。</span><span class="sxs-lookup"><span data-stu-id="1790f-124">Under the default XAML schema context for .NET XAML Services, which is based on CLR types, the value of this attribute is either the <xref:System.Reflection.MemberInfo.Name%2A> of the desired type, or contains that <xref:System.Reflection.MemberInfo.Name%2A> preceded by a prefix for a non-default XAML namespace mapping.</span></span>

<span data-ttu-id="1790f-125">標記`x:Type`擴展可用於物件元素語法。</span><span class="sxs-lookup"><span data-stu-id="1790f-125">The `x:Type` markup extension can be used in object element syntax.</span></span> <span data-ttu-id="1790f-126">在這種情況下,需要指定<xref:System.Windows.Markup.TypeExtension.TypeName%2A>屬性的值才能正確初始化擴展。</span><span class="sxs-lookup"><span data-stu-id="1790f-126">In this case, specifying the value of the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> property is required to properly initialize the extension.</span></span>

<span data-ttu-id="1790f-127">標記`x:Type`擴展也可以用作詳細屬性;但是,此用途並不常見:`<object property="{x:Type TypeName=typeNameValue}" .../>`</span><span class="sxs-lookup"><span data-stu-id="1790f-127">The `x:Type` markup extension can also be used as a verbose attribute; however this use is not typical: `<object property="{x:Type TypeName=typeNameValue}" .../>`</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="1790f-128">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="1790f-128">WPF Usage Notes</span></span>

### <a name="default-xaml-namespace-and-type-mapping"></a><span data-ttu-id="1790f-129">預設 XAML 命名空間和類型映射</span><span class="sxs-lookup"><span data-stu-id="1790f-129">Default XAML Namespace and Type Mapping</span></span>

<span data-ttu-id="1790f-130">WPF 程式設計的預設 XAML 命名空間包含典型 XAML 方案所需的大多數 XAML 類型;因此,在引用 XAML 類型值時,通常可以避免前綴。</span><span class="sxs-lookup"><span data-stu-id="1790f-130">The default XAML namespace for WPF programming contains most of the XAML types you need for typical XAML scenarios; therefore, you can often avoid prefixes when referencing XAML type values.</span></span> <span data-ttu-id="1790f-131">如果要從自訂程式集引用類型或 WPF 程式集中存在但來自未映射到預設 XAML 命名空間的 CLR 命名空間的類型,則可能需要映射前綴。</span><span class="sxs-lookup"><span data-stu-id="1790f-131">You might need to map a prefix if you are referencing a type from a custom assembly or for types that exist in a WPF assembly but are from a CLR namespace that was not mapped to the default XAML namespace.</span></span> <span data-ttu-id="1790f-132">有關前置碼、XAML 命名空間與映射 CLR 命名空間的詳細資訊,請參考[WPF XAML 的 XAML 命名空間與命名空間映射](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="1790f-132">For more information about prefixes, XAML namespaces, and mapping CLR namespaces, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>

### <a name="type-properties-that-support-typename-as-string"></a><span data-ttu-id="1790f-133">類型屬性支援類型名稱作為字串</span><span class="sxs-lookup"><span data-stu-id="1790f-133">Type Properties That Support Typename-as-String</span></span>

<span data-ttu-id="1790f-134">WPF 支援啟用指定某些<xref:System.Type>類型 屬性的值`x:Type`而無需 標記擴展用的技術。</span><span class="sxs-lookup"><span data-stu-id="1790f-134">WPF supports techniques that enable specifying the value of some properties of type <xref:System.Type> without requiring an `x:Type` markup extension usage.</span></span> <span data-ttu-id="1790f-135">相反,您可以將該值指定為命名類型的字串。</span><span class="sxs-lookup"><span data-stu-id="1790f-135">Instead, you can specify the value as a string that names the type.</span></span> <span data-ttu-id="1790f-136">這方面的範例是<xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType>與<xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1790f-136">Examples of this are <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> and <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1790f-137">不支援此行為不會透過類型轉換器或標記擴展提供。</span><span class="sxs-lookup"><span data-stu-id="1790f-137">Support for this behavior is not provided through either type converters or markup extensions.</span></span> <span data-ttu-id="1790f-138">相反,這是通過<xref:System.Windows.FrameworkElementFactory>實現的延遲行為。</span><span class="sxs-lookup"><span data-stu-id="1790f-138">Instead, this is a deferral behavior implemented through <xref:System.Windows.FrameworkElementFactory>.</span></span>

<span data-ttu-id="1790f-139">銀光支持類似的約定。</span><span class="sxs-lookup"><span data-stu-id="1790f-139">Silverlight supports a similar convention.</span></span> <span data-ttu-id="1790f-140">事實上,Silverlight 目前不`{x:Type}`支援 其 XAML 語言支援`{x:Type}`,並且不接受 用於支援 WPF-Silverlight XAML 遷移的少數情況以外的用法。</span><span class="sxs-lookup"><span data-stu-id="1790f-140">In fact, Silverlight does not currently support `{x:Type}` in its XAML language support, and does not accept `{x:Type}` usages outside of a few circumstances that are intended to support WPF-Silverlight XAML migration.</span></span> <span data-ttu-id="1790f-141">因此,類型名稱即字串行為內置於所有 Silverlight 本機屬性計算中<xref:System.Type>,</span><span class="sxs-lookup"><span data-stu-id="1790f-141">Therefore, the typename-as-string behavior is built-in to all Silverlight native property evaluation where a <xref:System.Type> is the value.</span></span>

## <a name="xaml-2009"></a><span data-ttu-id="1790f-142">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="1790f-142">XAML 2009</span></span>

<span data-ttu-id="1790f-143">XAML 2009 為泛型類型提供了其他支援,並`x:TypeArguments`修改`x:Type`了和的功能行為,並提供此支援。</span><span class="sxs-lookup"><span data-stu-id="1790f-143">XAML 2009 provides additional support for generic types and modifies the feature behavior of `x:TypeArguments` and `x:Type` to provide this support.</span></span>

- <span data-ttu-id="1790f-144">`x:TypeArguments`泛型物件實例化的關聯物件元素可以位於根以外的元素上。</span><span class="sxs-lookup"><span data-stu-id="1790f-144">`x:TypeArguments` and the associated object element for a generic object instantiation can be on elements other than the root.</span></span> <span data-ttu-id="1790f-145">有關詳細資訊,請參閱[x:Type 參數指令](xtypearguments-directive.md)的「XAML 2009」部分。</span><span class="sxs-lookup"><span data-stu-id="1790f-145">For more information, see the "XAML 2009" section of [x:TypeArguments Directive](xtypearguments-directive.md).</span></span>

- <span data-ttu-id="1790f-146">XAML 2009 支援用於在標記中指定泛型類型約束的語法。</span><span class="sxs-lookup"><span data-stu-id="1790f-146">XAML 2009 supports a syntax for specifying a generic type's constraint in markup.</span></span> <span data-ttu-id="1790f-147">這可以`x:TypeArguments`通過、`x:Type`由或兩個要素組合使用。</span><span class="sxs-lookup"><span data-stu-id="1790f-147">This can be used by `x:TypeArguments`, by `x:Type`, or by the two features in combination.</span></span>

- <span data-ttu-id="1790f-148">處理 XAML 2009 負載時實現的 WPF XAML 也會將此功能<xref:System.Type>添加到使用 類型的某些框架屬性的隱式類型轉換行為中。</span><span class="sxs-lookup"><span data-stu-id="1790f-148">WPF XAML implementation when processing XAML 2009 for load also adds this capability to the implicit type conversion behavior for certain framework properties that use type <xref:System.Type>.</span></span>

<span data-ttu-id="1790f-149">在 WPF 中,可以使用 XAML 2009 功能,但僅適用於鬆散的 XAML(未標記編譯的 XAML)。</span><span class="sxs-lookup"><span data-stu-id="1790f-149">In WPF, you can use XAML 2009 features but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="1790f-150">WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。</span><span class="sxs-lookup"><span data-stu-id="1790f-150">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>

## <a name="see-also"></a><span data-ttu-id="1790f-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1790f-151">See also</span></span>

- <xref:System.Windows.Style>
- [<span data-ttu-id="1790f-152">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="1790f-152">Styling and Templating</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="1790f-153">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="1790f-153">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
- [<span data-ttu-id="1790f-154">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="1790f-154">Markup Extensions and WPF XAML</span></span>](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
