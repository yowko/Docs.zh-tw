---
title: DynamicResource 標記延伸
ms.date: 03/30/2017
f1_keywords:
- DynamicResource
- DynamicResourceExtension
helpviewer_keywords:
- XAML [WPF], DynamicResource markup extension
- DynamicResource markup extensions [WPF]
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
ms.openlocfilehash: 5ccda8ba8f41a30e0ce1c832a6d3176b7fb8e8c2
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646266"
---
# <a name="dynamicresource-markup-extension"></a><span data-ttu-id="6b9ac-102">DynamicResource 標記延伸</span><span class="sxs-lookup"><span data-stu-id="6b9ac-102">DynamicResource Markup Extension</span></span>
<span data-ttu-id="6b9ac-103">通過將該值作為對[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]已定義資源的引用來為任何屬性屬性提供值。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by deferring that value to be a reference to a defined resource.</span></span> <span data-ttu-id="6b9ac-104">該資源的查找行為類似於運行時查找。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-104">Lookup behavior for that resource is analogous to run-time lookup.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="6b9ac-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="6b9ac-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{DynamicResource key}" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="6b9ac-106">XAML 屬性項目用法</span><span class="sxs-lookup"><span data-stu-id="6b9ac-106">XAML Property Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="6b9ac-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="6b9ac-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="6b9ac-108">要求資源的金鑰。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-108">The key for the requested resource.</span></span> <span data-ttu-id="6b9ac-109">如果在標記中創建了資源,則[x:Key 指令](../../../desktop-wpf/xaml-services/xkey-directive.md)最初分配此密鑰,或者`key`<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>在調用 資源時作為參數提供, 則調用資源是在代碼中創建的。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-109">This key was initially assigned by the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b9ac-110">備註</span><span class="sxs-lookup"><span data-stu-id="6b9ac-110">Remarks</span></span>  
 <span data-ttu-id="6b9ac-111">將在`DynamicResource`初始編譯期間創建臨時表達式,從而推遲查找資源,直到實際需要請求的資源值才能構造物件。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-111">A `DynamicResource` will create a temporary expression during the initial compilation and thus defer lookup for resources until the requested resource value is actually required in order to construct an object.</span></span> <span data-ttu-id="6b9ac-112">這可能是在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]載入頁面之後。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-112">This may potentially be after the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is loaded.</span></span> <span data-ttu-id="6b9ac-113">資源值將基於對從當前頁面作用域開始的所有活動資源字典的鍵搜索找到,並替換為編譯中的占位符運算式。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-113">The resource value will be found based on key search against all active resource dictionaries starting from the current page scope, and is substituted for the placeholder expression from compilation.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6b9ac-114">在依賴項屬性優先順序方面,`DynamicResource`運算式等效於應用動態資源引用的位置。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-114">In terms of dependency property precedence, a `DynamicResource` expression is equivalent to the position where the dynamic resource reference is applied.</span></span> <span data-ttu-id="6b9ac-115">如果為以前具有`DynamicResource`表示式為本地值的屬性設定局部值,則將完全刪除`DynamicResource`。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-115">If you set a local value for a property that previously had a `DynamicResource` expression as the local value, the `DynamicResource` is completely removed.</span></span> <span data-ttu-id="6b9ac-116">如需詳細資訊，請參閱[相依性屬性值優先順序](dependency-property-value-precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-116">For details, see [Dependency Property Value Precedence](dependency-property-value-precedence.md).</span></span>  
  
 <span data-ttu-id="6b9ac-117">某些資源存取機制特別`DynamicResource`適用於 靜態[資源標記延伸](staticresource-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-117">Certain resource access scenarios are particularly appropriate for `DynamicResource` as opposed to a [StaticResource Markup Extension](staticresource-markup-extension.md).</span></span> <span data-ttu-id="6b9ac-118">有關`DynamicResource``StaticResource`和的相對優點和性能影響,請參閱[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-118">See [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) for a discussion about the relative merits and performance implications of `DynamicResource` and `StaticResource`.</span></span>  
  
 <span data-ttu-id="6b9ac-119">指定的<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>應對應於[x:Key 指令](../../../desktop-wpf/xaml-services/xkey-directive.md)在頁面、應用程式、可用控制主題和外部資源或系統資源的某些級別確定的現有資源,並且資源查找將按該順序進行。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-119">The specified <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> should correspond to an existing resource determined by [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) at some level in your page, application, the available control themes and external resources, or system resources, and the resource lookup will happen in that order.</span></span> <span data-ttu-id="6b9ac-120">有關有關靜態和動態資源的資源尋找的詳細資訊,請參閱[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-120">For more information about resource lookup for static and dynamic resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>  
  
 <span data-ttu-id="6b9ac-121">資源鍵可以是[XamlName 語法](../../../desktop-wpf/xaml-services/xamlname-grammar.md)中定義的任何字串。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-121">A resource key may be any string defined in the [XamlName Grammar](../../../desktop-wpf/xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="6b9ac-122">資源金鑰也可以是其他物件類型,如<xref:System.Type>。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-122">A resource key may also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="6b9ac-123">鍵<xref:System.Type>是如何按主題設置控件樣式的基礎。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-123">A <xref:System.Type> key is fundamental to how controls can be styled by themes.</span></span> <span data-ttu-id="6b9ac-124">如需詳細資訊，請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-124">For more information, see [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="6b9ac-125">尋找資源值的 API,例如<xref:System.Windows.FrameworkElement.FindResource%2A>,遵循與使用的資源尋找邏輯相同的資源尋找邏輯`DynamicResource`。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-125">APIs for lookup of resource values, such as <xref:System.Windows.FrameworkElement.FindResource%2A>, follow the same resource lookup logic as used by `DynamicResource`.</span></span>  
  
 <span data-ttu-id="6b9ac-126">參考資源的替代方法宣告性方法是為[靜態資源標記延伸](staticresource-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-126">The alternative declarative means of referencing a resource is as a [StaticResource Markup Extension](staticresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="6b9ac-127">屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-127">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="6b9ac-128">`DynamicResource` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 延伸類別的 <xref:System.Windows.DynamicResourceExtension> 值。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-128">The string token provided after the `DynamicResource` identifier string is assigned as the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.DynamicResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="6b9ac-129">`DynamicResource`可用於物件元素語法。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-129">`DynamicResource` can be used in object element syntax.</span></span> <span data-ttu-id="6b9ac-130">在這種情況下,需要指定<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>屬性的值。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-130">In this case, specifying the value of the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="6b9ac-131">`DynamicResource` 也可以用於會指定 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 屬性 (Property) 做為 property=value 配對組的詳細屬性 (Attribute) 使用方式中。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-131">`DynamicResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="6b9ac-132">詳細使用方式通常是適用於具有一個以上可設定屬性或有些屬性為選擇性屬性的標記延伸。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-132">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="6b9ac-133">因為 `DynamicResource` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-133">Because `DynamicResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="6b9ac-134">在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器實現中,此標記擴展的處理由<xref:System.Windows.DynamicResourceExtension>類定義。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-134">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.DynamicResourceExtension> class.</span></span>  
  
 <span data-ttu-id="6b9ac-135">`DynamicResource` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-135">`DynamicResource` is a markup extension.</span></span> <span data-ttu-id="6b9ac-136">如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-136">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="6b9ac-137">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-137">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="6b9ac-138">如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="6b9ac-138">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b9ac-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b9ac-139">See also</span></span>

- [<span data-ttu-id="6b9ac-140">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="6b9ac-140">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="6b9ac-141">資源和程式碼</span><span class="sxs-lookup"><span data-stu-id="6b9ac-141">Resources and Code</span></span>](resources-and-code.md)
- [<span data-ttu-id="6b9ac-142">x:Key 指示詞</span><span class="sxs-lookup"><span data-stu-id="6b9ac-142">x:Key Directive</span></span>](../../../desktop-wpf/xaml-services/xkey-directive.md)
- [<span data-ttu-id="6b9ac-143">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="6b9ac-143">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="6b9ac-144">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="6b9ac-144">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="6b9ac-145">StaticResource 標記延伸</span><span class="sxs-lookup"><span data-stu-id="6b9ac-145">StaticResource Markup Extension</span></span>](staticresource-markup-extension.md)
- [<span data-ttu-id="6b9ac-146">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="6b9ac-146">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
