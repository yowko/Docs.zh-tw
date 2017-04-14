---
title: "StaticResource 標記延伸 | Microsoft Docs"
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
  - "StaticResource"
  - "StaticResourceExtension"
helpviewer_keywords: 
  - "StaticResource 標記延伸"
  - "XAML, StaticResource 標記延伸"
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# StaticResource 標記延伸
透過查閱已定義資源的參考，提供任何 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 屬性 \(Property\) 屬性 \(Attribute\) 的值。  這種資源的查閱行為與載入時間的查閱類似，它會尋找先前從目前 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面之標記以及其他應用程式來源載入的資源，並產生該資源值，做為執行階段物件中的屬性值。  
  
## XAML Attribute Usage  
  
```  
<object property="{StaticResource key}" .../>  
```  
  
## XAML 物件項目用法  
  
```  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|`key`|要求之資源的索引鍵。  這個索引鍵一開始是由 [x:Key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)指派 \(如果在標記中建立資源\)，或是在呼叫 <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=fullName> 時提供以做為 `key` 參數 \(如果在程式碼中建立資源\)。|  
  
## 備註  
  
> [!IMPORTANT]
>  如果資源已用語彙形式在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案內進一步定義，`StaticResource` 就不能嘗試建立該資源的向前參考 \(Forward Reference\)。  這種嘗試不受支援，而且即使這類參考並未失敗，在搜尋代表 <xref:System.Windows.ResourceDictionary> 的內部雜湊表時，嘗試進行向前參考也會對載入時間 \(Load Time\) 效能產生負面影響。  為了達到最佳結果，請調整資源字典的組合，以避免進行向前參考。  如果無法避免向前參考，請改用 [DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)。  
  
 指定的 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 應該對應於 [x:Key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)在頁面、應用程式、可用控制項佈景主題和外部資源的某個層級上定義的現有資源，或是對應於系統資源。  資源查閱將會按照該順序來執行。  如需靜態 \(Static\) 和動態 \(Dynamic\) 資源之資源查閱行為的詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
 資源索引鍵可以是 [XamlName 文法](../../../../docs/framework/xaml-services/xamlname-grammar.md)中定義的任何字串。  資源索引鍵也可以是其他物件型別，例如 <xref:System.Type>。  <xref:System.Type> 索引鍵是透過隱含樣式索引鍵，依佈景主題設定控制項樣式的基礎。  如需詳細資訊，請參閱[控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)。  
  
 另一種參考資源的宣告方式是 [DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)。  
  
 屬性 \(Attribute\) 語法是最常配合這個標記延伸使用的語法。  `StaticResource` 識別項字串後提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.StaticResourceExtension> 延伸類別的 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 值。  
  
 `StaticResource` 可用於物件項目語法。  在這種情況下，您必須指定 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 屬性的值。  
  
 `StaticResource` 也可用於將 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 屬性 \(Property\) 指定為 property\=value 配對的詳細屬性 \(Attribute\) 使用方式。  
  
```  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 繁複的使用方法所適用的擴充，通常是具有一個以上可設定屬性或有些屬性為選擇性。  因為 `StaticResource` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。  
  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器實作中，這個標記延伸的處理是由 <xref:System.Windows.StaticResourceExtension> 類別定義的。  
  
 `StaticResource` 是一種標記延伸。  如果必須將屬性 \(Attribute\) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 \(而不是只對特定型別或屬性 \(Property\) 設定型別轉換子 \(Type Converter\)\)，則通常會實作標記延伸。  所有 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記延伸都會在其屬性 \(Attribute\) 語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性 \(Attribute\)。  如需詳細資訊，請參閱 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
## 請參閱  
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [資源和程式碼](../../../../docs/framework/wpf/advanced/resources-and-code.md)