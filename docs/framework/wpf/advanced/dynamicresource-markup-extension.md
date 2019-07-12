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
ms.openlocfilehash: 90768a0c816e790138ba60bd24afee242e41e652
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860278"
---
# <a name="dynamicresource-markup-extension"></a><span data-ttu-id="59cbf-102">DynamicResource 標記延伸</span><span class="sxs-lookup"><span data-stu-id="59cbf-102">DynamicResource Markup Extension</span></span>
<span data-ttu-id="59cbf-103">提供值的任何[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]延後該值是定義資源的參考的屬性。</span><span class="sxs-lookup"><span data-stu-id="59cbf-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by deferring that value to be a reference to a defined resource.</span></span> <span data-ttu-id="59cbf-104">該資源查閱行為相當於執行階段查閱。</span><span class="sxs-lookup"><span data-stu-id="59cbf-104">Lookup behavior for that resource is analogous to run-time lookup.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="59cbf-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="59cbf-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{DynamicResource key}" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="59cbf-106">XAML 屬性項目用法</span><span class="sxs-lookup"><span data-stu-id="59cbf-106">XAML Property Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="59cbf-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="59cbf-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="59cbf-108">要求資源的金鑰。</span><span class="sxs-lookup"><span data-stu-id="59cbf-108">The key for the requested resource.</span></span> <span data-ttu-id="59cbf-109">此機碼一開始已由[X:key 指示詞](../../xaml-services/x-key-directive.md)如果資源在標記中，已建立，或已提供為`key`參數呼叫時<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>如果程式碼中所建立的資源。</span><span class="sxs-lookup"><span data-stu-id="59cbf-109">This key was initially assigned by the [x:Key Directive](../../xaml-services/x-key-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59cbf-110">備註</span><span class="sxs-lookup"><span data-stu-id="59cbf-110">Remarks</span></span>  
 <span data-ttu-id="59cbf-111">A`DynamicResource`會建立初始的編譯期間的暫時運算式，並因此延後資源的查閱，直到實際需要以建構物件，而要求的資源值。</span><span class="sxs-lookup"><span data-stu-id="59cbf-111">A `DynamicResource` will create a temporary expression during the initial compilation and thus defer lookup for resources until the requested resource value is actually required in order to construct an object.</span></span> <span data-ttu-id="59cbf-112">這可能很之後[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]載入頁面。</span><span class="sxs-lookup"><span data-stu-id="59cbf-112">This may potentially be after the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is loaded.</span></span> <span data-ttu-id="59cbf-113">資源值會根據對目前的頁面範圍，從開始的所有作用中的資源字典的索引鍵搜尋找到，且用來替代預留位置運算式編譯。</span><span class="sxs-lookup"><span data-stu-id="59cbf-113">The resource value will be found based on key search against all active resource dictionaries starting from the current page scope, and is substituted for the placeholder expression from compilation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="59cbf-114">相依性屬性在優先順序方面，`DynamicResource`運算式就相當於套用動態資源參考所在的位置。</span><span class="sxs-lookup"><span data-stu-id="59cbf-114">In terms of dependency property precedence, a `DynamicResource` expression is equivalent to the position where the dynamic resource reference is applied.</span></span> <span data-ttu-id="59cbf-115">如果您設定的屬性，先前的區域數值`DynamicResource`做為區域數值，運算式`DynamicResource`已完全移除。</span><span class="sxs-lookup"><span data-stu-id="59cbf-115">If you set a local value for a property that previously had a `DynamicResource` expression as the local value, the `DynamicResource` is completely removed.</span></span> <span data-ttu-id="59cbf-116">如需詳細資訊，請參閱[相依性屬性值優先順序](dependency-property-value-precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="59cbf-116">For details, see [Dependency Property Value Precedence](dependency-property-value-precedence.md).</span></span>  
  
 <span data-ttu-id="59cbf-117">某些資源的存取情況下會特別適合`DynamicResource`相對於[StaticResource 標記延伸](staticresource-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="59cbf-117">Certain resource access scenarios are particularly appropriate for `DynamicResource` as opposed to a [StaticResource Markup Extension](staticresource-markup-extension.md).</span></span> <span data-ttu-id="59cbf-118">請參閱[XAML 資源](xaml-resources.md)如需有關的效能含意與相對優點的討論`DynamicResource`和`StaticResource`。</span><span class="sxs-lookup"><span data-stu-id="59cbf-118">See [XAML Resources](xaml-resources.md) for a discussion about the relative merits and performance implications of `DynamicResource` and `StaticResource`.</span></span>  
  
 <span data-ttu-id="59cbf-119">指定<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>應該會對應至現有的資源取決於[X:key 指示詞](../../xaml-services/x-key-directive.md)在您的頁面、 應用程式、 可用的控制項主題和外部資源或系統資源，某些層級和資源查閱會依此順序。</span><span class="sxs-lookup"><span data-stu-id="59cbf-119">The specified <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> should correspond to an existing resource determined by [x:Key Directive](../../xaml-services/x-key-directive.md) at some level in your page, application, the available control themes and external resources, or system resources, and the resource lookup will happen in that order.</span></span> <span data-ttu-id="59cbf-120">如需靜態和動態資源的資源查閱的詳細資訊，請參閱[XAML 資源](xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="59cbf-120">For more information about resource lookup for static and dynamic resources, see [XAML Resources](xaml-resources.md).</span></span>  
  
 <span data-ttu-id="59cbf-121">資源索引鍵可能是任何字串中定義[XamlName 文法](../../xaml-services/xamlname-grammar.md)。</span><span class="sxs-lookup"><span data-stu-id="59cbf-121">A resource key may be any string defined in the [XamlName Grammar](../../xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="59cbf-122">資源索引鍵可能也是其他物件類型，例如<xref:System.Type>。</span><span class="sxs-lookup"><span data-stu-id="59cbf-122">A resource key may also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="59cbf-123">A<xref:System.Type>金鑰是由佈景主題樣式的控制項可以為何的基礎。</span><span class="sxs-lookup"><span data-stu-id="59cbf-123">A <xref:System.Type> key is fundamental to how controls can be styled by themes.</span></span> <span data-ttu-id="59cbf-124">如需詳細資訊，請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="59cbf-124">For more information, see [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="59cbf-125">Api 資源的查閱值，例如<xref:System.Windows.FrameworkElement.FindResource%2A>，請依照下列所用的相同的資源查閱邏輯`DynamicResource`。</span><span class="sxs-lookup"><span data-stu-id="59cbf-125">APIs for lookup of resource values, such as <xref:System.Windows.FrameworkElement.FindResource%2A>, follow the same resource lookup logic as used by `DynamicResource`.</span></span>  
  
 <span data-ttu-id="59cbf-126">豐富的宣告式方法的參考資源是以[StaticResource 標記延伸](staticresource-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="59cbf-126">The alternative declarative means of referencing a resource is as a [StaticResource Markup Extension](staticresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="59cbf-127">屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。</span><span class="sxs-lookup"><span data-stu-id="59cbf-127">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="59cbf-128">`DynamicResource` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 延伸類別的 <xref:System.Windows.DynamicResourceExtension> 值。</span><span class="sxs-lookup"><span data-stu-id="59cbf-128">The string token provided after the `DynamicResource` identifier string is assigned as the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.DynamicResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="59cbf-129">`DynamicResource` 可用於物件元素語法。</span><span class="sxs-lookup"><span data-stu-id="59cbf-129">`DynamicResource` can be used in object element syntax.</span></span> <span data-ttu-id="59cbf-130">在此案例中，指定的值<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>屬性是必要項。</span><span class="sxs-lookup"><span data-stu-id="59cbf-130">In this case, specifying the value of the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="59cbf-131">`DynamicResource` 也可以用於會指定 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 屬性 (Property) 做為 property=value 配對組的詳細屬性 (Attribute) 使用方式中。</span><span class="sxs-lookup"><span data-stu-id="59cbf-131">`DynamicResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="59cbf-132">詳細使用方式通常是適用於具有一個以上可設定屬性或有些屬性為選擇性屬性的標記延伸。</span><span class="sxs-lookup"><span data-stu-id="59cbf-132">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="59cbf-133">因為 `DynamicResource` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。</span><span class="sxs-lookup"><span data-stu-id="59cbf-133">Because `DynamicResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="59cbf-134">在  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器實作中，這個標記延伸的處理由定義<xref:System.Windows.DynamicResourceExtension>類別。</span><span class="sxs-lookup"><span data-stu-id="59cbf-134">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.DynamicResourceExtension> class.</span></span>  
  
 <span data-ttu-id="59cbf-135">`DynamicResource` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="59cbf-135">`DynamicResource` is a markup extension.</span></span> <span data-ttu-id="59cbf-136">如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。</span><span class="sxs-lookup"><span data-stu-id="59cbf-136">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="59cbf-137">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。</span><span class="sxs-lookup"><span data-stu-id="59cbf-137">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="59cbf-138">如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="59cbf-138">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59cbf-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59cbf-139">See also</span></span>

- [<span data-ttu-id="59cbf-140">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="59cbf-140">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="59cbf-141">資源和程式碼</span><span class="sxs-lookup"><span data-stu-id="59cbf-141">Resources and Code</span></span>](resources-and-code.md)
- [<span data-ttu-id="59cbf-142">x:Key 指示詞</span><span class="sxs-lookup"><span data-stu-id="59cbf-142">x:Key Directive</span></span>](../../xaml-services/x-key-directive.md)
- [<span data-ttu-id="59cbf-143">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="59cbf-143">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="59cbf-144">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="59cbf-144">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="59cbf-145">StaticResource 標記延伸</span><span class="sxs-lookup"><span data-stu-id="59cbf-145">StaticResource Markup Extension</span></span>](staticresource-markup-extension.md)
- [<span data-ttu-id="59cbf-146">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="59cbf-146">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
