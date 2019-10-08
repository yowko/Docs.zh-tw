---
title: HOW TO：使用事件建立變換效果
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: 806056397200fa5c567e83227499ba721544f523
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005187"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>HOW TO：使用事件建立變換效果
這個範例示範如何在滑鼠指標進入並離開元素所佔用的區域時，變更專案的色彩。  
  
 這個範例是由 @no__t 0 檔案和程式碼後置檔案所組成。  
  
> [!NOTE]
> 這個範例示範如何使用事件，但達成此相同效果的建議方式是使用樣式中的 @no__t 0。 如需詳細資訊，請參閱 [設定樣式和範本](../controls/styling-and-templating.md)。  
  
## <a name="example"></a>範例  
 下列 XAML 會建立使用者介面，其中包含 <xref:System.Windows.Controls.TextBlock> 周圍的 <xref:System.Windows.Controls.Border>，並將 <xref:System.Windows.Input.Mouse.MouseEnter> 和 <xref:System.Windows.UIElement.MouseLeave> 事件處理常式附加至 <xref:System.Windows.Controls.Border>。  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 下列程式碼後置會建立 <xref:System.Windows.UIElement.MouseEnter> 和 @no__t 1 事件處理常式。  當滑鼠指標進入 <xref:System.Windows.Controls.Border> 時，<xref:System.Windows.Controls.Border> 的背景會變更為紅色。  當滑鼠指標離開 <xref:System.Windows.Controls.Border> 時，<xref:System.Windows.Controls.Border> 的背景會變更回白色。  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
