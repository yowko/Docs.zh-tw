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
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a>HOW TO：設定物件隨滑鼠指標移動
這個範例示範如何在滑鼠指標移到螢幕上時，變更物件的維度。  
  
 此範例包含 @no__t 0 的檔案，它會建立 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 和建立事件處理常式的程式碼後置檔案。  
  
## <a name="example"></a>範例  
 下列 XAML 會建立 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，這是由 <xref:System.Windows.Controls.StackPanel> 內的 <xref:System.Windows.Shapes.Ellipse> 所組成，並且會附加 <xref:System.Windows.UIElement.MouseMove> 事件的事件處理常式。  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 下列程式碼後置會建立 <xref:System.Windows.UIElement.MouseMove> 事件處理常式。  當滑鼠指標移動時，會增加並減少 <xref:System.Windows.Shapes.Ellipse> 的高度和寬度。  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a>另請參閱

- [輸入概觀](input-overview.md)
