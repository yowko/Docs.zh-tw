---
title: "如何：使用 CompositionTarget 在單格間隔轉譯 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CompositionTarget 物件, 單格轉譯"
  - "使用 CompositionTarget 物件單格轉譯"
ms.assetid: 701246cd-66b7-4d69-ada9-17b3b433d95d
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：使用 CompositionTarget 在單格間隔轉譯
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫引擎提供許多功能，可以用來建立畫面格架構的動畫。  不過，在某些應用程式案例中，您需要針對每一個畫面格進行更精細的呈現控制。  <xref:System.Windows.Media.CompositionTarget> 物件提供了依據單格回呼 \(Callback\) 建立自訂動畫的功能。  
  
 <xref:System.Windows.Media.CompositionTarget> 是一種靜態類別，代表用來繪製應用程式的顯示介面。  每次繪製應用程式的場景時，都會引發 <xref:System.Windows.Media.CompositionTarget.Rendering> 事件。  呈現畫面播放速率就是每秒繪製場景的次數。  
  
> [!NOTE]
>  如需使用 <xref:System.Windows.Media.CompositionTarget> 的完整程式碼範例，請參閱[使用 CompositionTarget 範例](http://go.microsoft.com/fwlink/?LinkID=160045) \(英文\)。  
  
## 範例  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 呈現處理過程中會引發 <xref:System.Windows.Media.CompositionTarget.Rendering> 事件。  下列範例顯示如何將 <xref:System.EventHandler> 委派註冊到 <xref:System.Windows.Media.CompositionTarget> 上的靜態 <xref:System.Windows.Media.CompositionTarget.Rendering> 方法。  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 您可以使用自己的呈現事件處理常式 \(Event Handler\) 方法來建立自訂繪製內容。  每個畫面格都會呼叫此事件處理常式方法一次。  每次 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 將[視覺化樹狀結構](GTMT)中保留的呈現資料封送處理至複合場景圖形時，就會呼叫事件處理常式方法。  此外，如果[視覺化樹狀結構](GTMT)的變更強制更新複合場景圖形，也會呼叫事件處理常式方法。  請注意，事件處理常式方法是在配置計算完成之後呼叫。  不過，您可以在事件處理常式方法中修改配置，而這代表配置會在呈現之前再計算一次。  
  
 下列範例說明如何在 <xref:System.Windows.Media.CompositionTarget> 事件處理常式方法中提供自訂繪圖。  這個案例使用以滑鼠座標位置為準的色彩值來繪製 <xref:System.Windows.Controls.Canvas> 的背景色彩。  如果您將滑鼠移到 <xref:System.Windows.Controls.Canvas> 內，它的背景色彩就會改變。  此外，這個範例也會根據目前已耗用的時間和呈現的畫面格總數，計算平均畫面播放速率。  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 您可能會發現自己的自訂繪圖在不同電腦上的執行速度也不同。  這是因為您的自訂繪圖受到畫面播放速率的限制。  依據您所執行的系統和系統的工作負載而定，每秒呼叫 <xref:System.Windows.Media.CompositionTarget.Rendering> 事件的次數可能各不相同。  如需判斷執行 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 之裝置的圖形硬體功能和效能的詳細資訊，請參閱[圖形轉譯層](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)。  
  
 在引發事件時加入或移除呈現 <xref:System.EventHandler> 委派的作業將會延後到事件引發完成之後。  這與在 Common Language Runtime \(CLR\) 中處理 <xref:System.MulticastDelegate> 架構事件的方式一致。  另外請注意，呈現事件不一定會以任何特定的順序呼叫。  如果您有多項必須遵照特定順序的 <xref:System.EventHandler> 委派，應該註冊單一 <xref:System.Windows.Media.CompositionTarget.Rendering> 事件，然後再自行按照正確的順序多工處理這些委派。  
  
## 請參閱  
 <xref:System.Windows.Media.CompositionTarget>   
 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)