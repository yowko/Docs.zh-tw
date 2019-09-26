---
title: 作法：使用設計工具在 Windows Forms ListView 控制項中分組項目
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: b63bcd9e5e357db350cc2987e09af84eb58bdcff
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "69039405"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="92444-102">HOW TO：使用設計工具在 Windows Forms ListView 控制項中分組項目</span><span class="sxs-lookup"><span data-stu-id="92444-102">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="92444-103"><xref:System.Windows.Forms.ListView>控制項的群組功能可讓您在群組中顯示相關的專案集合。</span><span class="sxs-lookup"><span data-stu-id="92444-103">The grouping feature of the <xref:System.Windows.Forms.ListView> control enables you to display related sets of items in groups.</span></span> <span data-ttu-id="92444-104">這些群組會以包含群組標題的水準群組標頭分隔在畫面上。</span><span class="sxs-lookup"><span data-stu-id="92444-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="92444-105">您可以使用<xref:System.Windows.Forms.ListView>群組，讓您更輕鬆地流覽大型清單，方法是依字母順序、依日期或任何其他邏輯群組來分組專案。</span><span class="sxs-lookup"><span data-stu-id="92444-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="92444-106">下圖顯示一些群組專案：</span><span class="sxs-lookup"><span data-stu-id="92444-106">The following image shows some grouped items:</span></span>

![以奇數和偶數群組分隔的數位。](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

<span data-ttu-id="92444-108">下列程式需要具有包含<xref:System.Windows.Forms.ListView>控制項之表單的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="92444-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="92444-109">如需設定這類專案的相關資訊， [請參閱如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ， [以及如何：將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="92444-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

<span data-ttu-id="92444-110">若要啟用群組，您必須先在設計師或<xref:System.Windows.Forms.ListViewGroup>以程式設計方式建立一或多個物件。</span><span class="sxs-lookup"><span data-stu-id="92444-110">To enable grouping, you must first create one or more <xref:System.Windows.Forms.ListViewGroup> objects either in the designer or programmatically.</span></span> <span data-ttu-id="92444-111">定義群組之後，您就可以將專案指派給它。</span><span class="sxs-lookup"><span data-stu-id="92444-111">Once a group has been defined, you can assign items to it.</span></span>

> [!NOTE]
> <span data-ttu-id="92444-112"><xref:System.Windows.Forms.ListView>只有[!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)]當您的應用程式<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>呼叫方法時，才可以使用群組。</span><span class="sxs-lookup"><span data-stu-id="92444-112"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="92444-113">在舊版作業系統上，與群組相關的任何程式碼都不會有任何作用，群組也不會出現。</span><span class="sxs-lookup"><span data-stu-id="92444-113">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="92444-114">如需詳細資訊，請參閱<xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="92444-114">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>

## <a name="to-add-or-remove-groups-in-the-designer"></a><span data-ttu-id="92444-115">若要在設計工具中新增或移除群組</span><span class="sxs-lookup"><span data-stu-id="92444-115">To add or remove groups in the designer</span></span>

1. <span data-ttu-id="92444-116">在 [**屬性**] 視窗中<xref:System.Windows.Forms.ListView.Groups%2A> ，按一下屬性![旁邊的**省略號**（[Visual Studio](./media/visual-studio-ellipsis-button.png)的屬性視窗中的省略號按鈕（...）] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="92444-116">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Groups%2A> property.</span></span>

     <span data-ttu-id="92444-117">[ **ListViewGroup 集合編輯器**] 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="92444-117">The **ListViewGroup Collection Editor** appears.</span></span>

2. <span data-ttu-id="92444-118">若要新增群組，請按一下 [**新增**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="92444-118">To add a group, click the **Add** button.</span></span> <span data-ttu-id="92444-119">接著，您可以設定新群組的屬性，例如<xref:System.Windows.Forms.ListViewGroup.Header%2A>和<xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="92444-119">You can then set properties of the new group, such as the <xref:System.Windows.Forms.ListViewGroup.Header%2A> and <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> properties.</span></span> <span data-ttu-id="92444-120">若要移除群組，請選取它，然後按一下 [**移除**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="92444-120">To remove a group, select it and click the **Remove** button.</span></span>

## <a name="to-assign-items-to-groups-in-the-designer"></a><span data-ttu-id="92444-121">若要在設計工具中將專案指派給群組</span><span class="sxs-lookup"><span data-stu-id="92444-121">To assign items to groups in the designer</span></span>

1. <span data-ttu-id="92444-122">在 [**屬性**] 視窗中<xref:System.Windows.Forms.ListView.Items%2A> ，按一下屬性![旁邊的**省略號**（[Visual Studio](./media/visual-studio-ellipsis-button.png)的屬性視窗中的省略號按鈕（...）] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="92444-122">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>

     <span data-ttu-id="92444-123">[ **ListViewItem 集合編輯器**] 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="92444-123">The **ListViewItem Collection Editor** appears.</span></span>

2. <span data-ttu-id="92444-124">若要加入新專案，請按一下 **[新增**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="92444-124">To add a new item, click the **Add** button.</span></span> <span data-ttu-id="92444-125">接著，您可以設定新專案的屬性，例如<xref:System.Windows.Forms.ListViewItem.Text%2A>和<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="92444-125">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListViewItem.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>

3. <span data-ttu-id="92444-126"><xref:System.Windows.Forms.ListViewItem.Group%2A>選取屬性，並從下拉式清單中選擇群組。</span><span class="sxs-lookup"><span data-stu-id="92444-126">Select the <xref:System.Windows.Forms.ListViewItem.Group%2A> property and choose a group from the drop-down list.</span></span>

## <a name="see-also"></a><span data-ttu-id="92444-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92444-127">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="92444-128">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="92444-128">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="92444-129">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="92444-129">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="92444-130">如何：使用 Windows Forms ListView 控制項新增和移除專案</span><span class="sxs-lookup"><span data-stu-id="92444-130">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
