---
title: 作法：使用設計工具將資料行新增至 Windows Forms ListView 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: a37f5d64e8ca10b26a8897d45b8757113ce900c9
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877602"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="3cdf6-102">HOW TO：使用設計工具將資料行新增至 Windows Forms ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="3cdf6-102">How to: Add Columns to the Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="3cdf6-103">Windows Forms<xref:System.Windows.Forms.ListView>控制項可以顯示多個資料行，每個清單項目中的時機**詳細資料**檢視。</span><span class="sxs-lookup"><span data-stu-id="3cdf6-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item when in the **Details** view.</span></span> <span data-ttu-id="3cdf6-104">您可以使用資料行來顯示數種類型的每個清單項目的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3cdf6-104">You can use the columns to display several types of information about each list item.</span></span> <span data-ttu-id="3cdf6-105">例如，檔案名稱、 檔案類型、 大小和檔案上次修改的日期，可以顯示一份檔案。</span><span class="sxs-lookup"><span data-stu-id="3cdf6-105">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="3cdf6-106">如需有關擴展的資料行，建立之後，請參閱[How to:使用 Windows 的資料行顯示子項目 Form ListView 控制項](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="3cdf6-106">For information on populating the columns once they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>  
  
 <span data-ttu-id="3cdf6-107">下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="3cdf6-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="3cdf6-108">如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="3cdf6-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3cdf6-109">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="3cdf6-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="3cdf6-110">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="3cdf6-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="3cdf6-111">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="3cdf6-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-columns-in-the-designer"></a><span data-ttu-id="3cdf6-112">若要加入至設計工具的資料行</span><span class="sxs-lookup"><span data-stu-id="3cdf6-112">To add columns in the designer</span></span>  
  
1. <span data-ttu-id="3cdf6-113">在 [**屬性**] 視窗中，將控制項的<xref:System.Windows.Forms.ListView.View%2A>屬性設<xref:System.Windows.Forms.View.Details>。</span><span class="sxs-lookup"><span data-stu-id="3cdf6-113">In the **Properties** window, set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
2.  <span data-ttu-id="3cdf6-114">在 [**屬性** 視窗中，按一下**省略符號** 按鈕 (![。 Visual Studio 的 [屬性] 視窗中的省略符號按鈕 （...）](./media/visual-studio-ellipsis-button.png)) 旁<xref:System.Windows.Forms.ListView.Columns%2A>屬性.</span><span class="sxs-lookup"><span data-stu-id="3cdf6-114">In the **Properties** window, click the **Ellipsis** button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>  
  
     <span data-ttu-id="3cdf6-115">**ColumnHeader 集合編輯器**隨即出現。</span><span class="sxs-lookup"><span data-stu-id="3cdf6-115">The **ColumnHeader Collection Editor** appears.</span></span>  
  
3. <span data-ttu-id="3cdf6-116">使用**新增**按鈕以新增新的資料行。</span><span class="sxs-lookup"><span data-stu-id="3cdf6-116">Use the **Add** button to add new columns.</span></span> <span data-ttu-id="3cdf6-117">然後，您可以選取資料行標頭，並設定其文字 （資料行的標題）、 文字對齊方式，與寬度。</span><span class="sxs-lookup"><span data-stu-id="3cdf6-117">You can then select the column header and set its text (the caption of the column), text alignment, and width.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cdf6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cdf6-118">See also</span></span>

- [<span data-ttu-id="3cdf6-119">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="3cdf6-119">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="3cdf6-120">如何：新增和移除項目，使用 Windows Forms ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="3cdf6-120">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="3cdf6-121">如何：使用 Windows Forms ListView 控制項的資料行顯示子項目</span><span class="sxs-lookup"><span data-stu-id="3cdf6-121">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="3cdf6-122">如何：Windows Form ListView 控制項中顯示的圖示</span><span class="sxs-lookup"><span data-stu-id="3cdf6-122">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="3cdf6-123">如何：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="3cdf6-123">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
