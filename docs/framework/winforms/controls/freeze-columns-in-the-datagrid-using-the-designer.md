---
title: 作法：使用設計工具凍結 Windows Forms DataGridView 控制項的資料行
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
ms.openlocfilehash: 7ebdf7a1598ac3cd61005ae607e5bfbe7cb49059
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933708"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="396d6-102">作法：使用設計工具凍結 Windows Forms DataGridView 控制項的資料行</span><span class="sxs-lookup"><span data-stu-id="396d6-102">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="396d6-103">當使用者檢視顯示於 Windows Form <xref:System.Windows.Forms.DataGridView> 控制項的資料時，有時候需要經常參考單一資料行或資料行集合。</span><span class="sxs-lookup"><span data-stu-id="396d6-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="396d6-104">例如, 當您顯示包含許多資料行的客戶資訊資料表時, 您可以隨時顯示客戶名稱, 同時讓其他資料行在可見區域之外滾動。</span><span class="sxs-lookup"><span data-stu-id="396d6-104">For example, when you display a table of customer information that contains many columns, it is useful for you to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>

 <span data-ttu-id="396d6-105">若要達到這種行為，您可以凍結控制項中的資料行。</span><span class="sxs-lookup"><span data-stu-id="396d6-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="396d6-106">當您凍結資料行時，也會凍結在該資料行左邊的所有資料行 (如果是從右至左的字集，則會凍結右邊的所有資料行)。</span><span class="sxs-lookup"><span data-stu-id="396d6-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="396d6-107">凍結的資料行會留在原處，而其他所有資料行則可以捲動。</span><span class="sxs-lookup"><span data-stu-id="396d6-107">Frozen columns remain in place while all other columns can scroll.</span></span> <span data-ttu-id="396d6-108">如果啟用了資料行重新調整順序，則會將凍結的資料行視為與未凍結的資料行有所區別的群組。</span><span class="sxs-lookup"><span data-stu-id="396d6-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="396d6-109">使用者可以在任一群組中重新調整資料行位置，但無法將資料行從一個群組移至另一個。</span><span class="sxs-lookup"><span data-stu-id="396d6-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>

 <span data-ttu-id="396d6-110">下列程式需要具有包含<xref:System.Windows.Forms.DataGridView>控制項之表單的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="396d6-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="396d6-111">如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="396d6-111">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-freeze-a-column-using-the-designer"></a><span data-ttu-id="396d6-112">若要使用設計工具凍結資料行</span><span class="sxs-lookup"><span data-stu-id="396d6-112">To freeze a column using the designer</span></span>

1. <span data-ttu-id="396d6-113">按一下<xref:System.Windows.Forms.DataGridView>控制項右上角的智慧標籤圖像 (![智慧標籤]圖像(./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), 然後選取 [編輯資料**行**]。</span><span class="sxs-lookup"><span data-stu-id="396d6-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="396d6-114">從 [選取的資料**行**] 清單中選取資料行。</span><span class="sxs-lookup"><span data-stu-id="396d6-114">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="396d6-115">在 [資料**行屬性**] 方格中<xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> , 將`true`屬性設定為。</span><span class="sxs-lookup"><span data-stu-id="396d6-115">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property to `true`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="396d6-116">您也可以選取 [**加入資料行**] 對話方塊中的 [**凍結**] 方塊來加入資料行。</span><span class="sxs-lookup"><span data-stu-id="396d6-116">You can also freeze a column when adding it by selecting the **Frozen** box in the **Add Column** dialog box.</span></span>

## <a name="see-also"></a><span data-ttu-id="396d6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="396d6-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- [<span data-ttu-id="396d6-118">如何：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行</span><span class="sxs-lookup"><span data-stu-id="396d6-118">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="396d6-119">如何：使用設計工具在 Windows Forms DataGridView 控制項中啟用資料行重新排列</span><span class="sxs-lookup"><span data-stu-id="396d6-119">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](enable-column-reordering-in-the-datagrid-using-the-designer.md)
- <span data-ttu-id="396d6-120">[如何：在全球化的 Windows Forms 中顯示由右至左的文字](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="396d6-120">[How to: Display Right-to-Left Text in Windows Forms for Globalization](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))</span></span>
- [<span data-ttu-id="396d6-121">如何：建立 Windows Forms 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="396d6-121">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="396d6-122">如何：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="396d6-122">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
