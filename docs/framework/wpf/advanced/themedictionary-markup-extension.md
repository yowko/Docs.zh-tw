---
title: "ThemeDictionary 標記延伸"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ThemeDictionaryExtension
- ThemeDictionary
helpviewer_keywords:
- ThemeDictionary markup extension [WPF]
- XAML [WPF], ThemeDictionary markup extension
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45f878ce89dcf76ae800ade10a0e67f019741f65
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
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
|`assemblyUri`|組件的 [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] ，包含佈景主題資訊。 一般而言，這個 Pack URI 會參考較大封裝中的組件。 組件資源和 Pack URI 可簡化部署問題。 如需詳細資訊，請參閱 [WPF 中的 Pack URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)。|  
  
## <a name="remarks"></a>備註  
 這項擴充功能要填滿只有一個特定的屬性值： 值<xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>。  
  
 藉由使用此延伸模組，您可以指定僅含資源的單一組件，其中包含只有在將 [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] 佈景主題套用至使用者的系統時才會使用的一些樣式、當 Luna 佈景主題為作用中時使用的其他樣式等資訊。 藉由使用此延伸模組，控制項特定的資源字典內容可在必要時自動失效並重新載入以專用於另一個佈景主題。  
  
 `assemblyUri`字串 (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>屬性值) 的命名慣例，識別哪些字典適用於特定的佈景主題的基礎。 <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>邏輯`ThemeDictionary`藉由產生完成慣例[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]，它會指向特定的佈景主題字典 variant，為包含在先行編譯的資源組件。 此處將不會完整說明此慣例，或是概念上與一般控制項樣式設定和頁面/應用程式層級樣式設定進行的佈景主題互動。 使用的基本案例`ThemeDictionary`是指定<xref:System.Windows.ResourceDictionary.Source%2A>屬性`ResourceDictionary`宣告應用程式層級。 當您透過 `ThemeDictionary` 延伸模組提供組件的 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ，而不是做為直接 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 時，延伸模組邏輯將提供每當系統佈景主題變更時適用的失效邏輯。  
  
 屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 `ThemeDictionary` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> 延伸類別的 <xref:System.Windows.ThemeDictionaryExtension> 值。  
  
 `ThemeDictionary` 可能也會用於物件元素語法中。 在此情況下，指定的值<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>是必要屬性。  
  
 `ThemeDictionary` 也可以用於會指定 <xref:System.Windows.Markup.StaticExtension.Member%2A> 屬性 (Property) 做為 property=value 配對組的詳細屬性 (Attribute) 使用方式中。  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 詳細使用方式通常是適用於具有一個以上可設定屬性或有些屬性為選擇性屬性的標記延伸。 因為 `ThemeDictionary` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。  
  
 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器實作所定義的這個標記延伸處理<xref:System.Windows.ThemeDictionaryExtension>類別。  
  
 `ThemeDictionary` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>另請參閱  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [WPF 應用程式資源、內容和資料檔案](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
