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
# <a name="how-to-create-a-rollover-effect-using-events"></a><span data-ttu-id="0755d-102">HOW TO：使用事件建立變換效果</span><span class="sxs-lookup"><span data-stu-id="0755d-102">How to: Create a Rollover Effect Using Events</span></span>
<span data-ttu-id="0755d-103">這個範例示範如何在滑鼠指標進入並離開元素所佔用的區域時, 變更專案的色彩。</span><span class="sxs-lookup"><span data-stu-id="0755d-103">This example shows how to change the color of an element as the mouse pointer enters and leaves the area occupied by the element.</span></span>  
  
 <span data-ttu-id="0755d-104">這個範例包含[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案和程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="0755d-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0755d-105">這個範例示範如何使用事件, 但達成此相同效果的建議方式是<xref:System.Windows.Trigger>在樣式中使用。</span><span class="sxs-lookup"><span data-stu-id="0755d-105">This example demonstrates how to use events, but the recommended way to achieve this same effect is to use a <xref:System.Windows.Trigger> in a style.</span></span> <span data-ttu-id="0755d-106">如需詳細資訊，請參閱 [設定樣式和範本](../controls/styling-and-templating.md)。</span><span class="sxs-lookup"><span data-stu-id="0755d-106">For more information, see [Styling and Templating](../controls/styling-and-templating.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0755d-107">範例</span><span class="sxs-lookup"><span data-stu-id="0755d-107">Example</span></span>  
 <span data-ttu-id="0755d-108">[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]下列程式會建立使用者介面, 其中包含的<xref:System.Windows.Controls.Border>周圍<xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.Border>並將<xref:System.Windows.Input.Mouse.MouseEnter>和<xref:System.Windows.UIElement.MouseLeave>事件處理常式附加至。</span><span class="sxs-lookup"><span data-stu-id="0755d-108">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of <xref:System.Windows.Controls.Border> around a <xref:System.Windows.Controls.TextBlock>, and attaches the <xref:System.Windows.Input.Mouse.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers to the <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 <span data-ttu-id="0755d-109">下列程式碼後置會<xref:System.Windows.UIElement.MouseEnter>建立<xref:System.Windows.UIElement.MouseLeave>和事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="0755d-109">The following code behind creates the <xref:System.Windows.UIElement.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers.</span></span>  <span data-ttu-id="0755d-110">當滑鼠指標進入<xref:System.Windows.Controls.Border>時, 的背景<xref:System.Windows.Controls.Border>會變更為紅色。</span><span class="sxs-lookup"><span data-stu-id="0755d-110">When the mouse pointer enters the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed to red.</span></span>  <span data-ttu-id="0755d-111">當滑鼠指標離開<xref:System.Windows.Controls.Border>時, 的背景<xref:System.Windows.Controls.Border>會變更回白色。</span><span class="sxs-lookup"><span data-stu-id="0755d-111">When the mouse pointer leaves the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed back to white.</span></span>  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
