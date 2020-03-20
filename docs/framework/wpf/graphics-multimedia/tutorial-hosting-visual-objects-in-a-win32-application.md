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
ms.openlocfilehash: d04357e0770bbf8eebe8f40a86a19ddc9baae3ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187432"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>教學課程：在 Win32 應用程式中裝載視覺物件
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供用來建立應用程式的豐富環境。 但是，當您對 Win32 代碼進行大量投資時，向應用程式添加[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]功能而不是重寫代碼可能更有效。 要支援應用程式中同時使用的 Win32 和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]圖形子系統，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]請提供一種在 Win32 視窗中託管物件的機制。  
  
 本教程介紹如何編寫應用程式範例，[即使用 Win32 交互操作示例進行點擊測試](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)，該[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]示例在 Win32 視窗中承載可視物件。  

<a name="requirements"></a>
## <a name="requirements"></a>需求  
 本教程假定對 Win32[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]程式設計和 Win32 程式設計基本熟悉。 有關[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]程式設計的基本介紹，請參閱[演練：我的第一個 WPF 桌面應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)。 有關 Win32 程式設計的介紹，請參閱有關該主題的眾多書籍中的任何一本書，特別是查理斯·佩佐德的*程式設計 Windows。*  
  
> [!NOTE]
> 本教學課程包含一些來自相關範例的程式碼範例。 不過，為了方便閱讀，並未包含完整的範例程式碼。 有關完整的示例代碼，請參閱[使用 Win32 交互操作示例進行點擊測試](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)。  
  
<a name="creating_the_host_win32_window"></a>
## <a name="creating-the-host-win32-window"></a>建立 Win32 主機視窗  
 在 Win32 視窗中託管[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]物件的關鍵是<xref:System.Windows.Interop.HwndSource>類。 此類將[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]物件包裝在 Win32 視窗中，允許將它們作為子視窗合併到您的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]視窗中。  
  
 下面的示例顯示了將<xref:System.Windows.Interop.HwndSource>物件創建為可視物件的 Win32 容器視窗的代碼。 要設置 Win32 視窗的視窗樣式、位置和其他參數，請使用 該<xref:System.Windows.Interop.HwndSourceParameters>物件。  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> 屬性的值<xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A>不能設置為WS_EX_TRANSPARENT。 這意味著主機 Win32 視窗不能透明。 因此，主機 Win32 視窗的背景顏色設置為與其父視窗相同的背景顏色。  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>
## <a name="adding-visual-objects-to-the-host-win32-window"></a>將視覺物件加入至主機 Win32 視窗  
 為可視物件創建主機 Win32 容器視窗後，可以向其添加可視物件。 您需要確保視覺物件的任何轉換（如動畫）不會超出主機 Win32 視窗的邊界矩形的邊界範圍。  
  
 下面的示例顯示了用於創建<xref:System.Windows.Interop.HwndSource>物件和向物件添加可視物件的代碼。  
  
> [!NOTE]
> <xref:System.Windows.Interop.HwndSource>物件<xref:System.Windows.Interop.HwndSource.RootVisual%2A>的屬性設置為添加到主機 Win32 視窗的第一個可視物件。 根視覺物件會定義視覺物件樹狀結構的最上層節點。 添加到主機 Win32 視窗的任何後續可視物件都添加為子物件。  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>
## <a name="implementing-the-win32-message-filter"></a>實作 Win32 訊息篩選器  
 視覺物件的主機 Win32 視窗需要視窗消息篩選器過程來處理從應用程式佇列發送到視窗的消息。 視窗過程接收來自 Win32 系統的消息。 這些可能是輸入訊息或視窗管理訊息。 您可以選擇性地在您的視窗程序中處理訊息，或者將訊息傳遞至系統進行預設處理。  
  
 您<xref:System.Windows.Interop.HwndSource>定義為可視物件的父物件必須引用您提供的視窗消息篩選器過程。 創建物件時，<xref:System.Windows.Interop.HwndSource>將<xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A>屬性設置為引用視窗過程。  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 下列範例顯示用來處理滑鼠左右按鈕訊息的程式碼。 滑鼠命中位置的座標值包含在`lParam`參數的值中。  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>
## <a name="processing-the-win32-messages"></a>處理 Win32 訊息  
 以下示例中的代碼顯示如何針對主機 Win32 視窗中中包含的可視物件的層次結構執行點擊測試。 通過使用<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法指定根可視物件和要點擊測試的座標值，可以識別點是否位於可視物件的幾何體內。 在這種情況下，根可視物件是<xref:System.Windows.Interop.HwndSource.RootVisual%2A><xref:System.Windows.Interop.HwndSource>物件屬性的值。  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 有關針對可視物件進行點擊測試的詳細資訊，請參閱[視覺化圖層中的點擊測試](hit-testing-in-the-visual-layer.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Interop.HwndSource>
- [使用 Win32 交互操作進行點擊測試範例 (英文)](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)
- [視覺分層中的點擊測試](hit-testing-in-the-visual-layer.md)
