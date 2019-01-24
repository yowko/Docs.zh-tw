---
title: HOW TO：Windows Form DataGridView 控制項中指定的編輯模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: fcb2014cc92a8a3e4afe7c3ed0365fd5947c70f3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628262"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="22265-102">HOW TO：Windows Form DataGridView 控制項中指定的編輯模式</span><span class="sxs-lookup"><span data-stu-id="22265-102">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="22265-103">根據預設，使用者可以編輯的目前內容<xref:System.Windows.Forms.DataGridView>文字 方塊中儲存格，在其中輸入，或按下 f2 鍵。</span><span class="sxs-lookup"><span data-stu-id="22265-103">By default, users can edit the contents of the current <xref:System.Windows.Forms.DataGridView> text box cell by typing in it or pressing F2.</span></span> <span data-ttu-id="22265-104">在編輯模式中，如果符合所有下列條件，這會使儲存格：</span><span class="sxs-lookup"><span data-stu-id="22265-104">This puts the cell in edit mode if all of the following conditions are met:</span></span>  
  
-   <span data-ttu-id="22265-105">基礎資料來源支援編輯。</span><span class="sxs-lookup"><span data-stu-id="22265-105">The underlying data source supports editing.</span></span>  
  
-   <span data-ttu-id="22265-106"><xref:System.Windows.Forms.DataGridView>啟用控制項。</span><span class="sxs-lookup"><span data-stu-id="22265-106">The <xref:System.Windows.Forms.DataGridView> control is enabled.</span></span>  
  
-   <span data-ttu-id="22265-107"><xref:System.Windows.Forms.DataGridView.EditMode%2A>屬性值不是<xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>。</span><span class="sxs-lookup"><span data-stu-id="22265-107">The <xref:System.Windows.Forms.DataGridView.EditMode%2A> property value is not <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span></span>  
  
-   <span data-ttu-id="22265-108">`ReadOnly`資料格、 資料列、 資料行和控制項的屬性都設為`false`。</span><span class="sxs-lookup"><span data-stu-id="22265-108">The `ReadOnly` properties of the cell, row, column, and control are all set to `false`.</span></span>  
  
 <span data-ttu-id="22265-109">在編輯模式中，使用者可以變更儲存格的值，然後按 ENTER 認可的變更或 esc 鍵還原為其原始值的資料格。</span><span class="sxs-lookup"><span data-stu-id="22265-109">In edit mode, the user can change the cell value and press ENTER to commit the change or ESC to revert the cell to its original value.</span></span>  
  
 <span data-ttu-id="22265-110">您可以設定<xref:System.Windows.Forms.DataGridView>控制項，使儲存格進入編輯模式，因為它會變成目前儲存格。</span><span class="sxs-lookup"><span data-stu-id="22265-110">You can configure a <xref:System.Windows.Forms.DataGridView> control so that a cell enters edit mode as soon as it becomes the current cell.</span></span> <span data-ttu-id="22265-111">ENTER 和 ESC 鍵行為不會變更在此情況下，但是之後的值是認可或還原的資料格會保留在編輯模式。</span><span class="sxs-lookup"><span data-stu-id="22265-111">The behavior of the ENTER and ESC keys is unchanged in this case, but the cell remains in edit mode after the value is committed or reverted.</span></span> <span data-ttu-id="22265-112">您也可以設定控制項，以便儲存格進入編輯模式，只在使用者輸入中的資料格，或只有當使用者按下 f2 鍵時，才。</span><span class="sxs-lookup"><span data-stu-id="22265-112">You can also configure the control so that cells enter edit mode only when users type in the cell or only when users press F2.</span></span> <span data-ttu-id="22265-113">最後，您可以防止儲存格進入編輯模式，但當您呼叫<xref:System.Windows.Forms.DataGridView.BeginEdit%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="22265-113">Finally, you can prevent cells from entering edit mode except when you call the <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> method.</span></span>  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a><span data-ttu-id="22265-114">若要變更 DataGridView 控制項的編輯模式</span><span class="sxs-lookup"><span data-stu-id="22265-114">To change the edit mode of a DataGridView control</span></span>  
  
-   <span data-ttu-id="22265-115">設定<xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>屬性為適當<xref:System.Windows.Forms.DataGridViewEditMode>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="22265-115">Set the <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> property to the appropriate <xref:System.Windows.Forms.DataGridViewEditMode> enumeration.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="22265-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="22265-116">Compiling the Code</span></span>  
 <span data-ttu-id="22265-117">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="22265-117">This example requires:</span></span>  
  
-   <span data-ttu-id="22265-118">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="22265-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="22265-119"><xref:System> 和 <xref:System.Windows.Forms> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="22265-119">References to the <xref:System> and <xref:System.Windows.Forms> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22265-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22265-120">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="22265-121">Windows Forms DataGridView 控制項中的資料輸入</span><span class="sxs-lookup"><span data-stu-id="22265-121">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)
