---
title: 如何：取得和設定 Windows Form DataGridView 控制項中目前的儲存格
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 0a3c8a891bf3f8424158a7266c3752edc33e8805
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527543"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="7c14a-102">如何：取得和設定 Windows Form DataGridView 控制項中目前的儲存格</span><span class="sxs-lookup"><span data-stu-id="7c14a-102">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7c14a-103">互動<xref:System.Windows.Forms.DataGridView>通常會要求您以程式設計方式探索哪些儲存格是目前作用中。</span><span class="sxs-lookup"><span data-stu-id="7c14a-103">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="7c14a-104">您也可能需要變更目前的儲存格。</span><span class="sxs-lookup"><span data-stu-id="7c14a-104">You may also need to change the current cell.</span></span> <span data-ttu-id="7c14a-105">您可以執行這些工作與<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="7c14a-105">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c14a-106">您無法設定目前的儲存格的資料列或資料行具有其<xref:System.Windows.Forms.DataGridViewBand.Visible%2A>屬性設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="7c14a-106">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="7c14a-107">取決於<xref:System.Windows.Forms.DataGridView>控制項的選取模式，變更目前的儲存格可以變更選取項目。</span><span class="sxs-lookup"><span data-stu-id="7c14a-107">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="7c14a-108">如需詳細資訊，請參閱[Windows Form DataGridView 控制項中的選取模式](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="7c14a-108">For more information, see [Selection Modes in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="7c14a-109">若要以程式設計方式取得目前儲存格</span><span class="sxs-lookup"><span data-stu-id="7c14a-109">To get the current cell programmatically</span></span>  
  
-   <span data-ttu-id="7c14a-110">使用<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="7c14a-110">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="7c14a-111">若要以程式設計方式設定的目前儲存格</span><span class="sxs-lookup"><span data-stu-id="7c14a-111">To set the current cell programmatically</span></span>  
  
-   <span data-ttu-id="7c14a-112">設定<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>屬性<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="7c14a-112">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="7c14a-113">在下列程式碼範例中，目前儲存格設定 0，資料行 1 的資料列。</span><span class="sxs-lookup"><span data-stu-id="7c14a-113">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7c14a-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="7c14a-114">Compiling the Code</span></span>  
 <span data-ttu-id="7c14a-115">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="7c14a-115">This example requires:</span></span>  
  
-   <span data-ttu-id="7c14a-116"><xref:System.Windows.Forms.Button> 控制項名為`getCurrentCellButton`和`setCurrentCellButton`。</span><span class="sxs-lookup"><span data-stu-id="7c14a-116"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="7c14a-117">在 Visual C# 中，您必須將附加<xref:System.Windows.Forms.Control.Click>至相關聯的事件處理常式，範例程式碼中的每個按鈕的事件。</span><span class="sxs-lookup"><span data-stu-id="7c14a-117">In Visual C#, you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
-   <span data-ttu-id="7c14a-118">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="7c14a-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="7c14a-119"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="7c14a-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c14a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c14a-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="7c14a-121">Windows Forms DataGridView 控制項中的基本資料行、資料列和儲存格功能</span><span class="sxs-lookup"><span data-stu-id="7c14a-121">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="7c14a-122">Windows Forms DataGridView 控制項中的選取模式</span><span class="sxs-lookup"><span data-stu-id="7c14a-122">Selection Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)
