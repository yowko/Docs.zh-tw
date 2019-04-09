---
title: HOW TO：使用 Win32 主機容器進行點擊測試
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
ms.openlocfilehash: ac5cae5bcd94dc8bf80ff95b8971914e1fa5ba2c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081459"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a>HOW TO：使用 Win32 主機容器進行點擊測試
您可以建立視覺物件內[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]藉由提供主機視窗容器為視覺物件的視窗。 若要針對包含的視覺物件提供事件處理，您必須處理傳遞至裝載視窗容器之訊息篩選迴圈的訊息。 請參閱[教學課程：裝載在 Win32 應用程式中的視覺物件](tutorial-hosting-visual-objects-in-a-win32-application.md)如需有關如何裝載中的視覺物件[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何設定滑鼠事件處理常式，如[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]可做為視覺物件的主應用程式容器的視窗。  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 下列範例示範如何設定點擊測試，以回應捕捉的特定滑鼠事件。  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <xref:System.Windows.Interop.HwndSource>物件呈現[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]內容[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]視窗。 值<xref:System.Windows.Interop.HwndSource.RootVisual%2A>屬性<xref:System.Windows.Interop.HwndSource>物件都代表在視覺化樹狀結構階層中的最上層節點。  
  
 如需點擊測試的完整範例物件，使用 Win32 裝載容器，請參閱 < [Win32 交互操作範例使用點擊測試](https://go.microsoft.com/fwlink/?LinkID=159995)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Interop.HwndSource>
- [視覺分層中的點擊測試](hit-testing-in-the-visual-layer.md)
- [教學課程：在 Win32 應用程式中裝載視覺物件](tutorial-hosting-visual-objects-in-a-win32-application.md)
