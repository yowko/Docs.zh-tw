---
title: 如何：在 Windows Form ListView 控制項中群組項目
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
ms.openlocfilehash: 1b716498ec5a45fbde499a1f53b2bdccd28a7176
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960170"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="0d475-102">如何：在 Windows Form ListView 控制項中群組項目</span><span class="sxs-lookup"><span data-stu-id="0d475-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="0d475-103">有了 <xref:System.Windows.Forms.ListView> 控制項的群組功能，您就可以在群組中顯示相關的專案集合。</span><span class="sxs-lookup"><span data-stu-id="0d475-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="0d475-104">這些群組會以包含群組標題的水準群組標頭分隔在畫面上。</span><span class="sxs-lookup"><span data-stu-id="0d475-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="0d475-105">您可以使用 <xref:System.Windows.Forms.ListView> 群組，讓您更輕鬆地流覽大型清單，方法是依字母順序、依日期或任何其他邏輯群組來分組專案。</span><span class="sxs-lookup"><span data-stu-id="0d475-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="0d475-106">下圖顯示一些群組的專案。</span><span class="sxs-lookup"><span data-stu-id="0d475-106">The following image shows some grouped items.</span></span>  
  
 ![奇數和偶數 ListView 群組的螢幕擷取畫面。](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  
   
 <span data-ttu-id="0d475-108">若要啟用群組，您必須先在設計工具或以程式設計方式建立一或多個群組。</span><span class="sxs-lookup"><span data-stu-id="0d475-108">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="0d475-109">定義群組之後，您可以將 <xref:System.Windows.Forms.ListView> 專案指派給群組。</span><span class="sxs-lookup"><span data-stu-id="0d475-109">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="0d475-110">您也可以透過程式設計的方式，將專案從一個群組移至另一個。</span><span class="sxs-lookup"><span data-stu-id="0d475-110">You can also move items from one group to another programmatically.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="0d475-111">新增群組</span><span class="sxs-lookup"><span data-stu-id="0d475-111">To add groups</span></span>  
  
1. <span data-ttu-id="0d475-112">使用 <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> 集合的 <xref:System.Windows.Forms.ListView.Groups%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="0d475-112">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="0d475-113">移除群組</span><span class="sxs-lookup"><span data-stu-id="0d475-113">To remove groups</span></span>  
  
1. <span data-ttu-id="0d475-114">使用 <xref:System.Windows.Forms.ListView.Groups%2A> 集合的 <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> 或 <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="0d475-114">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="0d475-115"><xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> 方法會移除單一群組;<xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> 方法會從清單中移除所有群組。</span><span class="sxs-lookup"><span data-stu-id="0d475-115">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0d475-116">移除群組並不會移除該群組內的專案。</span><span class="sxs-lookup"><span data-stu-id="0d475-116">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="0d475-117">將專案指派給群組或在群組之間移動專案</span><span class="sxs-lookup"><span data-stu-id="0d475-117">To assign items to groups or move items between groups</span></span>  
  
1. <span data-ttu-id="0d475-118">設定個別專案的 <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="0d475-118">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="0d475-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="0d475-119">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="0d475-120">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="0d475-120">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="0d475-121">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="0d475-121">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="0d475-122">操作說明：使用 Windows Forms ListView 控制項加入和移除項目</span><span class="sxs-lookup"><span data-stu-id="0d475-122">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
