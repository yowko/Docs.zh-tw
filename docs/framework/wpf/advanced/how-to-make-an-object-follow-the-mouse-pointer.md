---
title: HOW TO：設定物件隨滑鼠指標移動
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
ms.openlocfilehash: b9b13b4eec3e42744ba2be6031ec841fb5f215e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051594"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a><span data-ttu-id="6bc54-102">HOW TO：設定物件隨滑鼠指標移動</span><span class="sxs-lookup"><span data-stu-id="6bc54-102">How to: Make an Object Follow the Mouse Pointer</span></span>
<span data-ttu-id="6bc54-103">此範例示範如何變更維度的物件，當滑鼠指標在螢幕上移動時。</span><span class="sxs-lookup"><span data-stu-id="6bc54-103">This example shows how to change the dimensions of an object when the mouse pointer moves on the screen.</span></span>  
  
 <span data-ttu-id="6bc54-104">此範例也包含[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]建立的檔案[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]以及建立事件處理常式的程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="6bc54-104">The example includes an [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file that creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] and a code-behind file that creates the event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bc54-105">範例</span><span class="sxs-lookup"><span data-stu-id="6bc54-105">Example</span></span>  
 <span data-ttu-id="6bc54-106">下列[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]會建立[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，後者包含<xref:System.Windows.Shapes.Ellipse>內<xref:System.Windows.Controls.StackPanel>，並將附加事件處理常式，如<xref:System.Windows.UIElement.MouseMove>事件。</span><span class="sxs-lookup"><span data-stu-id="6bc54-106">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], which consists of an <xref:System.Windows.Shapes.Ellipse> inside of a <xref:System.Windows.Controls.StackPanel>, and attaches the event handler for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 <span data-ttu-id="6bc54-107">下列程式碼後置建立<xref:System.Windows.UIElement.MouseMove>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="6bc54-107">The following code behind creates the <xref:System.Windows.UIElement.MouseMove> event handler.</span></span>  <span data-ttu-id="6bc54-108">當滑鼠指標移動，高度和寬度<xref:System.Windows.Shapes.Ellipse>增加和減少。</span><span class="sxs-lookup"><span data-stu-id="6bc54-108">When the mouse pointer moves, the height and the width of the <xref:System.Windows.Shapes.Ellipse> are increased and decreased.</span></span>  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a><span data-ttu-id="6bc54-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bc54-109">See also</span></span>

- [<span data-ttu-id="6bc54-110">輸入概觀</span><span class="sxs-lookup"><span data-stu-id="6bc54-110">Input Overview</span></span>](input-overview.md)
