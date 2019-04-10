---
title: HOW TO：使用設計工具變更 Windows Forms DataGridView 控制項的資料行順序
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: 131ef2a04caa17aa268c0e8d229a1070061c4373
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175301"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="72d20-102">HOW TO：使用設計工具變更 Windows Forms DataGridView 控制項的資料行順序</span><span class="sxs-lookup"><span data-stu-id="72d20-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="72d20-103">當您繫結 Windows Form<xref:System.Windows.Forms.DataGridView>控制項資料來源時，會自動產生的資料行的顯示順序取決於資料來源。</span><span class="sxs-lookup"><span data-stu-id="72d20-103">When you bind a Windows Forms <xref:System.Windows.Forms.DataGridView> control to a data source, the display order of the automatically generated columns is dictated by the data source.</span></span> <span data-ttu-id="72d20-104">如果此順序是不是您所喜好，您可以變更使用設計工具的資料行的順序。</span><span class="sxs-lookup"><span data-stu-id="72d20-104">If this order is not what you prefer, you can change the order of the columns using the designer.</span></span> <span data-ttu-id="72d20-105">您也可以將未繫結的資料行新增至控制項，並變更其顯示順序。</span><span class="sxs-lookup"><span data-stu-id="72d20-105">You may also want to add unbound columns to the control and change their display order.</span></span> <span data-ttu-id="72d20-106">如需如何以程式設計方式變更的資料行順序的資訊，請參閱[How to:變更 Windows Form DataGridView 控制項中的資料行的順序](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="72d20-106">For information about how to change the column order programmatically, see [How to: Change the Order of Columns in the Windows Forms DataGridView Control](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="72d20-107">下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="72d20-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="72d20-108">如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="72d20-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72d20-109">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="72d20-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="72d20-110">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="72d20-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="72d20-111">如需詳細資訊，請參閱[Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)</span><span class="sxs-lookup"><span data-stu-id="72d20-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)</span></span>  
  
### <a name="to-change-the-column-order-using-the-designer"></a><span data-ttu-id="72d20-112">若要變更使用設計工具的資料行順序</span><span class="sxs-lookup"><span data-stu-id="72d20-112">To change the column order using the designer</span></span>  
  
1.  <span data-ttu-id="72d20-113">按一下智慧標籤圖像 (![智慧標籤圖像](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 的右上角<xref:System.Windows.Forms.DataGridView>控制項，然後再選取**編輯資料行**。</span><span class="sxs-lookup"><span data-stu-id="72d20-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="72d20-114">選取的資料行**選取的資料行**清單。</span><span class="sxs-lookup"><span data-stu-id="72d20-114">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="72d20-115">按一下向上箭頭或向下箭號右側**所選資料行**清單，直到所選資料行是在您要的位置。</span><span class="sxs-lookup"><span data-stu-id="72d20-115">Click the up or down arrow to the right of the **Selected Columns** list until the selected column is in the position you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72d20-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72d20-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="72d20-117">HOW TO：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行</span><span class="sxs-lookup"><span data-stu-id="72d20-117">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="72d20-118">HOW TO：建立 Windows Forms 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="72d20-118">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="72d20-119">HOW TO：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="72d20-119">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
