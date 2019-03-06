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
ms.openlocfilehash: 6b86cadba19e82c487be88bcfb08edb51f93c540
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358297"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a>HOW TO：設定物件隨滑鼠指標移動
此範例示範如何變更維度的物件，當滑鼠指標在螢幕上移動時。  
  
 此範例也包含[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]建立的檔案[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]以及建立事件處理常式的程式碼後置檔案。  
  
## <a name="example"></a>範例  
 下列[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]會建立[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，後者包含<xref:System.Windows.Shapes.Ellipse>內<xref:System.Windows.Controls.StackPanel>，並將附加事件處理常式，如<xref:System.Windows.UIElement.MouseMove>事件。  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 下列程式碼後置建立<xref:System.Windows.UIElement.MouseMove>事件處理常式。  當滑鼠指標移動，高度和寬度<xref:System.Windows.Shapes.Ellipse>增加和減少。  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a>另請參閱
- [輸入概觀](input-overview.md)
