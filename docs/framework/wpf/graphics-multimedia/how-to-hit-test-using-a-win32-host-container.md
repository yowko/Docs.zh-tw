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
ms.openlocfilehash: bb175e0f8aeb126b7f7fa85d5af1c4afcf5bea61
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46008278"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a><span data-ttu-id="82a1a-102">操作說明：使用 Win32 裝載容器進行點擊測試</span><span class="sxs-lookup"><span data-stu-id="82a1a-102">How to: Hit Test Using a Win32 Host Container</span></span>
<span data-ttu-id="82a1a-103">您可以建立視覺物件內[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]藉由提供主機視窗容器為視覺物件的視窗。</span><span class="sxs-lookup"><span data-stu-id="82a1a-103">You can create visual objects within a [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] window by providing a host window container for the visual objects.</span></span> <span data-ttu-id="82a1a-104">若要針對包含的視覺物件提供事件處理，您必須處理傳遞至裝載視窗容器之訊息篩選迴圈的訊息。</span><span class="sxs-lookup"><span data-stu-id="82a1a-104">To provide event handling for the contained visual objects you process the messages passed to the host window container’s message filter loop.</span></span> <span data-ttu-id="82a1a-105">請參閱[教學課程： 在 Win32 應用程式中裝載視覺物件](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)如需有關如何裝載中的視覺物件[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗。</span><span class="sxs-lookup"><span data-stu-id="82a1a-105">Refer to [Tutorial: Hosting Visual Objects in a Win32 Application](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md) for more information on how to host visual objects in a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82a1a-106">範例</span><span class="sxs-lookup"><span data-stu-id="82a1a-106">Example</span></span>  
 <span data-ttu-id="82a1a-107">下列程式碼示範如何設定滑鼠事件處理常式，如[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]可做為視覺物件的主應用程式容器的視窗。</span><span class="sxs-lookup"><span data-stu-id="82a1a-107">The following code shows how to set up mouse event handlers for a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] window that is used as a host container for visual objects.</span></span>  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 <span data-ttu-id="82a1a-108">下列範例示範如何設定點擊測試，以回應捕捉的特定滑鼠事件。</span><span class="sxs-lookup"><span data-stu-id="82a1a-108">The following example shows how to set up a hit test in response to trapping specific mouse events.</span></span>  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <span data-ttu-id="82a1a-109"><xref:System.Windows.Interop.HwndSource>物件呈現[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]內容[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]視窗。</span><span class="sxs-lookup"><span data-stu-id="82a1a-109">The <xref:System.Windows.Interop.HwndSource> object presents [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content within a [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] window.</span></span> <span data-ttu-id="82a1a-110">值<xref:System.Windows.Interop.HwndSource.RootVisual%2A>屬性<xref:System.Windows.Interop.HwndSource>物件都代表在視覺化樹狀結構階層中的最上層節點。</span><span class="sxs-lookup"><span data-stu-id="82a1a-110">The value of the <xref:System.Windows.Interop.HwndSource.RootVisual%2A> property of the <xref:System.Windows.Interop.HwndSource> object represents the top-most node in the visual tree hierarchy.</span></span>  
  
 <span data-ttu-id="82a1a-111">如需點擊測試的完整範例物件，使用 Win32 裝載容器，請參閱 < [Win32 交互操作範例使用點擊測試](https://go.microsoft.com/fwlink/?LinkID=159995)。</span><span class="sxs-lookup"><span data-stu-id="82a1a-111">For the complete sample on hit testing objects using a Win32 host container, see [Hit Test with Win32 Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=159995).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82a1a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82a1a-112">See Also</span></span>  
 <xref:System.Windows.Interop.HwndSource>  
 [<span data-ttu-id="82a1a-113">視覺分層中的點擊測試</span><span class="sxs-lookup"><span data-stu-id="82a1a-113">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [<span data-ttu-id="82a1a-114">教學課程：在 Win32 應用程式中裝載視覺物件</span><span class="sxs-lookup"><span data-stu-id="82a1a-114">Tutorial: Hosting Visual Objects in a Win32 Application</span></span>](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)
