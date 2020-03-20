---
title: 清單查看控制項中的組專案
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
ms.openlocfilehash: a1754d10de2bbb5895ae861cd17f4af1f18810e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141987"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="7d7f3-102">如何：在 Windows Form ListView 控制項中群組項目</span><span class="sxs-lookup"><span data-stu-id="7d7f3-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="7d7f3-103">使用<xref:System.Windows.Forms.ListView>控制項的分組功能，可以分組顯示相關的專案集。</span><span class="sxs-lookup"><span data-stu-id="7d7f3-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="7d7f3-104">這些組在螢幕上由包含組標題的水準組標題分隔。</span><span class="sxs-lookup"><span data-stu-id="7d7f3-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="7d7f3-105">您可以使用<xref:System.Windows.Forms.ListView>組通過按字母順序、按日期或通過任何其他邏輯分組對專案進行分組，使導航大型清單變得更加容易。</span><span class="sxs-lookup"><span data-stu-id="7d7f3-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="7d7f3-106">下圖顯示了一些分組專案。</span><span class="sxs-lookup"><span data-stu-id="7d7f3-106">The following image shows some grouped items.</span></span>  
  
 ![奇數和偶數清單視圖組的螢幕截圖。](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  

 <span data-ttu-id="7d7f3-108">要啟用分組，必須首先在設計器中或以程式設計方式創建一個或多個組。</span><span class="sxs-lookup"><span data-stu-id="7d7f3-108">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="7d7f3-109">定義組後，可以將專案分配給<xref:System.Windows.Forms.ListView>組。</span><span class="sxs-lookup"><span data-stu-id="7d7f3-109">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="7d7f3-110">您還可以以程式設計方式將專案從一個組移動到另一個組。</span><span class="sxs-lookup"><span data-stu-id="7d7f3-110">You can also move items from one group to another programmatically.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="7d7f3-111">添加組</span><span class="sxs-lookup"><span data-stu-id="7d7f3-111">To add groups</span></span>  
  
1. <span data-ttu-id="7d7f3-112">使用 <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> 集合的 <xref:System.Windows.Forms.ListView.Groups%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7d7f3-112">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="7d7f3-113">刪除組</span><span class="sxs-lookup"><span data-stu-id="7d7f3-113">To remove groups</span></span>  
  
1. <span data-ttu-id="7d7f3-114">使用<xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A>集合<xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A>的<xref:System.Windows.Forms.ListView.Groups%2A>或 方法。</span><span class="sxs-lookup"><span data-stu-id="7d7f3-114">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="7d7f3-115">該方法<xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A>刪除單個組;因此，該方法將刪除單個組。該方法<xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A>從清單中刪除所有組。</span><span class="sxs-lookup"><span data-stu-id="7d7f3-115">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7d7f3-116">刪除組不會刪除該組中的專案。</span><span class="sxs-lookup"><span data-stu-id="7d7f3-116">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="7d7f3-117">將專案分配給組或在組之間移動專案</span><span class="sxs-lookup"><span data-stu-id="7d7f3-117">To assign items to groups or move items between groups</span></span>  
  
1. <span data-ttu-id="7d7f3-118">設置<xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType>單個項的屬性。</span><span class="sxs-lookup"><span data-stu-id="7d7f3-118">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="7d7f3-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d7f3-119">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="7d7f3-120">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="7d7f3-120">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="7d7f3-121">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="7d7f3-121">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="7d7f3-122">操作說明：使用 Windows Forms ListView 控制項加入和移除項目</span><span class="sxs-lookup"><span data-stu-id="7d7f3-122">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
