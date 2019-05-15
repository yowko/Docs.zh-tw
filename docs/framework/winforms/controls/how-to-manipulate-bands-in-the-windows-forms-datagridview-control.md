---
title: 作法：管理 Windows Forms DataGridView 控制項中的寬線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], manipulating bands
- bands [Windows Forms], manipulating in Windows Forms
- DataGridView control [Windows Forms], manipulating bands
ms.assetid: 1ea3470e-480f-4edc-bcbd-51373eca3856
ms.openlocfilehash: 5e62f5d31b9d24469455ab31f9771ebc81f74967
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592351"
---
# <a name="how-to-manipulate-bands-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d1be6-102">作法：管理 Windows Forms DataGridView 控制項中的寬線</span><span class="sxs-lookup"><span data-stu-id="d1be6-102">How to: Manipulate Bands in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d1be6-103">下列程式碼範例示範使用 <xref:System.Windows.Forms.DataGridViewBand> 類別的屬性來管理 <xref:System.Windows.Forms.DataGridView> 資料列和資料行的各種方式，<xref:System.Windows.Forms.DataGridViewRow> 和 <xref:System.Windows.Forms.DataGridViewColumn> 類別便是衍生自這個類別。</span><span class="sxs-lookup"><span data-stu-id="d1be6-103">The following code example shows various ways to manipulate <xref:System.Windows.Forms.DataGridView> rows and columns using properties of the <xref:System.Windows.Forms.DataGridViewBand> class from which the <xref:System.Windows.Forms.DataGridViewRow> and <xref:System.Windows.Forms.DataGridViewColumn> classes derive.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1be6-104">範例</span><span class="sxs-lookup"><span data-stu-id="d1be6-104">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.ButtonDemos#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CPP/DataGridViewBandDemo.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.ButtonDemos#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CS/DataGridViewBandDemo.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.ButtonDemos#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/VB/datagridviewbanddemo.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d1be6-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="d1be6-105">Compiling the Code</span></span>  
 <span data-ttu-id="d1be6-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="d1be6-106">This example requires:</span></span>  
  
- <span data-ttu-id="d1be6-107">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="d1be6-107">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1be6-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1be6-108">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewBand>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [<span data-ttu-id="d1be6-109">在 Windows Forms DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計</span><span class="sxs-lookup"><span data-stu-id="d1be6-109">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)
