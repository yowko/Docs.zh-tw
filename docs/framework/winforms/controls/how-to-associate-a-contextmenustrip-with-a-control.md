---
title: HOW TO：建立 ContextMenuStrip 與控制項的關聯
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [Windows Forms], relating
- ContextMenuStrips [Windows Forms], associating with controls
- context menus [Windows Forms], associating with controls
- ContextMenuStrips [Windows Forms], relating
ms.assetid: 6fc40a42-5d69-427f-aa30-0a146193226b
ms.openlocfilehash: 4e39769621c46ead92076489014f6e0e9dc7863d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122365"
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a><span data-ttu-id="8c0d0-102">HOW TO：建立 ContextMenuStrip 與控制項的關聯</span><span class="sxs-lookup"><span data-stu-id="8c0d0-102">How to: Associate a ContextMenuStrip with a Control</span></span>
<span data-ttu-id="8c0d0-103">在建立您的控制項和捷徑功能表之後，請使用下列程序，在使用者以滑鼠右鍵按一下控制項時顯示指定的捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="8c0d0-103">After creating your controls and shortcut menus, use the following procedures to display a given shortcut menu when the user right-clicks the control.</span></span> <span data-ttu-id="8c0d0-104">這些程序將 <xref:System.Windows.Forms.ContextMenuStrip> 與 Windows Form 和 <xref:System.Windows.Forms.ToolStrip> 控制項產生關聯。</span><span class="sxs-lookup"><span data-stu-id="8c0d0-104">These procedures associate a <xref:System.Windows.Forms.ContextMenuStrip> with a Windows Form and with a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a><span data-ttu-id="8c0d0-105">將 ContextMenuStrip 與 Windows Form 產生關聯</span><span class="sxs-lookup"><span data-stu-id="8c0d0-105">To associate a ContextMenuStrip with a Windows Form</span></span>  
  
1.  <span data-ttu-id="8c0d0-106">將 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> 屬性設定為關聯的 <xref:System.Windows.Forms.ContextMenuStrip> 名稱。</span><span class="sxs-lookup"><span data-stu-id="8c0d0-106">Set the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a><span data-ttu-id="8c0d0-107">將 ContextMenuStrip 與 ToolStrip 產生關聯</span><span class="sxs-lookup"><span data-stu-id="8c0d0-107">To associate a ContextMenuStrip with a ToolStrip control</span></span>  
  
1.  <span data-ttu-id="8c0d0-108">將控制項的 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> 屬性設定為關聯的 <xref:System.Windows.Forms.ContextMenuStrip> 名稱。</span><span class="sxs-lookup"><span data-stu-id="8c0d0-108">Set the control's <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c0d0-109">範例</span><span class="sxs-lookup"><span data-stu-id="8c0d0-109">Example</span></span>  
 <span data-ttu-id="8c0d0-110">下列程式碼範例會建立 Windows Form 和 <xref:System.Windows.Forms.ToolStrip>，並將不同的 <xref:System.Windows.Forms.ContextMenuStrip> 控制項與每個項目產生關聯。</span><span class="sxs-lookup"><span data-stu-id="8c0d0-110">The following code example creates a Windows Form and a <xref:System.Windows.Forms.ToolStrip>, and associates a different <xref:System.Windows.Forms.ContextMenuStrip> control with each of them.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8c0d0-111">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="8c0d0-111">Compiling the Code</span></span>  
 <span data-ttu-id="8c0d0-112">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="8c0d0-112">This example requires:</span></span>  
  
-   <span data-ttu-id="8c0d0-113">System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="8c0d0-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="8c0d0-114">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="8c0d0-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="8c0d0-115">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="8c0d0-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c0d0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c0d0-116">See also</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="8c0d0-117">HOW TO：將功能表項目新增至 ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="8c0d0-117">How to: Add Menu Items to a ContextMenuStrip</span></span>](how-to-add-menu-items-to-a-contextmenustrip.md)
- [<span data-ttu-id="8c0d0-118">ContextMenuStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="8c0d0-118">ContextMenuStrip Control</span></span>](contextmenustrip-control.md)
