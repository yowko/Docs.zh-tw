---
title: "DynamicResource 標記延伸"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DynamicResource
- DynamicResourceExtension
helpviewer_keywords:
- XAML [WPF], DynamicResource markup extension
- DynamicResource markup extensions [WPF]
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f6c8500f9b9cd6d617789a2da3444519971ae81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="dynamicresource-markup-extension"></a><span data-ttu-id="8d99c-102">DynamicResource 標記延伸</span><span class="sxs-lookup"><span data-stu-id="8d99c-102">DynamicResource Markup Extension</span></span>
<span data-ttu-id="8d99c-103">提供的任何值[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]可以延遲是定義資源的參考值的屬性。</span><span class="sxs-lookup"><span data-stu-id="8d99c-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by deferring that value to be a reference to a defined resource.</span></span> <span data-ttu-id="8d99c-104">該資源的查閱行為相當於執行階段查閱。</span><span class="sxs-lookup"><span data-stu-id="8d99c-104">Lookup behavior for that resource is analogous to run-time lookup.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="8d99c-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="8d99c-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{DynamicResource key}" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="8d99c-106">XAML 屬性項目用法</span><span class="sxs-lookup"><span data-stu-id="8d99c-106">XAML Property Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="8d99c-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="8d99c-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="8d99c-108">要求資源的金鑰。</span><span class="sxs-lookup"><span data-stu-id="8d99c-108">The key for the requested resource.</span></span> <span data-ttu-id="8d99c-109">此機碼一開始指派[X:key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)如果資源在標記中，建立或提供做為`key`參數呼叫時<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>如果此資源原先建立在程式碼中。</span><span class="sxs-lookup"><span data-stu-id="8d99c-109">This key was initially assigned by the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d99c-110">備註</span><span class="sxs-lookup"><span data-stu-id="8d99c-110">Remarks</span></span>  
 <span data-ttu-id="8d99c-111">A`DynamicResource`會建立暫存的運算式，在初始的編譯期間和直到實際需要才能建構物件，而要求的資源值，因此延遲的資源查閱。</span><span class="sxs-lookup"><span data-stu-id="8d99c-111">A `DynamicResource` will create a temporary expression during the initial compilation and thus defer lookup for resources until the requested resource value is actually required in order to construct an object.</span></span> <span data-ttu-id="8d99c-112">這可能很之後[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]載入頁面。</span><span class="sxs-lookup"><span data-stu-id="8d99c-112">This may potentially be after the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is loaded.</span></span> <span data-ttu-id="8d99c-113">資源值會根據針對從目前的頁面範圍，開始的所有作用中的資源字典的索引鍵搜尋找到並取代為來自編譯預留位置的運算式。</span><span class="sxs-lookup"><span data-stu-id="8d99c-113">The resource value will be found based on key search against all active resource dictionaries starting from the current page scope, and is substituted for the placeholder expression from compilation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8d99c-114">相依性屬性在優先順序方面，`DynamicResource`運算式就相當於套用動態資源參考所在的位置。</span><span class="sxs-lookup"><span data-stu-id="8d99c-114">In terms of dependency property precedence, a `DynamicResource` expression is equivalent to the position where the dynamic resource reference is applied.</span></span> <span data-ttu-id="8d99c-115">如果您設定如先前所擁有的屬性為區域數值`DynamicResource`運算式做為區域數值，`DynamicResource`完全移除。</span><span class="sxs-lookup"><span data-stu-id="8d99c-115">If you set a local value for a property that previously had a `DynamicResource` expression as the local value, the `DynamicResource` is completely removed.</span></span> <span data-ttu-id="8d99c-116">如需詳細資訊，請參閱[相依性屬性值優先順序](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="8d99c-116">For details, see [Dependency Property Value Precedence](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).</span></span>  
  
 <span data-ttu-id="8d99c-117">特定資源的存取情況會特別適用於`DynamicResource`相[StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="8d99c-117">Certain resource access scenarios are particularly appropriate for `DynamicResource` as opposed to a [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).</span></span> <span data-ttu-id="8d99c-118">請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)有關的相對優點和效能影響`DynamicResource`和`StaticResource`。</span><span class="sxs-lookup"><span data-stu-id="8d99c-118">See [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md) for a discussion about the relative merits and performance implications of `DynamicResource` and `StaticResource`.</span></span>  
  
 <span data-ttu-id="8d99c-119">指定<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>應該對應至現有的資源取決於[X:key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)某個層級中頁面、 應用程式、 可用的控制項佈景主題和外部資源或系統資源，而資源查閱將會發生的順序。</span><span class="sxs-lookup"><span data-stu-id="8d99c-119">The specified <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> should correspond to an existing resource determined by [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) at some level in your page, application, the available control themes and external resources, or system resources, and the resource lookup will happen in that order.</span></span> <span data-ttu-id="8d99c-120">如需靜態和動態資源的資源查閱的詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="8d99c-120">For more information about resource lookup for static and dynamic resources, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="8d99c-121">資源索引鍵可能是任何字串中定義[XamlName 文法](../../../../docs/framework/xaml-services/xamlname-grammar.md)。</span><span class="sxs-lookup"><span data-stu-id="8d99c-121">A resource key may be any string defined in the [XamlName Grammar](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="8d99c-122">資源索引鍵可能也是其他物件類型，例如<xref:System.Type>。</span><span class="sxs-lookup"><span data-stu-id="8d99c-122">A resource key may also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="8d99c-123">A<xref:System.Type>索引鍵是基本的佈景主題樣式的控制項可以為何。</span><span class="sxs-lookup"><span data-stu-id="8d99c-123">A <xref:System.Type> key is fundamental to how controls can be styled by themes.</span></span> <span data-ttu-id="8d99c-124">如需詳細資訊，請參閱[控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="8d99c-124">For more information, see [Control Authoring Overview](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span></span>  
  
 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]<span data-ttu-id="8d99c-125">查閱的資源值，例如<xref:System.Windows.FrameworkElement.FindResource%2A>，請依照下列所用的相同的資源查閱邏輯`DynamicResource`。</span><span class="sxs-lookup"><span data-stu-id="8d99c-125"> for lookup of resource values, such as <xref:System.Windows.FrameworkElement.FindResource%2A>, follow the same resource lookup logic as used by `DynamicResource`.</span></span>  
  
 <span data-ttu-id="8d99c-126">其他的宣告式方法的參考的資源是為[StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="8d99c-126">The alternative declarative means of referencing a resource is as a [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="8d99c-127">屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。</span><span class="sxs-lookup"><span data-stu-id="8d99c-127">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="8d99c-128">`DynamicResource` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 延伸類別的 <xref:System.Windows.DynamicResourceExtension> 值。</span><span class="sxs-lookup"><span data-stu-id="8d99c-128">The string token provided after the `DynamicResource` identifier string is assigned as the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.DynamicResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="8d99c-129">`DynamicResource`可用於物件項目語法。</span><span class="sxs-lookup"><span data-stu-id="8d99c-129">`DynamicResource` can be used in object element syntax.</span></span> <span data-ttu-id="8d99c-130">在此情況下，指定的值<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>是必要屬性。</span><span class="sxs-lookup"><span data-stu-id="8d99c-130">In this case, specifying the value of the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="8d99c-131">`DynamicResource` 也可以用於會指定 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 屬性 (Property) 做為 property=value 配對組的詳細屬性 (Attribute) 使用方式中。</span><span class="sxs-lookup"><span data-stu-id="8d99c-131">`DynamicResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="8d99c-132">詳細使用方式通常是適用於具有一個以上可設定屬性或有些屬性為選擇性屬性的標記延伸。</span><span class="sxs-lookup"><span data-stu-id="8d99c-132">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="8d99c-133">因為 `DynamicResource` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。</span><span class="sxs-lookup"><span data-stu-id="8d99c-133">Because `DynamicResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="8d99c-134">在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器實作所定義的這個標記延伸處理<xref:System.Windows.DynamicResourceExtension>類別。</span><span class="sxs-lookup"><span data-stu-id="8d99c-134">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.DynamicResourceExtension> class.</span></span>  
  
 <span data-ttu-id="8d99c-135">`DynamicResource` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="8d99c-135">`DynamicResource` is a markup extension.</span></span> <span data-ttu-id="8d99c-136">如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。</span><span class="sxs-lookup"><span data-stu-id="8d99c-136">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="8d99c-137">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。</span><span class="sxs-lookup"><span data-stu-id="8d99c-137">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="8d99c-138">如需詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="8d99c-138">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d99c-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="8d99c-139">See Also</span></span>  
 [<span data-ttu-id="8d99c-140">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="8d99c-140">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="8d99c-141">資源和程式碼</span><span class="sxs-lookup"><span data-stu-id="8d99c-141">Resources and Code</span></span>](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [<span data-ttu-id="8d99c-142">x:Key 指示詞</span><span class="sxs-lookup"><span data-stu-id="8d99c-142">x:Key Directive</span></span>](../../../../docs/framework/xaml-services/x-key-directive.md)  
 [<span data-ttu-id="8d99c-143">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="8d99c-143">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="8d99c-144">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="8d99c-144">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="8d99c-145">StaticResource 標記延伸</span><span class="sxs-lookup"><span data-stu-id="8d99c-145">StaticResource Markup Extension</span></span>](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)  
 [<span data-ttu-id="8d99c-146">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="8d99c-146">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
