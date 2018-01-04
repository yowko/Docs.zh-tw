---
title: "如何：使用事件建立變化效果"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fc65c9342cc86d4ceebd65e91c05cc1bea464e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-rollover-effect-using-events"></a><span data-ttu-id="facff-102">如何：使用事件建立變化效果</span><span class="sxs-lookup"><span data-stu-id="facff-102">How to: Create a Rollover Effect Using Events</span></span>
<span data-ttu-id="facff-103">這個範例示範如何變更項目的色彩，當滑鼠指標進入及離開項目所佔據的區域。</span><span class="sxs-lookup"><span data-stu-id="facff-103">This example shows how to change the color of an element as the mouse pointer enters and leaves the area occupied by the element.</span></span>  
  
 <span data-ttu-id="facff-104">這個範例包含[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案和程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="facff-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="facff-105">此範例示範如何使用事件，但若要達成這個相同的效果的建議的方式是使用<xref:System.Windows.Trigger>樣式。</span><span class="sxs-lookup"><span data-stu-id="facff-105">This example demonstrates how to use events, but the recommended way to achieve this same effect is to use a <xref:System.Windows.Trigger> in a style.</span></span> <span data-ttu-id="facff-106">如需詳細資訊，請參閱 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。</span><span class="sxs-lookup"><span data-stu-id="facff-106">For more information, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="facff-107">範例</span><span class="sxs-lookup"><span data-stu-id="facff-107">Example</span></span>  
 <span data-ttu-id="facff-108">下列[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]建立使用者介面，其中包含<xref:System.Windows.Controls.Border>周圍<xref:System.Windows.Controls.TextBlock>，並附加<xref:System.Windows.Input.Mouse.MouseEnter>和<xref:System.Windows.UIElement.MouseLeave>事件處理常式， <xref:System.Windows.Controls.Border>。</span><span class="sxs-lookup"><span data-stu-id="facff-108">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of <xref:System.Windows.Controls.Border> around a <xref:System.Windows.Controls.TextBlock>, and attaches the <xref:System.Windows.Input.Mouse.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers to the <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 <span data-ttu-id="facff-109">下列程式碼後置建立<xref:System.Windows.UIElement.MouseEnter>和<xref:System.Windows.UIElement.MouseLeave>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="facff-109">The following code behind creates the <xref:System.Windows.UIElement.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers.</span></span>  <span data-ttu-id="facff-110">當滑鼠指標進入<xref:System.Windows.Controls.Border>，背景的<xref:System.Windows.Controls.Border>會變成紅色。</span><span class="sxs-lookup"><span data-stu-id="facff-110">When the mouse pointer enters the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed to red.</span></span>  <span data-ttu-id="facff-111">當滑鼠指標離開<xref:System.Windows.Controls.Border>，背景的<xref:System.Windows.Controls.Border>變更回為白色。</span><span class="sxs-lookup"><span data-stu-id="facff-111">When the mouse pointer leaves the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed back to white.</span></span>  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
