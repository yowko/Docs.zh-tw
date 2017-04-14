---
title: "教學課程：在 Win32 應用程式中裝載視覺物件 | Microsoft Docs"
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
  - "裝載, Win32 程式碼中的視覺物件"
  - "Win32 程式碼中的視覺物件"
  - "Win32 程式碼, 視覺物件"
ms.assetid: f0e1600c-3217-43d5-875d-1864fa7fe628
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 教學課程：在 Win32 應用程式中裝載視覺物件
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供用來建立應用程式的豐富環境。  不過，若您已對 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 程式碼投入相當的心力，更有效的方法是將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能加入應用程式，而不是重新撰寫程式碼。  為了提供在應用程式中同時 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 圖形子系統的支援，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供了一種將物件裝載在 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗中的機制。  
  
 本教學課程說明如何撰寫範例應用程式[使用 Win32 互通性進行點擊測試範例](http://go.microsoft.com/fwlink/?LinkID=159995) \(英文\)，該應用程式會將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 視覺物件裝載在 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗中。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="requirements"></a>   
## 需求  
 本教學課程假設您已熟悉 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 程式設計的基本概念。  如需 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 程式設計的基本簡介，請參閱[逐步解說：WPF 使用者入門](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)。  如需 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 程式設計的簡介，請參閱討論此主題的各種書籍，尤其是 Charles Petzold 所著的《*Programming Windows*》。  
  
> [!NOTE]
>  本教學課程包括摘錄自相關範例的許多程式碼範例。  不過，為了方便閱讀，此課程並未包含完整的範例程式碼。  如需完整範例程式碼，請參閱[使用 Win32 互通性進行點擊測試範例](http://go.microsoft.com/fwlink/?LinkID=159995) \(英文\)。  
  
<a name="creating_the_host_win32_window"></a>   
## 建立裝載 Win32 視窗  
 將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 物件裝載在 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗中的關鍵在於 <xref:System.Windows.Interop.HwndSource> 類別。  這個類別會將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 物件包裝在 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗中，讓您可以將這些物件當做子視窗加入 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中。  
  
 下列範例顯示的程式碼可用來建立 <xref:System.Windows.Interop.HwndSource> 物件，做為視覺物件的 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 容器視窗。  若要設定 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 的視窗樣式、位置和其他參數，請使用 <xref:System.Windows.Interop.HwndSourceParameters> 物件。  
  
 [!code-csharp[VisualsHitTesting#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
>  <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> 屬性的值不能設定為 WS\_EX\_TRANSPARENT。  這表示裝載 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗不能是透明的。  因此，裝載 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗的背景色彩會設定成與其父視窗相同的背景色彩。  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## 將視覺物件加入至裝載 Host Win32 視窗  
 建立視覺物件的裝載 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 容器視窗之後，您就可以將視覺物件加入視窗中。  您必須確定視覺物件的任何變化 \(例如動畫\) 都不會超過裝載 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗周框的範圍。  
  
 下列範例顯示的程式碼可用來建立 <xref:System.Windows.Interop.HwndSource> 物件，並將視覺物件加入其中。  
  
> [!NOTE]
>  <xref:System.Windows.Interop.HwndSource> 物件的 <xref:System.Windows.Interop.HwndSource.RootVisual%2A> 屬性會設定為加入至裝載 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗的第一個視覺物件。  這個根 \(Root\) 視覺物件定義了視覺物件樹狀結構的最上層節點。  後續加入至裝載 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗的任何物件都會變成子物件。  
  
 [!code-csharp[VisualsHitTesting#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## 實作 Win32 訊息篩選  
 視覺物件的裝載 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗需要使用視窗訊息篩選程序來處理從應用程式佇列傳送到視窗的訊息。  視窗程序會接收 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 系統傳來的訊息。  這些訊息可能是輸入訊息或視窗管理訊息。  您可以選擇在視窗程序中處理訊息，或是將訊息傳送給系統進行預設處理。  
  
 已定義為視覺物件父代 \(Parent\) 的 <xref:System.Windows.Interop.HwndSource> 物件必須參考您所提供的視窗訊息篩選程序。  當您建立 <xref:System.Windows.Interop.HwndSource> 物件時，請設定 <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> 屬性來參考該視窗程序。  
  
 [!code-csharp[VisualsHitTesting#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 下列範例顯示的程式碼可用來處理滑鼠左右鍵訊息。  滑鼠點擊位置的座標值包含在 `lParam` 參數值中。  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## 處理 Win32 訊息  
 下列範例中的程式碼示範如何針對裝載 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗中包含的視覺物件階層架構，執行點擊測試。  您可以使用 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> 方法指定根視覺物件和要進行點擊測試的座標值，以識別某個點是否在視覺物件的幾何範圍內。  在這個案例中，根視覺物件是 <xref:System.Windows.Interop.HwndSource> 物件的 <xref:System.Windows.Interop.HwndSource.RootVisual%2A> 屬性值。  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 如需對視覺物件進行點擊測試的詳細資訊，請參閱[視覺分層中的點擊測試](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)。  
  
## 請參閱  
 <xref:System.Windows.Interop.HwndSource>   
 [使用 Win32 互通性進行點擊測試範例](http://go.microsoft.com/fwlink/?LinkID=159995)   
 [視覺分層中的點擊測試](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)