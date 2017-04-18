---
title: "x:Name Directive | Microsoft Docs"
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
  - "x:Name"
  - "xName"
  - "Name"
helpviewer_keywords: 
  - "x:Name attribute [XAML Services]"
  - "XAML [XAML Services], x:Name attribute"
  - "Name attribute in XAML [XAML Services]"
ms.assetid: b7e61222-e8cf-48d2-acd0-6df3b7685d48
caps.latest.revision: 27
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 27
---
# x:Name Directive
在 XAML 名稱範圍中唯一識別 XAML 定義的項目。  當架構提供 API 或實作在執行階段存取 XAML 建立之物件圖形的行為時，可以將 XAML 名稱範圍及其唯一性模型套用至具現化的物件。  
  
## XAML Attribute Usage  
  
```  
<object x:Name="XAMLNameValue".../>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|`XAMLNameValue`|符合 [XamlName 文法](../../../docs/framework/xaml-services/xamlname-grammar.md)之限制的字串。|  
  
## 備註  
 將 `x:Name` 套用於 Framework 的支援程式撰寫模型後，名稱即相當於裝載物件參考的變數或建構函式所傳回的執行個體。  
  
 `x:Name` 指示詞使用方式的值在 XAML 名稱範圍中必須是唯一的。  預設情況下，當主要 XAML 名稱範圍是由 .NET Framework XAML Services API 使用時，這個名稱範圍是在單一 XAML 產物的 XAML 根項目中定義，並且包含該 XAML 產物中所包含的項目。  Framework 可以定義產生單一 XAML 時可能出現的其他離散 XAML 名稱範圍，以解決特定情況。  例如，在 WPF 中，新的 XAML 名稱範圍都是由同樣在該 XAML 產物上定義的範本所定義和建立。  如需 XAML 名稱範圍 \(針對 WPF 撰寫，但與許多 XAML 名稱範圍概念相關\) 的詳細資訊，請參閱 [WPF XAML 名稱範圍](../../../ocs/framework/wpf/advanced/wpf-xaml-namescopes.md)。  
  
 `x:Name` 通常不應該在同時使用 `x:Key` 的情況下套用。  由特定現有架構所完成的 XAML 實作已引入 `x:Key` 與 `x:Name` 之間的替代概念，但這不是建議的作法。  處理名稱\/金鑰資訊，例如 <xref:System.Windows.Markup.INameScope> 或 <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute> 時，.NET Framework XAML Services 並不支援這種替換概念。  
  
 特定的實作架構可能會定義 `x:Name` 的權限規則和名稱唯一性強制。  然而，為可以用於 .NET Framework XAML Services，XAML 名稱範圍唯一性的框架定義應與此文件中 <xref:System.Windows.Markup.INameScope>資訊的定義一致，且應針對適用的資訊使用相同的規則。  例如，[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 實作會將各種標記項目分成不同的 <xref:System.Windows.NameScope> 範圍，例如資源字典、頁面層級 XAML 所建立的邏輯樹狀結構、範本，以及其他延後的內容，然後在每個這些 XAML 名稱範圍內強制 XAML 名稱唯一性。  
  
 對於使用 .NET Framework XAML 服務 XAML 物件寫入器的自訂型別，都可以建立或變更對應至型別上 `x:Name` 的屬性。  您可以參考要在型別定義程式碼中與 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 對應的屬性名稱，來定義這個行為。  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>是型別等級的屬性。  
  
 使用 .NET Framework XAML Services，XAML 名稱範圍支援的支援邏輯可以藉由實作 <xref:System.Windows.Markup.INameScope> 介面，以架構中性的方式定義。  
  
## WPF 使用注意事項  
 在使用 XAML、部分類別和程式碼後置 \(Code\-Behind\) 之 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 應用程式的標準組建組態下，指定的 `x:Name` 在標記編譯建置工作處理 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 時，會變成基礎程式碼中建立的欄位名稱，而欄位中會保存對物件的參考。建立的欄位預設是內部的欄位。  您可以指定 [x:FieldModifier 屬性](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md) \(Attribute\) 來變更欄位存取。  在 WPF 和 Silverlight 中，序列是標記編譯定義並病名部分類別中的欄位，但初始值是空的。  然後，從類別建構函式中呼叫產生的 `InitializeComponent` 方法。  `InitializeComponent`包括`FindName`呼叫，使用每個`x:Name`值, 這些值以輸入字串的形式存在於部分類別中的 XAML 定義部分。  傳回值會接著指派給類似名稱的欄位參考，以 XAML 剖析所建立的物件填入欄位值。  執行 `InitializeComponent` 可讓您在需要 XAML 定義的物件參考時直接使用 `x:Name` \/ 欄位名稱參考執行階段物件圖形，而不必明確呼叫 `FindName`。  
  
 對於使用 [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)] 目標，並以 `Page` 建置動作包含 XAML 檔案的 WPF 應用程式，會在編譯期間建立個別參考屬性，將 `WithEvents` 關鍵字加入至具有 `x:Name` 的所有項目，以支援事件處理常式委派的 `Handles` 語法。  這個屬性一定是公用的。  如需詳細資訊，請參閱 [Visual Basic 和 WPF 事件處理](../../../ocs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md)。  
  
 `x:Name` 是由 WPF XAML 處理器在載入期間用來將名稱登錄到 XAML 名稱範圍中，即使建置動作尚未對頁面進行標記編譯情況也是如此 \(例如，資源字典的鬆散 XAML\)。  這種行為的原因之一是因為<xref:System.Windows.Data.Binding.ElementName%2A>繫結可能需要`x:Name`。  如需詳細資訊，請參閱 [資料繫結概觀](../../../ocs/framework/wpf/data/data-binding-overview.md)。  
  
 前面提過，`x:Name` \(或 `Name`\) 不應該在也使用 `x:Key` 的情況下套用。  [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> 會一種特殊的行為，就是將其本身定義為 XAML 名稱範圍，但會對 <xref:System.Windows.Markup.INameScope> API 傳回「未實作」或 Null 值以做為強制此行為的方式。  如果 WPF XAML 剖析器遇到 `Name`或 XAML 定義 <xref:System.Windows.ResourceDictionary> 中的`x:Name`，不會將名稱新增至任何 XAML 命名空間。  嘗試從任何 XAML 命名空間找到該名稱，且`FindName`方法將不會傳回有效的結果。  
  
### x:Name 和名稱  
 許多 WPF 應用程式情節可以避免使用任何 `x:Name` 屬性，因為在預設 XAML 命名空間中針對幾個重要類別 \(例如，<xref:System.Windows.FrameworkElement> 和 <xref:System.Windows.FrameworkContentElement>\) 指定的 `Name` 相依性屬性可滿足與此相同的目的。  仍有一些常見的 XAML 和 WPF 情節，還是很重視在架構層級上對沒有 `Name` 屬性之項目的程式碼存取。  例如，某些動畫和腳本支援類別不支援 `Name`屬性，但在程式碼中往往需要參考它們才能控制動畫。  如果您想於稍後從程式碼參考在 XAML 中建立的時刻表和轉換，則應該將 `x:Name` 指定為這些時刻表和轉換上的屬性。  
  
 如果 <xref:System.Windows.FrameworkElement.Name%2A> 可做為類別上的屬性 \(Property\) 使用，則可以交替使用 <xref:System.Windows.FrameworkElement.Name%2A> 和 `x:Name` 做為屬性 \(Attribute\)，但是如果在相同項目上同時指定兩者，則會產生剖析例外狀況。  如果 XAML 以標記編譯，進行標記編譯時就會發生此例外狀況，不然也會於載入時發生。  
  
 <xref:System.Windows.FrameworkElement.Name%2A> 可以使用 <xref:System.Windows.DependencyObject.SetValue%2A> 以程式碼設定為使用 XAML 屬性語法。不過，請注意在程式碼中設定 <xref:System.Windows.FrameworkElement.Name%2A> 屬性時，於已經載入 XAML 的多數情況下，都不會在 XAML 名稱範圍內建立表示欄位參考。  不要嘗試在程式碼中設定 <xref:System.Windows.FrameworkElement.Name%2A>，請根據適當的名稱範圍，在程式碼中使用 <xref:System.Windows.NameScope> 方法。  
  
 <xref:System.Windows.FrameworkElement.Name%2A> 也可用內部文字設定為使用屬性項目語法，但這並不常見。  相較之下，`x:Name` 無法以 XAML 屬性 \(Property\) 項目語法設定，或是在使用 <xref:System.Windows.DependencyObject.SetValue%2A> 的程式碼中設定。因為它是指示詞，所以只能使用物件上的屬性 \(Attribute\) 語法來設定。  
  
## Silverlight 使用方式備註  
 Silverlight 的 `x:Name` 會在其他篇幅中做說明。  如需詳細資訊，請參閱[XAML 命名空間 \(x:\) 語言功能 \(Silverlight\)](http://go.microsoft.com/fwlink/?LinkId=199081)。  
  
## 請參閱  
 <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=fullName>   
 <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=fullName>   
 [WPF 中的樹狀結構](../../../ocs/framework/wpf/advanced/trees-in-wpf.md)