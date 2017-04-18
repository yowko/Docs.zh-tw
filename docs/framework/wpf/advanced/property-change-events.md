---
title: "屬性變更事件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "變更事件 [WPF], 屬性"
  - "建立屬性觸發程序 [WPF]"
  - "相依性屬性 [WPF], 變更事件"
  - "事件 [WPF], 屬性值的變更"
  - "識別變更的屬性事件 [WPF]"
  - "屬性變更事件 [WPF]"
  - "屬性變更事件 [WPF], 類型"
  - "屬性觸發程序 [WPF]"
  - "屬性觸發程序 [WPF], 定義"
  - "屬性值變更 [WPF]"
ms.assetid: 0a7989df-9674-4cc1-bc50-5d8ef5d9c055
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 屬性變更事件
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 定義有數個事件，會引發來回應屬性值的變更。  屬性通常是[相依性屬性](GTMT)。  事件本身有時候是[路由事件](GTMT)，有時則是標準 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 事件。  事件的定義會視情況而定，因為部分屬性變更比較適合透過項目樹狀結構路由，而其他屬性變更則通常只與屬性變更的物件相關。  
  
## 識別屬性變更事件  
 報告屬性變更的事件不一定都會明確識別為屬性變更事件，不論是透過簽章模式或命名模式。  一般來說，根據[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] 文件中的事件描述，是要看事件是否直接繫結至屬性值變更，並提供屬性與事件之間的交互參考。  
  
### RoutedPropertyChanged 事件  
 某些事件會使用明確用於屬性變更事件的事件資料型別和委派。  此事件資料型別是 <xref:System.Windows.RoutedPropertyChangedEventArgs%601>，而委派是 <xref:System.Windows.RoutedPropertyChangedEventHandler%601>。  此事件資料和委派都有一個泛型型別參數，可在您定義處理常式時用來指定變更屬性的實際型別。  事件資料包含兩個屬性，分別為 <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> 和 <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>，這兩個屬性會當做事件資料中的型別引數傳遞。  
  
 名稱的 "Routed" 部分會指出屬性變更事件是否註冊為路由事件。  路由屬性變更事件的優點是，如果子項目 \(控制項的複合部分\) 上的屬性變更值，控制項的最上層可收到屬性變更事件。  例如，您可能會建立控制項，其中包含有像是 <xref:System.Windows.Controls.Slider> 的 <xref:System.Windows.Controls.Primitives.RangeBase> 控制項。  如果滑桿部分上的 <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> 屬性變更，您可能會想在父控制項上處理該變更，而非在部分上。  
  
 由於有舊值和新值，您可能會想要使用這個事件處理常式做為屬性值的驗證程式。  不過，大多數屬性變更事件的設計用意並不在此。  一般來說，之所以提供值，是要讓您在程式碼的其他邏輯區域對這些值執行動作，但不建議在事件處理常式內實際變更值，而且根據處理常式的實作方式而定，這可能會導致意外遞迴。  
  
 如果您的屬性是自訂相依性屬性，或如果您使用已定義執行個體化 \(Instantiation\) 程式碼的衍生類別，則有更好的機制可追蹤屬性變更，此機制內建在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統，即屬性系統回呼 <xref:System.Windows.CoerceValueCallback> 和 <xref:System.Windows.PropertyChangedCallback>。  如需如何使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統進行驗證和強制型轉 \(Coercion\) 的詳細資訊，請參閱[相依性屬性回呼和驗證](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)和[自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)。  
  
### DependencyPropertyChanged 事件  
 與屬性變更事件有關的另一組型別是 <xref:System.Windows.DependencyPropertyChangedEventArgs> 和 <xref:System.Windows.DependencyPropertyChangedEventHandler>。  這些屬性變更的事件不會進行路由；它們是標準 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件。  <xref:System.Windows.DependencyPropertyChangedEventArgs> 是特殊的事件資料報告型別，因為它不是衍生自 <xref:System.EventArgs>；<xref:System.Windows.DependencyPropertyChangedEventArgs> 是結構而非類別。  
  
 使用 <xref:System.Windows.DependencyPropertyChangedEventArgs> 和 <xref:System.Windows.DependencyPropertyChangedEventHandler> 的事件比 `RoutedPropertyChanged` 事件更常見些。  使用這些型別的事件如 <xref:System.Windows.UIElement.IsMouseCapturedChanged>。  
  
 如同 <xref:System.Windows.RoutedPropertyChangedEventArgs%601>，<xref:System.Windows.DependencyPropertyChangedEventArgs> 也會報告屬性的舊值和新值。  此外，能對值所執行的動作也有同樣的限制，一般不建議嘗試在傳送端再次變更值來回應事件。  
  
## 屬性觸發程序  
 有一個與屬性變更事件密切相關的概念就是屬性觸發程序。  屬性觸發程序會在樣式或樣板內建立，可讓您根據指派屬性觸發程序之屬性的值，建立條件式行為。  
  
 屬性觸發程序的屬性必須是相依性屬性。  它可以是 \(也經常是\) 唯讀相依性屬性。  當控制項公開的相依性屬性至少有部分設計為屬性觸發程序時，可以從屬性名稱是否以 "Is" 開頭來辨識。  以此命名的屬性通常是唯讀布林值相依性屬性，主要用途是報告可能對即時 UI 有影響的控制項狀態，因此適合當做屬性觸發程序使用。  
  
 部分屬性也有專用的屬性變更事件。  例如，屬性 <xref:System.Windows.UIElement.IsMouseCaptured%2A> 有屬性變更事件 <xref:System.Windows.UIElement.IsMouseCapturedChanged>。  屬性本身是唯讀的，它的值會由輸入系統調整，而且輸入系統會在每次即時變更時引發 <xref:System.Windows.UIElement.IsMouseCapturedChanged>。  
  
 相較於真正的屬性變更事件，使用屬性觸發程序對屬性變更採取動作有一些限制。  
  
 屬性觸發程序是透過完全相符邏輯運作的。  您會指定屬性和值，指出觸發程序將執行動作的特定值。  例如：：`<Setter Property="IsMouseCaptured" Value="true"> ... </Setter>`。  由於有此限制，屬性觸發程序多用於布林值屬性，或是接受專用列舉值的屬性，因為可能的值範圍容易管理，可為每種情況定義觸發程序。  或者，屬性觸發程序只能用於特殊值，例如當項目計數到達零，而且沒有觸發程序負責屬性值再從零變成其他數字的情況 \(這裡不使用適用所有情況的觸發程序，而可能需要程式碼事件處理常式，或是當值為非零值時，再次從觸發程序狀態切換回來的預設行為\)。  
  
 屬性觸發程序類似於程式設計中的 "if" 陳述式。  如果觸發程序條件為 true，就會「執行」屬性觸發程序的「主體」。  屬性觸發程序的「主體」不是程式碼，而是標記。  該標記只能使用一個或多個 <xref:System.Windows.Setter> 項目設定套用樣式或樣板之物件的其他屬性。  
  
 要位移有各種可能值之屬性觸發程序的 "if" 條件，一般建議使用 <xref:System.Windows.Setter>，將該相同的屬性值設為預設值。  這樣一來，當觸發程序條件為 true 時，<xref:System.Windows.Trigger> 包含的會優先適用，而只要觸發程序條件為 false 時，不在 <xref:System.Windows.Trigger> 內的 <xref:System.Windows.Setter> 則會優先適用。  
  
 一般適合使用屬性觸發程序的情況是，一個或多個外觀屬性會根據同一項目上的其他屬性狀態而變更的情況。  
  
 若要進一步了解屬性觸發程序，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
## 請參閱  
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)