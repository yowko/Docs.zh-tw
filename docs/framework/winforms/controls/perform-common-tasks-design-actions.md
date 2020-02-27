---
title: 使用控制項上的設計工具動作執行一般工作
ms.date: 02/13/2019
helpviewer_keywords:
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 342741b9ce032b1b8ec50a6c689d9109d12f5b3b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634880"
---
# <a name="walkthrough-perform-common-tasks-using-designer-actions"></a><span data-ttu-id="f7ac9-102">逐步解說：使用設計工具動作執行一般工作</span><span class="sxs-lookup"><span data-stu-id="f7ac9-102">Walkthrough: Perform common tasks using designer actions</span></span>

<span data-ttu-id="f7ac9-103">當您為 Windows Forms 應用程式建立表單和控制項時，您會重複執行許多工作。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-103">As you construct forms and controls for your Windows Forms application, there are many tasks you'll perform repeatedly.</span></span> <span data-ttu-id="f7ac9-104">下列清單顯示您將會遇到的一些常見工作：</span><span class="sxs-lookup"><span data-stu-id="f7ac9-104">The following list shows some of the commonly performed tasks you'll come across:</span></span>

- <span data-ttu-id="f7ac9-105">新增或移除 <xref:System.Windows.Forms.TabControl>上的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>
- <span data-ttu-id="f7ac9-106">將控制項停駐于其父系。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-106">Docking a control to its parent.</span></span>
- <span data-ttu-id="f7ac9-107">變更 <xref:System.Windows.Forms.SplitContainer> 控制項的方向。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="f7ac9-108">為了加速開發，許多控制項都有提供設計工具動作，這是即時線上功能表，可讓您在設計階段于單一手勢中執行這類常見工作。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-108">To speed development, many controls offer designer actions, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="f7ac9-109">這些工作稱為「*設計工具動作」動詞*。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-109">These tasks are called *designer actions verbs*.</span></span>

<span data-ttu-id="f7ac9-110">設計工具動作會在設計工具中保持附加至控制項實例的存留期，而且一律可供使用。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-110">Designer actions remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="f7ac9-111">建立專案</span><span class="sxs-lookup"><span data-stu-id="f7ac9-111">Create the project</span></span>

<span data-ttu-id="f7ac9-112">第一個步驟是建立專案並設定表單。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-112">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="f7ac9-113">在 Visual Studio 中，建立名為**DesignerActionsExample**的 Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-113">In Visual Studio, create a Windows-based application project called **DesignerActionsExample**.</span></span>

2. <span data-ttu-id="f7ac9-114">在  **Windows Form 設計工具**中選取表單。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-114">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-designer-actions"></a><span data-ttu-id="f7ac9-115">使用設計工具動作</span><span class="sxs-lookup"><span data-stu-id="f7ac9-115">Use designer actions</span></span>

<span data-ttu-id="f7ac9-116">在設計階段，設計工具動作一定會在提供它們的控制項上使用。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-116">Designer actions are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="f7ac9-117">將 <xref:System.Windows.Forms.TabControl> 從 **工具箱** 拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-117">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="f7ac9-118">請注意，出現在 <xref:System.Windows.Forms.TabControl>側邊的設計工具動作圖像（![小型黑色箭號](./media/designer-actions-glyph.gif)）。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-118">Note the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="f7ac9-119">按一下 [設計工具動作] 圖像。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-119">Click the designer actions glyph.</span></span> <span data-ttu-id="f7ac9-120">在出現在字元旁邊的快捷方式功能表中，選取 [**加入]** 索引標籤專案。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-120">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="f7ac9-121">請注意，新的索引標籤頁已加入至 <xref:System.Windows.Forms.TabControl>。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-121">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="f7ac9-122">從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-122">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="f7ac9-123">按一下 [設計工具動作] 圖像。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-123">Click the designer actions glyph.</span></span> <span data-ttu-id="f7ac9-124">在顯示于圖像的快捷方式功能表中，選取 [**加入資料行**] 專案。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-124">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="f7ac9-125">請注意，新的資料行會加入至 <xref:System.Windows.Forms.TableLayoutPanel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-125">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="f7ac9-126">從 [工具箱] <xref:System.Windows.Forms.SplitContainer>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-126">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="f7ac9-127">按一下 [設計工具動作] 圖像。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-127">Click the designer actions glyph.</span></span> <span data-ttu-id="f7ac9-128">在顯示于圖像旁邊的快捷方式功能表中，選取**水準分隔器方向**專案。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-128">In the shortcut menu that appears next to the glyph, select the **Horizontal Splitter Orientation** item.</span></span> <span data-ttu-id="f7ac9-129">請注意，<xref:System.Windows.Forms.SplitContainer> 控制項的分隔器列現在是水準方向。</span><span class="sxs-lookup"><span data-stu-id="f7ac9-129">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7ac9-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7ac9-130">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
