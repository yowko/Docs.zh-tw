---
title: 如何：設定物件隨滑鼠指標移動
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
ms.openlocfilehash: 860b42f4dc068bc3063001e25e8b012c50b59213
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543868"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a>如何：設定物件隨滑鼠指標移動
這個範例示範如何在螢幕上移動滑鼠指標時變更維度的物件。  
  
 此範例也包含[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案建立[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]和建立事件處理常式的程式碼後置檔案。  
  
## <a name="example"></a>範例  
 下列[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]建立[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，其中包含的<xref:System.Windows.Shapes.Ellipse>內<xref:System.Windows.Controls.StackPanel>，並將附加的事件處理常式<xref:System.Windows.UIElement.MouseMove>事件。  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 下列程式碼後置建立<xref:System.Windows.UIElement.MouseMove>事件處理常式。  當滑鼠指標移動，高度和寬度<xref:System.Windows.Shapes.Ellipse>來增加或減少。  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a>另請參閱  
 [輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)
