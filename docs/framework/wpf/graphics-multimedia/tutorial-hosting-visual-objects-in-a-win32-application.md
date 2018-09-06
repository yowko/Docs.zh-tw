---
title: 教學課程：在 Win32 應用程式中裝載視覺物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual objects in Win32 code [WPF]
- Win32 code [WPF], visual objects in
- hosting [WPF], visual objects in Win32 code
ms.assetid: f0e1600c-3217-43d5-875d-1864fa7fe628
ms.openlocfilehash: 4db60418512080d6bf13ef00b1c6e7dce797a16b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785907"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>教學課程：在 Win32 應用程式中裝載視覺物件
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供用來建立應用程式的豐富環境。 不過，如果您已長期開發[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]程式碼，它可能會更有效率，以新增[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]您的應用程式的功能而不是重寫程式碼。 若要提供支援[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]並[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式，同時使用的圖形子系統[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供一個機制，來裝載中的物件[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗。  
  
 本教學課程說明如何撰寫範例應用程式[Win32 交互操作範例使用點擊測試](https://go.microsoft.com/fwlink/?LinkID=159995)，、 該主機[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]視覺物件中[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗。  
  

  
<a name="requirements"></a>   
## <a name="requirements"></a>需求  
 本教學課程假設您對 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 程式設計已有基本的熟悉度。 如需基本簡介[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]程式設計，請參閱[逐步解說： 我第一個 WPF 桌面應用程式](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)。 如需簡介[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]程式設計，請參閱書籍的任何主題，特別*程式設計 Windows* Charles petzold 的。  
  
> [!NOTE]
>  本教學課程包含一些來自相關範例的程式碼範例。 不過，為了方便閱讀，並未包含完整的範例程式碼。 完整範例程式碼，請參閱[Win32 交互操作範例使用點擊測試](https://go.microsoft.com/fwlink/?LinkID=159995)。  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>建立 Win32 主機視窗  
 要裝載的索引鍵[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中的物件[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗是<xref:System.Windows.Interop.HwndSource>類別。 這個類別會包裝[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中的物件[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗中，讓他們能夠整合到您[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]做為子視窗。  
  
 下列範例顯示建立的程式碼<xref:System.Windows.Interop.HwndSource>物件做為[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]容器 視窗中的視覺物件。 若要設定的視窗樣式、 位置和其他參數[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗中，使用<xref:System.Windows.Interop.HwndSourceParameters>物件。  
  
 [!code-csharp[VisualsHitTesting#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
>  值<xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A>屬性無法設定為 WS_EX_TRANSPARENT。 這表示主機[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗不可為透明。 基於這個理由，主應用程式的背景色彩[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]範圍設定為其父視窗相同的背景色彩。  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>將視覺物件加入至主機 Win32 視窗  
 當您建立主機[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]容器視窗為視覺物件中，您可以將視覺物件加入它。 您會想要確保視覺物件，例如動畫，任何轉換，不會延伸 překračuje meze 主機[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗之週框。  
  
 下列範例顯示建立的程式碼<xref:System.Windows.Interop.HwndSource>物件，並加入視覺物件。  
  
> [!NOTE]
>  <xref:System.Windows.Interop.HwndSource.RootVisual%2A>的屬性<xref:System.Windows.Interop.HwndSource>物件設定為第一個視覺物件加入至主機[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗。 根視覺物件會定義視覺物件樹狀結構的最上層節點。 任何後續的視覺物件加入至主機[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗將會新增為子物件。  
  
 [!code-csharp[VisualsHitTesting#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>實作 Win32 訊息篩選器  
 主機[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]為視覺物件的視窗需要視窗訊息篩選程序來處理從應用程式佇列傳送至視窗的訊息。 視窗程序接收來自訊息[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]系統。 這些可能是輸入訊息或視窗管理訊息。 您可以選擇性地在您的視窗程序中處理訊息，或者將訊息傳遞至系統進行預設處理。  
  
 <xref:System.Windows.Interop.HwndSource>物件，您將定義為視覺物件的父系必須參考您所提供的視窗訊息篩選程序。 當您建立<xref:System.Windows.Interop.HwndSource>物件，設定<xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A>參考視窗程序的屬性。  
  
 [!code-csharp[VisualsHitTesting#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 下列範例顯示用來處理滑鼠左右按鈕訊息的程式碼。 座標值的滑鼠點擊位置的值包含`lParam`參數。  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>處理 Win32 訊息  
 下列範例的程式碼示範如何針對主機中所包含之視覺物件階層執行點擊的測試[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗。 您可以識別某個點是否視覺物件的幾何內使用<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法，以指定的根視覺物件和要進行點擊測試的座標值。 在此情況下，根視覺物件是值<xref:System.Windows.Interop.HwndSource.RootVisual%2A>屬性<xref:System.Windows.Interop.HwndSource>物件。  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 如需有關視覺物件的點擊測試的詳細資訊，請參閱[視覺分層中的點擊測試](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Interop.HwndSource>  
 [點擊測試使用 Win32 交互操作範例](https://go.microsoft.com/fwlink/?LinkID=159995)  
 [視覺分層中的點擊測試](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)
