---
title: ThemeDictionary 標記延伸
ms.date: 03/30/2017
f1_keywords:
- ThemeDictionaryExtension
- ThemeDictionary
helpviewer_keywords:
- ThemeDictionary markup extension [WPF]
- XAML [WPF], ThemeDictionary markup extension
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
ms.openlocfilehash: f6ba0fe45aa11063c79d673b26794072968f4200
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646181"
---
# <a name="themedictionary-markup-extension"></a><span data-ttu-id="35dcb-102">ThemeDictionary 標記延伸</span><span class="sxs-lookup"><span data-stu-id="35dcb-102">ThemeDictionary Markup Extension</span></span>
<span data-ttu-id="35dcb-103">為自訂控制項的作者或應用程式提供一種方式，整合協力廠商的控制項來載入佈景主題特定的資源字典，以便在設定控制項樣式時使用。</span><span class="sxs-lookup"><span data-stu-id="35dcb-103">Provides a way for custom control authors or applications that integrate third-party controls to load theme-specific resource dictionaries to use in styling the control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="35dcb-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="35dcb-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="35dcb-105">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="35dcb-105">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="35dcb-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="35dcb-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`assemblyUri`|<span data-ttu-id="35dcb-107">包含主題資訊的程式集的統一資源標識符 (URI)。</span><span class="sxs-lookup"><span data-stu-id="35dcb-107">The uniform resource identifier (URI) of the assembly that contains theme information.</span></span> <span data-ttu-id="35dcb-108">一般而言，這個 Pack URI 會參考較大封裝中的組件。</span><span class="sxs-lookup"><span data-stu-id="35dcb-108">Typically, this is a pack URI that references an assembly in the larger package.</span></span> <span data-ttu-id="35dcb-109">組件資源和 Pack URI 可簡化部署問題。</span><span class="sxs-lookup"><span data-stu-id="35dcb-109">Assembly resources and pack URIs simplify deployment issues.</span></span> <span data-ttu-id="35dcb-110">如需詳細資訊，請參閱 [WPF 中的 Pack URI](../app-development/pack-uris-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="35dcb-110">For more information see [Pack URIs in WPF](../app-development/pack-uris-in-wpf.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35dcb-111">備註</span><span class="sxs-lookup"><span data-stu-id="35dcb-111">Remarks</span></span>  
 <span data-ttu-id="35dcb-112">此延伸檔只有填充一個特定屬性值: 的<xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>值 。</span><span class="sxs-lookup"><span data-stu-id="35dcb-112">This extension is intended to fill only one specific property value: a value for <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="35dcb-113">使用此擴展,可以指定單個僅資源程式集,該程式集包含僅在將 Windows Aero 主題應用於使用者系統時要使用的某些樣式,其他樣式僅在 Luna 主題處於活動狀態時使用,等等。</span><span class="sxs-lookup"><span data-stu-id="35dcb-113">By using this extension, you can specify a single resources-only assembly that contains some styles to use only when the Windows Aero theme is applied to the user's system, other styles only when the Luna theme is active, and so on.</span></span> <span data-ttu-id="35dcb-114">藉由使用此延伸模組，控制項特定的資源字典內容可在必要時自動失效並重新載入以專用於另一個佈景主題。</span><span class="sxs-lookup"><span data-stu-id="35dcb-114">By using this extension, the contents of a control-specific resource dictionary can be automatically invalidated and reloaded to be specific for another theme when required.</span></span>  
  
 <span data-ttu-id="35dcb-115">字串`assemblyUri`(<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>屬性值) 構成命名約定的基礎,該命名約定標識適用於特定主題的字典。</span><span class="sxs-lookup"><span data-stu-id="35dcb-115">The `assemblyUri` string (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property value) forms the basis of a naming convention that identifies which dictionary applies for a particular theme.</span></span> <span data-ttu-id="35dcb-116">的邏輯<xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>`ThemeDictionary`通過生成一個統一的資源標識符 (URI) 來完成約定,該標識符指向特定主題字典變體,包含在預編譯的資源程式集中。</span><span class="sxs-lookup"><span data-stu-id="35dcb-116">The <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> logic for `ThemeDictionary` completes the convention by generating a uniform resource identifier (URI) that points to a particular theme dictionary variant, as contained within a precompiled resource assembly.</span></span> <span data-ttu-id="35dcb-117">此處將不會完整說明此慣例，或是概念上與一般控制項樣式設定和頁面/應用程式層級樣式設定進行的佈景主題互動。</span><span class="sxs-lookup"><span data-stu-id="35dcb-117">Describing this convention, or theme interactions with general control styling and page/application level styling as a concept, is not covered fully here.</span></span> <span data-ttu-id="35dcb-118">使用`ThemeDictionary`的基本方案是在應用程式級別指定<xref:System.Windows.ResourceDictionary.Source%2A>`ResourceDictionary`聲明的屬性。</span><span class="sxs-lookup"><span data-stu-id="35dcb-118">The basic scenario for using `ThemeDictionary` is to specify the <xref:System.Windows.ResourceDictionary.Source%2A> property of a `ResourceDictionary` declared at the application level.</span></span> <span data-ttu-id="35dcb-119">當您透過`ThemeDictionary`擴展而不是直接 URI 為程式集提供 URI 時,擴展邏輯將提供適用於系統主題更改的失效邏輯。</span><span class="sxs-lookup"><span data-stu-id="35dcb-119">When you provide a URI for the assembly through a `ThemeDictionary` extension rather than as a direct URI, the extension logic will provide invalidation logic that applies whenever the system theme changes.</span></span>  
  
 <span data-ttu-id="35dcb-120">屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。</span><span class="sxs-lookup"><span data-stu-id="35dcb-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="35dcb-121">`ThemeDictionary` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> 延伸類別的 <xref:System.Windows.ThemeDictionaryExtension> 值。</span><span class="sxs-lookup"><span data-stu-id="35dcb-121">The string token provided after the `ThemeDictionary` identifier string is assigned as the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> value of the underlying <xref:System.Windows.ThemeDictionaryExtension> extension class.</span></span>  
  
 <span data-ttu-id="35dcb-122">`ThemeDictionary` 可能也會用於物件元素語法中。</span><span class="sxs-lookup"><span data-stu-id="35dcb-122">`ThemeDictionary` may also be used in object element syntax.</span></span> <span data-ttu-id="35dcb-123">在這種情況下,需要指定<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>屬性的值。</span><span class="sxs-lookup"><span data-stu-id="35dcb-123">In this case, specifying the value of the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property is required.</span></span>  
  
 <span data-ttu-id="35dcb-124">`ThemeDictionary` 也可以用於會指定 <xref:System.Windows.Markup.StaticExtension.Member%2A> 屬性 (Property) 做為 property=value 配對組的詳細屬性 (Attribute) 使用方式中。</span><span class="sxs-lookup"><span data-stu-id="35dcb-124">`ThemeDictionary` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.Markup.StaticExtension.Member%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 <span data-ttu-id="35dcb-125">詳細使用方式通常是適用於具有一個以上可設定屬性或有些屬性為選擇性屬性的標記延伸。</span><span class="sxs-lookup"><span data-stu-id="35dcb-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="35dcb-126">因為 `ThemeDictionary` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。</span><span class="sxs-lookup"><span data-stu-id="35dcb-126">Because `ThemeDictionary` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="35dcb-127">在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器實現中,此標記擴展的處理由<xref:System.Windows.ThemeDictionaryExtension>類定義。</span><span class="sxs-lookup"><span data-stu-id="35dcb-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.ThemeDictionaryExtension> class.</span></span>  
  
 <span data-ttu-id="35dcb-128">`ThemeDictionary` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="35dcb-128">`ThemeDictionary` is a markup extension.</span></span> <span data-ttu-id="35dcb-129">如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。</span><span class="sxs-lookup"><span data-stu-id="35dcb-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="35dcb-130">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。</span><span class="sxs-lookup"><span data-stu-id="35dcb-130">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="35dcb-131">如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="35dcb-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35dcb-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35dcb-132">See also</span></span>

- [<span data-ttu-id="35dcb-133">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="35dcb-133">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="35dcb-134">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="35dcb-134">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="35dcb-135">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="35dcb-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="35dcb-136">WPF 應用程式資源、內容和資料檔案</span><span class="sxs-lookup"><span data-stu-id="35dcb-136">WPF Application Resource, Content, and Data Files</span></span>](../app-development/wpf-application-resource-content-and-data-files.md)
