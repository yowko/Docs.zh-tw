---
title: "如何：定義分隔視窗的調整大小和位置行為"
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
- split windows [Windows Forms], resizing
- splitter windows [Windows Forms], resizing
- SplitContainer control [Windows Forms], resizing
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: db4a99c7dae7783e8ea51f43ad51fcd2214997e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a><span data-ttu-id="9ff70-102">如何：定義分隔視窗的調整大小和位置行為</span><span class="sxs-lookup"><span data-stu-id="9ff70-102">How to: Define Resize and Positioning Behavior in a Split Window</span></span>
<span data-ttu-id="9ff70-103">個面板<xref:System.Windows.Forms.SplitContainer>控制項擔任也正在調整大小，並由使用者操作。</span><span class="sxs-lookup"><span data-stu-id="9ff70-103">The panels of the <xref:System.Windows.Forms.SplitContainer> control lend themselves well to being resized and manipulated by users.</span></span> <span data-ttu-id="9ff70-104">不過，可能會當您將想要以程式設計方式控制分隔器，它會定位，並且程度就可以移動它。</span><span class="sxs-lookup"><span data-stu-id="9ff70-104">However, there will be times when you will want to programmatically control the splitter—where it is positioned and to what degree it can be moved.</span></span>  
  
 <span data-ttu-id="9ff70-105"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>屬性與其他屬性上的<xref:System.Windows.Forms.SplitContainer>控制項可讓您精確掌控您的使用者介面，以符合您需求的行為。</span><span class="sxs-lookup"><span data-stu-id="9ff70-105">The <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property and the other properties on the <xref:System.Windows.Forms.SplitContainer> control give you precise control over the behavior of your user interface to suit your needs.</span></span> <span data-ttu-id="9ff70-106">下表會列出這些屬性。</span><span class="sxs-lookup"><span data-stu-id="9ff70-106">These properties are listed in the following table.</span></span>  
  
|<span data-ttu-id="9ff70-107">名稱</span><span class="sxs-lookup"><span data-stu-id="9ff70-107">Name</span></span>|<span data-ttu-id="9ff70-108">描述</span><span class="sxs-lookup"><span data-stu-id="9ff70-108">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="9ff70-109"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="9ff70-109"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> property</span></span>|<span data-ttu-id="9ff70-110">決定分隔器是否可以透過鍵盤或滑鼠移動。</span><span class="sxs-lookup"><span data-stu-id="9ff70-110">Determines if the splitter is movable by means of the keyboard or mouse.</span></span>|  
|<span data-ttu-id="9ff70-111"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="9ff70-111"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> property</span></span>|<span data-ttu-id="9ff70-112">決定從左方或上方的邊緣可移動的分隔列以像素為單位的距離。</span><span class="sxs-lookup"><span data-stu-id="9ff70-112">Determines the distance in pixels from the left or upper edge to the movable splitter bar.</span></span>|  
|<span data-ttu-id="9ff70-113"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="9ff70-113"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property</span></span>|<span data-ttu-id="9ff70-114">決定最小距離，單位為像素，使用者可以移動分隔器。</span><span class="sxs-lookup"><span data-stu-id="9ff70-114">Determines the minimum distance, in pixels, that the splitter can be moved by the user.</span></span>|  
  
 <span data-ttu-id="9ff70-115">下列範例會修改<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>屬性來建立 「 貼齊分隔器 」 效果; 當使用者拖曳分隔器，它會自動遞增單位的 10 個像素，而不是預設值 1。</span><span class="sxs-lookup"><span data-stu-id="9ff70-115">The example below modifies the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to create a "snapping splitter" effect; when the user drags the splitter, it increments in units of 10 pixels rather than the default 1.</span></span>  
  
### <a name="to-define-splitcontainer-resize-behavior"></a><span data-ttu-id="9ff70-116">若要定義 SplitContainer 調整大小行為</span><span class="sxs-lookup"><span data-stu-id="9ff70-116">To define SplitContainer resize behavior</span></span>  
  
1.  <span data-ttu-id="9ff70-117">在程序，設定<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>屬性至所需的大小達到 '貼齊' 分隔器的行為。</span><span class="sxs-lookup"><span data-stu-id="9ff70-117">In a procedure, set the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to the desired size, so that the 'snapping' behavior of the splitter is achieved.</span></span>  
  
     <span data-ttu-id="9ff70-118">在下列程式碼範例中，表單內<xref:System.Windows.Forms.Form.Load>事件、 分隔器內<xref:System.Windows.Forms.SplitContainer>控制設為跳 10 個像素拖曳時。</span><span class="sxs-lookup"><span data-stu-id="9ff70-118">In the following code example, within the form's <xref:System.Windows.Forms.Form.Load> event, the splitter within the <xref:System.Windows.Forms.SplitContainer> control is set to jump 10 pixels when dragged.</span></span>  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
        ByVal e As System.EventArgs) Handles MyBase.Load  
        Dim splitSnapper as new SplitContainer()  
        splitSnapper.SplitterIncrement = 10  
        splitSnapper.Dock = DockStyle.Fill  
        splitSnapper.Parent = me  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Load(System.Object sender, System.EventArgs e)  
    {  
        SplitContainer splitSnapper = new SplitContainer();  
        splitSnapper.SplitterIncrement = 10;  
        splitSnapper.Dock = DockStyle.Fill;  
        splitSnapper.Parent = this;  
    }  
    ```  
  
     <span data-ttu-id="9ff70-119">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="9ff70-119">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     <span data-ttu-id="9ff70-120">稍微向左或向右移動分隔器不會影響差別。不過，當滑鼠指標進入任一方向的 10 個像素，分隔器會貼齊至新位置中。</span><span class="sxs-lookup"><span data-stu-id="9ff70-120">Moving the splitter slightly to the left or right will have no discernible effect; however, when the mouse pointer goes 10 pixels in either direction, the splitter will snap to the new position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ff70-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ff70-121">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>
