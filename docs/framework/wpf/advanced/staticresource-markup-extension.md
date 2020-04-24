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
ms.openlocfilehash: 5c0bb247bae525658d89d53f1672e57b87aba7bc
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646218"
---
# <a name="staticresource-markup-extension"></a><span data-ttu-id="99495-102">StaticResource 標記延伸</span><span class="sxs-lookup"><span data-stu-id="99495-102">StaticResource Markup Extension</span></span>
<span data-ttu-id="99495-103">通過查找對已定義的[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]資源的引用,為任何屬性屬性提供值。</span><span class="sxs-lookup"><span data-stu-id="99495-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="99495-104">該資源的查找行為類似於載入時間查找,它將查找以前從當前[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面標記和其他應用程式源載入的資源,並將該資源值生成為運行時物件中的屬性值。</span><span class="sxs-lookup"><span data-stu-id="99495-104">Lookup behavior for that resource is analogous to load-time lookup, which will look for resources that were previously loaded from the markup of the current [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page as well as other application sources, and will generate that resource value as the property value in the run-time objects.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="99495-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="99495-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="99495-106">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="99495-106">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="99495-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="99495-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="99495-108">要求資源的金鑰。</span><span class="sxs-lookup"><span data-stu-id="99495-108">The key for the requested resource.</span></span> <span data-ttu-id="99495-109">如果在標記中創建了資源,則[x:Key 指令](../../../desktop-wpf/xaml-services/xkey-directive.md)最初分配此密鑰,或者`key`<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>在調用 資源時作為參數提供, 則調用資源是在代碼中創建的。</span><span class="sxs-lookup"><span data-stu-id="99495-109">This key was initially assigned by the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99495-110">備註</span><span class="sxs-lookup"><span data-stu-id="99495-110">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="99495-111">不得`StaticResource`嘗試對[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]文件中進一步定義的資源進行轉發引用。</span><span class="sxs-lookup"><span data-stu-id="99495-111">A `StaticResource` must not attempt to make a forward reference to a resource that is defined lexically further within the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="99495-112">不支援嘗試執行此操作,即使此類引用未失敗,在搜索表示<xref:System.Windows.ResourceDictionary>a 的內部哈希表時,嘗試正向引用也會造成載入時間性能損失。</span><span class="sxs-lookup"><span data-stu-id="99495-112">Attempting to do so is not supported, and even if such a reference does not fail, attempting the forward reference will incur a load time performance penalty when the internal hash tables representing a <xref:System.Windows.ResourceDictionary> are searched.</span></span> <span data-ttu-id="99495-113">為獲得最佳效果,請調整資源字典的組成,以避免轉發引用。</span><span class="sxs-lookup"><span data-stu-id="99495-113">For best results, adjust the composition of your resource dictionaries such that forward references can be avoided.</span></span> <span data-ttu-id="99495-114">如果無法避免正向參考,請改用[動態資源標記延伸](dynamicresource-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="99495-114">If you cannot avoid a forward reference, use [DynamicResource Markup Extension](dynamicresource-markup-extension.md) instead.</span></span>  
  
 <span data-ttu-id="99495-115">指定的<xref:System.Windows.StaticResourceExtension.ResourceKey%2A>資源應對應於現有資源,該資源在頁面、應用程式、可用控制主題和外部資源或系統資源的某個級別使用[x:Key 指令](../../../desktop-wpf/xaml-services/xkey-directive.md)標識。</span><span class="sxs-lookup"><span data-stu-id="99495-115">The specified <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> should correspond to an existing resource, identified with an [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) at some level in your page, application, the available control themes and external resources, or system resources.</span></span> <span data-ttu-id="99495-116">資源查找按該順序進行。</span><span class="sxs-lookup"><span data-stu-id="99495-116">The resource lookup occurs in that order.</span></span> <span data-ttu-id="99495-117">有關靜態和動態資源的資源查找行為的詳細資訊,請參閱[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="99495-117">For more information about resource lookup behavior for static and dynamic resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>  
  
 <span data-ttu-id="99495-118">資源鍵可以是[XamlName 語法](../../../desktop-wpf/xaml-services/xamlname-grammar.md)中定義的任何字串。</span><span class="sxs-lookup"><span data-stu-id="99495-118">A resource key can be any string defined in the [XamlName Grammar](../../../desktop-wpf/xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="99495-119">資源金鑰也可以是其他物件類型,如<xref:System.Type>。</span><span class="sxs-lookup"><span data-stu-id="99495-119">A resource key can also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="99495-120">鍵<xref:System.Type>是如何通過隱式樣式鍵按主題設置控件樣式的基礎。</span><span class="sxs-lookup"><span data-stu-id="99495-120">A <xref:System.Type> key is fundamental to how controls can be styled by themes, through an implicit style key.</span></span> <span data-ttu-id="99495-121">如需詳細資訊，請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="99495-121">For more information, see [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="99495-122">參考資源的替代方法宣告性方法是作為[動態資源標記延伸](dynamicresource-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="99495-122">The alternative declarative means of referencing a resource is as a [DynamicResource Markup Extension](dynamicresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="99495-123">屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。</span><span class="sxs-lookup"><span data-stu-id="99495-123">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="99495-124">`StaticResource` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 延伸類別的 <xref:System.Windows.StaticResourceExtension> 值。</span><span class="sxs-lookup"><span data-stu-id="99495-124">The string token provided after the `StaticResource` identifier string is assigned as the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.StaticResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="99495-125">`StaticResource`可用於物件元素語法。</span><span class="sxs-lookup"><span data-stu-id="99495-125">`StaticResource` can be used in object element syntax.</span></span> <span data-ttu-id="99495-126">在這種情況下,需要指定<xref:System.Windows.StaticResourceExtension.ResourceKey%2A>屬性的值。</span><span class="sxs-lookup"><span data-stu-id="99495-126">In this case, specifying the value of the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="99495-127">`StaticResource` 也可以用於會指定 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 屬性 (Property) 做為 property=value 配對組的詳細屬性 (Attribute) 使用方式中。</span><span class="sxs-lookup"><span data-stu-id="99495-127">`StaticResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="99495-128">詳細使用方式通常是適用於具有一個以上可設定屬性或有些屬性為選擇性屬性的標記延伸。</span><span class="sxs-lookup"><span data-stu-id="99495-128">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="99495-129">因為 `StaticResource` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。</span><span class="sxs-lookup"><span data-stu-id="99495-129">Because `StaticResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="99495-130">在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器實現中,此標記擴展的處理由<xref:System.Windows.StaticResourceExtension>類定義。</span><span class="sxs-lookup"><span data-stu-id="99495-130">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.StaticResourceExtension> class.</span></span>  
  
 <span data-ttu-id="99495-131">`StaticResource` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="99495-131">`StaticResource` is a markup extension.</span></span> <span data-ttu-id="99495-132">如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。</span><span class="sxs-lookup"><span data-stu-id="99495-132">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="99495-133">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。</span><span class="sxs-lookup"><span data-stu-id="99495-133">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="99495-134">如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="99495-134">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99495-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99495-135">See also</span></span>

- [<span data-ttu-id="99495-136">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="99495-136">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="99495-137">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="99495-137">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="99495-138">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="99495-138">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="99495-139">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="99495-139">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="99495-140">資源和程式碼</span><span class="sxs-lookup"><span data-stu-id="99495-140">Resources and Code</span></span>](resources-and-code.md)
