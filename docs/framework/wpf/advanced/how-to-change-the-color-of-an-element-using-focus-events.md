---
title: HOW TO：使用焦點事件變更項目的色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus events [WPF], changing element color for
- colors of elements [WPF], changing
- elements [WPF], changing color of
ms.assetid: 7e246802-3625-47a7-ae9d-c8a2a40fd040
ms.openlocfilehash: 744963cc543110121a777e1d4c3cdcb3cec40d9e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776866"
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a><span data-ttu-id="00aea-102">HOW TO：使用焦點事件變更項目的色彩</span><span class="sxs-lookup"><span data-stu-id="00aea-102">How to: Change the Color of an Element Using Focus Events</span></span>
<span data-ttu-id="00aea-103">此範例示範如何取得及使用失去焦點時，變更項目的色彩<xref:System.Windows.UIElement.GotFocus>和<xref:System.Windows.UIElement.LostFocus>事件。</span><span class="sxs-lookup"><span data-stu-id="00aea-103">This example shows how to change the color of an element when it gains and loses focus by using the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events.</span></span>  
  
 <span data-ttu-id="00aea-104">此範例中組成[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案和程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="00aea-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00aea-105">範例</span><span class="sxs-lookup"><span data-stu-id="00aea-105">Example</span></span>  
 <span data-ttu-id="00aea-106">下列[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]建立使用者介面，其中包含兩個<xref:System.Windows.Controls.Button>物件，並將附加事件處理常式<xref:System.Windows.UIElement.GotFocus>並<xref:System.Windows.UIElement.LostFocus>事件<xref:System.Windows.Controls.Button>物件。</span><span class="sxs-lookup"><span data-stu-id="00aea-106">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of two <xref:System.Windows.Controls.Button> objects, and attaches event handlers for the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events to the <xref:System.Windows.Controls.Button> objects.</span></span>  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 <span data-ttu-id="00aea-107">建立下列的程式碼後置<xref:System.Windows.UIElement.GotFocus>和<xref:System.Windows.UIElement.LostFocus>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="00aea-107">The following code behind creates the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> event handlers.</span></span>  <span data-ttu-id="00aea-108">當<xref:System.Windows.Controls.Button>提升鍵盤焦點<xref:System.Windows.Controls.Control.Background%2A>的<xref:System.Windows.Controls.Button>會變成紅色。</span><span class="sxs-lookup"><span data-stu-id="00aea-108">When the <xref:System.Windows.Controls.Button> gains keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed to red.</span></span>  <span data-ttu-id="00aea-109">當<xref:System.Windows.Controls.Button>失去鍵盤焦點<xref:System.Windows.Controls.Control.Background%2A>的<xref:System.Windows.Controls.Button>變更回白色。</span><span class="sxs-lookup"><span data-stu-id="00aea-109">When the <xref:System.Windows.Controls.Button> loses keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed back to white.</span></span>  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a><span data-ttu-id="00aea-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00aea-110">See also</span></span>

- [<span data-ttu-id="00aea-111">輸入概觀</span><span class="sxs-lookup"><span data-stu-id="00aea-111">Input Overview</span></span>](input-overview.md)
