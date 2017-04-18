---
title: "Visual Basic 和 WPF 事件處理 | Microsoft Docs"
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
  - "事件處理常式, Visual Basic"
  - "Visual Basic, 事件處理常式"
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Visual Basic 和 WPF 事件處理
您可特別針對 [!INCLUDE[TLA#tla_visualbnet](../../../../includes/tlasharptla-visualbnet-md.md)] 語言，使用語言特定 `Handles` 關鍵字建立事件處理常式與執行個體的關聯，而不必附加事件處理常式和屬性，或是使用 <xref:System.Windows.UIElement.AddHandler%2A> 方法。  不過，將處理常式附加至執行個體的 `Handles` 技巧確實有些限制，因為 `Handles` 語法不能支援 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 事件系統的某些特定[路由事件](GTMT)功能。  
  
## 在 WPF 應用程式中使用 "Handles"  
 使用 `Handles` 連接至執行個體和事件的事件處理常式全都必須在執行個體的部分類別宣告 \(Class Declaration\) 內定義，而這項需求條件也適用於透過項目屬性值指派的事件處理常式。  您只能為頁面上具有 <xref:System.Windows.FrameworkContentElement.Name%2A> 屬性值 \(或已宣告 [x:Name 指示詞](../../../../docs/framework/xaml-services/x-name-directive.md)\) 的項目指定 `Handles`。  這是因為 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的 <xref:System.Windows.FrameworkContentElement.Name%2A> 會建立支援 `Handles` 語法所需 *Instance.Event* 參考格式的必要執行個體參考。  可用於沒有 <xref:System.Windows.FrameworkContentElement.Name%2A> 參考的 `Handles` 唯一一個項目是定義部分類別的根項目執行個體。  
  
 您可以使用逗號分隔 `Handles` 後面的 *Instance.Event* 參考，將相同的處理常式指派給多個項目。  
  
 您可以使用 `Handles` 將一個以上的處理常式指派給同一個 *Instance.Event* 參考。  請勿針對在 `Handles` 參考中指定事件常式的順序指定任何重要性；您應該假設處理相同事件的處理常式可以按照任何順序來叫用 \(Invoke\)。  
  
 若要移除在宣告中以 `Handles` 加入的處理常式，您可以呼叫 <xref:System.Windows.UIElement.RemoveHandler%2A>。  
  
 只要將處理常式附加至執行個體，以定義在其成員表中處理的事件，您就可以使用 `Handles` 附加[路由事件](GTMT)的處理常式。  對於[路由事件](GTMT)，使用 `Handles` 附加的處理常式遵循的路由規則與附加為 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 屬性或具有 <xref:System.Windows.UIElement.AddHandler%2A> 通用簽章的處理常式相同。  這表示如果事件已標記為已處理 \(事件資料中的 <xref:System.Windows.RoutedEventArgs.Handled%2A> 屬性為 `True`\)，則不會叫用 \(Invoke\) 已附加 `Handles` 的處理常式來回應該事件執行個體。  路由中其他項目上的執行個體處理常式，或是路由過程中目前之項目或先前之項目上的類別處理，都可以將事件標示為已處理。  對於支援配對之通道\/反昇事件的輸入事件，通道路由可能已將事件配對標記為已處理。  如需路由事件的詳細資訊，請參閱[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。  
  
## 使用 "Handles" 加入事件處理常式的限制  
 `Handles` 無法參考[附加事件](GTMT)的處理常式。  您必須使用該附加事件的 `add` 存取子方法，或是 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的 *typename.eventname* 事件屬性。  如需詳細資訊，請參閱[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。  
  
 對於[路由事件](GTMT)，您只能使用 `Handles`，針對事件存在執行個體成員表中的執行個體，指派其處理常式。  不過，對於一般路由事件，父項目可以是子項目傳回事件的接聽程式 \(Listener\)，即使父項目在其成員表中沒有該事件也一樣。  在屬性 \(Attribute\) 語法中，您可以透過 *typename.membername* 屬性格式，限定實際定義您要處理之事件的型別，以指定這項功能。  例如，父代 `Page` \(未定義 `Clic`k 事件\) 可以透過指派 `Button.Click` 格式的屬性接聽常式，接聽按一下按鈕的事件。  但是 `Handles` 不支援 *typename.membername* 格式，因為它必須支援衝突的 *Instance.Event* 格式。  如需詳細資訊，請參閱[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。  
  
 `Handles` 無法附加針對已經標記為已處理之事件所叫用的處理常式。  您必須改用程式碼並呼叫 <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> 的 `handledEventsToo` 多載 \(Overload\)。  
  
> [!NOTE]
>  當您在 XAML 中為相同的事件指定事件處理常式時，請勿使用 [!INCLUDE[vb_current_short](../../../../includes/vb-current-short-md.md)] 程式碼中的 `Handles` 語法。  在這個情況下，會呼叫事件處理常式兩次。  
  
## WPF 實作 "Handles" 功能的方式  
 編譯[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 頁面時，中繼檔案會宣告頁面上已設定 <xref:System.Windows.FrameworkContentElement.Name%2A> 屬性 \(或是已宣告 [x:Name 指示詞](../../../../docs/framework/xaml-services/x-name-directive.md)\) 之每個項目的 `Friend` `WithEvents` 參考。  每個具名執行個體都有可能是可以透過 `Handles` 指派至處理常式的項目。  
  
> [!NOTE]
>  在 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 內，[!INCLUDE[TLA2#tla_intellisense](../../../../includes/tla2sharptla-intellisense-md.md)] 可以顯示頁面中適用於 `Handles` 參考的項目完成狀態。  不過，這可能會採用一個編譯傳遞，使中繼檔案能夠填入 \(Populate\) 所有的 `Friends` 參考。  
  
## 請參閱  
 <xref:System.Windows.UIElement.AddHandler%2A>   
 [將路由事件標記為已處理以及類別處理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)   
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)