---
title: 逐步解說：使用 Windows Form 控制項中的智慧標籤執行一般工作
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: d1c69d2e9e89e0a4fed767216e8743a0ac9ac81d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741129"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a><span data-ttu-id="f57de-102">逐步解說：使用 Windows Form 控制項中的智慧標籤執行一般工作</span><span class="sxs-lookup"><span data-stu-id="f57de-102">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>
<span data-ttu-id="f57de-103">您建構表單和控制項的 Windows Forms 應用程式時，有許多重複執行的工作。</span><span class="sxs-lookup"><span data-stu-id="f57de-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="f57de-104">以下是一些經常執行的工作就會發生：</span><span class="sxs-lookup"><span data-stu-id="f57de-104">These are some of the commonly performed tasks you will encounter:</span></span>  
  
-   <span data-ttu-id="f57de-105">新增或移除工作索引標籤上<xref:System.Windows.Forms.TabControl>。</span><span class="sxs-lookup"><span data-stu-id="f57de-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>  
  
-   <span data-ttu-id="f57de-106">將控制項固定到其父代。</span><span class="sxs-lookup"><span data-stu-id="f57de-106">Docking a control to its parent.</span></span>  
  
-   <span data-ttu-id="f57de-107">變更的方向<xref:System.Windows.Forms.SplitContainer>控制項。</span><span class="sxs-lookup"><span data-stu-id="f57de-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>  
  
 <span data-ttu-id="f57de-108">若要加快開發的速度，許多控制項都提供智慧標籤，也就是可讓您在設計階段執行常見工作，像是這些功能是以單一軌跡的即時線上功能表。</span><span class="sxs-lookup"><span data-stu-id="f57de-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="f57de-109">這些工作會呼叫*智慧標籤動詞*。</span><span class="sxs-lookup"><span data-stu-id="f57de-109">These tasks are called *smart-tag verbs*.</span></span>  
  
 <span data-ttu-id="f57de-110">智慧標籤的設計工具中的存留期保持附加至控制項執行個體，並永遠都可以使用。</span><span class="sxs-lookup"><span data-stu-id="f57de-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>  
  
 <span data-ttu-id="f57de-111">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="f57de-111">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="f57de-112">建立 Windows Forms 專案</span><span class="sxs-lookup"><span data-stu-id="f57de-112">Creating a Windows Forms project</span></span>  
  
-   <span data-ttu-id="f57de-113">使用智慧標籤</span><span class="sxs-lookup"><span data-stu-id="f57de-113">Using smart tags</span></span>  
  
-   <span data-ttu-id="f57de-114">啟用和停用智慧標籤</span><span class="sxs-lookup"><span data-stu-id="f57de-114">Enabling and Disabling Smart Tags</span></span>  
  
 <span data-ttu-id="f57de-115">完成後，您就會了解這些重要配置功能所扮演的角色。</span><span class="sxs-lookup"><span data-stu-id="f57de-115">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f57de-116">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="f57de-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f57de-117">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="f57de-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f57de-118">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="f57de-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="f57de-119">建立專案</span><span class="sxs-lookup"><span data-stu-id="f57de-119">Creating the Project</span></span>  
 <span data-ttu-id="f57de-120">第一個步驟是建立專案並設定表單。</span><span class="sxs-lookup"><span data-stu-id="f57de-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="f57de-121">若要建立專案</span><span class="sxs-lookup"><span data-stu-id="f57de-121">To create the project</span></span>  
  
1.  <span data-ttu-id="f57de-122">建立以 Windows 為基礎的應用程式專案，稱為 「 SmartTagsExample"(**檔案** > **新增** > **專案** >  **Visual C#** 或是**Visual Basic** > **傳統桌面** > **Windows Forms 應用程式**)。</span><span class="sxs-lookup"><span data-stu-id="f57de-122">Create a Windows-based application project called "SmartTagsExample" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="f57de-123">選取中的表單**Windows Form 設計工具**。</span><span class="sxs-lookup"><span data-stu-id="f57de-123">Select the form in the **Windows Forms Designer**.</span></span>  
  
## <a name="using-smart-tags"></a><span data-ttu-id="f57de-124">使用智慧標籤</span><span class="sxs-lookup"><span data-stu-id="f57de-124">Using Smart Tags</span></span>  
 <span data-ttu-id="f57de-125">在設計階段，它們提供的控制項上，都可以使用智慧標籤。</span><span class="sxs-lookup"><span data-stu-id="f57de-125">Smart tags are always available at design time on controls that offer them.</span></span>  
  
#### <a name="to-use-smart-tags"></a><span data-ttu-id="f57de-126">若要使用智慧標籤</span><span class="sxs-lookup"><span data-stu-id="f57de-126">To use smart tags</span></span>  
  
1.  <span data-ttu-id="f57de-127">拖曳<xref:System.Windows.Forms.TabControl>從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="f57de-127">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="f57de-128">請注意智慧標籤圖像 (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))，會出現在並存的<xref:System.Windows.Forms.TabControl>。</span><span class="sxs-lookup"><span data-stu-id="f57de-128">Note the smart-tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
2.  <span data-ttu-id="f57de-129">按一下智慧標籤圖像 （glyph）。</span><span class="sxs-lookup"><span data-stu-id="f57de-129">Click the smart-tag glyph.</span></span> <span data-ttu-id="f57de-130">在字符旁邊會出現快顯功能表中，選取**加入索引標籤**項目。</span><span class="sxs-lookup"><span data-stu-id="f57de-130">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="f57de-131">觀察新的索引標籤頁加入<xref:System.Windows.Forms.TabControl>。</span><span class="sxs-lookup"><span data-stu-id="f57de-131">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
3.  <span data-ttu-id="f57de-132">拖曳<xref:System.Windows.Forms.TableLayoutPanel>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="f57de-132">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
4.  <span data-ttu-id="f57de-133">按一下智慧標籤圖像 （glyph）。</span><span class="sxs-lookup"><span data-stu-id="f57de-133">Click the smart-tag glyph.</span></span> <span data-ttu-id="f57de-134">在字符旁邊會出現快顯功能表中，選取**加入資料行**項目。</span><span class="sxs-lookup"><span data-stu-id="f57de-134">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="f57de-135">觀察出新的資料行已經新增到<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="f57de-135">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
5.  <span data-ttu-id="f57de-136">拖曳<xref:System.Windows.Forms.SplitContainer>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="f57de-136">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>  
  
6.  <span data-ttu-id="f57de-137">按一下智慧標籤圖像 （glyph）。</span><span class="sxs-lookup"><span data-stu-id="f57de-137">Click the smart-tag glyph.</span></span> <span data-ttu-id="f57de-138">在字符旁邊會出現快顯功能表中，選取**水平分隔器方向**項目。</span><span class="sxs-lookup"><span data-stu-id="f57de-138">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="f57de-139">觀察<xref:System.Windows.Forms.SplitContainer>控制的分隔器列現在是水平方向。</span><span class="sxs-lookup"><span data-stu-id="f57de-139">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f57de-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f57de-140">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 <xref:System.Windows.Forms.TabControl>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.ComponentModel.Design.DesignerActionList>  
 [<span data-ttu-id="f57de-141">逐步解說： 將智慧標籤加入至 Windows Form 元件</span><span class="sxs-lookup"><span data-stu-id="f57de-141">Walkthrough: Adding Smart Tags to a Windows Forms Component</span></span>](https://msdn.microsoft.com/library/a6814169-fa7d-4527-808c-637ca5c95f63)
