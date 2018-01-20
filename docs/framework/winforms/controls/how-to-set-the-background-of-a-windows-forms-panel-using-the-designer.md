---
title: "如何：使用設計工具設定 Windows Form 面板的背景"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 451fa6433a53255f5fe45557c2d8b03ac319de71
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a><span data-ttu-id="96cc4-102">如何：使用設計工具設定 Windows Form 面板的背景</span><span class="sxs-lookup"><span data-stu-id="96cc4-102">How to: Set the Background of a Windows Forms Panel Using the Designer</span></span>
<span data-ttu-id="96cc4-103">Windows Form<xref:System.Windows.Forms.Panel>控制項可以顯示的背景色彩和背景影像。</span><span class="sxs-lookup"><span data-stu-id="96cc4-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="96cc4-104"><xref:System.Windows.Forms.Control.BackColor%2A>屬性會設定包含在面板中，例如標籤和選項按鈕控制項的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="96cc4-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for controls that are contained in the panel, such as labels and radio buttons.</span></span> <span data-ttu-id="96cc4-105">如果<xref:System.Windows.Forms.Control.BackgroundImage%2A>未設定屬性，<xref:System.Windows.Forms.Control.BackColor%2A>選取項目將會填滿所有面板。</span><span class="sxs-lookup"><span data-stu-id="96cc4-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill all of the panel.</span></span> <span data-ttu-id="96cc4-106">如果<xref:System.Windows.Forms.Control.BackgroundImage%2A>屬性設定，會在 [面板] 中所包含的控制項後面顯示的影像。</span><span class="sxs-lookup"><span data-stu-id="96cc4-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the controls that are contained in the panel.</span></span>  
  
 <span data-ttu-id="96cc4-107">下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.Panel>控制項。</span><span class="sxs-lookup"><span data-stu-id="96cc4-107">The following procedure requires a **Windows Application** project with a form that contains a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="96cc4-108">如需如何設定這類專案的資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="96cc4-108">For information about how to set up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96cc4-109">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="96cc4-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="96cc4-110">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="96cc4-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="96cc4-111">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="96cc4-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a><span data-ttu-id="96cc4-112">在 Windows Form 設計工具中設定背景</span><span class="sxs-lookup"><span data-stu-id="96cc4-112">To set the background in the Windows Forms Designer</span></span>  
  
1.  <span data-ttu-id="96cc4-113">選取 <xref:System.Windows.Forms.Panel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="96cc4-113">Select the <xref:System.Windows.Forms.Panel> control.</span></span>  
  
2.  <span data-ttu-id="96cc4-114">在**屬性**視窗中，按一下箭號按鈕的下的一步<xref:System.Windows.Forms.Control.BackColor%2A>屬性來顯示具有三個索引標籤的視窗。</span><span class="sxs-lookup"><span data-stu-id="96cc4-114">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackColor%2A> property to display a window with three tabs.</span></span>  
  
3.  <span data-ttu-id="96cc4-115">選取**自訂**索引標籤，顯示色的調色盤。</span><span class="sxs-lookup"><span data-stu-id="96cc4-115">Select the **Custom** tab to display a palette of colors.</span></span>  
  
4.  <span data-ttu-id="96cc4-116">選取**Web**或**系統**索引標籤上顯示預先定義的色彩名稱清單，然後選取色彩。</span><span class="sxs-lookup"><span data-stu-id="96cc4-116">Select the **Web** or **System** tab to display a list of predefined names for colors, and then select a color.</span></span>  
  
5.  <span data-ttu-id="96cc4-117">在**屬性**視窗中，按一下箭號按鈕的下的一步<xref:System.Windows.Forms.Control.BackgroundImage%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="96cc4-117">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span>  
  
6.  <span data-ttu-id="96cc4-118">在**開啟**對話方塊方塊中，選取您想要顯示的檔案。</span><span class="sxs-lookup"><span data-stu-id="96cc4-118">In the **Open** dialog box, select the file that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96cc4-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="96cc4-119">See Also</span></span>  
 <xref:System.Windows.Forms.Control.BackColor%2A>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>  
 [<span data-ttu-id="96cc4-120">Panel 控制項</span><span class="sxs-lookup"><span data-stu-id="96cc4-120">Panel Control</span></span>](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [<span data-ttu-id="96cc4-121">Panel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="96cc4-121">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [<span data-ttu-id="96cc4-122">操作說明：搭配 Windows Forms Panel 控制項使用設計工具群組控制項</span><span class="sxs-lookup"><span data-stu-id="96cc4-122">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)
