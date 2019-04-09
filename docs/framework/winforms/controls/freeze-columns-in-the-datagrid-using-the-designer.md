---
title: HOW TO：使用設計工具凍結 Windows Forms DataGridView 控制項的資料行
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
ms.openlocfilehash: 437e49a1f8e5a154f1a54fc7a266579cb5f0122c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099998"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="7a7a2-102">HOW TO：使用設計工具凍結 Windows Forms DataGridView 控制項的資料行</span><span class="sxs-lookup"><span data-stu-id="7a7a2-102">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="7a7a2-103">當使用者檢視顯示於 Windows Form <xref:System.Windows.Forms.DataGridView> 控制項的資料時，有時候需要經常參考單一資料行或資料行集合。</span><span class="sxs-lookup"><span data-stu-id="7a7a2-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="7a7a2-104">比方說，當您顯示客戶資訊，其中包含許多資料行的資料表時，它可用於您隨時都能在其他資料行的可見區域外捲動時顯示客戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="7a7a2-104">For example, when you display a table of customer information that contains many columns, it is useful for you to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>  
  
 <span data-ttu-id="7a7a2-105">若要達到這種行為，您可以凍結控制項中的資料行。</span><span class="sxs-lookup"><span data-stu-id="7a7a2-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="7a7a2-106">當您凍結資料行時，也會凍結在該資料行左邊的所有資料行 (如果是從右至左的字集，則會凍結右邊的所有資料行)。</span><span class="sxs-lookup"><span data-stu-id="7a7a2-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="7a7a2-107">凍結的資料行會留在原處，而其他所有資料行則可以捲動。</span><span class="sxs-lookup"><span data-stu-id="7a7a2-107">Frozen columns remain in place while all other columns can scroll.</span></span> <span data-ttu-id="7a7a2-108">如果啟用了資料行重新調整順序，則會將凍結的資料行視為與未凍結的資料行有所區別的群組。</span><span class="sxs-lookup"><span data-stu-id="7a7a2-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="7a7a2-109">使用者可以在任一群組中重新調整資料行位置，但無法將資料行從一個群組移至另一個。</span><span class="sxs-lookup"><span data-stu-id="7a7a2-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>  
  
 <span data-ttu-id="7a7a2-110">下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="7a7a2-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="7a7a2-111">如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="7a7a2-111">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a7a2-112">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="7a7a2-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7a7a2-113">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="7a7a2-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7a7a2-114">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="7a7a2-114">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-freeze-a-column-using-the-designer"></a><span data-ttu-id="7a7a2-115">若要凍結資料行使用設計工具</span><span class="sxs-lookup"><span data-stu-id="7a7a2-115">To freeze a column using the designer</span></span>  
  
1.  <span data-ttu-id="7a7a2-116">按一下智慧標籤圖像 (![智慧標籤圖像](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 的右上角<xref:System.Windows.Forms.DataGridView>控制項，然後再選取**編輯資料行**。</span><span class="sxs-lookup"><span data-stu-id="7a7a2-116">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="7a7a2-117">選取的資料行**選取的資料行**清單。</span><span class="sxs-lookup"><span data-stu-id="7a7a2-117">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="7a7a2-118">在 **資料行屬性**方格中，設定<xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="7a7a2-118">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7a7a2-119">您也可以將它加入選取時凍結資料行**Frozen**方塊中**加入資料行** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7a7a2-119">You can also freeze a column when adding it by selecting the **Frozen** box in the **Add Column** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a7a2-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a7a2-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7a7a2-121">HOW TO：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行</span><span class="sxs-lookup"><span data-stu-id="7a7a2-121">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="7a7a2-122">HOW TO：使用設計工具重新調整 Windows Forms DataGridView 控制項的資料行順序</span><span class="sxs-lookup"><span data-stu-id="7a7a2-122">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](enable-column-reordering-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="7a7a2-123">HOW TO：顯示全球化 Windows Form 中由右至左的文字</span><span class="sxs-lookup"><span data-stu-id="7a7a2-123">How to: Display Right-to-Left Text in Windows Forms for Globalization</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))
- [<span data-ttu-id="7a7a2-124">HOW TO：建立 Windows Forms 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="7a7a2-124">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="7a7a2-125">HOW TO：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a7a2-125">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
