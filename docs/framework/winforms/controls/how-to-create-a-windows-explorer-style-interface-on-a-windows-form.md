---
title: 作法：在 Windows Forms 中建立 Windows 檔案總管樣式的介面
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: db2c5431dfb0156c1508a18ef13d2af80eb4981b
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039527"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a><span data-ttu-id="bec87-102">作法：在 Windows Forms 中建立 Windows 檔案總管樣式的介面</span><span class="sxs-lookup"><span data-stu-id="bec87-102">How to: Create a Windows Explorer–Style Interface on a Windows Form</span></span>
<span data-ttu-id="bec87-103">Windows Explorer 是應用程式的常見使用者介面選擇, 因為它已經很熟悉。</span><span class="sxs-lookup"><span data-stu-id="bec87-103">Windows Explorer is a common user-interface choice for applications because of its ready familiarity.</span></span>

 <span data-ttu-id="bec87-104">Windows Explorer 基本上<xref:System.Windows.Forms.TreeView>是控制項<xref:System.Windows.Forms.ListView>和控制項, 分別位於不同的面板上。</span><span class="sxs-lookup"><span data-stu-id="bec87-104">Windows Explorer is, essentially, a <xref:System.Windows.Forms.TreeView> control and a <xref:System.Windows.Forms.ListView> control on separate panels.</span></span> <span data-ttu-id="bec87-105">這些面板可透過分隔器進行調整。</span><span class="sxs-lookup"><span data-stu-id="bec87-105">The panels are made resizable by a splitter.</span></span> <span data-ttu-id="bec87-106">這種控制項的相片順序對於顯示和流覽資訊非常有效。</span><span class="sxs-lookup"><span data-stu-id="bec87-106">This arrangement of controls is very effective for displaying and browsing information.</span></span>

 <span data-ttu-id="bec87-107">下列步驟示範如何在類似 Windows Explorer 的表單中排列控制項。</span><span class="sxs-lookup"><span data-stu-id="bec87-107">The following steps show how to arrange controls in a Windows Explorer-like form.</span></span> <span data-ttu-id="bec87-108">它們不會示範如何新增 Windows Explorer 應用程式的檔案流覽功能。</span><span class="sxs-lookup"><span data-stu-id="bec87-108">They do not show how to add the file-browsing functionality of the Windows Explorer application.</span></span>

## <a name="to-create-a-windows-explorer-style-windows-form"></a><span data-ttu-id="bec87-109">建立 Windows Explorer 樣式的 Windows Form</span><span class="sxs-lookup"><span data-stu-id="bec87-109">To create a Windows Explorer-style Windows Form</span></span>

1. <span data-ttu-id="bec87-110">建立新的 Windows 應用程式專案  > (檔案 **新增** > **專案** > **視覺效果C#** 或**Visual Basic**  > **傳統桌面** >  **Windows Forms 應用程式**)。</span><span class="sxs-lookup"><span data-stu-id="bec87-110">Create a new Windows Application project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="bec87-111">從 [**工具箱**]:</span><span class="sxs-lookup"><span data-stu-id="bec87-111">From the **Toolbox**:</span></span>

    1. <span data-ttu-id="bec87-112"><xref:System.Windows.Forms.SplitContainer>將控制項拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="bec87-112">Drag a <xref:System.Windows.Forms.SplitContainer> control onto your form.</span></span>

    2. <span data-ttu-id="bec87-113">將控制項拖曳至**SplitterPanel1** (標示為**Panel1**之<xref:System.Windows.Forms.SplitContainer>控制項的面板)。 <xref:System.Windows.Forms.TreeView></span><span class="sxs-lookup"><span data-stu-id="bec87-113">Drag a <xref:System.Windows.Forms.TreeView> control into **SplitterPanel1** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel1**).</span></span>

    3. <span data-ttu-id="bec87-114">將控制項拖曳至**SplitterPanel2** (標示為**Panel2**之<xref:System.Windows.Forms.SplitContainer>控制項的面板)。 <xref:System.Windows.Forms.ListView></span><span class="sxs-lookup"><span data-stu-id="bec87-114">Drag a <xref:System.Windows.Forms.ListView> control into **SplitterPanel2** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel2**).</span></span>

3. <span data-ttu-id="bec87-115">按下 CTRL 鍵並依序按一下, 以選取所有三個控制項。</span><span class="sxs-lookup"><span data-stu-id="bec87-115">Select all three controls by pressing the CTRL key and clicking them in turn.</span></span> <span data-ttu-id="bec87-116">當您選取<xref:System.Windows.Forms.SplitContainer>控制項時, 請按一下分隔欄, 而不是面板。</span><span class="sxs-lookup"><span data-stu-id="bec87-116">When you select the <xref:System.Windows.Forms.SplitContainer> control, click the splitter bar, rather than the panels.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="bec87-117">請勿使用 [**編輯**] 功能表上的 [**全選**] 命令。</span><span class="sxs-lookup"><span data-stu-id="bec87-117">Do not use the **Select All** command on the **Edit** menu.</span></span> <span data-ttu-id="bec87-118">如果您這樣做, 下一個步驟所需的屬性將不會出現在 [**屬性**] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="bec87-118">If you do so, the property needed in the next step will not appear in the **Properties** window.</span></span>

4. <span data-ttu-id="bec87-119">在 [屬性] 視窗中，將 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="bec87-119">In the **Properties** window, set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

5. <span data-ttu-id="bec87-120">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="bec87-120">Press F5 to run the application.</span></span>

     <span data-ttu-id="bec87-121">表單會顯示兩部分的使用者介面, 類似于 Windows Explorer。</span><span class="sxs-lookup"><span data-stu-id="bec87-121">The form displays a two-part user interface, similar to that of the Windows Explorer.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="bec87-122">當您拖曳分隔器時, 面板會自行調整大小。</span><span class="sxs-lookup"><span data-stu-id="bec87-122">When you drag the splitter, the panels resize themselves.</span></span>

## <a name="see-also"></a><span data-ttu-id="bec87-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bec87-123">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="bec87-124">如何：建立具有 Windows Forms 的多窗格使用者介面</span><span class="sxs-lookup"><span data-stu-id="bec87-124">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)
- [<span data-ttu-id="bec87-125">如何：定義分割視窗中的調整大小和位置行為</span><span class="sxs-lookup"><span data-stu-id="bec87-125">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)
- [<span data-ttu-id="bec87-126">如何：水準分割視窗</span><span class="sxs-lookup"><span data-stu-id="bec87-126">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)
- [<span data-ttu-id="bec87-127">SplitContainer 控制項</span><span class="sxs-lookup"><span data-stu-id="bec87-127">SplitContainer Control</span></span>](splitcontainer-control-windows-forms.md)
