---
title: 逐步解說：使用 Windows Forms 控制項的智慧標籤執行一般工作
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: 1cc854d735ba88a301d6e2f6a83fe5c8bf881380
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211410"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a><span data-ttu-id="80d8f-102">逐步解說：使用 Windows Forms 控制項的智慧標籤執行一般工作</span><span class="sxs-lookup"><span data-stu-id="80d8f-102">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>

<span data-ttu-id="80d8f-103">您建構表單和控制項的 Windows Forms 應用程式時，有許多重複執行的工作。</span><span class="sxs-lookup"><span data-stu-id="80d8f-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="80d8f-104">以下是一些經常執行的工作就會發生：</span><span class="sxs-lookup"><span data-stu-id="80d8f-104">These are some of the commonly performed tasks you will encounter:</span></span>

- <span data-ttu-id="80d8f-105">新增或移除工作索引標籤上<xref:System.Windows.Forms.TabControl>。</span><span class="sxs-lookup"><span data-stu-id="80d8f-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>

- <span data-ttu-id="80d8f-106">將控制項固定到其父代。</span><span class="sxs-lookup"><span data-stu-id="80d8f-106">Docking a control to its parent.</span></span>

- <span data-ttu-id="80d8f-107">變更的方向<xref:System.Windows.Forms.SplitContainer>控制項。</span><span class="sxs-lookup"><span data-stu-id="80d8f-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="80d8f-108">若要加快開發的速度，許多控制項都提供智慧標籤，也就是可讓您在設計階段執行常見工作，像是這些功能是以單一軌跡的即時線上功能表。</span><span class="sxs-lookup"><span data-stu-id="80d8f-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="80d8f-109">這些工作會呼叫*智慧標籤動詞*。</span><span class="sxs-lookup"><span data-stu-id="80d8f-109">These tasks are called *smart-tag verbs*.</span></span>

<span data-ttu-id="80d8f-110">智慧標籤的設計工具中的存留期保持附加至控制項執行個體，並永遠都可以使用。</span><span class="sxs-lookup"><span data-stu-id="80d8f-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

<span data-ttu-id="80d8f-111">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="80d8f-111">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="80d8f-112">建立 Windows Forms 專案</span><span class="sxs-lookup"><span data-stu-id="80d8f-112">Creating a Windows Forms project</span></span>

- <span data-ttu-id="80d8f-113">使用智慧標籤</span><span class="sxs-lookup"><span data-stu-id="80d8f-113">Using smart tags</span></span>

- <span data-ttu-id="80d8f-114">啟用和停用智慧標籤</span><span class="sxs-lookup"><span data-stu-id="80d8f-114">Enabling and Disabling Smart Tags</span></span>

<span data-ttu-id="80d8f-115">完成後，您就會了解這些重要配置功能所扮演的角色。</span><span class="sxs-lookup"><span data-stu-id="80d8f-115">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="80d8f-116">建立專案</span><span class="sxs-lookup"><span data-stu-id="80d8f-116">Create the project</span></span>

<span data-ttu-id="80d8f-117">第一個步驟是建立專案並設定表單。</span><span class="sxs-lookup"><span data-stu-id="80d8f-117">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="80d8f-118">在 Visual Studio 中建立名為"SmartTagsExample 」 的 Windows 架構應用程式專案 (**檔案** > **新增** > **專案** > **視覺化C#** 或是**Visual Basic** > **傳統桌面** > **Windows Form應用程式**)。</span><span class="sxs-lookup"><span data-stu-id="80d8f-118">In Visual Studio, create a Windows-based application project called "SmartTagsExample" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="80d8f-119">選取中的表單**Windows Form 設計工具**。</span><span class="sxs-lookup"><span data-stu-id="80d8f-119">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-smart-tags"></a><span data-ttu-id="80d8f-120">使用智慧標籤</span><span class="sxs-lookup"><span data-stu-id="80d8f-120">Use smart tags</span></span>

<span data-ttu-id="80d8f-121">在設計階段，它們提供的控制項上，都可以使用智慧標籤。</span><span class="sxs-lookup"><span data-stu-id="80d8f-121">Smart tags are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="80d8f-122">拖曳<xref:System.Windows.Forms.TabControl>從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="80d8f-122">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="80d8f-123">請注意智慧標籤圖像 (![智慧標籤圖像](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))，會出現在並存的<xref:System.Windows.Forms.TabControl>。</span><span class="sxs-lookup"><span data-stu-id="80d8f-123">Note the smart-tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="80d8f-124">按一下智慧標籤圖像 （glyph）。</span><span class="sxs-lookup"><span data-stu-id="80d8f-124">Click the smart-tag glyph.</span></span> <span data-ttu-id="80d8f-125">在字符旁邊會出現快顯功能表中，選取**加入索引標籤**項目。</span><span class="sxs-lookup"><span data-stu-id="80d8f-125">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="80d8f-126">觀察新的索引標籤頁加入<xref:System.Windows.Forms.TabControl>。</span><span class="sxs-lookup"><span data-stu-id="80d8f-126">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="80d8f-127">從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="80d8f-127">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="80d8f-128">按一下智慧標籤圖像 （glyph）。</span><span class="sxs-lookup"><span data-stu-id="80d8f-128">Click the smart-tag glyph.</span></span> <span data-ttu-id="80d8f-129">在字符旁邊會出現快顯功能表中，選取**加入資料行**項目。</span><span class="sxs-lookup"><span data-stu-id="80d8f-129">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="80d8f-130">觀察出新的資料行已經新增到<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="80d8f-130">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="80d8f-131">從 [工具箱] <xref:System.Windows.Forms.SplitContainer>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="80d8f-131">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="80d8f-132">按一下智慧標籤圖像 （glyph）。</span><span class="sxs-lookup"><span data-stu-id="80d8f-132">Click the smart-tag glyph.</span></span> <span data-ttu-id="80d8f-133">在字符旁邊會出現快顯功能表中，選取**水平分隔器方向**項目。</span><span class="sxs-lookup"><span data-stu-id="80d8f-133">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="80d8f-134">觀察<xref:System.Windows.Forms.SplitContainer>控制的分隔器列現在是水平方向。</span><span class="sxs-lookup"><span data-stu-id="80d8f-134">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="80d8f-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80d8f-135">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
- <span data-ttu-id="80d8f-136">[逐步解說：將智慧標籤加入至 Windows Form 元件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="80d8f-136">[Walkthrough: Adding Smart Tags to a Windows Forms Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))</span></span>
