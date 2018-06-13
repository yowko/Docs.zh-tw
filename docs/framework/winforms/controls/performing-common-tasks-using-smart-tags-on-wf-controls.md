---
title: 逐步解說：使用 Windows Form 控制項中的智慧標籤執行一般工作
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: a558f6d274f260fc91fd140e9dae2c740b1ae00d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537940"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a><span data-ttu-id="f156f-102">逐步解說：使用 Windows Form 控制項中的智慧標籤執行一般工作</span><span class="sxs-lookup"><span data-stu-id="f156f-102">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>
<span data-ttu-id="f156f-103">Windows Form 應用程式中建構表單和控制項，有許多工作，您將會重複執行。</span><span class="sxs-lookup"><span data-stu-id="f156f-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="f156f-104">以下是一些經常執行的工作，您將會遇到的：</span><span class="sxs-lookup"><span data-stu-id="f156f-104">These are some of the commonly performed tasks you will encounter:</span></span>  
  
-   <span data-ttu-id="f156f-105">新增或移除索引標籤上<xref:System.Windows.Forms.TabControl>。</span><span class="sxs-lookup"><span data-stu-id="f156f-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>  
  
-   <span data-ttu-id="f156f-106">將控制項固定到其父代。</span><span class="sxs-lookup"><span data-stu-id="f156f-106">Docking a control to its parent.</span></span>  
  
-   <span data-ttu-id="f156f-107">變更的方向<xref:System.Windows.Forms.SplitContainer>控制項。</span><span class="sxs-lookup"><span data-stu-id="f156f-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>  
  
 <span data-ttu-id="f156f-108">為加速開發，許多控制項都提供智慧標籤，也就是即時線上功能表可讓您在設計階段執行常見工作，像是在單一的筆勢。</span><span class="sxs-lookup"><span data-stu-id="f156f-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="f156f-109">這些工作會呼叫*智慧標籤動詞*。</span><span class="sxs-lookup"><span data-stu-id="f156f-109">These tasks are called *smart-tag verbs*.</span></span>  
  
 <span data-ttu-id="f156f-110">智慧標籤在設計工具中的存留期間保持附加至控制項的執行個體，並永遠都可以使用。</span><span class="sxs-lookup"><span data-stu-id="f156f-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>  
  
 <span data-ttu-id="f156f-111">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="f156f-111">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="f156f-112">建立 Windows Forms 專案</span><span class="sxs-lookup"><span data-stu-id="f156f-112">Creating a Windows Forms project</span></span>  
  
-   <span data-ttu-id="f156f-113">使用智慧標籤</span><span class="sxs-lookup"><span data-stu-id="f156f-113">Using smart tags</span></span>  
  
-   <span data-ttu-id="f156f-114">啟用和停用智慧標籤</span><span class="sxs-lookup"><span data-stu-id="f156f-114">Enabling and Disabling Smart Tags</span></span>  
  
 <span data-ttu-id="f156f-115">完成後，您就會了解這些重要配置功能所扮演的角色。</span><span class="sxs-lookup"><span data-stu-id="f156f-115">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f156f-116">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="f156f-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f156f-117">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="f156f-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f156f-118">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="f156f-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="f156f-119">建立專案</span><span class="sxs-lookup"><span data-stu-id="f156f-119">Creating the Project</span></span>  
 <span data-ttu-id="f156f-120">第一個步驟是建立專案並設定表單。</span><span class="sxs-lookup"><span data-stu-id="f156f-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="f156f-121">若要建立專案</span><span class="sxs-lookup"><span data-stu-id="f156f-121">To create the project</span></span>  
  
1.  <span data-ttu-id="f156f-122">建立 Windows 架構應用程式專案，稱為 「 SmartTagsExample"。</span><span class="sxs-lookup"><span data-stu-id="f156f-122">Create a Windows-based application project called "SmartTagsExample".</span></span> <span data-ttu-id="f156f-123">如需詳細資訊，請參閱[如何：建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)。</span><span class="sxs-lookup"><span data-stu-id="f156f-123">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="f156f-124">選取的表單中**Windows Form 設計工具**。</span><span class="sxs-lookup"><span data-stu-id="f156f-124">Select the form in the **Windows Forms Designer**.</span></span>  
  
## <a name="using-smart-tags"></a><span data-ttu-id="f156f-125">使用智慧標籤</span><span class="sxs-lookup"><span data-stu-id="f156f-125">Using Smart Tags</span></span>  
 <span data-ttu-id="f156f-126">控制項提供設計階段，仍可以使用智慧標籤。</span><span class="sxs-lookup"><span data-stu-id="f156f-126">Smart tags are always available at design time on controls that offer them.</span></span>  
  
#### <a name="to-use-smart-tags"></a><span data-ttu-id="f156f-127">若要使用智慧標籤</span><span class="sxs-lookup"><span data-stu-id="f156f-127">To use smart tags</span></span>  
  
1.  <span data-ttu-id="f156f-128">拖曳<xref:System.Windows.Forms.TabControl>從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="f156f-128">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="f156f-129">請注意智慧標籤圖像 (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 出現在並存的<xref:System.Windows.Forms.TabControl>。</span><span class="sxs-lookup"><span data-stu-id="f156f-129">Note the smart-tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
2.  <span data-ttu-id="f156f-130">按一下智慧標籤圖像 （glyph）。</span><span class="sxs-lookup"><span data-stu-id="f156f-130">Click the smart-tag glyph.</span></span> <span data-ttu-id="f156f-131">在字符旁邊會出現快顯功能表中選取**加入索引標籤**項目。</span><span class="sxs-lookup"><span data-stu-id="f156f-131">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="f156f-132">觀察，加入新的索引標籤頁面<xref:System.Windows.Forms.TabControl>。</span><span class="sxs-lookup"><span data-stu-id="f156f-132">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
3.  <span data-ttu-id="f156f-133">拖曳<xref:System.Windows.Forms.TableLayoutPanel>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="f156f-133">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
4.  <span data-ttu-id="f156f-134">按一下智慧標籤圖像 （glyph）。</span><span class="sxs-lookup"><span data-stu-id="f156f-134">Click the smart-tag glyph.</span></span> <span data-ttu-id="f156f-135">在字符旁邊會出現快顯功能表中選取**加入資料行**項目。</span><span class="sxs-lookup"><span data-stu-id="f156f-135">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="f156f-136">觀察，加入新的資料行<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="f156f-136">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
5.  <span data-ttu-id="f156f-137">拖曳<xref:System.Windows.Forms.SplitContainer>控制項從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="f156f-137">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>  
  
6.  <span data-ttu-id="f156f-138">按一下智慧標籤圖像 （glyph）。</span><span class="sxs-lookup"><span data-stu-id="f156f-138">Click the smart-tag glyph.</span></span> <span data-ttu-id="f156f-139">在字符旁邊會出現快顯功能表中選取**水平分隔器方向**項目。</span><span class="sxs-lookup"><span data-stu-id="f156f-139">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="f156f-140">觀察<xref:System.Windows.Forms.SplitContainer>控制項的分隔列現在是水平方向。</span><span class="sxs-lookup"><span data-stu-id="f156f-140">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f156f-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f156f-141">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 <xref:System.Windows.Forms.TabControl>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.ComponentModel.Design.DesignerActionList>  
 [<span data-ttu-id="f156f-142">逐步解說： 加入 Windows Form 元件中的智慧標籤</span><span class="sxs-lookup"><span data-stu-id="f156f-142">Walkthrough: Adding Smart Tags to a Windows Forms Component</span></span>](http://msdn.microsoft.com/library/a6814169-fa7d-4527-808c-637ca5c95f63)
