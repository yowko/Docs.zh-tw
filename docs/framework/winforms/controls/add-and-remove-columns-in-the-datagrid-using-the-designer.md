---
title: 作法：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 7a3029192ab0da4a954dfd7d3d258a00b154924e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957118"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="69d97-102">HOW TO：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行</span><span class="sxs-lookup"><span data-stu-id="69d97-102">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="69d97-103">Windows Forms <xref:System.Windows.Forms.DataGridView>控制項必須包含資料行, 才能顯示資料。</span><span class="sxs-lookup"><span data-stu-id="69d97-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control must contain columns in order to display data.</span></span> <span data-ttu-id="69d97-104">如果您打算手動填入控制項, 就必須自行加入資料行。</span><span class="sxs-lookup"><span data-stu-id="69d97-104">If you plan to populate the control manually, you must add the columns yourself.</span></span> <span data-ttu-id="69d97-105">或者, 您可以將控制項系結至資料來源, 以自動產生和填入資料行。</span><span class="sxs-lookup"><span data-stu-id="69d97-105">Alternately, you can bind the control to a data source, which generates and populates the columns automatically.</span></span> <span data-ttu-id="69d97-106">如果資料來源包含比您想要顯示的更多欄, 您可以移除不必要的資料行。</span><span class="sxs-lookup"><span data-stu-id="69d97-106">If the data source contains more columns than you want to display, you can remove the unwanted columns.</span></span>

 <span data-ttu-id="69d97-107">下列程式需要具有包含<xref:System.Windows.Forms.DataGridView>控制項之表單的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="69d97-107">The following procedures require a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="69d97-108">如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="69d97-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-add-a-column-using-the-designer"></a><span data-ttu-id="69d97-109">若要使用設計工具加入資料行</span><span class="sxs-lookup"><span data-stu-id="69d97-109">To add a column using the designer</span></span>

1. <span data-ttu-id="69d97-110">按一下<xref:System.Windows.Forms.DataGridView>控制項右上角的智慧標籤圖像 (![智慧標籤]圖像(./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), 然後選取 [加入資料**行**]。</span><span class="sxs-lookup"><span data-stu-id="69d97-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Add Column**.</span></span>

2. <span data-ttu-id="69d97-111">在 [**加入資料行**] 對話方塊中, 選擇 [資料系結資料**行**] 選項, 並從資料來源選取資料行, 或選擇 [未系結資料**行**] 選項, 並使用所提供的欄位來定義資料行。</span><span class="sxs-lookup"><span data-stu-id="69d97-111">In the **Add Column** dialog box, choose the **Databound Column** option and select a column from the data source, or choose the **Unbound Column** option and define the column using the fields provided.</span></span>

3. <span data-ttu-id="69d97-112">按一下 [**新增**] 按鈕以加入資料行, 如果現有的資料行尚未填滿控制項顯示區域, 則會使其出現在設計工具中。</span><span class="sxs-lookup"><span data-stu-id="69d97-112">Click the **Add** button to add the column, causing it to appear in the designer if the existing columns do not already fill the control display area.</span></span>

    > [!NOTE]
    > <span data-ttu-id="69d97-113">您可以在 [**編輯資料行**] 對話方塊中修改資料行屬性, 您可以從控制項的智慧標籤進行存取。</span><span class="sxs-lookup"><span data-stu-id="69d97-113">You can modify column properties in the **Edit Columns** dialog box, which you can access from the control's smart tag.</span></span>

## <a name="to-remove-a-column-using-the-designer"></a><span data-ttu-id="69d97-114">若要使用設計工具來移除資料行</span><span class="sxs-lookup"><span data-stu-id="69d97-114">To remove a column using the designer</span></span>

1. <span data-ttu-id="69d97-115">從控制項的智慧標籤中選擇 [**編輯資料行**]。</span><span class="sxs-lookup"><span data-stu-id="69d97-115">Choose **Edit Columns** from the control's smart tag.</span></span>

2. <span data-ttu-id="69d97-116">從 [選取的資料**行**] 清單中選取資料行。</span><span class="sxs-lookup"><span data-stu-id="69d97-116">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="69d97-117">按一下 [**移除**] 按鈕以刪除資料行, 使其從設計工具中消失。</span><span class="sxs-lookup"><span data-stu-id="69d97-117">Click the **Remove** button to delete the column, causing it to disappear from the designer.</span></span>

## <a name="see-also"></a><span data-ttu-id="69d97-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69d97-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="69d97-119">如何：建立 Windows Forms 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="69d97-119">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="69d97-120">如何：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="69d97-120">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
