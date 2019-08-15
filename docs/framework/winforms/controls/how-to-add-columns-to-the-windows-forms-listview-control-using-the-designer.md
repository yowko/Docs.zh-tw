---
title: 作法：使用設計工具將資料行新增至 Windows Forms ListView 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: e82fbcf63047873ebc6e5c40b8b9fbeb14a672e5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038174"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="c09d0-102">作法：使用設計工具將資料行新增至 Windows Forms ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="c09d0-102">How to: Add Columns to the Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="c09d0-103">當您<xref:System.Windows.Forms.ListView>在**詳細資料**視圖中時, Windows Forms 控制項可以顯示每個清單專案的多個欄位。</span><span class="sxs-lookup"><span data-stu-id="c09d0-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item when in the **Details** view.</span></span> <span data-ttu-id="c09d0-104">您可以使用這些資料行顯示每個清單專案的數種類型資訊。</span><span class="sxs-lookup"><span data-stu-id="c09d0-104">You can use the columns to display several types of information about each list item.</span></span> <span data-ttu-id="c09d0-105">例如, 檔案清單可以顯示檔案上次修改的檔案名、檔案類型、大小和日期。</span><span class="sxs-lookup"><span data-stu-id="c09d0-105">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="c09d0-106">如需建立資料行的相關資訊, 請參閱[如何:在具有 Windows Forms ListView 控制項](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)的資料行中顯示子項。</span><span class="sxs-lookup"><span data-stu-id="c09d0-106">For information on populating the columns once they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>

<span data-ttu-id="c09d0-107">下列程式需要具有包含<xref:System.Windows.Forms.ListView>控制項之表單的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="c09d0-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="c09d0-108">如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="c09d0-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>


### <a name="to-add-columns-in-the-designer"></a><span data-ttu-id="c09d0-109">若要在設計工具中加入資料行</span><span class="sxs-lookup"><span data-stu-id="c09d0-109">To add columns in the designer</span></span>

1. <span data-ttu-id="c09d0-110">在 [**屬性**] 視窗中, 將控制項<xref:System.Windows.Forms.ListView.View%2A>的屬性<xref:System.Windows.Forms.View.Details>設為。</span><span class="sxs-lookup"><span data-stu-id="c09d0-110">In the **Properties** window, set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>

2. <span data-ttu-id="c09d0-111">在 [**屬性**] 視窗中<xref:System.Windows.Forms.ListView.Columns%2A> , 按一下屬性旁邊![的**省略號**按鈕 (Visual Studio](./media/visual-studio-ellipsis-button.png)的屬性視窗中的省略號按鈕 (...)。</span><span class="sxs-lookup"><span data-stu-id="c09d0-111">In the **Properties** window, click the **Ellipsis** button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>

     <span data-ttu-id="c09d0-112">[ **ColumnHeader 集合編輯器**] 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="c09d0-112">The **ColumnHeader Collection Editor** appears.</span></span>

3. <span data-ttu-id="c09d0-113">使用 [**加入**] 按鈕來加入新的資料行。</span><span class="sxs-lookup"><span data-stu-id="c09d0-113">Use the **Add** button to add new columns.</span></span> <span data-ttu-id="c09d0-114">然後, 您可以選取資料行標頭, 並設定其文字 (欄的標題)、文字對齊和寬度。</span><span class="sxs-lookup"><span data-stu-id="c09d0-114">You can then select the column header and set its text (the caption of the column), text alignment, and width.</span></span>

## <a name="see-also"></a><span data-ttu-id="c09d0-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c09d0-115">See also</span></span>

- [<span data-ttu-id="c09d0-116">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="c09d0-116">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="c09d0-117">如何：使用 Windows Forms ListView 控制項新增和移除專案</span><span class="sxs-lookup"><span data-stu-id="c09d0-117">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="c09d0-118">如何：在具有 Windows Forms ListView 控制項的資料行中顯示子項</span><span class="sxs-lookup"><span data-stu-id="c09d0-118">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="c09d0-119">如何：顯示 Windows Forms ListView 控制項的圖示</span><span class="sxs-lookup"><span data-stu-id="c09d0-119">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="c09d0-120">如何：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c09d0-120">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
