---
title: 使用設計工具在 ListView 控制項中新增和移除專案
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: cab40c556d9e5d21ce15bcd3d4da367bc08f33ab
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732304"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="f8dee-102">如何：使用設計工具搭配 Windows Form ListView 控制項加入和移除項目</span><span class="sxs-lookup"><span data-stu-id="f8dee-102">How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="f8dee-103">將專案加入至 Windows Forms <xref:System.Windows.Forms.ListView> 控制項的程式主要是由指定專案，並為其指派屬性。</span><span class="sxs-lookup"><span data-stu-id="f8dee-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="f8dee-104">您可以隨時完成新增或移除清單專案。</span><span class="sxs-lookup"><span data-stu-id="f8dee-104">Adding or removing list items can be done at any time.</span></span>

<span data-ttu-id="f8dee-105">下列程式需要具有包含 <xref:System.Windows.Forms.ListView> 控制項之表單的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="f8dee-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="f8dee-106">如需設定這類專案的相關資訊，請參閱[如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：將控制項加入至 Windows Forms](how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="f8dee-106">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-add-or-remove-items-using-the-designer"></a><span data-ttu-id="f8dee-107">若要使用設計工具加入或移除專案</span><span class="sxs-lookup"><span data-stu-id="f8dee-107">To add or remove items using the designer</span></span>

1. <span data-ttu-id="f8dee-108">選取 <xref:System.Windows.Forms.ListView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="f8dee-108">Select the <xref:System.Windows.Forms.ListView> control.</span></span>

2. <span data-ttu-id="f8dee-109">在 [**屬性**] 視窗中，按一下 [<xref:System.Windows.Forms.ListView.Items%2A>] 屬性旁邊的**省略號**（![[屬性視窗的 Visual Studio.](./media/visual-studio-ellipsis-button.png)）] 按鈕中的省略號按鈕（...）。</span><span class="sxs-lookup"><span data-stu-id="f8dee-109">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>

     <span data-ttu-id="f8dee-110">[ **ListViewItem 集合編輯器**] 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="f8dee-110">The **ListViewItem Collection Editor** appears.</span></span>

3. <span data-ttu-id="f8dee-111">若要新增專案，請按一下 [**新增**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f8dee-111">To add an item, click the **Add** button.</span></span> <span data-ttu-id="f8dee-112">接著，您可以設定新專案的屬性，例如 [<xref:System.Windows.Forms.ListView.Text%2A>] 和 [<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> 屬性]。</span><span class="sxs-lookup"><span data-stu-id="f8dee-112">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListView.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>

4. <span data-ttu-id="f8dee-113">若要移除專案，請選取它，然後按一下 [**移除**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f8dee-113">To remove an item, select it and click the **Remove** button.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8dee-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8dee-114">See also</span></span>

- [<span data-ttu-id="f8dee-115">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="f8dee-115">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="f8dee-116">操作說明：將資料行加入至 Windows Forms ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="f8dee-116">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="f8dee-117">操作說明：使用 Windows Forms ListView 控制項以資料行顯示子項目</span><span class="sxs-lookup"><span data-stu-id="f8dee-117">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="f8dee-118">操作說明：顯示 Windows Forms ListView 控制項的圖示</span><span class="sxs-lookup"><span data-stu-id="f8dee-118">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="f8dee-119">操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f8dee-119">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [<span data-ttu-id="f8dee-120">操作說明：在 Windows Forms ListView 控制項中群組項目</span><span class="sxs-lookup"><span data-stu-id="f8dee-120">How to: Group Items in a Windows Forms ListView Control</span></span>](how-to-group-items-in-a-windows-forms-listview-control.md)
