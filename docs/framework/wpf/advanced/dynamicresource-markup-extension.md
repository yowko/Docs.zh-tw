---
title: "DynamicResource 標記延伸 | Microsoft Docs"
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
  - "DynamicResource"
  - "DynamicResourceExtension"
helpviewer_keywords: 
  - "DynamicResource 標記延伸"
  - "XAML, DynamicResource 標記延伸"
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# DynamicResource 標記延伸
提供任何 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 屬性 \(Property\) 屬性 \(Attribute\) 的值，方法是將該值延後，使其變成定義之資源的參考。  該資源的查閱行為與執行階段查閱類似。  
  
## XAML Attribute Usage  
  
```  
<object property="{DynamicResource key}" .../>  
```  
  
## XAML 屬性項目用法  
  
```  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|`key`|要求之資源的索引鍵。  這個索引鍵一開始是由 [x:Key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)指派 \(如果在標記中建立資源\)，或是在呼叫 <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=fullName> 時提供以做為 `key` 參數 \(如果在程式碼中建立資源\)。|  
  
## 備註  
 `DynamicResource` 會在初始編譯期間建立暫存運算式，因此在實際需要所要求的資源值以建構物件之前，並不會進行資源的查閱。  這個時機可能是在載入 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 之後。  尋找資源值的方式是從目前的頁面範圍開始，對所有使用中的資源字典進行索引鍵搜尋，並以找到的資源值取代來自編譯的運算式替代符號。  
  
> [!IMPORTANT]
>  就相依性屬性優先順序而言，`DynamicResource` 運算式相當於套用動態資源參考的位置。  如果您將本機值設定給原本使用 `DynamicResource` 運算式做為本機值的屬性，則會將這個 `DynamicResource` 完全移除。  如需詳細資訊，請參閱[相依性屬性值優先順序](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)。  
  
 相對於 [StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)，某些資源存取案例特別適用於 `DynamicResource`。  如需 `DynamicResource` 和 `StaticResource` 相對優勢與效能含意的相關討論，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
 指定的 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 應該對應於 [x:Key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)在頁面、應用程式、可用控制項佈景主題和外部資源的某個層級上定義的現有資源，或是對應該系統資源，而且資源查閱將按照該順序來執行。  如需靜態和動態資源之資詢查閱的詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
 資源索引鍵可以是 [XamlName 文法](../../../../docs/framework/xaml-services/xamlname-grammar.md)中定義的任何字串。  資源索引鍵也可以是其他物件型別，例如 <xref:System.Type>。  <xref:System.Type> 索引鍵是依佈景主題設定控制項樣式的基礎。  如需詳細資訊，請參閱[控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)。  
  
 用來查閱資源值的 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] \(例如 <xref:System.Windows.FrameworkElement.FindResource%2A>\)，其遵偱的資源查閱邏輯與 `DynamicResource` 使用的邏輯相同。  
  
 另一種參考資源的宣告方式是 [StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)。  
  
 屬性 \(Attribute\) 語法是最常配合這個標記延伸使用的語法。  `DynamicResource` 識別項字串之後所提供的字串語彙基元將會指派為基礎 <xref:System.Windows.DynamicResourceExtension> 延伸類別的 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 值。  
  
 `DynamicResource` 可用於物件項目語法。  在這種情況下，您必須指定 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 屬性的值。  
  
 `DynamicResource` 也可用於將 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 屬性 \(Property\) 指定為 property\=value 配對的詳細屬性 \(Attribute\) 使用方式。  
  
```  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 繁複的使用方法所適用的擴充，通常是具有一個以上可設定屬性或有些屬性為選擇性。  因為 `DynamicResource` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。  
  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器實作中，這個標記延伸的處理是由 <xref:System.Windows.DynamicResourceExtension> 類別定義的。  
  
 `DynamicResource` 是一種標記延伸。  如果必須將屬性 \(Attribute\) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 \(而不是只對特定型別或屬性 \(Property\) 設定型別轉換子 \(Type Converter\)\)，則通常會實作標記延伸。  所有 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記延伸都會在其屬性 \(Attribute\) 語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性 \(Attribute\)。  如需詳細資訊，請參閱 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
## 請參閱  
 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [資源和程式碼](../../../../docs/framework/wpf/advanced/resources-and-code.md)   
 [x:Key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)   
 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)   
 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)