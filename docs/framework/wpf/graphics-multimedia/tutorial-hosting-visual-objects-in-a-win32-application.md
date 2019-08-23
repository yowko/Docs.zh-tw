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
ms.openlocfilehash: c8baefbf01467a65626a77f300f34a145d5c7281
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962866"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>教學課程：在 Win32 應用程式中裝載視覺物件
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供用來建立應用程式的豐富環境。 不過, 當您對程式[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]代碼進行大量的投資時, 將功能新增[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]至您的應用程式, 而不是重寫程式碼, 可能會更有效率。 為了提供應用程式[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]同時使用之和圖形子系統的支援[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]提供在視窗中裝載物件的機制。  
  
 本教學課程說明如何撰寫在[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗中裝載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]視覺物件的範例應用程式、[使用 Win32 交互操作進行點擊測試範例](https://go.microsoft.com/fwlink/?LinkID=159995)。  

<a name="requirements"></a>   
## <a name="requirements"></a>需求  
 本教學課程假設您對 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 程式設計已有基本的熟悉度。 如需程式[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]設計的基本簡介, [請參閱逐步解說:我的第一個 WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)桌面應用程式。 如需程式[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]設計的簡介, 請參閱主題中的任何一本書, 特別是 Charles Petzold 的程式*設計視窗*。  
  
> [!NOTE]
> 本教學課程包含一些來自相關範例的程式碼範例。 不過，為了方便閱讀，並未包含完整的範例程式碼。 如需完整的範例程式碼, 請參閱[使用 Win32 交互操作進行點擊測試範例](https://go.microsoft.com/fwlink/?LinkID=159995)。  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>建立 Win32 主機視窗  
 在視窗中裝載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]物件的索引鍵是<xref:System.Windows.Interop.HwndSource>類別。 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 這個類別會包裝[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗中的物件, 讓它們併入[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]成為子視窗。  
  
 下列範例顯示將<xref:System.Windows.Interop.HwndSource>物件建立[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]為視覺物件之容器視窗的程式碼。 若要設定視窗的視窗樣式、位置和其他參數[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] , 請<xref:System.Windows.Interop.HwndSourceParameters>使用物件。  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A>屬性的值不能設定為 WS_EX_TRANSPARENT。 這表示主機[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗不可為透明。 因此, 主[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗的背景色彩會設定為與父視窗相同的背景色彩。  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>將視覺物件加入至主機 Win32 視窗  
 建立視覺物件的 [主機[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]容器] 視窗之後, 您就可以在其中加入視覺物件。 您會想要確保視覺物件的任何轉換 (例如動畫) 不會延伸超過主機[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗周框的範圍。  
  
 下列範例顯示用來建立<xref:System.Windows.Interop.HwndSource>物件並在其中加入視覺物件的程式碼。  
  
> [!NOTE]
> <xref:System.Windows.Interop.HwndSource>物件<xref:System.Windows.Interop.HwndSource.RootVisual%2A>的屬性會設定為新增至主機[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗的第一個視覺物件。 根視覺物件會定義視覺物件樹狀結構的最上層節點。 加入至主機[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗的任何後續視覺物件都會加入為子物件。  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>實作 Win32 訊息篩選器  
 視覺物件[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]的 [主機] 視窗需要視窗訊息篩選程式, 以處理從應用程式佇列傳送至視窗的訊息。 視窗程式會接收來自系統的[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]訊息。 這些可能是輸入訊息或視窗管理訊息。 您可以選擇性地在您的視窗程序中處理訊息，或者將訊息傳遞至系統進行預設處理。  
  
 您定義為視覺物件之父系的物件必須參考您提供的視窗訊息篩選器程式。<xref:System.Windows.Interop.HwndSource> 當您建立<xref:System.Windows.Interop.HwndSource>物件時, 請<xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A>將屬性設定為參考視窗程式。  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 下列範例顯示用來處理滑鼠左右按鈕訊息的程式碼。 滑鼠點擊位置的座標值包含在`lParam`參數的值中。  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>處理 Win32 訊息  
 下列範例中的程式碼顯示如何針對主機[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗中包含的視覺物件階層架構執行點擊測試。 您可以使用<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法來指定根視覺物件和要進行點擊測試的座標值, 以識別某個點是否在視覺物件的幾何內。 在此情況下, 根視覺物件是<xref:System.Windows.Interop.HwndSource.RootVisual%2A> <xref:System.Windows.Interop.HwndSource>物件的屬性值。  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 如需針對視覺物件進行點擊測試的詳細資訊, 請參閱[視覺分層中的點擊測試](hit-testing-in-the-visual-layer.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Interop.HwndSource>
- [使用 Win32 交互操作進行點擊測試範例](https://go.microsoft.com/fwlink/?LinkID=159995)
- [視覺分層中的點擊測試](hit-testing-in-the-visual-layer.md)
