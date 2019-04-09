---
title: HOW TO：使用設計工具隱藏 Windows Forms DataGridView 控制項的資料行
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: e0255cca5c614f07bbc4a7dfc9a908612e8867a6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122378"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="37658-102">HOW TO：使用設計工具隱藏 Windows Forms DataGridView 控制項的資料行</span><span class="sxs-lookup"><span data-stu-id="37658-102">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="37658-103">有時候您會想要只顯示 Windows Form <xref:System.Windows.Forms.DataGridView> 控制項中某些可用的資料行。</span><span class="sxs-lookup"><span data-stu-id="37658-103">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="37658-104">例如，您可能想要顯示員工薪資資料行具有管理認證，同時隱藏其他使用者的使用者。</span><span class="sxs-lookup"><span data-stu-id="37658-104">For example, you may want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="37658-105">或者，您可能要將控制項繫結至資料來源，其中包含您想要顯示的只有其中一些的許多資料行。</span><span class="sxs-lookup"><span data-stu-id="37658-105">Alternately, you may want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="37658-106">在此情況下，您通常會移除您不想要顯示，而不是隱藏它們的資料行。</span><span class="sxs-lookup"><span data-stu-id="37658-106">In this case, you will typically remove the columns you are not interested in displaying rather than hiding them.</span></span> <span data-ttu-id="37658-107">如需詳細資訊，請參閱[如何：新增和移除資料行中的 Windows Form DataGridView 控制項使用設計工具](add-and-remove-columns-in-the-datagrid-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="37658-107">For more information, see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
 <span data-ttu-id="37658-108">下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="37658-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="37658-109">如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="37658-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37658-110">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="37658-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="37658-111">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="37658-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="37658-112">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="37658-112">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-hide-a-column-using-the-designer"></a><span data-ttu-id="37658-113">若要隱藏資料行使用設計工具</span><span class="sxs-lookup"><span data-stu-id="37658-113">To hide a column using the designer</span></span>  
  
1.  <span data-ttu-id="37658-114">按一下智慧標籤圖像 (![智慧標籤圖像](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 的右上角<xref:System.Windows.Forms.DataGridView>控制項，然後再選取**編輯資料行**。</span><span class="sxs-lookup"><span data-stu-id="37658-114">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="37658-115">選取的資料行**選取的資料行**清單。</span><span class="sxs-lookup"><span data-stu-id="37658-115">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="37658-116">在 **資料行屬性**方格中，設定<xref:System.Windows.Forms.DataGridViewColumn.Visible%2A>屬性設`false`。</span><span class="sxs-lookup"><span data-stu-id="37658-116">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property to `false`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="37658-117">您也可以新增藉由清除時隱藏資料行**Visible**中的核取方塊**加入資料行** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="37658-117">You can also hide a column when adding it by clearing the **Visible** check box in the **Add Column** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37658-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37658-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="37658-119">HOW TO：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行</span><span class="sxs-lookup"><span data-stu-id="37658-119">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="37658-120">HOW TO：建立 Windows Forms 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="37658-120">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="37658-121">HOW TO：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="37658-121">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
