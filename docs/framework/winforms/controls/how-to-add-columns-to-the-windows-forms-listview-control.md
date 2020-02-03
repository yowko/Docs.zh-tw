---
title: 將資料行新增至 ListView 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: dd438ffbadddfc37ec9eb15e59a908bb58472a45
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744579"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a><span data-ttu-id="a501b-102">如何：將資料行加入至 Windows Form ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="a501b-102">How to: Add Columns to the Windows Forms ListView Control</span></span>
<span data-ttu-id="a501b-103">在詳細資料檢視中，<xref:System.Windows.Forms.ListView> 控制項可以顯示每個清單專案的多個資料行。</span><span class="sxs-lookup"><span data-stu-id="a501b-103">In the Details view, the <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item.</span></span> <span data-ttu-id="a501b-104">您可以使用資料行向使用者顯示每個清單專案的數種類型資訊。</span><span class="sxs-lookup"><span data-stu-id="a501b-104">You can use the columns to display to the user several types of information about each list item.</span></span> <span data-ttu-id="a501b-105">例如，檔案清單可以顯示檔案上次修改的檔案名、檔案類型、大小和日期。</span><span class="sxs-lookup"><span data-stu-id="a501b-105">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="a501b-106">如需建立資料行之後將其填入的詳細資訊，請參閱[如何：在具有 Windows Forms ListView 控制項的資料行中顯示](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)子工作。</span><span class="sxs-lookup"><span data-stu-id="a501b-106">For information about populating the columns after they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>  
  
### <a name="to-add-columns-programmatically"></a><span data-ttu-id="a501b-107">以程式設計方式新增資料行</span><span class="sxs-lookup"><span data-stu-id="a501b-107">To add columns programmatically</span></span>  
  
1. <span data-ttu-id="a501b-108">將控制項的 <xref:System.Windows.Forms.ListView.View%2A> 屬性設定為 [<xref:System.Windows.Forms.View.Details>]。</span><span class="sxs-lookup"><span data-stu-id="a501b-108">Set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
2. <span data-ttu-id="a501b-109">使用清單視圖之 <xref:System.Windows.Forms.ListView.Columns%2A> 屬性的 <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a501b-109">Use the <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> method of the list view's <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="a501b-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a501b-110">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- [<span data-ttu-id="a501b-111">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="a501b-111">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="a501b-112">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="a501b-112">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
