---
title: "x:Type 標記延伸"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "27"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4d645d5c953c0ff33435a5648024ace099455e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="xtype-markup-extension"></a><span data-ttu-id="cd348-102">x:Type 標記延伸</span><span class="sxs-lookup"><span data-stu-id="cd348-102">x:Type Markup Extension</span></span>
<span data-ttu-id="cd348-103">提供 CLR<xref:System.Type>是指定的 XAML 類型的基礎類型的物件。</span><span class="sxs-lookup"><span data-stu-id="cd348-103">Supplies the CLR <xref:System.Type> object that is the underlying type for a specified XAML type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="cd348-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="cd348-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Type prefix:typeNameValue}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="cd348-105">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="cd348-105">XAML Object Element Usage</span></span>  
  
```xaml  
<x:Type TypeName="prefix:typeNameValue"/>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="cd348-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="cd348-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`prefix`|<span data-ttu-id="cd348-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="cd348-107">Optional.</span></span> <span data-ttu-id="cd348-108">將非預設 XAML 命名空間對應前置詞。</span><span class="sxs-lookup"><span data-stu-id="cd348-108">A prefix that maps a non-default XAML namespace.</span></span> <span data-ttu-id="cd348-109">指定前置詞通常是不必要。</span><span class="sxs-lookup"><span data-stu-id="cd348-109">Specifying a prefix is frequently not necessary.</span></span> <span data-ttu-id="cd348-110">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="cd348-110">See Remarks.</span></span>|  
|`typeNameValue`|<span data-ttu-id="cd348-111">必要。</span><span class="sxs-lookup"><span data-stu-id="cd348-111">Required.</span></span> <span data-ttu-id="cd348-112">型別名稱解析成目前的預設 XAML 命名空間;或指定的對應前置詞，如果`prefix`提供。</span><span class="sxs-lookup"><span data-stu-id="cd348-112">A type name resolvable to the current default XAML namespace; or the specified mapped prefix if `prefix` is supplied.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd348-113">備註</span><span class="sxs-lookup"><span data-stu-id="cd348-113">Remarks</span></span>  
 <span data-ttu-id="cd348-114">`x:Type`標記延伸可以類似的函式來`typeof()`中的運算子[!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)]或`GetType`中的運算子[!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cd348-114">The `x:Type` markup extension has a similar function to the `typeof()` operator in [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] or the `GetType` operator in [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)].</span></span>  
  
 <span data-ttu-id="cd348-115">`x:Type`標記延伸提供針對接受的類型屬性，從字串轉換行為<xref:System.Type>。</span><span class="sxs-lookup"><span data-stu-id="cd348-115">The `x:Type` markup extension supplies a from-string conversion behavior for properties that take the type <xref:System.Type>.</span></span> <span data-ttu-id="cd348-116">輸入是 XAML 類型。</span><span class="sxs-lookup"><span data-stu-id="cd348-116">The input is a XAML type.</span></span> <span data-ttu-id="cd348-117">輸入的 XAML 型別與 CLR 的輸出之間的關聯性<xref:System.Type>在於輸出<xref:System.Type>是<xref:System.Xaml.XamlType.UnderlyingType%2A>輸入的<xref:System.Xaml.XamlType>之後查閱所需之,<xref:System.Xaml.XamlType>根據 XAML 結構描述內容和<xref:System.Windows.Markup.IXamlTypeResolver>內容提供的服務。</span><span class="sxs-lookup"><span data-stu-id="cd348-117">The relationship between the input XAML type and the output CLR <xref:System.Type> is that the output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input <xref:System.Xaml.XamlType>, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>  
  
 <span data-ttu-id="cd348-118">在.NET Framework XAML 服務，此標記延伸處理由定義<xref:System.Windows.Markup.TypeExtension>類別。</span><span class="sxs-lookup"><span data-stu-id="cd348-118">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.TypeExtension> class.</span></span>  
  
 <span data-ttu-id="cd348-119">在特定架構實作中，有些屬性可接受<xref:System.Type>值可以直接接受類型的名稱 (類型的字串值`Name`)。</span><span class="sxs-lookup"><span data-stu-id="cd348-119">In specific framework implementations, some properties that take <xref:System.Type> as a value can accept the name of the type directly (the string value of the type `Name`).</span></span> <span data-ttu-id="cd348-120">不過，實作這種行為是複雜的案例。</span><span class="sxs-lookup"><span data-stu-id="cd348-120">However, implementing this behavior is a complex scenario.</span></span> <span data-ttu-id="cd348-121">如需範例，請參閱 < WPF 使用量注意事項 > 一節。</span><span class="sxs-lookup"><span data-stu-id="cd348-121">For examples, see the "WPF Usage Notes" section that follows.</span></span>  
  
 <span data-ttu-id="cd348-122">屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。</span><span class="sxs-lookup"><span data-stu-id="cd348-122">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="cd348-123">`x:Type` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 延伸類別的 <xref:System.Windows.Markup.TypeExtension> 值。</span><span class="sxs-lookup"><span data-stu-id="cd348-123">The string token provided after the `x:Type` identifier string is assigned as the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> value of the underlying <xref:System.Windows.Markup.TypeExtension> extension class.</span></span> <span data-ttu-id="cd348-124">在預設 XAML 結構描述內容，針對.NET Framework XAML 服務，此作業取決於 CLR 型別，這個屬性的值是<xref:System.Reflection.MemberInfo.Name%2A>所需的型別，或包含的<xref:System.Reflection.MemberInfo.Name%2A>加上前置詞為非預設 XAML 命名空間對應。</span><span class="sxs-lookup"><span data-stu-id="cd348-124">Under the default XAML schema context for .NET Framework XAML Services, which is based on CLR types, the value of this attribute is either the <xref:System.Reflection.MemberInfo.Name%2A> of the desired type, or contains that <xref:System.Reflection.MemberInfo.Name%2A> preceded by a prefix for a non-default XAML namespace mapping.</span></span>  
  
 <span data-ttu-id="cd348-125">`x:Type`標記延伸可用於物件項目語法。</span><span class="sxs-lookup"><span data-stu-id="cd348-125">The `x:Type` markup extension can be used in object element syntax.</span></span> <span data-ttu-id="cd348-126">在此情況下，指定的值<xref:System.Windows.Markup.TypeExtension.TypeName%2A>屬性才能正確地初始化擴充功能。</span><span class="sxs-lookup"><span data-stu-id="cd348-126">In this case, specifying the value of the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> property is required to properly initialize the extension.</span></span>  
  
 <span data-ttu-id="cd348-127">`x:Type`標記延伸也可用做為詳細資訊的屬性; 不過此，請使用不是標準： `<``object``property``="{x:Type TypeName=``typeNameValue``}" .../>`</span><span class="sxs-lookup"><span data-stu-id="cd348-127">The `x:Type` markup extension can also be used as a verbose attribute; however this use is not typical: `<``object` `property``="{x:Type TypeName=``typeNameValue``}" .../>`</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="cd348-128">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="cd348-128">WPF Usage Notes</span></span>  
  
### <a name="default-xaml-namespace-and-type-mapping"></a><span data-ttu-id="cd348-129">預設 XAML 命名空間和型別對應</span><span class="sxs-lookup"><span data-stu-id="cd348-129">Default XAML Namespace and Type Mapping</span></span>  
 <span data-ttu-id="cd348-130">WPF 程式設計的預設 XAML 命名空間包含大部分的一般 XAML 情節; 所需的 XAML 型別因此，您通常可以避免前置詞時參考 XAML 類型的值。</span><span class="sxs-lookup"><span data-stu-id="cd348-130">The default XAML namespace for WPF programming contains most of the XAML types you need for typical XAML scenarios; therefore, you can often avoid prefixes when referencing XAML type values.</span></span> <span data-ttu-id="cd348-131">您可能需要對應前置詞，如果您從自訂組件或類型存在於 WPF 組件但未對應的預設 XAML 命名空間到 CLR 命名空間的參考型別。</span><span class="sxs-lookup"><span data-stu-id="cd348-131">You might need to map a prefix if you are referencing a type from a custom assembly or for types that exist in a WPF assembly but are from a CLR namespace that was not mapped to the default XAML namespace.</span></span> <span data-ttu-id="cd348-132">如需有關前置詞、 XAML 命名空間和對應的 CLR 命名空間的詳細資訊，請參閱[XAML 命名空間和 WPF XAML 命名空間對應](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="cd348-132">For more information about prefixes, XAML namespaces, and mapping CLR namespaces, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>  
  
### <a name="type-properties-that-support-typename-as-string"></a><span data-ttu-id="cd348-133">輸入屬性的支援類型名稱做為-字串</span><span class="sxs-lookup"><span data-stu-id="cd348-133">Type Properties That Support Typename-as-String</span></span>  
 <span data-ttu-id="cd348-134">WPF 支援技術可讓您指定的類型的某些內容值<xref:System.Type>而不需要`x:Type`標記延伸使用方式。</span><span class="sxs-lookup"><span data-stu-id="cd348-134">WPF supports techniques that enable specifying the value of some properties of type <xref:System.Type> without requiring an `x:Type` markup extension usage.</span></span> <span data-ttu-id="cd348-135">相反地，您可以指定值為命名類型的字串。</span><span class="sxs-lookup"><span data-stu-id="cd348-135">Instead, you can specify the value as a string that names the type.</span></span> <span data-ttu-id="cd348-136">此範例<xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType>和<xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="cd348-136">Examples of this are <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> and <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cd348-137">未透過型別轉換子或標記延伸提供支援這種行為。</span><span class="sxs-lookup"><span data-stu-id="cd348-137">Support for this behavior is not provided through either type converters or markup extensions.</span></span> <span data-ttu-id="cd348-138">相反地，這是透過實作延遲行為<xref:System.Windows.FrameworkElementFactory>。</span><span class="sxs-lookup"><span data-stu-id="cd348-138">Instead, this is a deferral behavior implemented through <xref:System.Windows.FrameworkElementFactory>.</span></span>  
  
 <span data-ttu-id="cd348-139">Silverlight 支援類似的慣例。</span><span class="sxs-lookup"><span data-stu-id="cd348-139">Silverlight supports a similar convention.</span></span> <span data-ttu-id="cd348-140">事實上，Silverlight 目前不支援`{x:Type}`中其 XAML 語言支援，而且不接受`{x:Type}`在某些情況下，為了支援 WPF Silverlight XAML 移轉之外的使用方式。</span><span class="sxs-lookup"><span data-stu-id="cd348-140">In fact, Silverlight does not currently support `{x:Type}` in its XAML language support, and does not accept `{x:Type}` usages outside of a few circumstances that are intended to support WPF-Silverlight XAML migration.</span></span> <span data-ttu-id="cd348-141">因此，類型名稱做為字串行為是內建於所有的 Silverlight 原生屬性評估其中<xref:System.Type>的值。</span><span class="sxs-lookup"><span data-stu-id="cd348-141">Therefore, the typename-as-string behavior is built-in to all Silverlight native property evaluation where a <xref:System.Type> is the value.</span></span>  
  
## <a name="xaml-2009"></a><span data-ttu-id="cd348-142">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="cd348-142">XAML 2009</span></span>  
 <span data-ttu-id="cd348-143">XAML 2009 支援其他的泛型類型，並修改功能行為的`x:TypeArguments`和`x:Type`提供這項支援。</span><span class="sxs-lookup"><span data-stu-id="cd348-143">XAML 2009 provides additional support for generic types and modifies the feature behavior of `x:TypeArguments` and `x:Type` to provide this support.</span></span>  
  
-   <span data-ttu-id="cd348-144">`x:TypeArguments`它的泛型物件具現化的相關聯的物件項目可以是根目錄以外的項目上。</span><span class="sxs-lookup"><span data-stu-id="cd348-144">`x:TypeArguments` and the associated object element for a generic object instantiation can be on elements other than the root.</span></span> <span data-ttu-id="cd348-145">如需詳細資訊，請參閱的 < XAML 2009 > 一節[X:typearguments 指示詞](../../../docs/framework/xaml-services/x-typearguments-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="cd348-145">For more information, see the "XAML 2009" section of [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md).</span></span>  
  
-   <span data-ttu-id="cd348-146">XAML 2009 支援語法標記中指定的泛型類型條件約束。</span><span class="sxs-lookup"><span data-stu-id="cd348-146">XAML 2009 supports a syntax for specifying a generic type's constraint in markup.</span></span> <span data-ttu-id="cd348-147">這可由`x:TypeArguments`、 藉由`x:Type`，或結合兩個功能。</span><span class="sxs-lookup"><span data-stu-id="cd348-147">This can be used by `x:TypeArguments`, by `x:Type`, or by the two features in combination.</span></span>  
  
-   <span data-ttu-id="cd348-148">WPF XAML 實作處理 XAML 2009 的負載也會將這項功能加入至特定 framework 內容的使用類型的隱含類型轉換行為時<xref:System.Type>。</span><span class="sxs-lookup"><span data-stu-id="cd348-148">WPF XAML implementation when processing XAML 2009 for load also adds this capability to the implicit type conversion behavior for certain framework properties that use type <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="cd348-149">在 WPF 中，您可以使用 XAML 2009 功能，但是僅針對鬆散的 XAML (未標記編譯 XAML)。</span><span class="sxs-lookup"><span data-stu-id="cd348-149">In WPF, you can use XAML 2009 features but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="cd348-150">WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。</span><span class="sxs-lookup"><span data-stu-id="cd348-150">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd348-151">請參閱</span><span class="sxs-lookup"><span data-stu-id="cd348-151">See Also</span></span>  
 <xref:System.Windows.Style>  
 [<span data-ttu-id="cd348-152">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="cd348-152">Styling and Templating</span></span>](../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="cd348-153">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="cd348-153">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="cd348-154">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="cd348-154">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
