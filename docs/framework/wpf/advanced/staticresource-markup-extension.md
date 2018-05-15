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
ms.openlocfilehash: 518a85c158c9a4472689d3c236b84278114cf3ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="staticresource-markup-extension"></a><span data-ttu-id="3b1a7-102">StaticResource 標記延伸</span><span class="sxs-lookup"><span data-stu-id="3b1a7-102">StaticResource Markup Extension</span></span>
<span data-ttu-id="3b1a7-103">提供的任何值[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]property 屬性，查看已定義之資源的參考。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="3b1a7-104">該資源的查閱行為相當於載入時查閱，從目前標記先前已載入的資源將會尋找[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面以及其他應用程式的來源，而且將會產生做為該資源值在執行階段物件的屬性值。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-104">Lookup behavior for that resource is analogous to load-time lookup, which will look for resources that were previously loaded from the markup of the current [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page as well as other application sources, and will generate that resource value as the property value in the run-time objects.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="3b1a7-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="3b1a7-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="3b1a7-106">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="3b1a7-106">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="3b1a7-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="3b1a7-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="3b1a7-108">要求資源的金鑰。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-108">The key for the requested resource.</span></span> <span data-ttu-id="3b1a7-109">此機碼一開始指派[X:key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)如果資源在標記中，建立或提供做為`key`參數呼叫時<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>如果此資源原先建立在程式碼中。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-109">This key was initially assigned by the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b1a7-110">備註</span><span class="sxs-lookup"><span data-stu-id="3b1a7-110">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3b1a7-111">A`StaticResource`不得嘗試進行向前參考到資源定義在語彙上應進一步[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-111">A `StaticResource` must not attempt to make a forward reference to a resource that is defined lexically further within the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="3b1a7-112">不支援嘗試執行這項操作，，即使這類的參考不會失敗，嘗試向前參考將會產生載入時間效能損失時代表內部的雜湊表<xref:System.Windows.ResourceDictionary>會搜尋。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-112">Attempting to do so is not supported, and even if such a reference does not fail, attempting the forward reference will incur a load time performance penalty when the internal hash tables representing a <xref:System.Windows.ResourceDictionary> are searched.</span></span> <span data-ttu-id="3b1a7-113">為獲得最佳結果，調整資源字典的組合，您可以避免向前參考。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-113">For best results, adjust the composition of your resource dictionaries such that forward references can be avoided.</span></span> <span data-ttu-id="3b1a7-114">如果您無法避免向前參考，請使用[DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)改為。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-114">If you cannot avoid a forward reference, use [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) instead.</span></span>  
  
 <span data-ttu-id="3b1a7-115">指定<xref:System.Windows.StaticResourceExtension.ResourceKey%2A>應該對應至現有的資源，以識別[X:key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)某個層級中頁面、 應用程式、 可用的控制項佈景主題和外部資源或系統資源。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-115">The specified <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> should correspond to an existing resource, identified with an [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) at some level in your page, application, the available control themes and external resources, or system resources.</span></span> <span data-ttu-id="3b1a7-116">依此順序，就會發生資源查閱。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-116">The resource lookup occurs in that order.</span></span> <span data-ttu-id="3b1a7-117">如需靜態和動態資源的資源查閱行為的詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-117">For more information about resource lookup behavior for static and dynamic resources, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="3b1a7-118">資源索引鍵可以是任何字串中定義[XamlName 文法](../../../../docs/framework/xaml-services/xamlname-grammar.md)。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-118">A resource key can be any string defined in the [XamlName Grammar](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="3b1a7-119">資源索引鍵也可以是其他物件類型，例如<xref:System.Type>。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-119">A resource key can also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="3b1a7-120">A<xref:System.Type>索引鍵是透過隱含樣式索引鍵，如何可由、 佈景主題樣式化控制項的基礎。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-120">A <xref:System.Type> key is fundamental to how controls can be styled by themes, through an implicit style key.</span></span> <span data-ttu-id="3b1a7-121">如需詳細資訊，請參閱[控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-121">For more information, see [Control Authoring Overview](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="3b1a7-122">其他的宣告式方法的參考的資源是為[DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-122">The alternative declarative means of referencing a resource is as a [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="3b1a7-123">屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-123">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="3b1a7-124">`StaticResource` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 延伸類別的 <xref:System.Windows.StaticResourceExtension> 值。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-124">The string token provided after the `StaticResource` identifier string is assigned as the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.StaticResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="3b1a7-125">`StaticResource` 可用於物件項目語法。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-125">`StaticResource` can be used in object element syntax.</span></span> <span data-ttu-id="3b1a7-126">在此情況下，指定的值<xref:System.Windows.StaticResourceExtension.ResourceKey%2A>是必要屬性。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-126">In this case, specifying the value of the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="3b1a7-127">`StaticResource` 也可以用於會指定 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 屬性 (Property) 做為 property=value 配對組的詳細屬性 (Attribute) 使用方式中。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-127">`StaticResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="3b1a7-128">詳細使用方式通常是適用於具有一個以上可設定屬性或有些屬性為選擇性屬性的標記延伸。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-128">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="3b1a7-129">因為 `StaticResource` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-129">Because `StaticResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="3b1a7-130">在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器實作所定義的這個標記延伸處理<xref:System.Windows.StaticResourceExtension>類別。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-130">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.StaticResourceExtension> class.</span></span>  
  
 <span data-ttu-id="3b1a7-131">`StaticResource` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-131">`StaticResource` is a markup extension.</span></span> <span data-ttu-id="3b1a7-132">如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-132">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="3b1a7-133">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-133">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="3b1a7-134">如需詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="3b1a7-134">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b1a7-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b1a7-135">See Also</span></span>  
 [<span data-ttu-id="3b1a7-136">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="3b1a7-136">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="3b1a7-137">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="3b1a7-137">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="3b1a7-138">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="3b1a7-138">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="3b1a7-139">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="3b1a7-139">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="3b1a7-140">資源和程式碼</span><span class="sxs-lookup"><span data-stu-id="3b1a7-140">Resources and Code</span></span>](../../../../docs/framework/wpf/advanced/resources-and-code.md)
