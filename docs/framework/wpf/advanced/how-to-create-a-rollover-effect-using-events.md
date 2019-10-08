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
# <a name="how-to-create-a-rollover-effect-using-events"></a><span data-ttu-id="691a5-102">HOW TO：使用事件建立變換效果</span><span class="sxs-lookup"><span data-stu-id="691a5-102">How to: Create a Rollover Effect Using Events</span></span>
<span data-ttu-id="691a5-103">這個範例示範如何在滑鼠指標進入並離開元素所佔用的區域時，變更專案的色彩。</span><span class="sxs-lookup"><span data-stu-id="691a5-103">This example shows how to change the color of an element as the mouse pointer enters and leaves the area occupied by the element.</span></span>  
  
 <span data-ttu-id="691a5-104">這個範例是由 @no__t 0 檔案和程式碼後置檔案所組成。</span><span class="sxs-lookup"><span data-stu-id="691a5-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="691a5-105">這個範例示範如何使用事件，但達成此相同效果的建議方式是使用樣式中的 @no__t 0。</span><span class="sxs-lookup"><span data-stu-id="691a5-105">This example demonstrates how to use events, but the recommended way to achieve this same effect is to use a <xref:System.Windows.Trigger> in a style.</span></span> <span data-ttu-id="691a5-106">如需詳細資訊，請參閱 [設定樣式和範本](../controls/styling-and-templating.md)。</span><span class="sxs-lookup"><span data-stu-id="691a5-106">For more information, see [Styling and Templating](../controls/styling-and-templating.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="691a5-107">範例</span><span class="sxs-lookup"><span data-stu-id="691a5-107">Example</span></span>  
 <span data-ttu-id="691a5-108">下列 XAML 會建立使用者介面，其中包含 <xref:System.Windows.Controls.TextBlock> 周圍的 <xref:System.Windows.Controls.Border>，並將 <xref:System.Windows.Input.Mouse.MouseEnter> 和 <xref:System.Windows.UIElement.MouseLeave> 事件處理常式附加至 <xref:System.Windows.Controls.Border>。</span><span class="sxs-lookup"><span data-stu-id="691a5-108">The following XAML creates the user interface, which consists of <xref:System.Windows.Controls.Border> around a <xref:System.Windows.Controls.TextBlock>, and attaches the <xref:System.Windows.Input.Mouse.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers to the <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 <span data-ttu-id="691a5-109">下列程式碼後置會建立 <xref:System.Windows.UIElement.MouseEnter> 和 @no__t 1 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="691a5-109">The following code behind creates the <xref:System.Windows.UIElement.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers.</span></span>  <span data-ttu-id="691a5-110">當滑鼠指標進入 <xref:System.Windows.Controls.Border> 時，<xref:System.Windows.Controls.Border> 的背景會變更為紅色。</span><span class="sxs-lookup"><span data-stu-id="691a5-110">When the mouse pointer enters the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed to red.</span></span>  <span data-ttu-id="691a5-111">當滑鼠指標離開 <xref:System.Windows.Controls.Border> 時，<xref:System.Windows.Controls.Border> 的背景會變更回白色。</span><span class="sxs-lookup"><span data-stu-id="691a5-111">When the mouse pointer leaves the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed back to white.</span></span>  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
