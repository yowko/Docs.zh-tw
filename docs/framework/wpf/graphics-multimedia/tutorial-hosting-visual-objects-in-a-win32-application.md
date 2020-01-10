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
ms.openlocfilehash: 621684e14f9d1b599c4ef60e3731f0f58f31aacd
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740170"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>教學課程：在 Win32 應用程式中裝載視覺物件
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供用來建立應用程式的豐富環境。 不過，當您在 Win32 程式碼中投入大量投資時，將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能加入至應用程式，而不是重寫您的程式碼，可能會更有效率。 為了提供應用程式中同時使用之 Win32 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 圖形子系統的支援，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供在 Win32 視窗中裝載物件的機制。  
  
 本教學課程說明如何撰寫範例應用程式，[使用 Win32 交互操作進行點擊測試範例](https://go.microsoft.com/fwlink/?LinkID=159995)，它會在 win32 視窗中裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的視覺物件。  

<a name="requirements"></a>   
## <a name="requirements"></a>需求  
 本教學課程假設您已熟悉 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 Win32 程式設計的基本概念。 如需 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 程式設計的基本簡介，請參閱[逐步解說：我的第一個 WPF 桌面應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)。 如需 Win32 程式設計的簡介，請參閱主題中的任何一本書，特別是 Charles Petzold 的程式*設計視窗*。  
  
> [!NOTE]
> 本教學課程包含一些來自相關範例的程式碼範例。 不過，為了方便閱讀，並未包含完整的範例程式碼。 如需完整的範例程式碼，請參閱[使用 Win32 交互操作進行點擊測試範例](https://go.microsoft.com/fwlink/?LinkID=159995)。  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>建立 Win32 主機視窗  
 在 Win32 視窗中裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 物件的關鍵是 <xref:System.Windows.Interop.HwndSource> 類別。 這個類別會將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 物件包裝在 Win32 視窗中，以便將它們併入您的 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 做為子視窗。  
  
 下列範例顯示用來建立 <xref:System.Windows.Interop.HwndSource> 物件做為視覺物件之 Win32 容器視窗的程式碼。 若要設定 Win32 視窗的視窗樣式、位置和其他參數，請使用 <xref:System.Windows.Interop.HwndSourceParameters> 物件。  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> 屬性的值不能設定為 WS_EX_TRANSPARENT。 這表示主機 Win32 視窗不可以是透明的。 因此，[主機 Win32] 視窗的背景色彩會設定為與父視窗相同的背景色彩。  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>將視覺物件加入至主機 Win32 視窗  
 建立視覺物件的 [主機 Win32 容器] 視窗之後，您就可以在其中加入視覺物件。 您會想要確保視覺物件的任何轉換（例如動畫）不會延伸超過主機 Win32 視窗周框的範圍。  
  
 下列範例顯示用來建立 <xref:System.Windows.Interop.HwndSource> 物件以及在其中加入視覺物件的程式碼。  
  
> [!NOTE]
> <xref:System.Windows.Interop.HwndSource> 物件的 <xref:System.Windows.Interop.HwndSource.RootVisual%2A> 屬性會設定為新增至 [主機 Win32] 視窗的第一個視覺物件。 根視覺物件會定義視覺物件樹狀結構的最上層節點。 加入至 [主機 Win32] 視窗的任何後續視覺物件都會加入為子物件。  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>實作 Win32 訊息篩選器  
 視覺物件的 [主機 Win32] 視窗需要視窗訊息篩選程式，以處理從應用程式佇列傳送至視窗的訊息。 視窗程式會接收來自 Win32 系統的訊息。 這些可能是輸入訊息或視窗管理訊息。 您可以選擇性地在您的視窗程序中處理訊息，或者將訊息傳遞至系統進行預設處理。  
  
 您定義為視覺物件之父系的 <xref:System.Windows.Interop.HwndSource> 物件必須參考您提供的視窗訊息篩選程式。 當您建立 <xref:System.Windows.Interop.HwndSource> 物件時，請將 <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> 屬性設定為參考視窗程式。  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 下列範例顯示用來處理滑鼠左右按鈕訊息的程式碼。 滑鼠點擊位置的座標值包含在 `lParam` 參數的值中。  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>處理 Win32 訊息  
 下列範例中的程式碼顯示如何針對主機 Win32 視窗中包含的視覺物件階層架構執行點擊測試。 您可以使用 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> 方法來指定根視覺物件和要進行點擊測試的座標值，以識別某個點是否在視覺物件的幾何內。 在此情況下，根視覺物件是 <xref:System.Windows.Interop.HwndSource> 物件之 <xref:System.Windows.Interop.HwndSource.RootVisual%2A> 屬性的值。  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 如需針對視覺物件進行點擊測試的詳細資訊，請參閱[視覺分層中的點擊測試](hit-testing-in-the-visual-layer.md)。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Interop.HwndSource>
- [使用 Win32 交互操作進行點擊測試範例](https://go.microsoft.com/fwlink/?LinkID=159995)
- [視覺分層中的點擊測試](hit-testing-in-the-visual-layer.md)
