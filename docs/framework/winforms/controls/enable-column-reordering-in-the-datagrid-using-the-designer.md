---
title: "如何：使用設計工具在 Windows Form DataGridView 控制項中啟用資料行重新調整順序"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- columns [Windows Forms], reordering
- data [Windows Forms], displaying
ms.assetid: d82bd69c-6799-4439-a32c-91139c5901d1
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ddbb86ef98befda8a246bdded4f30cf93f02e727
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="069dc-102">如何：使用設計工具在 Windows Form DataGridView 控制項中啟用資料行重新調整順序</span><span class="sxs-lookup"><span data-stu-id="069dc-102">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="069dc-103">檢視顯示 Windows Form 中的資料時<xref:System.Windows.Forms.DataGridView>控制項，使用者有時候想要比較的特定資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="069dc-103">When viewing data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, users sometimes want to compare the values in specific columns.</span></span> <span data-ttu-id="069dc-104">特別是如果使用者必須來回水平捲動以查看感興趣的資料行，這可以是資料行放在相隔在控制項中，如果很不方便。</span><span class="sxs-lookup"><span data-stu-id="069dc-104">This can be inconvenient if the columns are widely separated in the control, especially if users must scroll back and forth horizontally in order to see all the columns they are interested in.</span></span> <span data-ttu-id="069dc-105">您可以進行比較讓使用者重新排列資料行的資料行值更容易的工作。</span><span class="sxs-lookup"><span data-stu-id="069dc-105">You can make the task of comparing column values easier by enabling your users to reorder the columns.</span></span> <span data-ttu-id="069dc-106">當您啟用重新排列資料行時，使用者可以拖曳資料行標頭，使用滑鼠到新的位置移動資料行。</span><span class="sxs-lookup"><span data-stu-id="069dc-106">When you enable column reordering, users can move a column to a new position by dragging the column header with the mouse.</span></span>  
  
 <span data-ttu-id="069dc-107">下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="069dc-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="069dc-108">設定這類專案的詳細資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="069dc-108">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="069dc-109">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="069dc-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="069dc-110">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="069dc-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="069dc-111">如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。</span><span class="sxs-lookup"><span data-stu-id="069dc-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-enable-column-reordering"></a><span data-ttu-id="069dc-112">若要啟用資料行重新調整順序</span><span class="sxs-lookup"><span data-stu-id="069dc-112">To enable column reordering</span></span>  
  
-   <span data-ttu-id="069dc-113">按一下智慧標籤圖像 (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 上的右上角<xref:System.Windows.Forms.DataGridView>控制項，然後再選取**啟用資料行重新調整順序**.</span><span class="sxs-lookup"><span data-stu-id="069dc-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Enable Column Reordering**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="069dc-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="069dc-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="069dc-115">操作說明：使用設計工具凍結 Windows Forms DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="069dc-115">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/freeze-columns-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="069dc-116">如何： 建立 Windows 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="069dc-116">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="069dc-117">操作說明：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="069dc-117">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
