---
title: "如何：將 ContextMenuStrip 與控制項關聯"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [Windows Forms], relating
- ContextMenuStrips [Windows Forms], associating with controls
- context menus [Windows Forms], associating with controls
- ContextMenuStrips [Windows Forms], relating
ms.assetid: 6fc40a42-5d69-427f-aa30-0a146193226b
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7307af535dce39443b623e1fee4491dd48ffbd94
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a><span data-ttu-id="51a40-102">如何：將 ContextMenuStrip 與控制項關聯</span><span class="sxs-lookup"><span data-stu-id="51a40-102">How to: Associate a ContextMenuStrip with a Control</span></span>
<span data-ttu-id="51a40-103">在建立您的控制項和捷徑功能表之後，請使用下列程序，在使用者以滑鼠右鍵按一下控制項時顯示指定的捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="51a40-103">After creating your controls and shortcut menus, use the following procedures to display a given shortcut menu when the user right-clicks the control.</span></span> <span data-ttu-id="51a40-104">這些程序將 <xref:System.Windows.Forms.ContextMenuStrip> 與 Windows Form 和 <xref:System.Windows.Forms.ToolStrip> 控制項產生關聯。</span><span class="sxs-lookup"><span data-stu-id="51a40-104">These procedures associate a <xref:System.Windows.Forms.ContextMenuStrip> with a Windows Form and with a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a><span data-ttu-id="51a40-105">將 ContextMenuStrip 與 Windows Form 產生關聯</span><span class="sxs-lookup"><span data-stu-id="51a40-105">To associate a ContextMenuStrip with a Windows Form</span></span>  
  
1.  <span data-ttu-id="51a40-106">將 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> 屬性設定為關聯的 <xref:System.Windows.Forms.ContextMenuStrip> 名稱。</span><span class="sxs-lookup"><span data-stu-id="51a40-106">Set the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a><span data-ttu-id="51a40-107">將 ContextMenuStrip 與 ToolStrip 產生關聯</span><span class="sxs-lookup"><span data-stu-id="51a40-107">To associate a ContextMenuStrip with a ToolStrip control</span></span>  
  
1.  <span data-ttu-id="51a40-108">將控制項的 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> 屬性設定為關聯的 <xref:System.Windows.Forms.ContextMenuStrip> 名稱。</span><span class="sxs-lookup"><span data-stu-id="51a40-108">Set the control's <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51a40-109">範例</span><span class="sxs-lookup"><span data-stu-id="51a40-109">Example</span></span>  
 <span data-ttu-id="51a40-110">下列程式碼範例會建立 Windows Form 和 <xref:System.Windows.Forms.ToolStrip>，並將不同的 <xref:System.Windows.Forms.ContextMenuStrip> 控制項與每個項目產生關聯。</span><span class="sxs-lookup"><span data-stu-id="51a40-110">The following code example creates a Windows Form and a <xref:System.Windows.Forms.ToolStrip>, and associates a different <xref:System.Windows.Forms.ContextMenuStrip> control with each of them.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="51a40-111">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="51a40-111">Compiling the Code</span></span>  
 <span data-ttu-id="51a40-112">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="51a40-112">This example requires:</span></span>  
  
-   <span data-ttu-id="51a40-113">System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="51a40-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="51a40-114">如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置命令列](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="51a40-114">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="51a40-115">您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。</span><span class="sxs-lookup"><span data-stu-id="51a40-115">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="51a40-116">另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="51a40-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51a40-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="51a40-117">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>  
 <xref:System.Windows.Forms.ToolStrip>  
 [<span data-ttu-id="51a40-118">操作說明：將功能表項目新增至 ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="51a40-118">How to: Add Menu Items to a ContextMenuStrip</span></span>](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)  
 [<span data-ttu-id="51a40-119">ContextMenuStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="51a40-119">ContextMenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
