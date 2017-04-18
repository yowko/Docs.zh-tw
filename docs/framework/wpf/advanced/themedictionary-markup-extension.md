---
title: "ThemeDictionary 標記延伸 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ThemeDictionaryExtension"
  - "ThemeDictionary"
helpviewer_keywords: 
  - "ThemeDictionary 標記延伸"
  - "XAML, ThemeDictionary 標記延伸"
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# ThemeDictionary 標記延伸
提供一種方法，讓自訂控制項作者或整合協力廠商控制項的應用程式載入佈景主題專用的資源字典，以用於設定控制項的樣式。  
  
## XAML Attribute Usage  
  
```  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## XAML 物件項目用法  
  
```  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|`assemblyUri`|組件 \(Assembly\) 的[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]，其中包含佈景主題資訊。  這通常是參考較大封裝中之組件的 Pack URI。  組件資源和 Pack URI 簡化了部署問題。  如需詳細資訊，請參閱[WPF 中的 Pack URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)。|  
  
## 備註  
 這個延伸項目的目的只是要填入一個特定的屬性值：<xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=fullName> 的值。  
  
 使用這個延伸項目，您可以指定單一資源限定組件，而組件中則包含只有在將 [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] 佈景主題套用至使用者系統時才會使用的某些樣式、Luna 佈景主題正在作用時的其他樣式等等。  透過這個延伸項目，控制項專用資源字典的內容可以在必要時自動失效，並重新載入以變成另一種佈景主題的專用資源。  
  
 `assemblyUri` 字串 \(<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> 屬性值\) 構成命名規範的基礎，用以識別適用於特定佈景主題的字典。  `ThemeDictionary` 的 <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> 邏輯則讓此命名規範更為完備，方法是產生[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]，使其指向先行編譯之資源組件內的特定佈景主題字典變數。  本文並未涵蓋這種命名規範，或是佈景主題與一般控制項樣式設定和頁面\/應用程式層級樣式設定的完整概念說明。  使用 `ThemeDictionary` 的基本案例是指定在應用程式層級宣告之 `ResourceDictionary` 的 <xref:System.Windows.ResourceDictionary.Source%2A> 屬性。  當您透過 `ThemeDictionary` 延伸項目提供組件的 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]，而非直接的 direct [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 時，此延伸邏輯便會提供系統佈景主題變更時適用的失效邏輯。  
  
 屬性 \(Attribute\) 語法是最常配合這個標記延伸使用的語法。  `ThemeDictionary` 識別項字串後提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.ThemeDictionaryExtension> 延伸類別的 <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> 值。  
  
 `ThemeDictionary` 也可在物件項目語法中使用。  在這種情況下，您必須指定 <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> 屬性的值。  
  
 `ThemeDictionary` 也可用於將 <xref:System.Windows.Markup.StaticExtension.Member%2A> 屬性 \(Property\) 指定為 property\=value 配對的詳細屬性 \(Attribute\) 使用方式。  
  
```  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 繁複的使用方法所適用的擴充，通常是具有一個以上可設定屬性或有些屬性為選擇性。  因為 `ThemeDictionary` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。  
  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器實作中，這個標記延伸的處理是由 <xref:System.Windows.ThemeDictionaryExtension> 類別定義的。  
  
 `ThemeDictionary` 是一種標記延伸。  如果必須將屬性 \(Attribute\) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 \(而不是只對特定型別或屬性 \(Property\) 設定型別轉換子 \(Type Converter\)\)，則通常會實作標記延伸。  所有 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記延伸都會在其屬性 \(Attribute\) 語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性 \(Attribute\)。  如需詳細資訊，請參閱 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
## 請參閱  
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [WPF 應用程式資源、內容和資料檔案](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)