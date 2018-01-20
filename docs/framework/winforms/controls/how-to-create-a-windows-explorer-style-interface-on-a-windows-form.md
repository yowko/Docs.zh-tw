---
title: "如何：在 Windows Form 建立 Windows 檔案總管樣式的介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26a91052586843f87c04adf1a31025991d9973db
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a><span data-ttu-id="9b5d3-102">如何：在 Windows Form 建立 Windows 檔案總管樣式的介面</span><span class="sxs-lookup"><span data-stu-id="9b5d3-102">How to: Create a Windows Explorer–Style Interface on a Windows Form</span></span>
<span data-ttu-id="9b5d3-103">Windows 檔案總管 是常見的使用者介面方式的應用程式，因為其程度。</span><span class="sxs-lookup"><span data-stu-id="9b5d3-103">Windows Explorer is a common user-interface choice for applications because of its ready familiarity.</span></span>  
  
 <span data-ttu-id="9b5d3-104">基本上，Windows 檔案總管已<xref:System.Windows.Forms.TreeView>控制項和<xref:System.Windows.Forms.ListView>個別面板上的控制項。</span><span class="sxs-lookup"><span data-stu-id="9b5d3-104">Windows Explorer is, essentially, a <xref:System.Windows.Forms.TreeView> control and a <xref:System.Windows.Forms.ListView> control on separate panels.</span></span> <span data-ttu-id="9b5d3-105">面板是透過分隔器建立可調整大小。</span><span class="sxs-lookup"><span data-stu-id="9b5d3-105">The panels are made resizable by a splitter.</span></span> <span data-ttu-id="9b5d3-106">此控制項的排列方式可有效地顯示及瀏覽資訊。</span><span class="sxs-lookup"><span data-stu-id="9b5d3-106">This arrangement of controls is very effective for displaying and browsing information.</span></span>  
  
 <span data-ttu-id="9b5d3-107">下列步驟顯示如何排列在 Windows 檔案總管類似的表單中的控制項。</span><span class="sxs-lookup"><span data-stu-id="9b5d3-107">The following steps show how to arrange controls in a Windows Explorer-like form.</span></span> <span data-ttu-id="9b5d3-108">他們不要顯示如何將檔案瀏覽功能的 Windows 檔案總管應用程式。</span><span class="sxs-lookup"><span data-stu-id="9b5d3-108">They do not show how to add the file-browsing functionality of the Windows Explorer application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b5d3-109">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="9b5d3-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9b5d3-110">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="9b5d3-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9b5d3-111">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="9b5d3-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a><span data-ttu-id="9b5d3-112">若要建立 Windows 檔案總管樣式的 Windows Form</span><span class="sxs-lookup"><span data-stu-id="9b5d3-112">To create a Windows Explorer-style Windows Form</span></span>  
  
1.  <span data-ttu-id="9b5d3-113">建立新的 Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="9b5d3-113">Create a new Windows Application project.</span></span> <span data-ttu-id="9b5d3-114">如需詳細資訊，請參閱[如何：建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)。</span><span class="sxs-lookup"><span data-stu-id="9b5d3-114">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="9b5d3-115">從**工具箱**:</span><span class="sxs-lookup"><span data-stu-id="9b5d3-115">From the **Toolbox**:</span></span>  
  
    1.  <span data-ttu-id="9b5d3-116">拖曳<xref:System.Windows.Forms.SplitContainer>控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="9b5d3-116">Drag a <xref:System.Windows.Forms.SplitContainer> control onto your form.</span></span>  
  
    2.  <span data-ttu-id="9b5d3-117">拖曳<xref:System.Windows.Forms.TreeView>控制項放入**SplitterPanel1** (的面板<xref:System.Windows.Forms.SplitContainer>控制項標示**Panel1**)。</span><span class="sxs-lookup"><span data-stu-id="9b5d3-117">Drag a <xref:System.Windows.Forms.TreeView> control into **SplitterPanel1** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel1**).</span></span>  
  
    3.  <span data-ttu-id="9b5d3-118">拖曳<xref:System.Windows.Forms.ListView>控制項放入**SplitterPanel2** (的面板<xref:System.Windows.Forms.SplitContainer>控制項標示**Panel2**)。</span><span class="sxs-lookup"><span data-stu-id="9b5d3-118">Drag a <xref:System.Windows.Forms.ListView> control into **SplitterPanel2** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel2**).</span></span>  
  
3.  <span data-ttu-id="9b5d3-119">按下 CTRL 鍵並依序按一下來選取所有的三個控制項。</span><span class="sxs-lookup"><span data-stu-id="9b5d3-119">Select all three controls by pressing the CTRL key and clicking them in turn.</span></span> <span data-ttu-id="9b5d3-120">當您選取<xref:System.Windows.Forms.SplitContainer>控制，請按一下分割線，而不是在面板。</span><span class="sxs-lookup"><span data-stu-id="9b5d3-120">When you select the <xref:System.Windows.Forms.SplitContainer> control, click the splitter bar, rather than the panels.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9b5d3-121">請勿使用**全選**命令**編輯**功能表。</span><span class="sxs-lookup"><span data-stu-id="9b5d3-121">Do not use the **Select All** command on the **Edit** menu.</span></span> <span data-ttu-id="9b5d3-122">如果您這樣做，請在下一個步驟所需的屬性不會出現在**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="9b5d3-122">If you do so, the property needed in the next step will not appear in the **Properties** window.</span></span>  
  
4.  <span data-ttu-id="9b5d3-123">在**屬性**視窗中，將<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性<xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="9b5d3-123">In the **Properties** window, set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
5.  <span data-ttu-id="9b5d3-124">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="9b5d3-124">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="9b5d3-125">此表單顯示兩個部分的使用者介面，類似於 Windows 檔案總管。</span><span class="sxs-lookup"><span data-stu-id="9b5d3-125">The form displays a two-part user interface, similar to that of the Windows Explorer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9b5d3-126">當您拖曳分隔器時，面板自動調整。</span><span class="sxs-lookup"><span data-stu-id="9b5d3-126">When you drag the splitter, the panels resize themselves.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b5d3-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="9b5d3-127">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 [<span data-ttu-id="9b5d3-128">逐步解說：利用 Windows Forms 建立多窗格使用者介面</span><span class="sxs-lookup"><span data-stu-id="9b5d3-128">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 [<span data-ttu-id="9b5d3-129">操作說明：定義分隔視窗的調整大小和位置行為</span><span class="sxs-lookup"><span data-stu-id="9b5d3-129">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 [<span data-ttu-id="9b5d3-130">操作說明：水平分隔視窗</span><span class="sxs-lookup"><span data-stu-id="9b5d3-130">How to: Split a Window Horizontally</span></span>](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 [<span data-ttu-id="9b5d3-131">SplitContainer 控制項</span><span class="sxs-lookup"><span data-stu-id="9b5d3-131">SplitContainer Control</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
