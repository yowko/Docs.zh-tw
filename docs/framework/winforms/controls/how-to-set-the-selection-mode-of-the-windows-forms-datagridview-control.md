---
title: "如何：設定 Windows Form DataGridView 控制項的選取模式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
- data grids [Windows Forms], selection mode
ms.assetid: 2f241643-7f82-4583-8757-03494f63b465
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb0f9d0cff7be2dd1243916e6505aab9cc63dd0d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="b7d49-102">如何：設定 Windows Form DataGridView 控制項的選取模式</span><span class="sxs-lookup"><span data-stu-id="b7d49-102">How to: Set the Selection Mode of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b7d49-103">下列程式碼範例示範如何設定<xref:System.Windows.Forms.DataGridView>控制項，以便自動任意處按一下資料列內選取整個資料列，並因此選取一次該只有一個資料列。</span><span class="sxs-lookup"><span data-stu-id="b7d49-103">The following code example demonstrates how to configure a <xref:System.Windows.Forms.DataGridView> control so that clicking anywhere within a row automatically selects the entire row, and so that only one row at a time can be selected.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7d49-104">範例</span><span class="sxs-lookup"><span data-stu-id="b7d49-104">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#065](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#065)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#065](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#065)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b7d49-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b7d49-105">Compiling the Code</span></span>  
 <span data-ttu-id="b7d49-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="b7d49-106">This example requires:</span></span>  
  
-   <span data-ttu-id="b7d49-107">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="b7d49-107">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="b7d49-108"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="b7d49-108">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7d49-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7d49-109">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>  
 <xref:System.Windows.Forms.DataGridViewSelectionMode>  
 [<span data-ttu-id="b7d49-110">選取範圍和剪貼簿與 Windows Forms DataGridView 控制項搭配使用</span><span class="sxs-lookup"><span data-stu-id="b7d49-110">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="b7d49-111">Windows Forms DataGridView 控制項中的選取模式</span><span class="sxs-lookup"><span data-stu-id="b7d49-111">Selection Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)
