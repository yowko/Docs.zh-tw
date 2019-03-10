---
title: HOW TO：使用設計工具將 Windows Forms ListView 控制項中的群組項目
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: 4c3e20ad7a09cc21e6c1d2a6d8fbbc47d11c903d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703552"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="e1aa4-102">HOW TO：使用設計工具將 Windows Forms ListView 控制項中的群組項目</span><span class="sxs-lookup"><span data-stu-id="e1aa4-102">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="e1aa4-103">分組功能<xref:System.Windows.Forms.ListView>控制項可讓您以群組顯示相關的項目集。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-103">The grouping feature of the <xref:System.Windows.Forms.ListView> control enables you to display related sets of items in groups.</span></span> <span data-ttu-id="e1aa4-104">這些群組是在螢幕上分隔包含群組標題的水平群組標頭。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="e1aa4-105">您可以使用<xref:System.Windows.Forms.ListView>群組，使導覽更容易的大型清單依字母順序，分組項目，依日期，或任何其他的邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="e1aa4-106">下圖顯示一些分組的項目。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-106">The following image shows some grouped items.</span></span>  
  
 <span data-ttu-id="e1aa4-107">![ListView 群組](./media/listviewgroups.gif "ListViewGroups")</span><span class="sxs-lookup"><span data-stu-id="e1aa4-107">![ListView Groups](./media/listviewgroups.gif "ListViewGroups")</span></span>  
  
 <span data-ttu-id="e1aa4-108">下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="e1aa4-109">如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
 <span data-ttu-id="e1aa4-110">若要啟用群組，您必須先建立一或多個<xref:System.Windows.Forms.ListViewGroup>物件在設計工具或以程式設計的方式。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-110">To enable grouping, you must first create one or more <xref:System.Windows.Forms.ListViewGroup> objects either in the designer or programmatically.</span></span> <span data-ttu-id="e1aa4-111">一旦已定義的群組，您可以指派給它的項目。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-111">Once a group has been defined, you can assign items to it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1aa4-112"><xref:System.Windows.Forms.ListView> 群組是僅適用於[!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)]當您的應用程式呼叫<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-112"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e1aa4-113">在舊版的作業系統，與群組相關的任何程式碼沒有任何作用，並不會出現群組。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-113">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="e1aa4-114">如需詳細資訊，請參閱<xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-114">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>  
>   
>  <span data-ttu-id="e1aa4-115">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-115">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e1aa4-116">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-116">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e1aa4-117">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-117">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-groups-in-the-designer"></a><span data-ttu-id="e1aa4-118">若要新增或移除群組，在設計工具</span><span class="sxs-lookup"><span data-stu-id="e1aa4-118">To add or remove groups in the designer</span></span>  
  
1.  <span data-ttu-id="e1aa4-119">在 [**屬性**] 視窗中，按一下**省略符號**(![VisualStudioEllipsesButton 螢幕擷取畫面](../media/vbellipsesbutton.png "vbEllipsesButton")) 下一步按鈕<xref:System.Windows.Forms.ListView.Groups%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-119">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.ListView.Groups%2A> property.</span></span>  
  
     <span data-ttu-id="e1aa4-120">**ListViewGroup 集合編輯器**隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-120">The **ListViewGroup Collection Editor** appears.</span></span>  
  
2.  <span data-ttu-id="e1aa4-121">若要新增的群組，請按一下**新增** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-121">To add a group, click the **Add** button.</span></span> <span data-ttu-id="e1aa4-122">您可以再設定屬性的新群組，例如<xref:System.Windows.Forms.ListViewGroup.Header%2A>和<xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-122">You can then set properties of the new group, such as the <xref:System.Windows.Forms.ListViewGroup.Header%2A> and <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> properties.</span></span> <span data-ttu-id="e1aa4-123">若要移除群組，請選取它，然後按一下**移除** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-123">To remove a group, select it and click the **Remove** button.</span></span>  
  
### <a name="to-assign-items-to-groups-in-the-designer"></a><span data-ttu-id="e1aa4-124">若要將項目指派給設計工具中的群組</span><span class="sxs-lookup"><span data-stu-id="e1aa4-124">To assign items to groups in the designer</span></span>  
  
1.  <span data-ttu-id="e1aa4-125">在 [**屬性**] 視窗中，按一下**省略符號**(![VisualStudioEllipsesButton 螢幕擷取畫面](../media/vbellipsesbutton.png "vbEllipsesButton")) 下一步按鈕<xref:System.Windows.Forms.ListView.Items%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-125">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     <span data-ttu-id="e1aa4-126">**ListViewItem 集合編輯器**隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-126">The **ListViewItem Collection Editor** appears.</span></span>  
  
2.  <span data-ttu-id="e1aa4-127">若要加入新項目，按一下**新增** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-127">To add a new item, click the **Add** button.</span></span> <span data-ttu-id="e1aa4-128">您可以再設定屬性的新的項目，例如<xref:System.Windows.Forms.ListViewItem.Text%2A>和<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-128">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListViewItem.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>  
  
3.  <span data-ttu-id="e1aa4-129">選取<xref:System.Windows.Forms.ListViewItem.Group%2A>屬性，然後從下拉式清單中選擇 群組。</span><span class="sxs-lookup"><span data-stu-id="e1aa4-129">Select the <xref:System.Windows.Forms.ListViewItem.Group%2A> property and choose a group from the drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1aa4-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1aa4-130">See also</span></span>
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="e1aa4-131">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="e1aa4-131">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="e1aa4-132">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="e1aa4-132">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="e1aa4-133">如何：新增和移除項目，使用 Windows Forms ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="e1aa4-133">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
