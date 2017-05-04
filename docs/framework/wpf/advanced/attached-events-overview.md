---
title: "附加事件概觀 | Microsoft Docs"
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
  - "附加事件 [WPF], 定義"
  - "附加事件 [WPF], 情節"
  - "附加事件與路由事件的比較 [WPF]"
  - "使用路由事件支援附加事件 [WPF]"
  - "將附加事件定義為路由事件 [WPF]"
  - "處理附加事件 [WPF]"
ms.assetid: 2c40eae3-80e4-4a45-ae09-df6c9ab4d91e
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 附加事件概觀
[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 會定義語言元件和稱為「*附加事件*」\(Attached Event\) 的事件類型。  附加事件的概念可以讓您將特定事件的處理常式加入到任意項目中，而非實際定義或繼承該事件的項目中。  在這種情況下，事件並非由可能引發事件的物件或是處理事件的目的執行個體所定義或擁有。  
  
   
  
<a name="prerequisites"></a>   
## 必要條件  
 本主題假設您已經讀過[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)和 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)。  
  
<a name="Syntax"></a>   
## 附加事件語法  
 附加事件具有 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 語法和程式撰寫模式，支援程式碼必須使用這種語法和模式才能支援附加事件的使用。  
  
 在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 語法中，附加事件並不是只由其事件名稱指定，而是由它的擁有者型別加上事件名稱 \(中間以點 \(.\) 分隔\) 來指定。  由於事件名稱中包含其擁有者型別的名稱，因此附加事件語法可以將任何附加事件附加到可以執行個體化的任何項目。  
  
 例如，下列 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 語法可以用來附加自訂 `NeedsCleaning` 附加事件的處理常式：  
  
 [!code-xml[WPFAquariumSln#AE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 請注意其中的 `aqua:` 前置字元；這個案例需要加入此前置字元，因為該附加事件是來自自訂對應 xmlns 的自訂事件。  
  
<a name="WPFImplements"></a>   
## WPF 實作附加事件的方式  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，附加事件是由 <xref:System.Windows.RoutedEvent> 欄位支援，而且在引發之後將會透過樹狀結構路由傳送。  附加事件的來源 \(也就是引發事件的物件\) 通常是系統或服務來源，因此執行引發事件之程式碼的物件並不是項目樹狀結構的一部分。  
  
<a name="Scenarios"></a>   
## 附加事件的案例  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，附加事件是存在具有服務層級抽取作業的特定功能區域中，例如由靜態 <xref:System.Windows.Input.Mouse> 類別或 <xref:System.Windows.Controls.Validation> 類別所啟用的事件。  與服務互動或是使用服務的類別可以透過附加事件語法來使用事件，或是選擇支援附加事件做為路由事件，使其成為類別整合服務功能所採用之方式的一部分。  
  
 雖然 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 定義了許多附加事件，但是您會直接使用或處理附加事件的情況非常有限。  附加事件通常用於架構用途，但接著則會轉送到非附加 \(由 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件「包裝函式」支援\) 路由事件。  
  
 例如，在任何指定的 <xref:System.Windows.UIElement> 上都可以更輕鬆處理基礎附加事件 <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=fullName>，方法是藉由在該 <xref:System.Windows.UIElement> 上使用 <xref:System.Windows.UIElement.MouseDown>，而不是在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 或程式碼中處理附加事件語法。  由於附加事件可讓您在未來擴充輸入事件，因此可以提供結構上的用途。  模擬裝置只需要引發 <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=fullName> 來模擬滑鼠輸入，而不需要從 <xref:System.Windows.Input.Mouse> 衍生。  不過，這個案例牽涉到事件的程式碼處理，而附加事件的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理則與此案例無關。  
  
<a name="Handling"></a>   
## 在 WPF 中處理附加事件  
 處理附加事件的程序，以及您所要撰寫的處理常式程式碼，基本上都與路由事件相同。  
  
 一般來說，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 附加事件與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 路由事件差異不大。  兩者的差異在於回溯事件來源的方式，以及類別將事件公開為成員的方式 \(這也會影響 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理常式語法\)。  
  
 不過，如前面所述，現有的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 附加事件並不特別適合在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中處理。  這種事件的用途通常是要讓複合項目能夠對複合 \(Compositing\) 中的父項目報告狀態，而在此情況下，事件通常在程式碼引發，也需依賴相關父類別中的類別處理。  例如，<xref:System.Windows.Controls.Primitives.Selector> 內的項目應該會引發附加的 <xref:System.Windows.Controls.Primitives.Selector.Selected> 事件，接著由 <xref:System.Windows.Controls.Primitives.Selector> 類別處理該事件，然後 <xref:System.Windows.Controls.Primitives.Selector> 類別可能會將它轉換成不同的路由事件 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>。  如需路由事件和類別處理的詳細資訊，請參閱[將路由事件標記為已處理以及類別處理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)。  
  
<a name="Custom"></a>   
## 將自己的附加事件定義為路由事件  
 如果您是從一般的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 基底類別衍生，可以透過在類別中加入特定模式方法，以及使用基底類別中既有的公用程式方法，實作您自己的附加事件。  
  
 此模式如下：  
  
-   具有兩個參數的 `Add*Handler` 方法。  第一個參數必須識別事件，而識別的事件必須符合方法名稱中具有 \* 的名稱。  第二個參數是要加入的處理常式。  這個方法必須是公用、靜態且沒有傳回值的方法。  
  
-   具有兩個參數的 `Remove*Handler` 方法。  第一個參數必須識別事件，而識別的事件必須符合方法名稱中具有 \* 的名稱。  第二個參數是要移除的處理常式。  這個方法必須是公用、靜態且沒有傳回值的方法。  
  
 在項目上宣告附加事件處理常式屬性時，`Add*Handler` 存取子方法可加速 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的處理程序。  `Add*Handler` 和 `Remove*Handler` 方法也可提供附加事件之事件處理常式存放區的程式碼存取權。  
  
 這種一般性模式還不夠精確，無法實際在架構中實作，因為任何特定 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 讀取器的實作可能都有不同的配置，用以識別支援語言和架構中的基礎事件。  這是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 將附加事件實作為路由事件的其中一個原因；[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 事件系統中已經定義了用於事件 \(<xref:System.Windows.RoutedEvent>\) 的識別項。  此外，在附加事件的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 語言層級的概念中，傳送事件是自然的實作擴充功能。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 附加事件的 `Add*Handler` 實作包括以路由事件和處理常式做為參數來呼叫 <xref:System.Windows.UIElement.AddHandler%2A>。  
  
 這種實作策略和路由事件系統通常會將附加事件的處理限制為 <xref:System.Windows.UIElement> 衍生類別 \(Derived Class\) 或 <xref:System.Windows.ContentElement> 衍生類別，因為只有這些類別具有 <xref:System.Windows.UIElement.AddHandler%2A> 實作。  
  
 例如，下列範例使用將附加事件宣告成路由事件的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 附加事件策略，定義擁有者類別 `Aquarium` 上的 `NeedsCleaning` 附加事件。  
  
 [!code-csharp[WPFAquariumSln#AECode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 請注意，用於建立附加事件識別項欄位 <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> 的方法實際上與用來註冊非附加路由事件的方法相同。  附加事件和路由事件全都會註冊到集中式的內部存放區中。  這種事件存放區實作可啟用[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)中所討論的「以事件做為介面」的概念性考量。  
  
<a name="Raising"></a>   
## 引發 WPF 附加事件  
 您通常不需要從程式碼引發 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 定義的附加事件。  這些事件是遵照一般的「服務」概念模型，而由諸如 <xref:System.Windows.Input.InputManager> 等的服務類別負責引發事件。  
  
 不過，如果您是依據以 <xref:System.Windows.RoutedEvent> 做為基礎的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 模型來定義自訂附加事件，則可使用 <xref:System.Windows.UIElement.RaiseEvent%2A>，從任何 <xref:System.Windows.UIElement> 或 <xref:System.Windows.ContentElement> 引發附加事件。  引發路由事件 \(附加或非附加\) 時，您必須將項目樹狀結構中的特定項目宣告為事件來源；該來源將會報告為 <xref:System.Windows.UIElement.RaiseEvent%2A> 呼叫端。  您的服務必須負責判斷要將樹狀結構中的哪個項目報告為來源。  
  
## 請參閱  
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)   
 [WPF 的 XAML 和自訂類別](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)