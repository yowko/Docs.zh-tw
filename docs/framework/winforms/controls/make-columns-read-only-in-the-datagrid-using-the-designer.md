---
title: "如何：使用設計工具將 Windows Form DataGridView 控制項中的資料行設為唯讀"
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
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 426c47010a7b1d3f20700d8041ed882e149aaa7d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="b7dee-102">如何：使用設計工具將 Windows Form DataGridView 控制項中的資料行設為唯讀</span><span class="sxs-lookup"><span data-stu-id="b7dee-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="b7dee-103">根據預設，使用者可以修改文字和數字的資料顯示在 Windows Form<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="b7dee-103">By default, users can modify text and numerical data displayed in the Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="b7dee-104">如果您想要顯示不可用來修改的資料，您必須讓包含唯讀資料的資料行。</span><span class="sxs-lookup"><span data-stu-id="b7dee-104">If you want to display data that is not meant for modification, you must make the columns that contain the data read-only.</span></span> <span data-ttu-id="b7dee-105">如需如何使控制項為完全唯讀資訊，請參閱[如何： 防止資料列新增和刪除使用 Windows Form DataGridView 控制項設計工具中的](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="b7dee-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span></span>  
  
 <span data-ttu-id="b7dee-106">下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="b7dee-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="b7dee-107">設定這類專案的詳細資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="b7dee-107">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7dee-108">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="b7dee-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b7dee-109">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="b7dee-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b7dee-110">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="b7dee-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-make-a-column-read-only-by-using-the-designer"></a><span data-ttu-id="b7dee-111">使用設計工具唯讀讓資料行</span><span class="sxs-lookup"><span data-stu-id="b7dee-111">To make a column read-only by using the designer</span></span>  
  
1.  <span data-ttu-id="b7dee-112">按一下智慧標籤圖像 (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 上的右上角<xref:System.Windows.Forms.DataGridView>控制項，然後再選取**編輯資料行**。</span><span class="sxs-lookup"><span data-stu-id="b7dee-112">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="b7dee-113">選取的資料行**選取的資料行**清單。</span><span class="sxs-lookup"><span data-stu-id="b7dee-113">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="b7dee-114">在**資料行屬性**方格中，設定<xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="b7dee-114">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b7dee-115">您也可以將資料行唯讀狀態時將它加入選取**Read Only**中核取方塊**加入資料行** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b7dee-115">You can also make a column read-only when you add it by selecting the **Read Only** check box in the **Add Column** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7dee-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="b7dee-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="b7dee-117">操作說明：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行</span><span class="sxs-lookup"><span data-stu-id="b7dee-117">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="b7dee-118">操作說明：使用設計工具防止在 Windows Forms DataGridView 控制項中新增和刪除資料列</span><span class="sxs-lookup"><span data-stu-id="b7dee-118">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="b7dee-119">如何： 建立 Windows 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="b7dee-119">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="b7dee-120">操作說明：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b7dee-120">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
