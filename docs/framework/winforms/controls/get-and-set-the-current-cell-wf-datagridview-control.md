---
title: 取得並設定 DataGridView 控制項中的目前儲存格
description: 瞭解如何藉由取得並設定 Windows Forms DataGridView 控制項中的目前儲存格，以程式設計方式探索目前作用中的儲存格。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 1651ca9c8fa0329f9435a70ce777bce68f15ff63
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622207"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="38924-103">如何：取得和設定 Windows Form DataGridView 控制項中目前的儲存格</span><span class="sxs-lookup"><span data-stu-id="38924-103">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="38924-104">與互動 <xref:System.Windows.Forms.DataGridView> 通常需要您以程式設計方式探索目前使用中的儲存格。</span><span class="sxs-lookup"><span data-stu-id="38924-104">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="38924-105">您也可能需要變更目前的儲存格。</span><span class="sxs-lookup"><span data-stu-id="38924-105">You may also need to change the current cell.</span></span> <span data-ttu-id="38924-106">您可以使用屬性來執行這些工作 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> 。</span><span class="sxs-lookup"><span data-stu-id="38924-106">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38924-107">您無法在其屬性設定為的資料列或資料行中，設定目前的儲存格 <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> `false` 。</span><span class="sxs-lookup"><span data-stu-id="38924-107">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="38924-108">根據 <xref:System.Windows.Forms.DataGridView> 控制項的選取模式，變更目前的儲存格可以變更選取範圍。</span><span class="sxs-lookup"><span data-stu-id="38924-108">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="38924-109">如需詳細資訊，請參閱[Windows Forms DataGridView 控制項中的選取模式](selection-modes-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="38924-109">For more information, see [Selection Modes in the Windows Forms DataGridView Control](selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="38924-110">以程式設計方式取得目前的儲存格</span><span class="sxs-lookup"><span data-stu-id="38924-110">To get the current cell programmatically</span></span>  
  
- <span data-ttu-id="38924-111">使用 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="38924-111">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="38924-112">以程式設計方式設定目前的儲存格</span><span class="sxs-lookup"><span data-stu-id="38924-112">To set the current cell programmatically</span></span>  
  
- <span data-ttu-id="38924-113">設定 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> 控制項的屬性 <xref:System.Windows.Forms.DataGridView> 。</span><span class="sxs-lookup"><span data-stu-id="38924-113">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="38924-114">在下列程式碼範例中，目前儲存格設定為數據列0，資料行1。</span><span class="sxs-lookup"><span data-stu-id="38924-114">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="38924-115">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="38924-115">Compiling the Code</span></span>  
 <span data-ttu-id="38924-116">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="38924-116">This example requires:</span></span>  
  
- <span data-ttu-id="38924-117"><xref:System.Windows.Forms.Button>名為 `getCurrentCellButton` 和 `setCurrentCellButton` 的控制項。</span><span class="sxs-lookup"><span data-stu-id="38924-117"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="38924-118">在 Visual c # 中，您必須將 <xref:System.Windows.Forms.Control.Click> 每個按鈕的事件附加至範例程式碼中相關聯的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="38924-118">In Visual C#, you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
- <span data-ttu-id="38924-119">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="38924-119">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="38924-120"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="38924-120">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38924-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38924-121">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [<span data-ttu-id="38924-122">Windows Forms DataGridView 控制項中的基本資料行、資料列和儲存格功能</span><span class="sxs-lookup"><span data-stu-id="38924-122">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="38924-123">Windows Forms DataGridView 控制項中的選取模式</span><span class="sxs-lookup"><span data-stu-id="38924-123">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)
