---
title: 作法：設定 Windows Forms TreeView 控制項的圖示
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
ms.openlocfilehash: 451f9ab2b35ad1fbbe9401dacbc8aab44e302701
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909801"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a><span data-ttu-id="a5230-102">HOW TO：設定 Windows Forms TreeView 控制項的圖示</span><span class="sxs-lookup"><span data-stu-id="a5230-102">How to: Set Icons for the Windows Forms TreeView Control</span></span>
<span data-ttu-id="a5230-103">Windows Forms <xref:System.Windows.Forms.TreeView>控制項可以顯示每個節點旁邊的圖示。</span><span class="sxs-lookup"><span data-stu-id="a5230-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control can display icons next to each node.</span></span> <span data-ttu-id="a5230-104">圖示會定位於節點文字的直接左側。</span><span class="sxs-lookup"><span data-stu-id="a5230-104">The icons are positioned to the immediate left of the node text.</span></span> <span data-ttu-id="a5230-105">若要顯示這些圖示, 您必須將樹狀檢視與控制項<xref:System.Windows.Forms.ImageList>產生關聯。</span><span class="sxs-lookup"><span data-stu-id="a5230-105">To display these icons, you must associate the tree view with an <xref:System.Windows.Forms.ImageList> control.</span></span> <span data-ttu-id="a5230-106">如需影像清單的詳細資訊, 請參閱[ImageList 元件](imagelist-component-windows-forms.md)和[如何:使用 Windows Forms ImageList 元件](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)來新增或移除映射。</span><span class="sxs-lookup"><span data-stu-id="a5230-106">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5230-107">Microsoft .NET Framework 版本1.1 中的錯誤, 可防止在您<xref:System.Windows.Forms.TreeView>的應用程式呼叫<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>時, 在節點上顯示影像。</span><span class="sxs-lookup"><span data-stu-id="a5230-107">A bug in Microsoft .NET Framework version 1.1 prevents images from appearing on <xref:System.Windows.Forms.TreeView> nodes when your application calls <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a5230-108">若要解決這個錯誤, 請<xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> `Main`在呼叫<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>之後立即呼叫方法中的。</span><span class="sxs-lookup"><span data-stu-id="a5230-108">To work around this bug, call <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> in your `Main` method immediately after calling <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span></span> <span data-ttu-id="a5230-109">此 bug 在 .NET Framework 2.0 中已修正。</span><span class="sxs-lookup"><span data-stu-id="a5230-109">This bug is fixed in .NET Framework 2.0.</span></span>  
  
### <a name="to-display-images-in-a-tree-view"></a><span data-ttu-id="a5230-110">若要在樹狀檢視中顯示影像</span><span class="sxs-lookup"><span data-stu-id="a5230-110">To display images in a tree view</span></span>  
  
1. <span data-ttu-id="a5230-111">將控制項的<xref:System.Windows.Forms.TreeView.ImageList%2A>屬性設為您想<xref:System.Windows.Forms.ImageList>要使用的現有控制項。 <xref:System.Windows.Forms.TreeView></span><span class="sxs-lookup"><span data-stu-id="a5230-111">Set the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.ImageList%2A> property to the existing <xref:System.Windows.Forms.ImageList> control you wish to use.</span></span>  
  
     <span data-ttu-id="a5230-112">這些屬性可以在設計工具中, 使用屬性視窗或程式碼來設定。</span><span class="sxs-lookup"><span data-stu-id="a5230-112">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. <span data-ttu-id="a5230-113">設定節點的<xref:System.Windows.Forms.TreeNode.ImageIndex%2A>和<xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a5230-113">Set the node's <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> and <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> properties.</span></span> <span data-ttu-id="a5230-114">屬性會決定針對節點的正常和擴充狀態顯示的影像, <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A>而屬性會決定針對節點所選取狀態顯示的影像。 <xref:System.Windows.Forms.TreeNode.ImageIndex%2A></span><span class="sxs-lookup"><span data-stu-id="a5230-114">The <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> property determines the image displayed for the node's normal and expanded states, and the <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> property determines the image displayed for the node's selected state.</span></span>  
  
     <span data-ttu-id="a5230-115">這些屬性可以在程式碼中設定, 或在 TreeNode 編輯器中設定。</span><span class="sxs-lookup"><span data-stu-id="a5230-115">These properties can be set in code, or within the TreeNode Editor.</span></span> <span data-ttu-id="a5230-116">若要開啟 [TreeNode 編輯器], 請按一下 ![屬性視窗上<xref:System.Windows.Forms.TreeView.Nodes%2A>屬性旁邊的省略號按鈕 (](./media/visual-studio-ellipsis-button.png)Visual Studio 的屬性視窗中的省略號按鈕 (...)。</span><span class="sxs-lookup"><span data-stu-id="a5230-116">To open the TreeNode Editor, click the ellipsis button ( ![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property on the Properties window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a5230-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5230-117">See also</span></span>

- [<span data-ttu-id="a5230-118">TreeView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="a5230-118">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="a5230-119">如何：使用 Windows Forms TreeView 控制項加入和移除節點</span><span class="sxs-lookup"><span data-stu-id="a5230-119">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="a5230-120">如何：逐一查看 Windows Forms TreeView 控制項的所有節點</span><span class="sxs-lookup"><span data-stu-id="a5230-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="a5230-121">如何：判斷按一下哪個 TreeView 節點</span><span class="sxs-lookup"><span data-stu-id="a5230-121">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="a5230-122">如何：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a5230-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
