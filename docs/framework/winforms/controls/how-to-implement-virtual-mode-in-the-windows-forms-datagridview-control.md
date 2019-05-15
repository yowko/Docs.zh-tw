---
title: 作法：在 Windows Forms DataGridView 控制項中實作虛擬模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode
- DataGridView control [Windows Forms], large data sets
ms.assetid: 98236267-f08e-4918-bcf9-77acf050a3ca
ms.openlocfilehash: 064b58b64e0a9f55e3ef7d15b4962cfec514eff3
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592402"
---
# <a name="how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="32e1c-102">作法：在 Windows Forms DataGridView 控制項中實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="32e1c-102">How to: Implement Virtual Mode in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="32e1c-103">下列程式碼範例示範如何使用 <xref:System.Windows.Forms.DataGridView> 控制項 (其 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性設定為 `true`) 來管理大量的資料。</span><span class="sxs-lookup"><span data-stu-id="32e1c-103">The following code example demonstrates how to manage large sets of data using a <xref:System.Windows.Forms.DataGridView> control with its <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property set to `true`.</span></span>  
  
 <span data-ttu-id="32e1c-104">如需這個程式碼範例的完整說明，請參閱[逐步解說：實作虛擬模式中的 Windows Form DataGridView 控制項](implementing-virtual-mode-wf-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="32e1c-104">For a complete explanation of this code example, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="32e1c-105">範例</span><span class="sxs-lookup"><span data-stu-id="32e1c-105">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#000](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#000)]
 [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="32e1c-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="32e1c-106">Compiling the Code</span></span>  
 <span data-ttu-id="32e1c-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="32e1c-107">This example requires:</span></span>  
  
- <span data-ttu-id="32e1c-108">System 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="32e1c-108">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32e1c-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32e1c-109">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [<span data-ttu-id="32e1c-110">逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="32e1c-110">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-wf-datagridview-control.md)
- [<span data-ttu-id="32e1c-111">Windows Forms DataGridView 控制項中的效能微調</span><span class="sxs-lookup"><span data-stu-id="32e1c-111">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="32e1c-112">Windows Forms DataGridView 控制項中的虛擬模式</span><span class="sxs-lookup"><span data-stu-id="32e1c-112">Virtual Mode in the Windows Forms DataGridView Control</span></span>](virtual-mode-in-the-windows-forms-datagridview-control.md)
