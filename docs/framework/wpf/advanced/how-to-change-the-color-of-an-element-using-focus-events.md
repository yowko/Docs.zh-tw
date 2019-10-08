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
ms.openlocfilehash: 5c59dc5f2f8f26fac69933f9ef641a3a51306619
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004831"
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a><span data-ttu-id="c5d36-102">HOW TO：使用焦點事件變更項目的色彩</span><span class="sxs-lookup"><span data-stu-id="c5d36-102">How to: Change the Color of an Element Using Focus Events</span></span>
<span data-ttu-id="c5d36-103">這個範例示範如何在專案取得和失去焦點時，使用 <xref:System.Windows.UIElement.GotFocus> 和 <xref:System.Windows.UIElement.LostFocus> 事件來變更元素的色彩。</span><span class="sxs-lookup"><span data-stu-id="c5d36-103">This example shows how to change the color of an element when it gains and loses focus by using the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events.</span></span>  
  
 <span data-ttu-id="c5d36-104">這個範例是由 @no__t 0 檔案和程式碼後置檔案所組成。</span><span class="sxs-lookup"><span data-stu-id="c5d36-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5d36-105">範例</span><span class="sxs-lookup"><span data-stu-id="c5d36-105">Example</span></span>  
 <span data-ttu-id="c5d36-106">下列 XAML 會建立使用者介面，其中包含兩個 @no__t 0 的物件，並將 <xref:System.Windows.UIElement.GotFocus> 和 @no__t 2 事件的事件處理常式附加至 <xref:System.Windows.Controls.Button> 物件。</span><span class="sxs-lookup"><span data-stu-id="c5d36-106">The following XAML creates the user interface, which consists of two <xref:System.Windows.Controls.Button> objects, and attaches event handlers for the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events to the <xref:System.Windows.Controls.Button> objects.</span></span>  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 <span data-ttu-id="c5d36-107">下列程式碼後置會建立 <xref:System.Windows.UIElement.GotFocus> 和 @no__t 1 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="c5d36-107">The following code behind creates the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> event handlers.</span></span>  <span data-ttu-id="c5d36-108">當 @no__t 0 取得鍵盤焦點時，<xref:System.Windows.Controls.Button> 的 <xref:System.Windows.Controls.Control.Background%2A> 會變更為紅色。</span><span class="sxs-lookup"><span data-stu-id="c5d36-108">When the <xref:System.Windows.Controls.Button> gains keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed to red.</span></span>  <span data-ttu-id="c5d36-109">當 @no__t 0 失去鍵盤焦點時，<xref:System.Windows.Controls.Button> 的 <xref:System.Windows.Controls.Control.Background%2A> 會變更回白色。</span><span class="sxs-lookup"><span data-stu-id="c5d36-109">When the <xref:System.Windows.Controls.Button> loses keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed back to white.</span></span>  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a><span data-ttu-id="c5d36-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5d36-110">See also</span></span>

- [<span data-ttu-id="c5d36-111">輸入概觀</span><span class="sxs-lookup"><span data-stu-id="c5d36-111">Input Overview</span></span>](input-overview.md)
