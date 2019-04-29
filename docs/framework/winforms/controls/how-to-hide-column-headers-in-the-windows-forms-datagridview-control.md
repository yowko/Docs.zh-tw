---
title: HOW TO：隱藏 Windows Forms DataGridView 控制項的資料行標頭
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], hiding column headers
- column headers [Windows Forms], hiding
- DataGridView control [Windows Forms], column headers
ms.assetid: e4ad5f68-50d2-4b9e-93ee-9d622423a8ab
ms.openlocfilehash: 85332bfdbb80e4c49bab1ff208228a88337fbb43
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941280"
---
# <a name="how-to-hide-column-headers-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="8cc70-102">HOW TO：隱藏 Windows Forms DataGridView 控制項的資料行標頭</span><span class="sxs-lookup"><span data-stu-id="8cc70-102">How to: Hide Column Headers in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8cc70-103">有時候您會想要顯示<xref:System.Windows.Forms.DataGridView>不含資料行的標頭。</span><span class="sxs-lookup"><span data-stu-id="8cc70-103">Sometimes you will want to display a <xref:System.Windows.Forms.DataGridView> without column headers.</span></span> <span data-ttu-id="8cc70-104">在 <xref:System.Windows.Forms.DataGridView>控制項，<xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A>屬性值會決定是否要顯示資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="8cc70-104">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> property value determines whether the column headers are displayed.</span></span>  
  
### <a name="to-hide-the-column-headers"></a><span data-ttu-id="8cc70-105">若要隱藏資料行行首</span><span class="sxs-lookup"><span data-stu-id="8cc70-105">To hide the column headers</span></span>  
  
- <span data-ttu-id="8cc70-106">將 <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType> 屬性設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="8cc70-106">Set the <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType> property to `false`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#062](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#062)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#062](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#062)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8cc70-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="8cc70-107">Compiling the Code</span></span>  
 <span data-ttu-id="8cc70-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="8cc70-108">This example requires:</span></span>  
  
- <span data-ttu-id="8cc70-109">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="8cc70-109">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="8cc70-110"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="8cc70-110">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cc70-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cc70-111">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8cc70-112">Windows Forms DataGridView 控制項中的基本資料行、資料列和儲存格功能</span><span class="sxs-lookup"><span data-stu-id="8cc70-112">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
