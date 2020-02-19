---
title: 操作說明：使用 Win32 裝載容器進行點擊測試
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
ms.openlocfilehash: a86c1c36f75fa232d52731959371268a8b2593d7
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452801"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a>操作說明：使用 Win32 裝載容器進行點擊測試
您可以藉由提供視覺物件的主機視窗容器，在 Win32 視窗內建立視覺物件。 若要針對包含的視覺物件提供事件處理，您必須處理傳遞至裝載視窗容器之訊息篩選迴圈的訊息。 如需如何在 Win32 視窗中裝載視覺物件的詳細資訊，請參閱[教學課程：在 Win32 應用程式中裝載視覺物件](tutorial-hosting-visual-objects-in-a-win32-application.md)。  
  
## <a name="example"></a>範例  
 下列程式碼會示範如何設定 Win32 視窗的滑鼠事件處理常式，以當做視覺物件的主機容器使用。  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 下列範例示範如何設定點擊測試，以回應捕捉特定的滑鼠事件。  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <xref:System.Windows.Interop.HwndSource> 物件會在 Win32 視窗中呈現 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 內容。 <xref:System.Windows.Interop.HwndSource> 物件的 <xref:System.Windows.Interop.HwndSource.RootVisual%2A> 屬性值，代表視覺化樹狀結構階層中最上層的節點。  
  
 如需使用 Win32 主機容器進行點擊測試物件的完整範例，請參閱[使用 Win32 交互操作進行點擊測試範例](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Interop.HwndSource>
- [視覺分層中的點擊測試](hit-testing-in-the-visual-layer.md)
- [教學課程：在 Win32 應用程式中裝載視覺物件](tutorial-hosting-visual-objects-in-a-win32-application.md)
