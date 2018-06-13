---
title: 如何：使用 Windows Form ListView 控制項以資料行顯示子項目
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
ms.openlocfilehash: efee926301bc358bb7645ba67826f412c0d0dbbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532502"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a><span data-ttu-id="a24fa-102">如何：使用 Windows Form ListView 控制項以資料行顯示子項目</span><span class="sxs-lookup"><span data-stu-id="a24fa-102">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>
<span data-ttu-id="a24fa-103">Windows Form<xref:System.Windows.Forms.ListView>控制項可以顯示其他的文字或詳細資料檢視中的每個項目的子項目。</span><span class="sxs-lookup"><span data-stu-id="a24fa-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display additional text, or subitems, for each item in the Details view.</span></span> <span data-ttu-id="a24fa-104">第一個資料行顯示的項目文字，例如員工編號。</span><span class="sxs-lookup"><span data-stu-id="a24fa-104">The first column displays the item text, for example an employee number.</span></span> <span data-ttu-id="a24fa-105">第二、 第三和後續的資料行中顯示第一、 第二，以及後續的相關聯的子項目。</span><span class="sxs-lookup"><span data-stu-id="a24fa-105">The second, third, and subsequent columns display the first, second, and subsequent associated subitems.</span></span>  
  
### <a name="to-add-subitems-to-a-list-item"></a><span data-ttu-id="a24fa-106">若要將子項目加入至清單項目</span><span class="sxs-lookup"><span data-stu-id="a24fa-106">To add subitems to a list item</span></span>  
  
1.  <span data-ttu-id="a24fa-107">加入所需的任何資料行。</span><span class="sxs-lookup"><span data-stu-id="a24fa-107">Add any columns needed.</span></span> <span data-ttu-id="a24fa-108">因為第一欄會顯示項目的<xref:System.Windows.Forms.ListView.Text%2A>屬性，您需要一個多個資料行有子項目。</span><span class="sxs-lookup"><span data-stu-id="a24fa-108">Because the first column will display the item's <xref:System.Windows.Forms.ListView.Text%2A> property, you need one more column than there are subitems.</span></span> <span data-ttu-id="a24fa-109">如需有關如何加入資料行的詳細資訊，請參閱[How to： 將資料行加入 Windows Form ListView 控制項](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="a24fa-109">For more information on adding columns, see [How to: Add Columns to the Windows Forms ListView Control](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).</span></span>  
  
2.  <span data-ttu-id="a24fa-110">呼叫<xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A>方法所傳回的集合<xref:System.Windows.Forms.ListViewItem.SubItems%2A>項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="a24fa-110">Call the <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.ListViewItem.SubItems%2A> property of an item.</span></span> <span data-ttu-id="a24fa-111">下列程式碼範例會設定 employee name 和部門以取得的清單項目。</span><span class="sxs-lookup"><span data-stu-id="a24fa-111">The code example below sets the employee name and department for a list item.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="a24fa-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a24fa-112">See Also</span></span>  
 [<span data-ttu-id="a24fa-113">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="a24fa-113">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="a24fa-114">操作說明：使用 Windows Forms ListView 控制項加入和移除項目</span><span class="sxs-lookup"><span data-stu-id="a24fa-114">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="a24fa-115">操作說明：將資料行加入至 Windows Forms ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="a24fa-115">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="a24fa-116">操作說明：顯示 Windows Forms ListView 控制項的圖示</span><span class="sxs-lookup"><span data-stu-id="a24fa-116">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="a24fa-117">操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a24fa-117">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
