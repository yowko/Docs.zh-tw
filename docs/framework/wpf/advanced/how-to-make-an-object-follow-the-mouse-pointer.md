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
ms.openlocfilehash: 4ef3028b6c71b94a593d168ad6570c4aec12b86b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005061"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a><span data-ttu-id="98c10-102">HOW TO：設定物件隨滑鼠指標移動</span><span class="sxs-lookup"><span data-stu-id="98c10-102">How to: Make an Object Follow the Mouse Pointer</span></span>
<span data-ttu-id="98c10-103">這個範例示範如何在滑鼠指標移到螢幕上時，變更物件的維度。</span><span class="sxs-lookup"><span data-stu-id="98c10-103">This example shows how to change the dimensions of an object when the mouse pointer moves on the screen.</span></span>  
  
 <span data-ttu-id="98c10-104">此範例包含 @no__t 0 的檔案，它會建立 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 和建立事件處理常式的程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="98c10-104">The example includes an [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file that creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] and a code-behind file that creates the event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98c10-105">範例</span><span class="sxs-lookup"><span data-stu-id="98c10-105">Example</span></span>  
 <span data-ttu-id="98c10-106">下列 XAML 會建立 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，這是由 <xref:System.Windows.Controls.StackPanel> 內的 <xref:System.Windows.Shapes.Ellipse> 所組成，並且會附加 <xref:System.Windows.UIElement.MouseMove> 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="98c10-106">The following XAML creates the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], which consists of an <xref:System.Windows.Shapes.Ellipse> inside of a <xref:System.Windows.Controls.StackPanel>, and attaches the event handler for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 <span data-ttu-id="98c10-107">下列程式碼後置會建立 <xref:System.Windows.UIElement.MouseMove> 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="98c10-107">The following code behind creates the <xref:System.Windows.UIElement.MouseMove> event handler.</span></span>  <span data-ttu-id="98c10-108">當滑鼠指標移動時，會增加並減少 <xref:System.Windows.Shapes.Ellipse> 的高度和寬度。</span><span class="sxs-lookup"><span data-stu-id="98c10-108">When the mouse pointer moves, the height and the width of the <xref:System.Windows.Shapes.Ellipse> are increased and decreased.</span></span>  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a><span data-ttu-id="98c10-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98c10-109">See also</span></span>

- [<span data-ttu-id="98c10-110">輸入概觀</span><span class="sxs-lookup"><span data-stu-id="98c10-110">Input Overview</span></span>](input-overview.md)
