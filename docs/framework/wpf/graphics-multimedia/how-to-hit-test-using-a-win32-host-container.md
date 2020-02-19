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
# <a name="how-to-hit-test-using-a-win32-host-container"></a><span data-ttu-id="22e24-102">操作說明：使用 Win32 裝載容器進行點擊測試</span><span class="sxs-lookup"><span data-stu-id="22e24-102">How to: Hit Test Using a Win32 Host Container</span></span>
<span data-ttu-id="22e24-103">您可以藉由提供視覺物件的主機視窗容器，在 Win32 視窗內建立視覺物件。</span><span class="sxs-lookup"><span data-stu-id="22e24-103">You can create visual objects within a Win32 window by providing a host window container for the visual objects.</span></span> <span data-ttu-id="22e24-104">若要針對包含的視覺物件提供事件處理，您必須處理傳遞至裝載視窗容器之訊息篩選迴圈的訊息。</span><span class="sxs-lookup"><span data-stu-id="22e24-104">To provide event handling for the contained visual objects you process the messages passed to the host window container’s message filter loop.</span></span> <span data-ttu-id="22e24-105">如需如何在 Win32 視窗中裝載視覺物件的詳細資訊，請參閱[教學課程：在 Win32 應用程式中裝載視覺物件](tutorial-hosting-visual-objects-in-a-win32-application.md)。</span><span class="sxs-lookup"><span data-stu-id="22e24-105">Refer to [Tutorial: Hosting Visual Objects in a Win32 Application](tutorial-hosting-visual-objects-in-a-win32-application.md) for more information on how to host visual objects in a Win32 window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22e24-106">範例</span><span class="sxs-lookup"><span data-stu-id="22e24-106">Example</span></span>  
 <span data-ttu-id="22e24-107">下列程式碼會示範如何設定 Win32 視窗的滑鼠事件處理常式，以當做視覺物件的主機容器使用。</span><span class="sxs-lookup"><span data-stu-id="22e24-107">The following code shows how to set up mouse event handlers for a Win32 window that is used as a host container for visual objects.</span></span>  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 <span data-ttu-id="22e24-108">下列範例示範如何設定點擊測試，以回應捕捉特定的滑鼠事件。</span><span class="sxs-lookup"><span data-stu-id="22e24-108">The following example shows how to set up a hit test in response to trapping specific mouse events.</span></span>  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <span data-ttu-id="22e24-109"><xref:System.Windows.Interop.HwndSource> 物件會在 Win32 視窗中呈現 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 內容。</span><span class="sxs-lookup"><span data-stu-id="22e24-109">The <xref:System.Windows.Interop.HwndSource> object presents [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content within a Win32 window.</span></span> <span data-ttu-id="22e24-110"><xref:System.Windows.Interop.HwndSource> 物件的 <xref:System.Windows.Interop.HwndSource.RootVisual%2A> 屬性值，代表視覺化樹狀結構階層中最上層的節點。</span><span class="sxs-lookup"><span data-stu-id="22e24-110">The value of the <xref:System.Windows.Interop.HwndSource.RootVisual%2A> property of the <xref:System.Windows.Interop.HwndSource> object represents the top-most node in the visual tree hierarchy.</span></span>  
  
 <span data-ttu-id="22e24-111">如需使用 Win32 主機容器進行點擊測試物件的完整範例，請參閱[使用 Win32 交互操作進行點擊測試範例](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)。</span><span class="sxs-lookup"><span data-stu-id="22e24-111">For the complete sample on hit testing objects using a Win32 host container, see [Hit Test with Win32 Interoperation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22e24-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22e24-112">See also</span></span>

- <xref:System.Windows.Interop.HwndSource>
- [<span data-ttu-id="22e24-113">視覺分層中的點擊測試</span><span class="sxs-lookup"><span data-stu-id="22e24-113">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
- [<span data-ttu-id="22e24-114">教學課程：在 Win32 應用程式中裝載視覺物件</span><span class="sxs-lookup"><span data-stu-id="22e24-114">Tutorial: Hosting Visual Objects in a Win32 Application</span></span>](tutorial-hosting-visual-objects-in-a-win32-application.md)
