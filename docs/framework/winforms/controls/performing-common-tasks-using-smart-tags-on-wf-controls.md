---
title: Performi 在控制項上使用智慧標籤的一般工作
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 826313d0a89410f62c034a5fba4dee32e90a1750
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744253"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a><span data-ttu-id="ac180-102">逐步解說：使用智慧標籤執行一般工作</span><span class="sxs-lookup"><span data-stu-id="ac180-102">Walkthrough: Perform Common Tasks Using Smart Tags</span></span>

<span data-ttu-id="ac180-103">當您為 Windows Forms 應用程式建立表單和控制項時，您會重複執行許多工作。</span><span class="sxs-lookup"><span data-stu-id="ac180-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="ac180-104">以下是您將會遇到的一些經常執行的工作：</span><span class="sxs-lookup"><span data-stu-id="ac180-104">These are some of the commonly performed tasks you will encounter:</span></span>

- <span data-ttu-id="ac180-105">新增或移除 <xref:System.Windows.Forms.TabControl>上的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ac180-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>

- <span data-ttu-id="ac180-106">將控制項停駐于其父系。</span><span class="sxs-lookup"><span data-stu-id="ac180-106">Docking a control to its parent.</span></span>

- <span data-ttu-id="ac180-107">變更 <xref:System.Windows.Forms.SplitContainer> 控制項的方向。</span><span class="sxs-lookup"><span data-stu-id="ac180-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="ac180-108">為了加速開發，許多控制項都提供智慧標籤，這些都是即時線上的功能表，可讓您在設計階段于單一手勢中執行像這些的一般工作。</span><span class="sxs-lookup"><span data-stu-id="ac180-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="ac180-109">這些工作稱為*智慧標籤動詞*。</span><span class="sxs-lookup"><span data-stu-id="ac180-109">These tasks are called *smart-tag verbs*.</span></span>

<span data-ttu-id="ac180-110">智慧標籤會在設計工具中保持附加至控制項實例的存留期，而且一律可供使用。</span><span class="sxs-lookup"><span data-stu-id="ac180-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="ac180-111">建立專案</span><span class="sxs-lookup"><span data-stu-id="ac180-111">Create the project</span></span>

<span data-ttu-id="ac180-112">第一個步驟是建立專案並設定表單。</span><span class="sxs-lookup"><span data-stu-id="ac180-112">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="ac180-113">在 Visual Studio 中，建立名為**SmartTagsExample**的 Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="ac180-113">In Visual Studio, create a Windows-based application project called **SmartTagsExample**.</span></span>

2. <span data-ttu-id="ac180-114">在  **Windows Form 設計工具**中選取表單。</span><span class="sxs-lookup"><span data-stu-id="ac180-114">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-smart-tags"></a><span data-ttu-id="ac180-115">使用智慧標籤</span><span class="sxs-lookup"><span data-stu-id="ac180-115">Use smart tags</span></span>

<span data-ttu-id="ac180-116">在設計階段，智慧標籤在提供它們的控制項上一律可供使用。</span><span class="sxs-lookup"><span data-stu-id="ac180-116">Smart tags are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="ac180-117">將 <xref:System.Windows.Forms.TabControl> 從 **工具箱** 拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="ac180-117">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="ac180-118">請注意，出現在 <xref:System.Windows.Forms.TabControl>側邊的智慧標籤圖像（![智慧標籤圖像](./media/vs-winformsmttagglyph.gif)）。</span><span class="sxs-lookup"><span data-stu-id="ac180-118">Note the smart-tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif)) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="ac180-119">按一下智慧標籤圖像。</span><span class="sxs-lookup"><span data-stu-id="ac180-119">Click the smart-tag glyph.</span></span> <span data-ttu-id="ac180-120">在出現在字元旁邊的快捷方式功能表中，選取 [**加入]** 索引標籤專案。</span><span class="sxs-lookup"><span data-stu-id="ac180-120">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="ac180-121">請注意，新的索引標籤頁已加入至 <xref:System.Windows.Forms.TabControl>。</span><span class="sxs-lookup"><span data-stu-id="ac180-121">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="ac180-122">從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="ac180-122">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="ac180-123">按一下智慧標籤圖像。</span><span class="sxs-lookup"><span data-stu-id="ac180-123">Click the smart-tag glyph.</span></span> <span data-ttu-id="ac180-124">在顯示于圖像的快捷方式功能表中，選取 [**加入資料行**] 專案。</span><span class="sxs-lookup"><span data-stu-id="ac180-124">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="ac180-125">請注意，新的資料行會加入至 <xref:System.Windows.Forms.TableLayoutPanel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="ac180-125">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="ac180-126">從 [工具箱] <xref:System.Windows.Forms.SplitContainer>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="ac180-126">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="ac180-127">按一下智慧標籤圖像。</span><span class="sxs-lookup"><span data-stu-id="ac180-127">Click the smart-tag glyph.</span></span> <span data-ttu-id="ac180-128">在顯示于圖像旁邊的快捷方式功能表中，選取**水準分隔器方向**專案。</span><span class="sxs-lookup"><span data-stu-id="ac180-128">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="ac180-129">請注意，<xref:System.Windows.Forms.SplitContainer> 控制項的分隔器列現在是水準方向。</span><span class="sxs-lookup"><span data-stu-id="ac180-129">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac180-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="ac180-130">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
