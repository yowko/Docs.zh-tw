---
title: HOW TO：定義分割視窗的調整大小和位置行為
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- split windows [Windows Forms], resizing
- splitter windows [Windows Forms], resizing
- SplitContainer control [Windows Forms], resizing
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
ms.openlocfilehash: 8cdcfdfaa135a92ed6a6e96d4a72de2c97f2493d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328669"
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a><span data-ttu-id="70a8b-102">HOW TO：定義分割視窗的調整大小和位置行為</span><span class="sxs-lookup"><span data-stu-id="70a8b-102">How to: Define Resize and Positioning Behavior in a Split Window</span></span>
<span data-ttu-id="70a8b-103">個面板<xref:System.Windows.Forms.SplitContainer>控制項讓他們也正在調整大小，並由使用者操作。</span><span class="sxs-lookup"><span data-stu-id="70a8b-103">The panels of the <xref:System.Windows.Forms.SplitContainer> control lend themselves well to being resized and manipulated by users.</span></span> <span data-ttu-id="70a8b-104">不過，可能會當您將想要以程式設計方式控制分隔器，其中的位置，而哪種程度移動。</span><span class="sxs-lookup"><span data-stu-id="70a8b-104">However, there will be times when you will want to programmatically control the splitter—where it is positioned and to what degree it can be moved.</span></span>  
  
 <span data-ttu-id="70a8b-105"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>屬性和其他屬性，在<xref:System.Windows.Forms.SplitContainer>控制項讓您精確地控制您的使用者介面，以符合您需求的行為。</span><span class="sxs-lookup"><span data-stu-id="70a8b-105">The <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property and the other properties on the <xref:System.Windows.Forms.SplitContainer> control give you precise control over the behavior of your user interface to suit your needs.</span></span> <span data-ttu-id="70a8b-106">下表會列出這些屬性。</span><span class="sxs-lookup"><span data-stu-id="70a8b-106">These properties are listed in the following table.</span></span>  
  
|<span data-ttu-id="70a8b-107">名稱</span><span class="sxs-lookup"><span data-stu-id="70a8b-107">Name</span></span>|<span data-ttu-id="70a8b-108">描述</span><span class="sxs-lookup"><span data-stu-id="70a8b-108">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="70a8b-109"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="70a8b-109"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> property</span></span>|<span data-ttu-id="70a8b-110">判斷是否透過鍵盤或滑鼠可移動的分隔器。</span><span class="sxs-lookup"><span data-stu-id="70a8b-110">Determines if the splitter is movable by means of the keyboard or mouse.</span></span>|  
|<span data-ttu-id="70a8b-111"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="70a8b-111"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> property</span></span>|<span data-ttu-id="70a8b-112">決定在可移動的分隔器列的像素的左邊緣或上邊緣的距離。</span><span class="sxs-lookup"><span data-stu-id="70a8b-112">Determines the distance in pixels from the left or upper edge to the movable splitter bar.</span></span>|  
|<span data-ttu-id="70a8b-113"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="70a8b-113"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property</span></span>|<span data-ttu-id="70a8b-114">決定的最短距離，單位為像素，使用者可以移動分隔器。</span><span class="sxs-lookup"><span data-stu-id="70a8b-114">Determines the minimum distance, in pixels, that the splitter can be moved by the user.</span></span>|  
  
 <span data-ttu-id="70a8b-115">下列範例會修改<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>屬性來建立 「 貼齊分隔器 」 的效果; 當使用者拖曳分隔器，就會自動遞增單位為 10 個像素，而不是預設值 1。</span><span class="sxs-lookup"><span data-stu-id="70a8b-115">The example below modifies the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to create a "snapping splitter" effect; when the user drags the splitter, it increments in units of 10 pixels rather than the default 1.</span></span>  
  
### <a name="to-define-splitcontainer-resize-behavior"></a><span data-ttu-id="70a8b-116">若要定義 SplitContainer 調整大小行為</span><span class="sxs-lookup"><span data-stu-id="70a8b-116">To define SplitContainer resize behavior</span></span>  
  
1. <span data-ttu-id="70a8b-117">在程序，設定<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>屬性至所需的大小，以便達成 '貼齊' 起的分隔器行為。</span><span class="sxs-lookup"><span data-stu-id="70a8b-117">In a procedure, set the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to the desired size, so that the 'snapping' behavior of the splitter is achieved.</span></span>  
  
     <span data-ttu-id="70a8b-118">在下列的程式碼範例中，而表單內<xref:System.Windows.Forms.Form.Load>事件，在分隔器<xref:System.Windows.Forms.SplitContainer>控制項跳 10 個像素拖曳時設定。</span><span class="sxs-lookup"><span data-stu-id="70a8b-118">In the following code example, within the form's <xref:System.Windows.Forms.Form.Load> event, the splitter within the <xref:System.Windows.Forms.SplitContainer> control is set to jump 10 pixels when dragged.</span></span>  
  
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
  
     <span data-ttu-id="70a8b-119">(Visual C#)下列程式碼置於表單的建構函式，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="70a8b-119">(Visual C#) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     <span data-ttu-id="70a8b-120">向左或向右稍微移動分隔器會有任何顯著的作用中;不過，當滑鼠指標進入任一方向的 10 個像素，分隔器會貼齊至新位置中。</span><span class="sxs-lookup"><span data-stu-id="70a8b-120">Moving the splitter slightly to the left or right will have no discernible effect; however, when the mouse pointer goes 10 pixels in either direction, the splitter will snap to the new position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70a8b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70a8b-121">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>
