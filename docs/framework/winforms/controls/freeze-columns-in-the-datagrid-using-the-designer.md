---
title: "如何：使用設計工具凍結 Windows Form DataGridView 控制項中的資料行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 33606cc30ccc1d63e780d07bcb1757d62b7ebea2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="c7450-102">如何：使用設計工具凍結 Windows Form DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="c7450-102">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="c7450-103">當使用者檢視顯示於 Windows Form <xref:System.Windows.Forms.DataGridView> 控制項的資料時，有時候需要經常參考單一資料行或資料行集合。</span><span class="sxs-lookup"><span data-stu-id="c7450-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="c7450-104">比方說，當您顯示包含許多資料行的客戶資訊的資料表，它可用於其他資料行可在可見區域外捲動仍一直顯示客戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="c7450-104">For example, when you display a table of customer information that contains many columns, it is useful for you to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>  
  
 <span data-ttu-id="c7450-105">若要達到這種行為，您可以凍結控制項中的資料行。</span><span class="sxs-lookup"><span data-stu-id="c7450-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="c7450-106">當您凍結資料行時，也會凍結在該資料行左邊的所有資料行 (如果是從右至左的字集，則會凍結右邊的所有資料行)。</span><span class="sxs-lookup"><span data-stu-id="c7450-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="c7450-107">凍結的資料行會留在原處，而其他所有資料行則可以捲動。</span><span class="sxs-lookup"><span data-stu-id="c7450-107">Frozen columns remain in place while all other columns can scroll.</span></span> <span data-ttu-id="c7450-108">如果啟用了資料行重新調整順序，則會將凍結的資料行視為與未凍結的資料行有所區別的群組。</span><span class="sxs-lookup"><span data-stu-id="c7450-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="c7450-109">使用者可以在任一群組中重新調整資料行位置，但無法將資料行從一個群組移至另一個。</span><span class="sxs-lookup"><span data-stu-id="c7450-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>  
  
 <span data-ttu-id="c7450-110">下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="c7450-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="c7450-111">設定這類專案的詳細資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="c7450-111">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7450-112">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="c7450-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c7450-113">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="c7450-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c7450-114">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="c7450-114">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-freeze-a-column-using-the-designer"></a><span data-ttu-id="c7450-115">若要凍結資料行使用設計工具</span><span class="sxs-lookup"><span data-stu-id="c7450-115">To freeze a column using the designer</span></span>  
  
1.  <span data-ttu-id="c7450-116">按一下智慧標籤圖像 (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 上的右上角<xref:System.Windows.Forms.DataGridView>控制項，然後再選取**編輯資料行**。</span><span class="sxs-lookup"><span data-stu-id="c7450-116">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="c7450-117">選取的資料行**選取的資料行**清單。</span><span class="sxs-lookup"><span data-stu-id="c7450-117">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="c7450-118">在**資料行屬性**方格中，設定<xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="c7450-118">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c7450-119">您也可以凍結資料行資料時將它加入選取**Frozen**方塊中**加入資料行** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c7450-119">You can also freeze a column when adding it by selecting the **Frozen** box in the **Add Column** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7450-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="c7450-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="c7450-121">操作說明：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行</span><span class="sxs-lookup"><span data-stu-id="c7450-121">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="c7450-122">操作說明：使用設計工具在 Windows Forms DataGridView 控制項中啟用資料行重新調整順序</span><span class="sxs-lookup"><span data-stu-id="c7450-122">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="c7450-123">如何： 顯示 Windows Form 全球化由右至左文字</span><span class="sxs-lookup"><span data-stu-id="c7450-123">How to: Display Right-to-Left Text in Windows Forms for Globalization</span></span>](http://msdn.microsoft.com/library/f0663385-2354-4c65-8676-706422283b14)  
 [<span data-ttu-id="c7450-124">如何： 建立 Windows 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="c7450-124">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="c7450-125">操作說明：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7450-125">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
