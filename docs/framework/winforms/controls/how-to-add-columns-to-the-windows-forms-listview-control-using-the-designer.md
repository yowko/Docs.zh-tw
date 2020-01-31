---
title: 使用設計工具將資料行新增至 ListView 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: 627f8627aac861877a05c13def07427199807754
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744613"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="535b5-102">如何：使用設計工具在 Windows Form ListView 控制項中加入資料行</span><span class="sxs-lookup"><span data-stu-id="535b5-102">How to: Add Columns to the Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="535b5-103">在**詳細資料**視圖中，Windows Forms <xref:System.Windows.Forms.ListView> 控制項可以顯示每個清單專案的多個欄位。</span><span class="sxs-lookup"><span data-stu-id="535b5-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item when in the **Details** view.</span></span> <span data-ttu-id="535b5-104">您可以使用這些資料行顯示每個清單專案的數種類型資訊。</span><span class="sxs-lookup"><span data-stu-id="535b5-104">You can use the columns to display several types of information about each list item.</span></span> <span data-ttu-id="535b5-105">例如，檔案清單可以顯示檔案上次修改的檔案名、檔案類型、大小和日期。</span><span class="sxs-lookup"><span data-stu-id="535b5-105">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="535b5-106">如需建立資料行的相關資訊，請參閱[如何：在具有 Windows Forms ListView 控制項的資料行中顯示](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)子工作。</span><span class="sxs-lookup"><span data-stu-id="535b5-106">For information on populating the columns once they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>

<span data-ttu-id="535b5-107">下列程式需要具有包含 <xref:System.Windows.Forms.ListView> 控制項之表單的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="535b5-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="535b5-108">如需設定這類專案的相關資訊，請參閱[如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：將控制項加入至 Windows Forms](how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="535b5-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-add-columns-in-the-designer"></a><span data-ttu-id="535b5-109">若要在設計工具中加入資料行</span><span class="sxs-lookup"><span data-stu-id="535b5-109">To add columns in the designer</span></span>

1. <span data-ttu-id="535b5-110">在 [**屬性**] 視窗中，將控制項的 [<xref:System.Windows.Forms.ListView.View%2A>] 屬性設定為 [<xref:System.Windows.Forms.View.Details>]。</span><span class="sxs-lookup"><span data-stu-id="535b5-110">In the **Properties** window, set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>

2. <span data-ttu-id="535b5-111">在 [**屬性**] 視窗中，按一下 [<xref:System.Windows.Forms.ListView.Columns%2A>] 屬性旁邊的**省略號**按鈕（![Visual Studio.](./media/visual-studio-ellipsis-button.png)）屬性視窗中的省略號按鈕（...）。</span><span class="sxs-lookup"><span data-stu-id="535b5-111">In the **Properties** window, click the **Ellipsis** button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>

     <span data-ttu-id="535b5-112">[ **ColumnHeader 集合編輯器**] 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="535b5-112">The **ColumnHeader Collection Editor** appears.</span></span>

3. <span data-ttu-id="535b5-113">使用 [**加入**] 按鈕來加入新的資料行。</span><span class="sxs-lookup"><span data-stu-id="535b5-113">Use the **Add** button to add new columns.</span></span> <span data-ttu-id="535b5-114">然後，您可以選取資料行標頭，並設定其文字（欄的標題）、文字對齊和寬度。</span><span class="sxs-lookup"><span data-stu-id="535b5-114">You can then select the column header and set its text (the caption of the column), text alignment, and width.</span></span>

## <a name="see-also"></a><span data-ttu-id="535b5-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="535b5-115">See also</span></span>

- [<span data-ttu-id="535b5-116">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="535b5-116">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="535b5-117">操作說明：使用 Windows Forms ListView 控制項加入和移除項目</span><span class="sxs-lookup"><span data-stu-id="535b5-117">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="535b5-118">操作說明：使用 Windows Forms ListView 控制項以資料行顯示子項目</span><span class="sxs-lookup"><span data-stu-id="535b5-118">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="535b5-119">操作說明：顯示 Windows Forms ListView 控制項的圖示</span><span class="sxs-lookup"><span data-stu-id="535b5-119">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="535b5-120">操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="535b5-120">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
