---
title: HOW TO：將資料行新增至 Windows Form ListView 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: 5c87d43513f2125945145445c61f689cdd9d2aaf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345738"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a><span data-ttu-id="cbb12-102">HOW TO：將資料行新增至 Windows Form ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="cbb12-102">How to: Add Columns to the Windows Forms ListView Control</span></span>
<span data-ttu-id="cbb12-103">在詳細資料檢視中，<xref:System.Windows.Forms.ListView>控制項可以顯示多個資料行的每個清單項目。</span><span class="sxs-lookup"><span data-stu-id="cbb12-103">In the Details view, the <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item.</span></span> <span data-ttu-id="cbb12-104">若要向使用者顯示數種類型的每個清單項目的相關資訊，您可以使用資料行。</span><span class="sxs-lookup"><span data-stu-id="cbb12-104">You can use the columns to display to the user several types of information about each list item.</span></span> <span data-ttu-id="cbb12-105">例如，檔案名稱、 檔案類型、 大小和檔案上次修改的日期，可以顯示一份檔案。</span><span class="sxs-lookup"><span data-stu-id="cbb12-105">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="cbb12-106">如需在建立後，擴展資料行資訊，請參閱[How to:使用 Windows 的資料行顯示子項目 Form ListView 控制項](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="cbb12-106">For information about populating the columns after they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>  
  
### <a name="to-add-columns-programmatically"></a><span data-ttu-id="cbb12-107">以程式設計方式將資料行</span><span class="sxs-lookup"><span data-stu-id="cbb12-107">To add columns programmatically</span></span>  
  
1. <span data-ttu-id="cbb12-108">將控制項的<xref:System.Windows.Forms.ListView.View%2A>屬性設<xref:System.Windows.Forms.View.Details>。</span><span class="sxs-lookup"><span data-stu-id="cbb12-108">Set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
2. <span data-ttu-id="cbb12-109">使用<xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A>方法的清單檢視的<xref:System.Windows.Forms.ListView.Columns%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="cbb12-109">Use the <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> method of the list view's <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="cbb12-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbb12-110">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- [<span data-ttu-id="cbb12-111">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="cbb12-111">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="cbb12-112">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="cbb12-112">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
