---
title: "如何：設定物件隨滑鼠指標移動"
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
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7571b437c3879e829a11ed81c22dd12a0a1b592b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a><span data-ttu-id="f950a-102">如何：設定物件隨滑鼠指標移動</span><span class="sxs-lookup"><span data-stu-id="f950a-102">How to: Make an Object Follow the Mouse Pointer</span></span>
<span data-ttu-id="f950a-103">這個範例示範如何在螢幕上移動滑鼠指標時變更維度的物件。</span><span class="sxs-lookup"><span data-stu-id="f950a-103">This example shows how to change the dimensions of an object when the mouse pointer moves on the screen.</span></span>  
  
 <span data-ttu-id="f950a-104">此範例也包含[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案建立[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]和建立事件處理常式的程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="f950a-104">The example includes an [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file that creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] and a code-behind file that creates the event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f950a-105">範例</span><span class="sxs-lookup"><span data-stu-id="f950a-105">Example</span></span>  
 <span data-ttu-id="f950a-106">下列[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]建立[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，其中包含的<xref:System.Windows.Shapes.Ellipse>內<xref:System.Windows.Controls.StackPanel>，並將附加的事件處理常式<xref:System.Windows.UIElement.MouseMove>事件。</span><span class="sxs-lookup"><span data-stu-id="f950a-106">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], which consists of an <xref:System.Windows.Shapes.Ellipse> inside of a <xref:System.Windows.Controls.StackPanel>, and attaches the event handler for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 <span data-ttu-id="f950a-107">下列程式碼後置建立<xref:System.Windows.UIElement.MouseMove>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="f950a-107">The following code behind creates the <xref:System.Windows.UIElement.MouseMove> event handler.</span></span>  <span data-ttu-id="f950a-108">當滑鼠指標移動，高度和寬度<xref:System.Windows.Shapes.Ellipse>來增加或減少。</span><span class="sxs-lookup"><span data-stu-id="f950a-108">When the mouse pointer moves, the height and the width of the <xref:System.Windows.Shapes.Ellipse> are increased and decreased.</span></span>  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a><span data-ttu-id="f950a-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="f950a-109">See Also</span></span>  
 [<span data-ttu-id="f950a-110">輸入概觀</span><span class="sxs-lookup"><span data-stu-id="f950a-110">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)
