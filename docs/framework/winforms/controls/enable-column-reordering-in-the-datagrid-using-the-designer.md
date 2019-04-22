---
title: HOW TO：使用設計工具重新調整 Windows Forms DataGridView 控制項的資料行順序
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- columns [Windows Forms], reordering
- data [Windows Forms], displaying
ms.assetid: d82bd69c-6799-4439-a32c-91139c5901d1
ms.openlocfilehash: 966ffe131d10b97fe9632bb1ff23273b1dabd061
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59194964"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="48a8a-102">HOW TO：使用設計工具重新調整 Windows Forms DataGridView 控制項的資料行順序</span><span class="sxs-lookup"><span data-stu-id="48a8a-102">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="48a8a-103">檢視顯示 Windows Form 中的資料時<xref:System.Windows.Forms.DataGridView>控制項，使用者有時候想要比較特定的資料行的值。</span><span class="sxs-lookup"><span data-stu-id="48a8a-103">When viewing data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, users sometimes want to compare the values in specific columns.</span></span> <span data-ttu-id="48a8a-104">這可以是不太方便，如果資料行放在相隔在控制項中，特別是如果使用者必須來回水平捲動才能看到他們感興趣的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="48a8a-104">This can be inconvenient if the columns are widely separated in the control, especially if users must scroll back and forth horizontally in order to see all the columns they are interested in.</span></span> <span data-ttu-id="48a8a-105">您可以藉由讓使用者能夠重新排序資料行中比較您更輕鬆的資料行值的工作。</span><span class="sxs-lookup"><span data-stu-id="48a8a-105">You can make the task of comparing column values easier by enabling your users to reorder the columns.</span></span> <span data-ttu-id="48a8a-106">當您啟用資料行重新調整順序時，使用者可以拖曳資料行標頭，使用滑鼠到新的位置移動資料行。</span><span class="sxs-lookup"><span data-stu-id="48a8a-106">When you enable column reordering, users can move a column to a new position by dragging the column header with the mouse.</span></span>  
  
 <span data-ttu-id="48a8a-107">下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="48a8a-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="48a8a-108">如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="48a8a-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48a8a-109">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="48a8a-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="48a8a-110">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="48a8a-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="48a8a-111">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="48a8a-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-enable-column-reordering"></a><span data-ttu-id="48a8a-112">若要啟用資料行重新調整順序</span><span class="sxs-lookup"><span data-stu-id="48a8a-112">To enable column reordering</span></span>  
  
-   <span data-ttu-id="48a8a-113">按一下智慧標籤圖像 (![智慧標籤圖像](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 的右上角<xref:System.Windows.Forms.DataGridView>控制項，然後再選取**啟用資料行重新調整順序**.</span><span class="sxs-lookup"><span data-stu-id="48a8a-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Enable Column Reordering**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a8a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48a8a-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="48a8a-115">如何：凍結 Windows Form DataGridView 控制項中使用設計工具中的資料行</span><span class="sxs-lookup"><span data-stu-id="48a8a-115">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](freeze-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="48a8a-116">如何：建立 Windows Forms 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="48a8a-116">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="48a8a-117">如何：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="48a8a-117">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
