---
title: 使用設計工具在 ListView 控制項中群組專案
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: 935d8d75517e1028e686ca229f6ada656f58b01e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736678"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="d620f-102">如何：使用設計工具群組 Windows Form ListView 控制項中的項目</span><span class="sxs-lookup"><span data-stu-id="d620f-102">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="d620f-103">[<xref:System.Windows.Forms.ListView>] 控制項的 [群組] 功能可讓您在群組中顯示相關的專案集合。</span><span class="sxs-lookup"><span data-stu-id="d620f-103">The grouping feature of the <xref:System.Windows.Forms.ListView> control enables you to display related sets of items in groups.</span></span> <span data-ttu-id="d620f-104">這些群組會以包含群組標題的水準群組標頭分隔在畫面上。</span><span class="sxs-lookup"><span data-stu-id="d620f-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="d620f-105">您可以使用 <xref:System.Windows.Forms.ListView> 群組，讓您更輕鬆地流覽大型清單，方法是依字母順序、依日期或任何其他邏輯群組來分組專案。</span><span class="sxs-lookup"><span data-stu-id="d620f-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="d620f-106">下圖顯示一些群組專案：</span><span class="sxs-lookup"><span data-stu-id="d620f-106">The following image shows some grouped items:</span></span>

![以奇數和偶數群組分隔的數位。](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

<span data-ttu-id="d620f-108">下列程式需要具有包含 <xref:System.Windows.Forms.ListView> 控制項之表單的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="d620f-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="d620f-109">如需設定這類專案的相關資訊，請參閱[如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：將控制項加入至 Windows Forms](how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="d620f-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

<span data-ttu-id="d620f-110">若要啟用群組，您必須先在設計師或以程式設計方式建立一或多個 <xref:System.Windows.Forms.ListViewGroup> 物件。</span><span class="sxs-lookup"><span data-stu-id="d620f-110">To enable grouping, you must first create one or more <xref:System.Windows.Forms.ListViewGroup> objects either in the designer or programmatically.</span></span> <span data-ttu-id="d620f-111">定義群組之後，您就可以將專案指派給它。</span><span class="sxs-lookup"><span data-stu-id="d620f-111">Once a group has been defined, you can assign items to it.</span></span>

## <a name="to-add-or-remove-groups-in-the-designer"></a><span data-ttu-id="d620f-112">若要在設計工具中新增或移除群組</span><span class="sxs-lookup"><span data-stu-id="d620f-112">To add or remove groups in the designer</span></span>

1. <span data-ttu-id="d620f-113">在 **屬性** 視窗中<xref:System.Windows.Forms.ListView.Groups%2A> ，按一下屬性 (![旁邊的**省略號**Visual Studio](./media/visual-studio-ellipsis-button.png)) 的屬性視窗中的省略號按鈕（...） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d620f-113">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Groups%2A> property.</span></span>

     <span data-ttu-id="d620f-114">[ **ListViewGroup 集合編輯器**] 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d620f-114">The **ListViewGroup Collection Editor** appears.</span></span>

2. <span data-ttu-id="d620f-115">若要新增群組，請按一下 [**新增**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d620f-115">To add a group, click the **Add** button.</span></span> <span data-ttu-id="d620f-116">接著，您可以設定新群組的屬性，例如 [<xref:System.Windows.Forms.ListViewGroup.Header%2A>] 和 [<xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> 屬性]。</span><span class="sxs-lookup"><span data-stu-id="d620f-116">You can then set properties of the new group, such as the <xref:System.Windows.Forms.ListViewGroup.Header%2A> and <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> properties.</span></span> <span data-ttu-id="d620f-117">若要移除群組，請選取它，然後按一下 [**移除**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d620f-117">To remove a group, select it and click the **Remove** button.</span></span>

## <a name="to-assign-items-to-groups-in-the-designer"></a><span data-ttu-id="d620f-118">若要在設計工具中將專案指派給群組</span><span class="sxs-lookup"><span data-stu-id="d620f-118">To assign items to groups in the designer</span></span>

1. <span data-ttu-id="d620f-119">在 **屬性** 視窗中<xref:System.Windows.Forms.ListView.Items%2A> ，按一下屬性 (![旁邊的**省略號**Visual Studio](./media/visual-studio-ellipsis-button.png)) 的屬性視窗中的省略號按鈕（...） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d620f-119">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>

     <span data-ttu-id="d620f-120">[ **ListViewItem 集合編輯器**] 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d620f-120">The **ListViewItem Collection Editor** appears.</span></span>

2. <span data-ttu-id="d620f-121">若要加入新專案，請按一下 **[新增**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d620f-121">To add a new item, click the **Add** button.</span></span> <span data-ttu-id="d620f-122">接著，您可以設定新專案的屬性，例如 [<xref:System.Windows.Forms.ListViewItem.Text%2A>] 和 [<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> 屬性]。</span><span class="sxs-lookup"><span data-stu-id="d620f-122">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListViewItem.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>

3. <span data-ttu-id="d620f-123">選取 [<xref:System.Windows.Forms.ListViewItem.Group%2A>] 屬性，並從下拉式清單中選擇一個群組。</span><span class="sxs-lookup"><span data-stu-id="d620f-123">Select the <xref:System.Windows.Forms.ListViewItem.Group%2A> property and choose a group from the drop-down list.</span></span>

## <a name="see-also"></a><span data-ttu-id="d620f-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="d620f-124">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="d620f-125">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="d620f-125">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="d620f-126">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="d620f-126">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="d620f-127">操作說明：使用 Windows Forms ListView 控制項加入和移除項目</span><span class="sxs-lookup"><span data-stu-id="d620f-127">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
