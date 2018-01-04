---
title: "如何：使用焦點事件變更項目的色彩"
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
- focus events [WPF], changing element color for
- colors of elements [WPF], changing
- elements [WPF], changing color of
ms.assetid: 7e246802-3625-47a7-ae9d-c8a2a40fd040
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8b0e3f1b0a3287be89aba6e26f0621525c458a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a><span data-ttu-id="5d476-102">如何：使用焦點事件變更項目的色彩</span><span class="sxs-lookup"><span data-stu-id="5d476-102">How to: Change the Color of an Element Using Focus Events</span></span>
<span data-ttu-id="5d476-103">這個範例示範如何取得及使用失去焦點時，變更項目的色彩<xref:System.Windows.UIElement.GotFocus>和<xref:System.Windows.UIElement.LostFocus>事件。</span><span class="sxs-lookup"><span data-stu-id="5d476-103">This example shows how to change the color of an element when it gains and loses focus by using the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events.</span></span>  
  
 <span data-ttu-id="5d476-104">這個範例包含[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案和程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="5d476-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d476-105">範例</span><span class="sxs-lookup"><span data-stu-id="5d476-105">Example</span></span>  
 <span data-ttu-id="5d476-106">下列[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]建立使用者介面，其中包含兩個<xref:System.Windows.Controls.Button>物件，並將事件處理常式附加<xref:System.Windows.UIElement.GotFocus>和<xref:System.Windows.UIElement.LostFocus>事件<xref:System.Windows.Controls.Button>物件。</span><span class="sxs-lookup"><span data-stu-id="5d476-106">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of two <xref:System.Windows.Controls.Button> objects, and attaches event handlers for the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events to the <xref:System.Windows.Controls.Button> objects.</span></span>  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 <span data-ttu-id="5d476-107">下列程式碼後置建立<xref:System.Windows.UIElement.GotFocus>和<xref:System.Windows.UIElement.LostFocus>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5d476-107">The following code behind creates the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> event handlers.</span></span>  <span data-ttu-id="5d476-108">當<xref:System.Windows.Controls.Button>提升鍵盤焦點，<xref:System.Windows.Controls.Control.Background%2A>的<xref:System.Windows.Controls.Button>會變成紅色。</span><span class="sxs-lookup"><span data-stu-id="5d476-108">When the <xref:System.Windows.Controls.Button> gains keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed to red.</span></span>  <span data-ttu-id="5d476-109">當<xref:System.Windows.Controls.Button>失去鍵盤焦點、<xref:System.Windows.Controls.Control.Background%2A>的<xref:System.Windows.Controls.Button>變更回為白色。</span><span class="sxs-lookup"><span data-stu-id="5d476-109">When the <xref:System.Windows.Controls.Button> loses keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed back to white.</span></span>  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a><span data-ttu-id="5d476-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="5d476-110">See Also</span></span>  
 [<span data-ttu-id="5d476-111">輸入概觀</span><span class="sxs-lookup"><span data-stu-id="5d476-111">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)
