---
title: 作法：定義停駐之 ToolStrip 控制項的疊置順序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], specifying z-order
- z-order
ms.assetid: 8b595429-ba9f-46af-9c55-3d5cc53f7fff
ms.openlocfilehash: 514c9dd1c91adcadf6f5d383ba734886dec3151d
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591899"
---
# <a name="how-to-define-z-ordering-of-docked-toolstrip-controls"></a><span data-ttu-id="8987f-102">作法：定義停駐之 ToolStrip 控制項的疊置順序</span><span class="sxs-lookup"><span data-stu-id="8987f-102">How to: Define Z-Ordering of Docked ToolStrip Controls</span></span>
<span data-ttu-id="8987f-103">若要使用停駐將 <xref:System.Windows.Forms.ToolStrip> 控制項正確地定位，您必須依照表單的疊置順序，將控制項正確地定位。</span><span class="sxs-lookup"><span data-stu-id="8987f-103">To position a <xref:System.Windows.Forms.ToolStrip> control correctly with docking, you must position the control correctly in the form's z-order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8987f-104">範例</span><span class="sxs-lookup"><span data-stu-id="8987f-104">Example</span></span>  
 <span data-ttu-id="8987f-105">下列程式碼範例示範如何指定疊置順序，以排列 <xref:System.Windows.Forms.ToolStrip> 控制項和停駐的 <xref:System.Windows.Forms.MenuStrip> 控制項。</span><span class="sxs-lookup"><span data-stu-id="8987f-105">The following code example demonstrates how to arrange a <xref:System.Windows.Forms.ToolStrip> control and a docked <xref:System.Windows.Forms.MenuStrip> control by specifying the z-order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#21)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#21)]  
  
 <span data-ttu-id="8987f-106">疊置順序取決於順序<xref:System.Windows.Forms.ToolStrip>和 <xref:System.Windows.Forms.MenuStrip></span><span class="sxs-lookup"><span data-stu-id="8987f-106">The z-order is determined by the order in which the <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.MenuStrip></span></span>  
  
 <span data-ttu-id="8987f-107">控制項會加入至表單的<xref:System.Windows.Forms.Control.Controls%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="8987f-107">controls are added to the form's <xref:System.Windows.Forms.Control.Controls%2A> collection.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#23)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#23)]  
  
 <span data-ttu-id="8987f-108">將對 <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> 方法的這些呼叫順序反轉，並檢視配置上的效果。</span><span class="sxs-lookup"><span data-stu-id="8987f-108">Reverse the order of these calls to the <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> method and view the effect on the layout.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8987f-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="8987f-109">Compiling the Code</span></span>  
 <span data-ttu-id="8987f-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="8987f-110">This example requires:</span></span>  
  
- <span data-ttu-id="8987f-111">System.Design、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="8987f-111">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8987f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8987f-112">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.ControlCollection.Add%2A>
- <xref:System.Windows.Forms.Control.Controls%2A>
- <xref:System.Windows.Forms.Control.Dock%2A>
- [<span data-ttu-id="8987f-113">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="8987f-113">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
