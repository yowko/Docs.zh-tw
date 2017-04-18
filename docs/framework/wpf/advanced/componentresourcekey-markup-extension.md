---
title: "ComponentResourceKey 標記延伸 | Microsoft Docs"
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
  - "ComponentResourceKey"
  - "ComponentResourceKeyExtension"
helpviewer_keywords: 
  - "ComponentResourceKey 標記延伸"
  - "XAML, ComponentResourceKey 標記延伸"
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# ComponentResourceKey 標記延伸
定義和參考自外部組件載入的資源索引鍵。  這樣可以讓資源查閱在組件中指定目標型別，而非在組件或類別中指定明確資源字典。  
  
## XAML 屬性使用 \(設定索引鍵、精簡\)  
  
```  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## XAML 屬性使用 \(設定索引鍵、詳細\)  
  
```  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## XAML 屬性使用 \(要求資源、精簡\)  
  
```  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## XAML 屬性使用 \(要求資源、詳細\)  
  
```  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|`targetTypeName`|定義於資源組件中的公用 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 型別的名稱。|  
|`targetID`|資源的索引鍵。  查閱資源時，`targetID` 類似於資源的 [x:Key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)。|  
  
## 備註  
 如上述使用方式所示，在兩個位置可找到 {`ComponentResourceKey`} 標記延伸使用方式：  
  
-   如控制項作者所提供的，佈景主題資源字典內索引鍵的定義。  
  
-   當您在重製控制項的樣板，但想要使用控制項的佈景主題所提供之資源的屬性值時，從組件存取佈景主題資源。  
  
 對於參考來自佈景主題的元件資源，一般都建議您使用 `{DynamicResource}`，而非 `{StaticResource}`。  這點會在使用方式中顯示。  建議使用 `{DynamicResource}`，因為使用者可以變更佈景主題本身。  如果您要用最接近控制項作者意圖的元件資源來支援佈景主題，也應該將元件資源參考啟用為動態。  
  
 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> 會識別存在於實際定義資源的目標組件中的型別。  `ComponentResourceKey` 的定義和使用，可以不需要知道實際定義 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> 的地方，但最後必須透過參考組件解析型別。  
  
 <xref:System.Windows.ComponentResourceKey> 的常見用法是定義接著要公開為類別成員的索引鍵。  關於這個使用方式，您使用的是 <xref:System.Windows.ComponentResourceKey> 類別建構函式，而非標記延伸。  如需詳細資訊，請參閱 <xref:System.Windows.ComponentResourceKey>，或是[控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)主題的＜定義和參考佈景主題資源的索引鍵＞章節。  
  
 在建立索引鍵和參考索引鍵資源時，通常都會對 `ComponentResourceKey` 標記延伸使用屬性語法。  
  
 顯示的簡潔語法會依靠 <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=fullName> 建構函式簽章和標記延伸的位置參數使用方式。  指定 `targetTypeName` 和 `targetID` 的順序非常重要。  詳細語法仰賴 <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=fullName> 預設建構函式，然後以類似於物件項目上真正的屬性 \(Attribute\) 語法的方式設定 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> 和 <xref:System.Windows.ComponentResourceKey.ResourceId%2A>。  在詳細語法中，屬性的設定順序並不重要。  如需這兩種替代用法 \(精簡和詳細\) 的關係和機制，請參閱主題[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md) 中的描述。  
  
 技術上，`targetID` 的值可為任何物件，它並不需要是字串。  不過，在 WPF 中最常見的用法是將 `targetID` 值與字串的形式對齊，其中這類字串都在 [XamlName 文法](../../../../docs/framework/xaml-services/xamlname-grammar.md) 中有效。  
  
 `ComponentResourceKey` 可用於物件項目語法。  在這個情況下，必須要同時指定 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> 和 <xref:System.Windows.ComponentResourceKey.ResourceId%2A> 屬性的值，才能適當初始化延伸。  
  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 讀取器實作中，這個標記延伸的處理是由 <xref:System.Windows.ComponentResourceKey> 類別定義的。  
  
 `ComponentResourceKey` 是一種標記延伸。  如果必須將屬性 \(Attribute\) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 \(而不是只對特定型別或屬性 \(Property\) 設定型別轉換子 \(Type Converter\)\)，則通常會實作標記延伸。  所有 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記延伸都會在其屬性 \(Attribute\) 語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性 \(Attribute\)。  如需詳細資訊，請參閱 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
## 請參閱  
 <xref:System.Windows.ComponentResourceKey>   
 <xref:System.Windows.Controls.ControlTemplate>   
 [控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)   
 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)