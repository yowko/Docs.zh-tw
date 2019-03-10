---
title: HOW TO：設定 Windows Form TreeView 控制項的圖示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], node icons
- ImageList component [Windows Forms], adding images
- icons [Windows Forms], setting for TreeView control
- tree nodes in TreeView control [Windows Forms], icons
ms.assetid: c14ddcc0-e5a6-4c21-a2d5-6799fd491781
ms.openlocfilehash: 515ff2bd4ab0f4fa93eada61396bd45c587cded6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703565"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a><span data-ttu-id="7a113-102">HOW TO：設定 Windows Form TreeView 控制項的圖示</span><span class="sxs-lookup"><span data-stu-id="7a113-102">How to: Set Icons for the Windows Forms TreeView Control</span></span>
<span data-ttu-id="7a113-103">Windows Form<xref:System.Windows.Forms.TreeView>控制項可以顯示每個節點旁邊的圖示。</span><span class="sxs-lookup"><span data-stu-id="7a113-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control can display icons next to each node.</span></span> <span data-ttu-id="7a113-104">圖示位於節點文字的左邊。</span><span class="sxs-lookup"><span data-stu-id="7a113-104">The icons are positioned to the immediate left of the node text.</span></span> <span data-ttu-id="7a113-105">若要顯示這些圖示，您必須建立關聯的樹狀檢視<xref:System.Windows.Forms.ImageList>控制項。</span><span class="sxs-lookup"><span data-stu-id="7a113-105">To display these icons, you must associate the tree view with an <xref:System.Windows.Forms.ImageList> control.</span></span> <span data-ttu-id="7a113-106">如需有關影像清單的詳細資訊，請參閱[ImageList 元件](imagelist-component-windows-forms.md)和[How to:新增或移除映像的 Windows Form ImageList 元件](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)。</span><span class="sxs-lookup"><span data-stu-id="7a113-106">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a113-107">Microsoft.NET Framework 1.1 版中的錯誤可防止映像上出現<xref:System.Windows.Forms.TreeView>節點，當您的應用程式呼叫<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="7a113-107">A bug in Microsoft .NET Framework version 1.1 prevents images from appearing on <xref:System.Windows.Forms.TreeView> nodes when your application calls <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7a113-108">若要解決這個錯誤，請呼叫<xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType>在您`Main`方法呼叫之後立即<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>。</span><span class="sxs-lookup"><span data-stu-id="7a113-108">To work around this bug, call <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> in your `Main` method immediately after calling <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span></span> <span data-ttu-id="7a113-109">已經修正這個錯誤[!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7a113-109">This bug is fixed in [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span>  
  
### <a name="to-display-images-in-a-tree-view"></a><span data-ttu-id="7a113-110">若要在樹狀檢視中顯示影像</span><span class="sxs-lookup"><span data-stu-id="7a113-110">To display images in a tree view</span></span>  
  
1.  <span data-ttu-id="7a113-111">設定<xref:System.Windows.Forms.TreeView>控制項的<xref:System.Windows.Forms.TreeView.ImageList%2A>屬性，以現有<xref:System.Windows.Forms.ImageList>您想要使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="7a113-111">Set the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.ImageList%2A> property to the existing <xref:System.Windows.Forms.ImageList> control you wish to use.</span></span>  
  
     <span data-ttu-id="7a113-112">在設計工具中使用 [屬性] 視窗中，或在程式碼，可以設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="7a113-112">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2.  <span data-ttu-id="7a113-113">將節點的設定<xref:System.Windows.Forms.TreeNode.ImageIndex%2A>和<xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="7a113-113">Set the node's <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> and <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> properties.</span></span> <span data-ttu-id="7a113-114"><xref:System.Windows.Forms.TreeNode.ImageIndex%2A>屬性會決定節點的一般或展開狀態，所顯示的影像和<xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A>屬性決定節點的選取狀態顯示的影像。</span><span class="sxs-lookup"><span data-stu-id="7a113-114">The <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> property determines the image displayed for the node's normal and expanded states, and the <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> property determines the image displayed for the node's selected state.</span></span>  
  
     <span data-ttu-id="7a113-115">在程式碼，或在 TreeNode 編輯器內，可以設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="7a113-115">These properties can be set in code, or within the TreeNode Editor.</span></span> <span data-ttu-id="7a113-116">若要開啟 TreeNode 編輯器，請按一下 [省略符號按鈕 ( ![VisualStudioEllipsesButton 螢幕擷取畫面](../media/vbellipsesbutton.png "vbEllipsesButton")) 旁<xref:System.Windows.Forms.TreeView.Nodes%2A>屬性] 視窗上的屬性。</span><span class="sxs-lookup"><span data-stu-id="7a113-116">To open the TreeNode Editor, click the ellipsis button ( ![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property on the Properties window.</span></span>  
  
    ```vb  
    ' (Assumes that ImageList1 contains at least two images and  
    ' the TreeView control contains a selected image.)  
    TreeView1.SelectedNode.ImageIndex = 0  
    TreeView1.SelectedNode.SelectedImageIndex = 1  
    ```  
  
    ```csharp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1.SelectedNode.ImageIndex = 0;  
    treeView1.SelectedNode.SelectedImageIndex = 1;  
    ```  
  
    ```cpp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1->SelectedNode->ImageIndex = 0;  
    treeView1->SelectedNode->SelectedImageIndex = 1;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7a113-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a113-117">See also</span></span>
- [<span data-ttu-id="7a113-118">TreeView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="7a113-118">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="7a113-119">如何：新增和移除節點，而在 Windows Form TreeView 控制項</span><span class="sxs-lookup"><span data-stu-id="7a113-119">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="7a113-120">如何：逐一查看 Windows Forms TreeView 控制項的所有節點</span><span class="sxs-lookup"><span data-stu-id="7a113-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="7a113-121">如何：判斷按下哪個 TreeView 節點</span><span class="sxs-lookup"><span data-stu-id="7a113-121">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="7a113-122">如何：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="7a113-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
