---
title: HOW TO：設定 Windows Forms DataGridView 控制項的選取模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
- data grids [Windows Forms], selection mode
ms.assetid: 2f241643-7f82-4583-8757-03494f63b465
ms.openlocfilehash: 65fb7360d45baea4fff20d06316d3955f0064207
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539736"
---
# <a name="how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="b2cf5-102">HOW TO：設定 Windows Forms DataGridView 控制項的選取模式</span><span class="sxs-lookup"><span data-stu-id="b2cf5-102">How to: Set the Selection Mode of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b2cf5-103">下列程式碼範例示範如何設定<xref:System.Windows.Forms.DataGridView>控制項，以便自動任意處按一下資料列中選取整個資料列，並因此可以選取一次該只有一個資料列。</span><span class="sxs-lookup"><span data-stu-id="b2cf5-103">The following code example demonstrates how to configure a <xref:System.Windows.Forms.DataGridView> control so that clicking anywhere within a row automatically selects the entire row, and so that only one row at a time can be selected.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2cf5-104">範例</span><span class="sxs-lookup"><span data-stu-id="b2cf5-104">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#065](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#065)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#065](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#065)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b2cf5-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b2cf5-105">Compiling the Code</span></span>  
 <span data-ttu-id="b2cf5-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="b2cf5-106">This example requires:</span></span>  
  
-   <span data-ttu-id="b2cf5-107">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="b2cf5-107">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="b2cf5-108"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="b2cf5-108">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2cf5-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2cf5-109">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [<span data-ttu-id="b2cf5-110">選取範圍和剪貼簿與 Windows Forms DataGridView 控制項搭配使用</span><span class="sxs-lookup"><span data-stu-id="b2cf5-110">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b2cf5-111">Windows Forms DataGridView 控制項中的選取模式</span><span class="sxs-lookup"><span data-stu-id="b2cf5-111">Selection Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)
