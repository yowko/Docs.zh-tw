---
title: "逐步解說：建立您的第一個觸控應用程式 | Microsoft Docs"
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
  - "建立觸控螢幕應用程式 [WPF]"
  - "建立觸控感應應用程式 [WPF]"
  - "觸控螢幕應用程式 [WPF], 建立"
  - "觸控感應應用程式 [WPF], 建立"
ms.assetid: d69e602e-9a25-4e24-950b-e89eaa2a906b
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 逐步解說：建立您的第一個觸控應用程式
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可讓應用程式回應觸控。  例如，您可以在觸控感應裝置 \(例如觸控螢幕\) 上使用一或多根手指與應用程式進行互動。本逐步解說會建立可讓使用者透過觸控方式移動、調整大小或旋轉單一物件的應用程式。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)].  
  
-   Windows 7。  
  
-   接受支援 Windows Touch 之觸控輸入的裝置，例如觸控螢幕。  
  
 此外，您應該對於如何在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中建立應用程式有基本的了解，尤其是訂閱和處理事件。  如需詳細資訊，請參閱 [逐步解說：WPF 使用者入門](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)。  
  
## 建立應用程式  
  
#### 若要建立應用程式  
  
1.  在 Visual Basic 或 Visual C\# 中，建立名為 `BasicManipulation` 的新 WPF 應用程式專案。  如需詳細資訊，請參閱 [HOW TO：建立新的 WPF 應用程式專案](http://msdn.microsoft.com/zh-tw/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)。  
  
2.  以下列 XAML 取代 MainWindow.xaml 的內容。  
  
     這個標記會建立簡單的應用程式，其中 <xref:System.Windows.Controls.Canvas> 上包含紅色的 <xref:System.Windows.Shapes.Rectangle>。  <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.UIElement.IsManipulationEnabled%2A> 屬性設定為 true，因此將會接收操作事件。  應用程式會訂閱 <xref:System.Windows.UIElement.ManipulationStarting>、<xref:System.Windows.UIElement.ManipulationDelta> 和 <xref:System.Windows.UIElement.ManipulationInertiaStarting> 事件。  這些事件包含在使用者操作 <xref:System.Windows.Shapes.Rectangle> 時將它移動的邏輯。  
  
     [!code-xml[BasicManipulation#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3.  如果您是使用 Visual Basic，則請將 MainWindow.xaml 的第一行中的 `x:Class="BasicManipulation.MainWindow"` 取代為 `x:Class="MainWindow"`。  
  
4.  在 `MainWindow` 類別中加入下列 <xref:System.Windows.UIElement.ManipulationStarting> 事件處理常式。  
  
     <xref:System.Windows.UIElement.ManipulationStarting> 事件會在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 偵測到控輸入開始操作物件時發生。  程式碼會透過設定 <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> 屬性的方式，指定操作的位置應該相對於 <xref:System.Windows.Window>。  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]  
  
5.  在 `MainWindow` 類別中加入下列 <xref:System.Windows.Input.ManipulationDelta> 事件處理常式。  
  
     <xref:System.Windows.Input.ManipulationDelta> 事件會在觸控輸入變更位置時發生，而且可能在操作期間多次發生。  此事件也可能在手指提起時發生。  例如，如果使用者拖曳手指橫跨螢幕，<xref:System.Windows.Input.ManipulationDelta> 事件會在手指移動時發生多次。  當使用者從螢幕提起手指時，<xref:System.Windows.Input.ManipulationDelta> 事件會繼續發生以模擬慣性。  
  
     程式碼會將 <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> 套用至 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.UIElement.RenderTransform%2A>，以便隨著使用者移動觸控輸入而移動。  程式碼還會在慣性期間事件發生時，檢查 <xref:System.Windows.Shapes.Rectangle> 是否在 <xref:System.Windows.Window> 的界限之外。  如果是的話，應用程式會呼叫 <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=fullName> 方法結束操作。  
  
     [!code-csharp[BasicManipulation#ManipulationDelta](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]  
  
6.  在 `MainWindow` 類別中加入下列 <xref:System.Windows.UIElement.ManipulationInertiaStarting> 事件處理常式。  
  
     <xref:System.Windows.UIElement.ManipulationInertiaStarting> 事件會在使用者從螢幕提起所有手指時發生。  程式碼會設定矩形移動、擴充和旋轉的初始速度和減速。  
  
     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]  
  
7.  建置及執行專案。  
  
     您應該會看到紅色正方形出現在視窗中。  
  
## 測試應用程式  
 若要測試應用程式，請嘗試下列操作。  請注意，您可以同時執行下列多項操作。  
  
-   若要移動 <xref:System.Windows.Shapes.Rectangle>，請將手指放在 <xref:System.Windows.Shapes.Rectangle> 上並且移動手指橫跨螢幕。  
  
-   若要調整 <xref:System.Windows.Shapes.Rectangle> 的大小，請將兩隻手指放在 <xref:System.Windows.Shapes.Rectangle> 上，並且將兩隻手指彼此移近或移開。  
  
-   若要旋轉 <xref:System.Windows.Shapes.Rectangle>，請將兩隻手指放在 <xref:System.Windows.Shapes.Rectangle> 上，並且讓兩隻手指繞彼此周圍旋轉。  
  
 若要製造慣性效果，請在您執行上述操作時，快速地將手指從螢幕提起。  <xref:System.Windows.Shapes.Rectangle> 將繼續移動、調整大小或旋轉幾秒鐘才停止。  
  
## 請參閱  
 <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=fullName>   
 <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=fullName>   
 <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=fullName>