---
title: 如何：使用事件建立變化效果
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: d458d87586614093b35fcd73969dea04fe620351
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543006"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>如何：使用事件建立變化效果
這個範例示範如何變更項目的色彩，當滑鼠指標進入及離開項目所佔據的區域。  
  
 這個範例包含[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案和程式碼後置檔案。  
  
> [!NOTE]
>  此範例示範如何使用事件，但若要達成這個相同的效果的建議的方式是使用<xref:System.Windows.Trigger>樣式。 如需詳細資訊，請參閱 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
## <a name="example"></a>範例  
 下列[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]建立使用者介面，其中包含<xref:System.Windows.Controls.Border>周圍<xref:System.Windows.Controls.TextBlock>，並附加<xref:System.Windows.Input.Mouse.MouseEnter>和<xref:System.Windows.UIElement.MouseLeave>事件處理常式， <xref:System.Windows.Controls.Border>。  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 下列程式碼後置建立<xref:System.Windows.UIElement.MouseEnter>和<xref:System.Windows.UIElement.MouseLeave>事件處理常式。  當滑鼠指標進入<xref:System.Windows.Controls.Border>，背景的<xref:System.Windows.Controls.Border>會變成紅色。  當滑鼠指標離開<xref:System.Windows.Controls.Border>，背景的<xref:System.Windows.Controls.Border>變更回為白色。  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
