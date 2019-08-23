---
title: HOW TO：在 Windows Forms ListView 控制項中分組項目
ms.date: 03/30/2017
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
ms.openlocfilehash: b4cd2b9ed23f377912270d33b1415ad39c9e80c0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966623"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="09342-102">HOW TO：在 Windows Forms ListView 控制項中分組項目</span><span class="sxs-lookup"><span data-stu-id="09342-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="09342-103">使用<xref:System.Windows.Forms.ListView>控制項的 [群組] 功能, 您可以在群組中顯示相關的專案集合。</span><span class="sxs-lookup"><span data-stu-id="09342-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="09342-104">這些群組會以包含群組標題的水準群組標頭分隔在畫面上。</span><span class="sxs-lookup"><span data-stu-id="09342-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="09342-105">您可以使用<xref:System.Windows.Forms.ListView>群組, 讓您更輕鬆地流覽大型清單, 方法是依字母順序、依日期或任何其他邏輯群組來分組專案。</span><span class="sxs-lookup"><span data-stu-id="09342-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="09342-106">下圖顯示一些群組的專案。</span><span class="sxs-lookup"><span data-stu-id="09342-106">The following image shows some grouped items.</span></span>  
  
 ![奇數和偶數 ListView 群組的螢幕擷取畫面。](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  
   
 <span data-ttu-id="09342-108">若要啟用群組, 您必須先在設計工具或以程式設計方式建立一或多個群組。</span><span class="sxs-lookup"><span data-stu-id="09342-108">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="09342-109">定義群組之後, 您可以將專案指派<xref:System.Windows.Forms.ListView>給群組。</span><span class="sxs-lookup"><span data-stu-id="09342-109">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="09342-110">您也可以透過程式設計的方式, 將專案從一個群組移至另一個。</span><span class="sxs-lookup"><span data-stu-id="09342-110">You can also move items from one group to another programmatically.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09342-111"><xref:System.Windows.Forms.ListView>只有[!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)]當您的應用程式<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>呼叫方法時, 才可以使用群組。</span><span class="sxs-lookup"><span data-stu-id="09342-111"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="09342-112">在舊版作業系統上, 與群組相關的任何程式碼都不會有任何作用, 群組也不會出現。</span><span class="sxs-lookup"><span data-stu-id="09342-112">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="09342-113">如需詳細資訊，請參閱 <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="09342-113">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="09342-114">新增群組</span><span class="sxs-lookup"><span data-stu-id="09342-114">To add groups</span></span>  
  
1. <span data-ttu-id="09342-115">使用 <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> 集合的 <xref:System.Windows.Forms.ListView.Groups%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="09342-115">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="09342-116">移除群組</span><span class="sxs-lookup"><span data-stu-id="09342-116">To remove groups</span></span>  
  
1. <span data-ttu-id="09342-117">使用<xref:System.Windows.Forms.ListView.Groups%2A>集合<xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A>的<xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A>或方法。</span><span class="sxs-lookup"><span data-stu-id="09342-117">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="09342-118">方法會移除單一群組; 此<xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A>方法會從清單中移除所有群組。 <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A></span><span class="sxs-lookup"><span data-stu-id="09342-118">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="09342-119">移除群組並不會移除該群組內的專案。</span><span class="sxs-lookup"><span data-stu-id="09342-119">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="09342-120">將專案指派給群組或在群組之間移動專案</span><span class="sxs-lookup"><span data-stu-id="09342-120">To assign items to groups or move items between groups</span></span>  
  
1. <span data-ttu-id="09342-121">設定個別專案的屬性。<xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="09342-121">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="09342-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09342-122">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="09342-123">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="09342-123">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="09342-124">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="09342-124">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="09342-125">如何：使用 Windows Forms ListView 控制項新增和移除專案</span><span class="sxs-lookup"><span data-stu-id="09342-125">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
