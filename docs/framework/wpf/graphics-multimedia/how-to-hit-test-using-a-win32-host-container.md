---
title: "操作說明：使用 Win32 裝載容器進行點擊測試"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 142c2faa01c32ac6602e80eaef18779f93154aea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a>操作說明：使用 Win32 裝載容器進行點擊測試
您可以建立視覺物件內[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]藉由提供視覺物件主機視窗容器的視窗。 若要針對包含的視覺物件提供事件處理，您必須處理傳遞至裝載視窗容器之訊息篩選迴圈的訊息。 是指[教學課程： 在 Win32 應用程式中裝載 Visual 物件](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)如需有關如何在裝載中的視覺物件[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]視窗。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何設定滑鼠事件處理常式，如[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]作為視覺物件裝載容器的視窗。  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 下列範例會示範如何設定以回應特定的滑鼠事件的設陷的點擊測試。  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <xref:System.Windows.Interop.HwndSource>物件代表[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]內容內[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]視窗。 值<xref:System.Windows.Interop.HwndSource.RootVisual%2A>屬性<xref:System.Windows.Interop.HwndSource>物件代表的視覺化樹狀結構階層架構中的最上層節點。  
  
 物件上的點擊測試的完整範例，使用 Win32 裝載容器，請參閱[點擊測試的互通性的 Win32 範例](http://go.microsoft.com/fwlink/?LinkID=159995)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Interop.HwndSource>  
 [視覺分層中的點擊測試](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [教學課程：在 Win32 應用程式中裝載視覺物件](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)
