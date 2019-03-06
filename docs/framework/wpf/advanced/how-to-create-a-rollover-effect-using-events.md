---
title: HOW TO：使用事件建立變化效果
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: 87740a215136863199d962a2704cf691f27fc3bc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369093"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>HOW TO：使用事件建立變化效果
此範例示範如何變更項目的色彩，當滑鼠指標進入及離開項目所佔用的區域。  
  
 此範例中組成[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案和程式碼後置檔案。  
  
> [!NOTE]
>  此範例示範如何使用事件，但若要達成此相同的效果的建議的方式是使用<xref:System.Windows.Trigger>樣式。 如需詳細資訊，請參閱 [設定樣式和範本](../controls/styling-and-templating.md)。  
  
## <a name="example"></a>範例  
 下列[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]建立使用者介面，其中包含<xref:System.Windows.Controls.Border>周圍<xref:System.Windows.Controls.TextBlock>，並附加<xref:System.Windows.Input.Mouse.MouseEnter>並<xref:System.Windows.UIElement.MouseLeave>事件處理常式<xref:System.Windows.Controls.Border>。  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 建立下列的程式碼後置<xref:System.Windows.UIElement.MouseEnter>和<xref:System.Windows.UIElement.MouseLeave>事件處理常式。  當滑鼠指標進入<xref:System.Windows.Controls.Border>，背景<xref:System.Windows.Controls.Border>會變成紅色。  當滑鼠指標離開<xref:System.Windows.Controls.Border>，背景<xref:System.Windows.Controls.Border>變更回白色。  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
