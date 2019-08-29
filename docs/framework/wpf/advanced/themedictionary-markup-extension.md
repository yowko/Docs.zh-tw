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
ms.openlocfilehash: 7fa729d600f25b73028bae0dd6d9248b5839dd4c
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133866"
---
# <a name="themedictionary-markup-extension"></a><span data-ttu-id="49d66-102">ThemeDictionary 標記延伸</span><span class="sxs-lookup"><span data-stu-id="49d66-102">ThemeDictionary Markup Extension</span></span>
<span data-ttu-id="49d66-103">為自訂控制項的作者或應用程式提供一種方式，整合協力廠商的控制項來載入佈景主題特定的資源字典，以便在設定控制項樣式時使用。</span><span class="sxs-lookup"><span data-stu-id="49d66-103">Provides a way for custom control authors or applications that integrate third-party controls to load theme-specific resource dictionaries to use in styling the control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="49d66-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="49d66-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="49d66-105">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="49d66-105">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="49d66-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="49d66-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`assemblyUri`|<span data-ttu-id="49d66-107">組件的 [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] ，包含佈景主題資訊。</span><span class="sxs-lookup"><span data-stu-id="49d66-107">The [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] of the assembly that contains theme information.</span></span> <span data-ttu-id="49d66-108">一般而言，這個 Pack URI 會參考較大封裝中的組件。</span><span class="sxs-lookup"><span data-stu-id="49d66-108">Typically, this is a pack URI that references an assembly in the larger package.</span></span> <span data-ttu-id="49d66-109">組件資源和 Pack URI 可簡化部署問題。</span><span class="sxs-lookup"><span data-stu-id="49d66-109">Assembly resources and pack URIs simplify deployment issues.</span></span> <span data-ttu-id="49d66-110">如需詳細資訊，請參閱 [WPF 中的 Pack URI](../app-development/pack-uris-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="49d66-110">For more information see [Pack URIs in WPF](../app-development/pack-uris-in-wpf.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49d66-111">備註</span><span class="sxs-lookup"><span data-stu-id="49d66-111">Remarks</span></span>  
 <span data-ttu-id="49d66-112">此延伸模組的目的是只填滿一個特定的<xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>屬性值: 的值。</span><span class="sxs-lookup"><span data-stu-id="49d66-112">This extension is intended to fill only one specific property value: a value for <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="49d66-113">藉由使用此延伸模組, 您可以指定僅限資源的單一元件, 其中包含一些樣式, 只有在 Windows Aero 主題套用至使用者的系統時才會使用, 其他樣式則僅適用于 Luna 主題作用中的情況等。</span><span class="sxs-lookup"><span data-stu-id="49d66-113">By using this extension, you can specify a single resources-only assembly that contains some styles to use only when the Windows Aero theme is applied to the user's system, other styles only when the Luna theme is active, and so on.</span></span> <span data-ttu-id="49d66-114">藉由使用此延伸模組，控制項特定的資源字典內容可在必要時自動失效並重新載入以專用於另一個佈景主題。</span><span class="sxs-lookup"><span data-stu-id="49d66-114">By using this extension, the contents of a control-specific resource dictionary can be automatically invalidated and reloaded to be specific for another theme when required.</span></span>  
  
 <span data-ttu-id="49d66-115">`assemblyUri`字串(<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>屬性值) 會形成命名慣例的基礎, 以識別特定主題所適用的字典。</span><span class="sxs-lookup"><span data-stu-id="49d66-115">The `assemblyUri` string (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property value) forms the basis of a naming convention that identifies which dictionary applies for a particular theme.</span></span> <span data-ttu-id="49d66-116">的<xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> 邏輯會[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]產生指向特定主題字典變異的, 其包含在先行編譯的資源元件中, 以完成慣例。`ThemeDictionary`</span><span class="sxs-lookup"><span data-stu-id="49d66-116">The <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> logic for `ThemeDictionary` completes the convention by generating a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] that points to a particular theme dictionary variant, as contained within a precompiled resource assembly.</span></span> <span data-ttu-id="49d66-117">此處將不會完整說明此慣例，或是概念上與一般控制項樣式設定和頁面/應用程式層級樣式設定進行的佈景主題互動。</span><span class="sxs-lookup"><span data-stu-id="49d66-117">Describing this convention, or theme interactions with general control styling and page/application level styling as a concept, is not covered fully here.</span></span> <span data-ttu-id="49d66-118">使用`ThemeDictionary`的基本案例是<xref:System.Windows.ResourceDictionary.Source%2A>指定在應用層級宣告之`ResourceDictionary`的屬性。</span><span class="sxs-lookup"><span data-stu-id="49d66-118">The basic scenario for using `ThemeDictionary` is to specify the <xref:System.Windows.ResourceDictionary.Source%2A> property of a `ResourceDictionary` declared at the application level.</span></span> <span data-ttu-id="49d66-119">當您透過 `ThemeDictionary` 延伸模組提供組件的 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ，而不是做為直接 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 時，延伸模組邏輯將提供每當系統佈景主題變更時適用的失效邏輯。</span><span class="sxs-lookup"><span data-stu-id="49d66-119">When you provide a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the assembly through a `ThemeDictionary` extension rather than as a direct [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], the extension logic will provide invalidation logic that applies whenever the system theme changes.</span></span>  
  
 <span data-ttu-id="49d66-120">屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。</span><span class="sxs-lookup"><span data-stu-id="49d66-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="49d66-121">`ThemeDictionary` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> 延伸類別的 <xref:System.Windows.ThemeDictionaryExtension> 值。</span><span class="sxs-lookup"><span data-stu-id="49d66-121">The string token provided after the `ThemeDictionary` identifier string is assigned as the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> value of the underlying <xref:System.Windows.ThemeDictionaryExtension> extension class.</span></span>  
  
 <span data-ttu-id="49d66-122">`ThemeDictionary` 可能也會用於物件元素語法中。</span><span class="sxs-lookup"><span data-stu-id="49d66-122">`ThemeDictionary` may also be used in object element syntax.</span></span> <span data-ttu-id="49d66-123">在此情況下, 必須指定<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>屬性的值。</span><span class="sxs-lookup"><span data-stu-id="49d66-123">In this case, specifying the value of the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property is required.</span></span>  
  
 <span data-ttu-id="49d66-124">`ThemeDictionary` 也可以用於會指定 <xref:System.Windows.Markup.StaticExtension.Member%2A> 屬性 (Property) 做為 property=value 配對組的詳細屬性 (Attribute) 使用方式中。</span><span class="sxs-lookup"><span data-stu-id="49d66-124">`ThemeDictionary` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.Markup.StaticExtension.Member%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 <span data-ttu-id="49d66-125">詳細使用方式通常是適用於具有一個以上可設定屬性或有些屬性為選擇性屬性的標記延伸。</span><span class="sxs-lookup"><span data-stu-id="49d66-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="49d66-126">因為 `ThemeDictionary` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。</span><span class="sxs-lookup"><span data-stu-id="49d66-126">Because `ThemeDictionary` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="49d66-127">在處理器執行中, 此標記<xref:System.Windows.ThemeDictionaryExtension>延伸模組的處理是由類別所定義。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49d66-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.ThemeDictionaryExtension> class.</span></span>  
  
 <span data-ttu-id="49d66-128">`ThemeDictionary` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="49d66-128">`ThemeDictionary` is a markup extension.</span></span> <span data-ttu-id="49d66-129">如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。</span><span class="sxs-lookup"><span data-stu-id="49d66-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="49d66-130">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。</span><span class="sxs-lookup"><span data-stu-id="49d66-130">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="49d66-131">如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="49d66-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49d66-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49d66-132">See also</span></span>

- [<span data-ttu-id="49d66-133">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="49d66-133">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="49d66-134">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="49d66-134">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="49d66-135">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="49d66-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="49d66-136">WPF 應用程式資源、內容和資料檔案</span><span class="sxs-lookup"><span data-stu-id="49d66-136">WPF Application Resource, Content, and Data Files</span></span>](../app-development/wpf-application-resource-content-and-data-files.md)
