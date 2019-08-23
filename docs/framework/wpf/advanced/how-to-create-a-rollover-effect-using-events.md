---
title: 作法：使用事件建立變換效果
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: 3996a3b9bb976dd5f2e5b675de3894bbaba7d9d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960380"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>HOW TO：使用事件建立變換效果
這個範例示範如何在滑鼠指標進入並離開元素所佔用的區域時, 變更專案的色彩。  
  
 這個範例包含[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案和程式碼後置檔案。  
  
> [!NOTE]
> 這個範例示範如何使用事件, 但達成此相同效果的建議方式是<xref:System.Windows.Trigger>在樣式中使用。 如需詳細資訊，請參閱 [設定樣式和範本](../controls/styling-and-templating.md)。  
  
## <a name="example"></a>範例  
 [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]下列程式會建立使用者介面, 其中包含的<xref:System.Windows.Controls.Border>周圍<xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.Border>並將<xref:System.Windows.Input.Mouse.MouseEnter>和<xref:System.Windows.UIElement.MouseLeave>事件處理常式附加至。  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 下列程式碼後置會<xref:System.Windows.UIElement.MouseEnter>建立<xref:System.Windows.UIElement.MouseLeave>和事件處理常式。  當滑鼠指標進入<xref:System.Windows.Controls.Border>時, 的背景<xref:System.Windows.Controls.Border>會變更為紅色。  當滑鼠指標離開<xref:System.Windows.Controls.Border>時, 的背景<xref:System.Windows.Controls.Border>會變更回白色。  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
