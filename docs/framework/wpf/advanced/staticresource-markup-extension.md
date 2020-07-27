---
title: StaticResource 標記延伸
description: 藉由查閱已定義資源的參考，提供任何 XAML 屬性屬性的值。
ms.date: 03/30/2017
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
ms.openlocfilehash: 77396c1867dcbe279d7ba158ed9e6f5f833f17b5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164685"
---
# <a name="staticresource-markup-extension"></a><span data-ttu-id="9293b-103">StaticResource 標記延伸</span><span class="sxs-lookup"><span data-stu-id="9293b-103">StaticResource Markup Extension</span></span>
<span data-ttu-id="9293b-104">藉 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 由查閱已定義資源的參考，提供任何屬性屬性的值。</span><span class="sxs-lookup"><span data-stu-id="9293b-104">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="9293b-105">該資源的查閱行為類似于載入時間查閱，它會尋找先前從目前頁面的標記載入的資源 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，以及其他應用程式來源，並且會產生該資源值做為執行時間物件中的屬性值。</span><span class="sxs-lookup"><span data-stu-id="9293b-105">Lookup behavior for that resource is analogous to load-time lookup, which will look for resources that were previously loaded from the markup of the current [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page as well as other application sources, and will generate that resource value as the property value in the run-time objects.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="9293b-106">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="9293b-106">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{StaticResource key}" ... />  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="9293b-107">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="9293b-107">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" ... />  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="9293b-108">XAML 值</span><span class="sxs-lookup"><span data-stu-id="9293b-108">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="9293b-109">要求資源的金鑰。</span><span class="sxs-lookup"><span data-stu-id="9293b-109">The key for the requested resource.</span></span> <span data-ttu-id="9293b-110">如果資源是在標記中建立，則此索引鍵一開始是由[x：Key](../../../desktop-wpf/xaml-services/xkey-directive.md)指示詞所指派，或在呼叫時當做參數提供（ `key` <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> 如果資源是在程式碼中建立）。</span><span class="sxs-lookup"><span data-stu-id="9293b-110">This key was initially assigned by the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9293b-111">備註</span><span class="sxs-lookup"><span data-stu-id="9293b-111">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9293b-112">`StaticResource`不得嘗試對檔案中進一步定義的資源進行向前參考 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9293b-112">A `StaticResource` must not attempt to make a forward reference to a resource that is defined lexically further within the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="9293b-113">不支援嘗試這麼做，而且即使這類參考不會失敗，當搜尋代表的內部雜湊表時，嘗試向前參考將會造成載入時間效能的負面影響 <xref:System.Windows.ResourceDictionary> 。</span><span class="sxs-lookup"><span data-stu-id="9293b-113">Attempting to do so is not supported, and even if such a reference does not fail, attempting the forward reference will incur a load time performance penalty when the internal hash tables representing a <xref:System.Windows.ResourceDictionary> are searched.</span></span> <span data-ttu-id="9293b-114">為了獲得最佳結果，請調整資源字典的組合，讓向前參考可以避免。</span><span class="sxs-lookup"><span data-stu-id="9293b-114">For best results, adjust the composition of your resource dictionaries such that forward references can be avoided.</span></span> <span data-ttu-id="9293b-115">如果您無法避免正向參考，請改用[DynamicResource 標記延伸](dynamicresource-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="9293b-115">If you cannot avoid a forward reference, use [DynamicResource Markup Extension](dynamicresource-markup-extension.md) instead.</span></span>  
  
 <span data-ttu-id="9293b-116">指定的 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 應該對應至現有的資源，並在頁面、應用程式、可用的控制項主題和外部資源或系統資源的某個層級以[x：Key](../../../desktop-wpf/xaml-services/xkey-directive.md)指示詞識別。</span><span class="sxs-lookup"><span data-stu-id="9293b-116">The specified <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> should correspond to an existing resource, identified with an [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) at some level in your page, application, the available control themes and external resources, or system resources.</span></span> <span data-ttu-id="9293b-117">資源查閱會依照該順序發生。</span><span class="sxs-lookup"><span data-stu-id="9293b-117">The resource lookup occurs in that order.</span></span> <span data-ttu-id="9293b-118">如需靜態和動態資源的資源查閱行為詳細資訊，請參閱[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="9293b-118">For more information about resource lookup behavior for static and dynamic resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>  
  
 <span data-ttu-id="9293b-119">資源索引鍵可以是[XamlName 文法](../../../desktop-wpf/xaml-services/xamlname-grammar.md)中定義的任何字串。</span><span class="sxs-lookup"><span data-stu-id="9293b-119">A resource key can be any string defined in the [XamlName Grammar](../../../desktop-wpf/xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="9293b-120">資源索引鍵也可以是其他物件類型，例如 <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="9293b-120">A resource key can also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="9293b-121">索引 <xref:System.Type> 鍵是透過隱含樣式索引鍵，以主題設計控制項樣式的基礎。</span><span class="sxs-lookup"><span data-stu-id="9293b-121">A <xref:System.Type> key is fundamental to how controls can be styled by themes, through an implicit style key.</span></span> <span data-ttu-id="9293b-122">如需詳細資訊，請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9293b-122">For more information, see [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="9293b-123">參考資源的替代宣告式方法是[DynamicResource 標記延伸](dynamicresource-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="9293b-123">The alternative declarative means of referencing a resource is as a [DynamicResource Markup Extension](dynamicresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="9293b-124">屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。</span><span class="sxs-lookup"><span data-stu-id="9293b-124">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="9293b-125">`StaticResource` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 延伸類別的 <xref:System.Windows.StaticResourceExtension> 值。</span><span class="sxs-lookup"><span data-stu-id="9293b-125">The string token provided after the `StaticResource` identifier string is assigned as the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.StaticResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="9293b-126">`StaticResource`可以在物件專案語法中使用。</span><span class="sxs-lookup"><span data-stu-id="9293b-126">`StaticResource` can be used in object element syntax.</span></span> <span data-ttu-id="9293b-127">在此情況下，必須指定屬性的值 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 。</span><span class="sxs-lookup"><span data-stu-id="9293b-127">In this case, specifying the value of the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="9293b-128">`StaticResource` 也可以用於會指定 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 屬性 (Property) 做為 property=value 配對組的詳細屬性 (Attribute) 使用方式中。</span><span class="sxs-lookup"><span data-stu-id="9293b-128">`StaticResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{StaticResource ResourceKey=key}" ... />  
```  
  
 <span data-ttu-id="9293b-129">詳細使用方式通常是適用於具有一個以上可設定屬性或有些屬性為選擇性屬性的標記延伸。</span><span class="sxs-lookup"><span data-stu-id="9293b-129">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="9293b-130">因為 `StaticResource` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。</span><span class="sxs-lookup"><span data-stu-id="9293b-130">Because `StaticResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="9293b-131">在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器執行中，此標記延伸模組的處理是由類別所定義 <xref:System.Windows.StaticResourceExtension> 。</span><span class="sxs-lookup"><span data-stu-id="9293b-131">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.StaticResourceExtension> class.</span></span>  
  
 <span data-ttu-id="9293b-132">`StaticResource` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="9293b-132">`StaticResource` is a markup extension.</span></span> <span data-ttu-id="9293b-133">如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。</span><span class="sxs-lookup"><span data-stu-id="9293b-133">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="9293b-134">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。</span><span class="sxs-lookup"><span data-stu-id="9293b-134">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="9293b-135">如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="9293b-135">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9293b-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9293b-136">See also</span></span>

- [<span data-ttu-id="9293b-137">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="9293b-137">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="9293b-138">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="9293b-138">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="9293b-139">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="9293b-139">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="9293b-140">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="9293b-140">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="9293b-141">資源和程式碼</span><span class="sxs-lookup"><span data-stu-id="9293b-141">Resources and Code</span></span>](resources-and-code.md)
