---
title: "如何：使用 Win32 裝載容器進行點擊測試 | Microsoft Docs"
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
  - "點擊測試, 使用 Win32 裝載容器"
  - "視覺物件, 點擊測試"
  - "Win32 裝載容器, 點擊測試使用"
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：使用 Win32 裝載容器進行點擊測試
您可以透過提供視覺物件的裝載視窗容器，在 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 視窗內建立視覺物件。  若要為包含的視覺物件提供事件處理功能，請處理傳遞至裝載視窗容器之訊息篩選迴圈 \(Loop\) 的訊息。  如需如何在 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗中裝載視覺物件的詳細資訊，請參閱[教學課程：在 Win32 應用程式中裝載視覺物件](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)。  
  
## 範例  
 下列程式碼示範如何設定滑鼠事件處理常式，以處理做為視覺物件裝載容器的 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗。  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 下列範例示範如何設定[點擊測試](GTMT) \(Hit Test\)，以回應截獲特定滑鼠事件。  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <xref:System.Windows.Interop.HwndSource> 物件代表 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 視窗內的 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 內容。<xref:System.Windows.Interop.HwndSource> 物件的 <xref:System.Windows.Interop.HwndSource.RootVisual%2A> 屬性值代表[視覺化樹狀結構](GTMT)階層中最上面的節點。  
  
 如需使用 Win32 裝載容器之點擊測試物件的完整範例，請參閱[使用 Win32 互通性進行點擊測試範例](http://go.microsoft.com/fwlink/?LinkID=159995) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Interop.HwndSource>   
 [視覺分層中的點擊測試](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)   
 [教學課程：在 Win32 應用程式中裝載視覺物件](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)