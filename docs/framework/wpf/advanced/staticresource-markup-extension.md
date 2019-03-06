---
title: StaticResource 標記延伸
ms.date: 03/30/2017
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
ms.openlocfilehash: f3fb2559510d85f6e55a4784f2b528f16737a2ab
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371108"
---
# <a name="staticresource-markup-extension"></a><span data-ttu-id="36e7d-102">StaticResource 標記延伸</span><span class="sxs-lookup"><span data-stu-id="36e7d-102">StaticResource Markup Extension</span></span>
<span data-ttu-id="36e7d-103">提供值的任何[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]屬性，藉由查閱已定義之資源的參考。</span><span class="sxs-lookup"><span data-stu-id="36e7d-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="36e7d-104">該資源查閱行為相當於載入時間對應，它會尋找先前已載入，從目前標記的資源[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]其他應用程式來源，以及頁面上，且會產生做為該資源值在執行階段物件中的屬性值。</span><span class="sxs-lookup"><span data-stu-id="36e7d-104">Lookup behavior for that resource is analogous to load-time lookup, which will look for resources that were previously loaded from the markup of the current [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page as well as other application sources, and will generate that resource value as the property value in the run-time objects.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="36e7d-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="36e7d-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="36e7d-106">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="36e7d-106">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="36e7d-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="36e7d-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="36e7d-108">要求資源的金鑰。</span><span class="sxs-lookup"><span data-stu-id="36e7d-108">The key for the requested resource.</span></span> <span data-ttu-id="36e7d-109">此機碼一開始已由[X:key 指示詞](../../xaml-services/x-key-directive.md)如果資源在標記中，已建立，或已提供為`key`參數呼叫時<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>如果程式碼中所建立的資源。</span><span class="sxs-lookup"><span data-stu-id="36e7d-109">This key was initially assigned by the [x:Key Directive](../../xaml-services/x-key-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36e7d-110">備註</span><span class="sxs-lookup"><span data-stu-id="36e7d-110">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="36e7d-111">A`StaticResource`不應嘗試要向前參考資源定義在語彙上進一步[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案。</span><span class="sxs-lookup"><span data-stu-id="36e7d-111">A `StaticResource` must not attempt to make a forward reference to a resource that is defined lexically further within the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="36e7d-112">不支援嘗試執行此作業，而且即使這類的參考不會失敗，嘗試向前參考將會產生載入時間效能產生負面影響時代表內部的雜湊表<xref:System.Windows.ResourceDictionary>會搜尋。</span><span class="sxs-lookup"><span data-stu-id="36e7d-112">Attempting to do so is not supported, and even if such a reference does not fail, attempting the forward reference will incur a load time performance penalty when the internal hash tables representing a <xref:System.Windows.ResourceDictionary> are searched.</span></span> <span data-ttu-id="36e7d-113">為了獲得最佳結果，調整資源字典的組合，使您可以避免向前參考。</span><span class="sxs-lookup"><span data-stu-id="36e7d-113">For best results, adjust the composition of your resource dictionaries such that forward references can be avoided.</span></span> <span data-ttu-id="36e7d-114">如果您不能避免向前參考，請使用[DynamicResource 標記延伸](dynamicresource-markup-extension.md)改。</span><span class="sxs-lookup"><span data-stu-id="36e7d-114">If you cannot avoid a forward reference, use [DynamicResource Markup Extension](dynamicresource-markup-extension.md) instead.</span></span>  
  
 <span data-ttu-id="36e7d-115">指定<xref:System.Windows.StaticResourceExtension.ResourceKey%2A>應該會對應至現有的資源，以識別[X:key 指示詞](../../xaml-services/x-key-directive.md)一些在您的頁面、 應用程式、 可用的控制項主題和外部資源或系統資源的層級。</span><span class="sxs-lookup"><span data-stu-id="36e7d-115">The specified <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> should correspond to an existing resource, identified with an [x:Key Directive](../../xaml-services/x-key-directive.md) at some level in your page, application, the available control themes and external resources, or system resources.</span></span> <span data-ttu-id="36e7d-116">依此順序，就會發生資源查閱。</span><span class="sxs-lookup"><span data-stu-id="36e7d-116">The resource lookup occurs in that order.</span></span> <span data-ttu-id="36e7d-117">如需靜態和動態資源的資源查閱行為的詳細資訊，請參閱[XAML 資源](xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="36e7d-117">For more information about resource lookup behavior for static and dynamic resources, see [XAML Resources](xaml-resources.md).</span></span>  
  
 <span data-ttu-id="36e7d-118">資源索引鍵可以是任何字串中定義[XamlName 文法](../../xaml-services/xamlname-grammar.md)。</span><span class="sxs-lookup"><span data-stu-id="36e7d-118">A resource key can be any string defined in the [XamlName Grammar](../../xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="36e7d-119">資源索引鍵也可以是其他物件類型，例如<xref:System.Type>。</span><span class="sxs-lookup"><span data-stu-id="36e7d-119">A resource key can also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="36e7d-120">A<xref:System.Type>金鑰是透過隱含樣式索引鍵，如何可以由佈景主題，有樣式控制項的基礎。</span><span class="sxs-lookup"><span data-stu-id="36e7d-120">A <xref:System.Type> key is fundamental to how controls can be styled by themes, through an implicit style key.</span></span> <span data-ttu-id="36e7d-121">如需詳細資訊，請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="36e7d-121">For more information, see [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="36e7d-122">豐富的宣告式方法的參考資源是以[DynamicResource 標記延伸](dynamicresource-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="36e7d-122">The alternative declarative means of referencing a resource is as a [DynamicResource Markup Extension](dynamicresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="36e7d-123">屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。</span><span class="sxs-lookup"><span data-stu-id="36e7d-123">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="36e7d-124">
  `StaticResource\` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 延伸類別的 <xref:System.Windows.StaticResourceExtension> 值。</span><span class="sxs-lookup"><span data-stu-id="36e7d-124">The string token provided after the `StaticResource` identifier string is assigned as the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.StaticResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="36e7d-125">`StaticResource` 可用於物件元素語法。</span><span class="sxs-lookup"><span data-stu-id="36e7d-125">`StaticResource` can be used in object element syntax.</span></span> <span data-ttu-id="36e7d-126">在此案例中，指定的值<xref:System.Windows.StaticResourceExtension.ResourceKey%2A>屬性是必要項。</span><span class="sxs-lookup"><span data-stu-id="36e7d-126">In this case, specifying the value of the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="36e7d-127">`StaticResource` 也可以用於會指定 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 屬性 (Property) 做為 property=value 配對組的詳細屬性 (Attribute) 使用方式中。</span><span class="sxs-lookup"><span data-stu-id="36e7d-127">`StaticResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="36e7d-128">詳細使用方式通常是適用於具有一個以上可設定屬性或有些屬性為選擇性屬性的標記延伸。</span><span class="sxs-lookup"><span data-stu-id="36e7d-128">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="36e7d-129">因為 `StaticResource` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。</span><span class="sxs-lookup"><span data-stu-id="36e7d-129">Because `StaticResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="36e7d-130">在  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器實作中，這個標記延伸的處理由定義<xref:System.Windows.StaticResourceExtension>類別。</span><span class="sxs-lookup"><span data-stu-id="36e7d-130">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.StaticResourceExtension> class.</span></span>  
  
 <span data-ttu-id="36e7d-131">`StaticResource` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="36e7d-131">`StaticResource` is a markup extension.</span></span> <span data-ttu-id="36e7d-132">如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。</span><span class="sxs-lookup"><span data-stu-id="36e7d-132">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="36e7d-133">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。</span><span class="sxs-lookup"><span data-stu-id="36e7d-133">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="36e7d-134">如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="36e7d-134">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36e7d-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36e7d-135">See also</span></span>
- [<span data-ttu-id="36e7d-136">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="36e7d-136">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="36e7d-137">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="36e7d-137">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="36e7d-138">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="36e7d-138">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="36e7d-139">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="36e7d-139">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="36e7d-140">資源和程式碼</span><span class="sxs-lookup"><span data-stu-id="36e7d-140">Resources and Code</span></span>](resources-and-code.md)
