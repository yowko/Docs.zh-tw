---
title: 如何：使用設計工具在 Windows Form DataGridView 控制項中加入和移除資料行
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 99fe1b8ffb7ccc2a5bef13ea8fef6ace5d5bdfdc
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452803"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="b360f-102">如何：使用設計工具在 Windows Form DataGridView 控制項中加入和移除資料行</span><span class="sxs-lookup"><span data-stu-id="b360f-102">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="b360f-103">Windows Form<xref:System.Windows.Forms.DataGridView>控制項必須包含資料行，以便顯示資料。</span><span class="sxs-lookup"><span data-stu-id="b360f-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control must contain columns in order to display data.</span></span> <span data-ttu-id="b360f-104">如果您打算以手動方式填入控制項，您必須自行加入資料行。</span><span class="sxs-lookup"><span data-stu-id="b360f-104">If you plan to populate the control manually, you must add the columns yourself.</span></span> <span data-ttu-id="b360f-105">或者，您可以控制項繫結至資料來源，會產生，並會自動填入資料行。</span><span class="sxs-lookup"><span data-stu-id="b360f-105">Alternately, you can bind the control to a data source, which generates and populates the columns automatically.</span></span> <span data-ttu-id="b360f-106">如果資料來源包含多個資料行，比您想要顯示，您可以移除不必要的資料行。</span><span class="sxs-lookup"><span data-stu-id="b360f-106">If the data source contains more columns than you want to display, you can remove the unwanted columns.</span></span>  
  
 <span data-ttu-id="b360f-107">下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="b360f-107">The following procedures require a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="b360f-108">如需這類專案的設定資訊，請參閱[如何： 建立 Windows 應用程式專案](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)並[如何： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="b360f-108">For information about setting up such a project, see [How to: Create a Windows Application Project](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b360f-109">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="b360f-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b360f-110">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="b360f-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b360f-111">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="b360f-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-a-column-using-the-designer"></a><span data-ttu-id="b360f-112">若要加入資料行使用設計工具</span><span class="sxs-lookup"><span data-stu-id="b360f-112">To add a column using the designer</span></span>  
  
1.  <span data-ttu-id="b360f-113">按一下智慧標籤圖像 (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 的右上角<xref:System.Windows.Forms.DataGridView>控制項，然後再選取**加入資料行**。</span><span class="sxs-lookup"><span data-stu-id="b360f-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Add Column**.</span></span>  
  
2.  <span data-ttu-id="b360f-114">在**加入資料行**對話方塊方塊中，選擇**資料繫結資料行**選項，並選取資料行從資料來源，或選擇**解除繫結的資料行**選項，並定義資料行使用提供的欄位。</span><span class="sxs-lookup"><span data-stu-id="b360f-114">In the **Add Column** dialog box, choose the **Databound Column** option and select a column from the data source, or choose the **Unbound Column** option and define the column using the fields provided.</span></span>  
  
3.  <span data-ttu-id="b360f-115">按一下 **新增**按鈕以新增資料行，使其出現在設計工具中，如果現有的資料行沒有已填滿控制項顯示區域。</span><span class="sxs-lookup"><span data-stu-id="b360f-115">Click the **Add** button to add the column, causing it to appear in the designer if the existing columns do not already fill the control display area.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b360f-116">您可以修改資料行中的屬性**編輯資料行** 對話方塊中，您可以存取從控制項的智慧標籤。</span><span class="sxs-lookup"><span data-stu-id="b360f-116">You can modify column properties in the **Edit Columns** dialog box, which you can access from the control's smart tag.</span></span>  
  
### <a name="to-remove-a-column-using-the-designer"></a><span data-ttu-id="b360f-117">若要移除資料行使用設計工具</span><span class="sxs-lookup"><span data-stu-id="b360f-117">To remove a column using the designer</span></span>  
  
1.  <span data-ttu-id="b360f-118">選擇**編輯資料行**從控制項的智慧標籤。</span><span class="sxs-lookup"><span data-stu-id="b360f-118">Choose **Edit Columns** from the control's smart tag.</span></span>  
  
2.  <span data-ttu-id="b360f-119">選取的資料行**選取的資料行**清單。</span><span class="sxs-lookup"><span data-stu-id="b360f-119">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="b360f-120">按一下 [**移除**] 按鈕來刪除資料行，使其從設計工具中消失。</span><span class="sxs-lookup"><span data-stu-id="b360f-120">Click the **Remove** button to delete the column, causing it to disappear from the designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b360f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b360f-121">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="b360f-122">如何： 建立 Windows 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="b360f-122">How to: Create a Windows Application Project</span></span>](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="b360f-123">操作說明：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b360f-123">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
