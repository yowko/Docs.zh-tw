---
title: 指定 DataGridView 控制項的編輯模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: c0318202a80f9a43f1b656201732ef032f430b5b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743759"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="bf06e-102">如何：指定 Windows Form DataGridView 控制項的編輯模式</span><span class="sxs-lookup"><span data-stu-id="bf06e-102">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="bf06e-103">根據預設，使用者可以藉由在 [目前 <xref:System.Windows.Forms.DataGridView> 文字方塊] 儲存格中輸入或按 F2 來編輯其內容。</span><span class="sxs-lookup"><span data-stu-id="bf06e-103">By default, users can edit the contents of the current <xref:System.Windows.Forms.DataGridView> text box cell by typing in it or pressing F2.</span></span> <span data-ttu-id="bf06e-104">這會在符合下列所有條件時，將儲存格置於編輯模式：</span><span class="sxs-lookup"><span data-stu-id="bf06e-104">This puts the cell in edit mode if all of the following conditions are met:</span></span>  
  
- <span data-ttu-id="bf06e-105">基礎資料來源支援編輯。</span><span class="sxs-lookup"><span data-stu-id="bf06e-105">The underlying data source supports editing.</span></span>  
  
- <span data-ttu-id="bf06e-106"><xref:System.Windows.Forms.DataGridView> 控制項已啟用。</span><span class="sxs-lookup"><span data-stu-id="bf06e-106">The <xref:System.Windows.Forms.DataGridView> control is enabled.</span></span>  
  
- <span data-ttu-id="bf06e-107"><xref:System.Windows.Forms.DataGridView.EditMode%2A> 屬性值不是 <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>。</span><span class="sxs-lookup"><span data-stu-id="bf06e-107">The <xref:System.Windows.Forms.DataGridView.EditMode%2A> property value is not <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span></span>  
  
- <span data-ttu-id="bf06e-108">資料格、資料列、資料行和控制項的 `ReadOnly` 屬性全都設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="bf06e-108">The `ReadOnly` properties of the cell, row, column, and control are all set to `false`.</span></span>  
  
 <span data-ttu-id="bf06e-109">在編輯模式中，使用者可以變更資料格的值，然後按 ENTER 來認可變更，或按 ESC 將資料格還原成其原始值。</span><span class="sxs-lookup"><span data-stu-id="bf06e-109">In edit mode, the user can change the cell value and press ENTER to commit the change or ESC to revert the cell to its original value.</span></span>  
  
 <span data-ttu-id="bf06e-110">您可以設定 <xref:System.Windows.Forms.DataGridView> 控制項，讓資料格在資料變成目前儲存格時進入編輯模式。</span><span class="sxs-lookup"><span data-stu-id="bf06e-110">You can configure a <xref:System.Windows.Forms.DataGridView> control so that a cell enters edit mode as soon as it becomes the current cell.</span></span> <span data-ttu-id="bf06e-111">在此情況下，ENTER 和 ESC 鍵的行為不會變更，但是在認可或還原值之後，資料格仍會保持編輯模式。</span><span class="sxs-lookup"><span data-stu-id="bf06e-111">The behavior of the ENTER and ESC keys is unchanged in this case, but the cell remains in edit mode after the value is committed or reverted.</span></span> <span data-ttu-id="bf06e-112">您也可以設定控制項，讓資料格只會在使用者輸入儲存格，或只有在使用者按下 F2 時才進入編輯模式。</span><span class="sxs-lookup"><span data-stu-id="bf06e-112">You can also configure the control so that cells enter edit mode only when users type in the cell or only when users press F2.</span></span> <span data-ttu-id="bf06e-113">最後，您可以防止資料格進入編輯模式，除非您呼叫 <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="bf06e-113">Finally, you can prevent cells from entering edit mode except when you call the <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> method.</span></span>  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a><span data-ttu-id="bf06e-114">變更 DataGridView 控制項的編輯模式</span><span class="sxs-lookup"><span data-stu-id="bf06e-114">To change the edit mode of a DataGridView control</span></span>  
  
- <span data-ttu-id="bf06e-115">將 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> 屬性設定為適當的 <xref:System.Windows.Forms.DataGridViewEditMode> 列舉。</span><span class="sxs-lookup"><span data-stu-id="bf06e-115">Set the <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> property to the appropriate <xref:System.Windows.Forms.DataGridViewEditMode> enumeration.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bf06e-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="bf06e-116">Compiling the Code</span></span>  
 <span data-ttu-id="bf06e-117">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="bf06e-117">This example requires:</span></span>  
  
- <span data-ttu-id="bf06e-118">名為 <xref:System.Windows.Forms.DataGridView> 的 `dataGridView1` 控制項。</span><span class="sxs-lookup"><span data-stu-id="bf06e-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="bf06e-119"><xref:System> 和 <xref:System.Windows.Forms> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="bf06e-119">References to the <xref:System> and <xref:System.Windows.Forms> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf06e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf06e-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bf06e-121">Windows Forms DataGridView 控制項中的資料輸入</span><span class="sxs-lookup"><span data-stu-id="bf06e-121">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
