---
title: 作法：使用設計工具隱藏 Windows Forms DataGridView 控制項的資料行
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: 35aa1cdeef919d4267cb27da79f183c4c52aefa2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916385"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="91b4f-102">HOW TO：使用設計工具隱藏 Windows Forms DataGridView 控制項的資料行</span><span class="sxs-lookup"><span data-stu-id="91b4f-102">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="91b4f-103">有時候您會想要只顯示 Windows Form <xref:System.Windows.Forms.DataGridView> 控制項中某些可用的資料行。</span><span class="sxs-lookup"><span data-stu-id="91b4f-103">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="91b4f-104">例如, 您可能會想要向具有管理認證的使用者顯示員工薪資資料行, 同時將其隱藏給其他使用者。</span><span class="sxs-lookup"><span data-stu-id="91b4f-104">For example, you may want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="91b4f-105">或者, 您可能會想要將控制項系結至包含許多資料行的資料來源, 而只是您想要顯示的部分。</span><span class="sxs-lookup"><span data-stu-id="91b4f-105">Alternately, you may want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="91b4f-106">在此情況下, 您通常會移除您不想要顯示的資料行, 而不是隱藏它們。</span><span class="sxs-lookup"><span data-stu-id="91b4f-106">In this case, you will typically remove the columns you are not interested in displaying rather than hiding them.</span></span> <span data-ttu-id="91b4f-107">如需詳細資訊，請參閱[如何：使用設計](add-and-remove-columns-in-the-datagrid-using-the-designer.md)工具在 Windows Forms DataGridView 控制項中新增和移除資料行。</span><span class="sxs-lookup"><span data-stu-id="91b4f-107">For more information, see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span></span>

 <span data-ttu-id="91b4f-108">下列程式需要具有包含<xref:System.Windows.Forms.DataGridView>控制項之表單的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="91b4f-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="91b4f-109">如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="91b4f-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-hide-a-column-using-the-designer"></a><span data-ttu-id="91b4f-110">若要使用設計工具隱藏資料行</span><span class="sxs-lookup"><span data-stu-id="91b4f-110">To hide a column using the designer</span></span>

1. <span data-ttu-id="91b4f-111">按一下<xref:System.Windows.Forms.DataGridView>控制項右上角的智慧標籤圖像 (![智慧標籤]圖像(./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), 然後選取 [編輯資料**行**]。</span><span class="sxs-lookup"><span data-stu-id="91b4f-111">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="91b4f-112">從 [選取的資料**行**] 清單中選取資料行。</span><span class="sxs-lookup"><span data-stu-id="91b4f-112">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="91b4f-113">在 [資料**行屬性**] 方格中<xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> , 將`false`屬性設定為。</span><span class="sxs-lookup"><span data-stu-id="91b4f-113">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property to `false`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="91b4f-114">藉由清除 [**加入資料行**] 對話方塊中的 [**可見**] 核取方塊, 您也可以在加入資料行時將它隱藏。</span><span class="sxs-lookup"><span data-stu-id="91b4f-114">You can also hide a column when adding it by clearing the **Visible** check box in the **Add Column** dialog box.</span></span>

## <a name="see-also"></a><span data-ttu-id="91b4f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91b4f-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="91b4f-116">如何：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行</span><span class="sxs-lookup"><span data-stu-id="91b4f-116">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="91b4f-117">如何：建立 Windows Forms 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="91b4f-117">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="91b4f-118">如何：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="91b4f-118">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
