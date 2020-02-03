---
title: 在具有 ListView 控制項的資料行中顯示子項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items
- Details view
- ListView control [Windows Forms], adding ListSubItems
- subitems
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
ms.openlocfilehash: 5c6d807410ad4ee0198d6334844bd65b148edff4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745540"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a><span data-ttu-id="00a4b-102">如何：使用 Windows Form ListView 控制項以資料行顯示子項目</span><span class="sxs-lookup"><span data-stu-id="00a4b-102">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>
<span data-ttu-id="00a4b-103">Windows Forms <xref:System.Windows.Forms.ListView> 控制項可以針對詳細資料檢視中的每個專案顯示額外的文字或子專案。</span><span class="sxs-lookup"><span data-stu-id="00a4b-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display additional text, or subitems, for each item in the Details view.</span></span> <span data-ttu-id="00a4b-104">第一個資料行顯示專案文字，例如員工編號。</span><span class="sxs-lookup"><span data-stu-id="00a4b-104">The first column displays the item text, for example an employee number.</span></span> <span data-ttu-id="00a4b-105">第二、第三和後續的資料行顯示第一個、第二個和後續相關聯的子工作。</span><span class="sxs-lookup"><span data-stu-id="00a4b-105">The second, third, and subsequent columns display the first, second, and subsequent associated subitems.</span></span>  
  
### <a name="to-add-subitems-to-a-list-item"></a><span data-ttu-id="00a4b-106">將子專案加入至清單專案</span><span class="sxs-lookup"><span data-stu-id="00a4b-106">To add subitems to a list item</span></span>  
  
1. <span data-ttu-id="00a4b-107">加入所需的任何資料行。</span><span class="sxs-lookup"><span data-stu-id="00a4b-107">Add any columns needed.</span></span> <span data-ttu-id="00a4b-108">因為第一個資料行會顯示專案的 <xref:System.Windows.Forms.ListView.Text%2A> 屬性，所以您所需的資料行比子專案多一個。</span><span class="sxs-lookup"><span data-stu-id="00a4b-108">Because the first column will display the item's <xref:System.Windows.Forms.ListView.Text%2A> property, you need one more column than there are subitems.</span></span> <span data-ttu-id="00a4b-109">如需新增資料行的詳細資訊，請參閱[如何：將資料行加入至 Windows Forms ListView 控制項](how-to-add-columns-to-the-windows-forms-listview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="00a4b-109">For more information on adding columns, see [How to: Add Columns to the Windows Forms ListView Control](how-to-add-columns-to-the-windows-forms-listview-control.md).</span></span>  
  
2. <span data-ttu-id="00a4b-110">呼叫專案的 <xref:System.Windows.Forms.ListViewItem.SubItems%2A> 屬性所傳回之集合的 <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="00a4b-110">Call the <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.ListViewItem.SubItems%2A> property of an item.</span></span> <span data-ttu-id="00a4b-111">下列程式碼範例會設定清單專案的員工名稱和部門。</span><span class="sxs-lookup"><span data-stu-id="00a4b-111">The code example below sets the employee name and department for a list item.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="00a4b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00a4b-112">See also</span></span>

- [<span data-ttu-id="00a4b-113">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="00a4b-113">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="00a4b-114">操作說明：使用 Windows Forms ListView 控制項加入和移除項目</span><span class="sxs-lookup"><span data-stu-id="00a4b-114">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="00a4b-115">操作說明：將資料行加入至 Windows Forms ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="00a4b-115">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="00a4b-116">操作說明：顯示 Windows Forms ListView 控制項的圖示</span><span class="sxs-lookup"><span data-stu-id="00a4b-116">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="00a4b-117">操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="00a4b-117">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
