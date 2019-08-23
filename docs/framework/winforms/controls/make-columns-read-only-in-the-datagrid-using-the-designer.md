---
title: HOW TO：使用設計工具將 Windows Forms DataGridView 控制項的資料行設為唯讀
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 82be9d31ff6bb3f2f5dd8a55b4426103d466bdd6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952098"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="d4ab6-102">作法：使用設計工具將 Windows Forms DataGridView 控制項的資料行設為唯讀</span><span class="sxs-lookup"><span data-stu-id="d4ab6-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="d4ab6-103">根據預設, 使用者可以修改顯示在 Windows Forms <xref:System.Windows.Forms.DataGridView>控制項中的文字和數值資料。</span><span class="sxs-lookup"><span data-stu-id="d4ab6-103">By default, users can modify text and numerical data displayed in the Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="d4ab6-104">如果您想要顯示不適用於修改的資料, 您必須將包含資料的資料行設為唯讀。</span><span class="sxs-lookup"><span data-stu-id="d4ab6-104">If you want to display data that is not meant for modification, you must make the columns that contain the data read-only.</span></span> <span data-ttu-id="d4ab6-105">如需如何讓控制項完全唯讀的相關資訊, 請參閱[如何:使用設計](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)工具防止在 Windows Forms DataGridView 控制項中新增和刪除資料列。</span><span class="sxs-lookup"><span data-stu-id="d4ab6-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span></span>

 <span data-ttu-id="d4ab6-106">下列程式需要具有包含<xref:System.Windows.Forms.DataGridView>控制項之表單的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="d4ab6-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="d4ab6-107">如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="d4ab6-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-make-a-column-read-only-by-using-the-designer"></a><span data-ttu-id="d4ab6-108">使用設計工具將資料行設為唯讀</span><span class="sxs-lookup"><span data-stu-id="d4ab6-108">To make a column read-only by using the designer</span></span>

1. <span data-ttu-id="d4ab6-109">按一下<xref:System.Windows.Forms.DataGridView>控制項右上角的智慧標籤圖像 (![智慧標籤]圖像(./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), 然後選取 [編輯資料**行**]。</span><span class="sxs-lookup"><span data-stu-id="d4ab6-109">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="d4ab6-110">從 [選取的資料**行**] 清單中選取資料行。</span><span class="sxs-lookup"><span data-stu-id="d4ab6-110">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="d4ab6-111">在 [資料**行屬性**] 方格中<xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> , 將`true`屬性設定為。</span><span class="sxs-lookup"><span data-stu-id="d4ab6-111">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d4ab6-112">您也可以選取 [**加入資料行**] 對話方塊中的 [**唯讀**] 核取方塊, 在加入資料行時將它設為唯讀。</span><span class="sxs-lookup"><span data-stu-id="d4ab6-112">You can also make a column read-only when you add it by selecting the **Read Only** check box in the **Add Column** dialog box.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4ab6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4ab6-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d4ab6-114">如何：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行</span><span class="sxs-lookup"><span data-stu-id="d4ab6-114">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="d4ab6-115">如何：使用設計工具防止在 Windows Forms DataGridView 控制項中新增和刪除資料列</span><span class="sxs-lookup"><span data-stu-id="d4ab6-115">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="d4ab6-116">如何：建立 Windows Forms 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="d4ab6-116">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="d4ab6-117">如何：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d4ab6-117">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
