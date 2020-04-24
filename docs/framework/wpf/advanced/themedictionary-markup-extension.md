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
# <a name="themedictionary-markup-extension"></a>ThemeDictionary 標記延伸
為自訂控制項的作者或應用程式提供一種方式，整合協力廠商的控制項來載入佈景主題特定的資源字典，以便在設定控制項樣式時使用。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>XAML 物件項目用法  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`assemblyUri`|包含主題資訊的程式集的統一資源標識符 (URI)。 一般而言，這個 Pack URI 會參考較大封裝中的組件。 組件資源和 Pack URI 可簡化部署問題。 如需詳細資訊，請參閱 [WPF 中的 Pack URI](../app-development/pack-uris-in-wpf.md)。|  
  
## <a name="remarks"></a>備註  
 此延伸檔只有填充一個特定屬性值: 的<xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>值 。  
  
 使用此擴展,可以指定單個僅資源程式集,該程式集包含僅在將 Windows Aero 主題應用於使用者系統時要使用的某些樣式,其他樣式僅在 Luna 主題處於活動狀態時使用,等等。 藉由使用此延伸模組，控制項特定的資源字典內容可在必要時自動失效並重新載入以專用於另一個佈景主題。  
  
 字串`assemblyUri`(<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>屬性值) 構成命名約定的基礎,該命名約定標識適用於特定主題的字典。 的邏輯<xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>`ThemeDictionary`通過生成一個統一的資源標識符 (URI) 來完成約定,該標識符指向特定主題字典變體,包含在預編譯的資源程式集中。 此處將不會完整說明此慣例，或是概念上與一般控制項樣式設定和頁面/應用程式層級樣式設定進行的佈景主題互動。 使用`ThemeDictionary`的基本方案是在應用程式級別指定<xref:System.Windows.ResourceDictionary.Source%2A>`ResourceDictionary`聲明的屬性。 當您透過`ThemeDictionary`擴展而不是直接 URI 為程式集提供 URI 時,擴展邏輯將提供適用於系統主題更改的失效邏輯。  
  
 屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 `ThemeDictionary` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> 延伸類別的 <xref:System.Windows.ThemeDictionaryExtension> 值。  
  
 `ThemeDictionary` 可能也會用於物件元素語法中。 在這種情況下,需要指定<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>屬性的值。  
  
 `ThemeDictionary` 也可以用於會指定 <xref:System.Windows.Markup.StaticExtension.Member%2A> 屬性 (Property) 做為 property=value 配對組的詳細屬性 (Attribute) 使用方式中。  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 詳細使用方式通常是適用於具有一個以上可設定屬性或有些屬性為選擇性屬性的標記延伸。 因為 `ThemeDictionary` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。  
  
 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器實現中,此標記擴展的處理由<xref:System.Windows.ThemeDictionaryExtension>類定義。  
  
 `ThemeDictionary` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>另請參閱

- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
- [WPF 應用程式資源、內容和資料檔案](../app-development/wpf-application-resource-content-and-data-files.md)
