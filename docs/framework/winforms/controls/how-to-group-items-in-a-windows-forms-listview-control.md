---
title: "如何：在 Windows Form ListView 控制項中群組項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- lists [Windows Forms], grouping items
- grouping
- list views [Windows Forms], grouping items
- groups
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 610416a1-8da4-436c-af19-5f19e654769b
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c22134513c2c6a3ff2bc621e68f546b7bcc93ba9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="d5cc7-102">如何：在 Windows Form ListView 控制項中群組項目</span><span class="sxs-lookup"><span data-stu-id="d5cc7-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="d5cc7-103">使用群組功能的<xref:System.Windows.Forms.ListView>控制項，您可以在群組中顯示相關的項目集。</span><span class="sxs-lookup"><span data-stu-id="d5cc7-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="d5cc7-104">這些群組是在螢幕上分隔包含群組標題的水平群組標頭。</span><span class="sxs-lookup"><span data-stu-id="d5cc7-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="d5cc7-105">您可以使用<xref:System.Windows.Forms.ListView>群組，使導覽更容易的大型清單分組為項目依字母順序，依日期，或任何其他邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="d5cc7-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="d5cc7-106">下圖顯示一些群組項目。</span><span class="sxs-lookup"><span data-stu-id="d5cc7-106">The following image shows some grouped items.</span></span>  
  
 <span data-ttu-id="d5cc7-107">![ListView 群組](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")</span><span class="sxs-lookup"><span data-stu-id="d5cc7-107">![ListView Groups](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")</span></span>  
<span data-ttu-id="d5cc7-108">ListView 群組項目</span><span class="sxs-lookup"><span data-stu-id="d5cc7-108">ListView grouped items</span></span>  
  
 <span data-ttu-id="d5cc7-109">若要啟用群組，您必須先建立一個或多個群組，在設計工具或以程式設計的方式。</span><span class="sxs-lookup"><span data-stu-id="d5cc7-109">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="d5cc7-110">定義群組之後，您可以指派<xref:System.Windows.Forms.ListView>到群組的項目。</span><span class="sxs-lookup"><span data-stu-id="d5cc7-110">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="d5cc7-111">您也可以移動項目從一個群組到另一個以程式設計的方式。</span><span class="sxs-lookup"><span data-stu-id="d5cc7-111">You can also move items from one group to another programmatically.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5cc7-112"><xref:System.Windows.Forms.ListView>群組是僅適用於[!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)]當您的應用程式呼叫<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="d5cc7-112"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d5cc7-113">在舊版作業系統，與群組相關的任何程式碼都無效，不會出現群組。</span><span class="sxs-lookup"><span data-stu-id="d5cc7-113">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="d5cc7-114">如需詳細資訊，請參閱<xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="d5cc7-114">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="d5cc7-115">若要加入群組</span><span class="sxs-lookup"><span data-stu-id="d5cc7-115">To add groups</span></span>  
  
1.  <span data-ttu-id="d5cc7-116">使用 <xref:System.Windows.Forms.ListView.Groups%2A> 集合的 <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d5cc7-116">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="d5cc7-117">若要移除群組</span><span class="sxs-lookup"><span data-stu-id="d5cc7-117">To remove groups</span></span>  
  
1.  <span data-ttu-id="d5cc7-118">使用<xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A>或<xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A>方法<xref:System.Windows.Forms.ListView.Groups%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="d5cc7-118">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="d5cc7-119"><xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A>方法會移除單一群組;<xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A>方法從清單中移除所有群組。</span><span class="sxs-lookup"><span data-stu-id="d5cc7-119">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d5cc7-120">移除群組並不會移除該群組內的項目。</span><span class="sxs-lookup"><span data-stu-id="d5cc7-120">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="d5cc7-121">若要將項目指派給群組或群組之間移動項目</span><span class="sxs-lookup"><span data-stu-id="d5cc7-121">To assign items to groups or move items between groups</span></span>  
  
1.  <span data-ttu-id="d5cc7-122">設定<xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType>個別項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="d5cc7-122">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="d5cc7-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5cc7-123">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ListViewGroup>  
 [<span data-ttu-id="d5cc7-124">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="d5cc7-124">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="d5cc7-125">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="d5cc7-125">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="d5cc7-126">Windows XP 功能和 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="d5cc7-126">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [<span data-ttu-id="d5cc7-127">操作說明：使用 Windows Forms ListView 控制項加入和移除項目</span><span class="sxs-lookup"><span data-stu-id="d5cc7-127">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
