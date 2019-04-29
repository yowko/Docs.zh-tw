---
title: HOW TO：在 Windows Forms 中建立 Windows 檔案總管樣式的介面
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: dd70feaba29e29748ac56729632fa359582a6914
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746651"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a><span data-ttu-id="14060-102">HOW TO：在 Windows Forms 中建立 Windows 檔案總管樣式的介面</span><span class="sxs-lookup"><span data-stu-id="14060-102">How to: Create a Windows Explorer–Style Interface on a Windows Form</span></span>
<span data-ttu-id="14060-103">Windows 檔案總管會是應用程式的一般使用者介面選擇，因為其準備好的熟悉度。</span><span class="sxs-lookup"><span data-stu-id="14060-103">Windows Explorer is a common user-interface choice for applications because of its ready familiarity.</span></span>  
  
 <span data-ttu-id="14060-104">基本上，Windows 檔案總管已<xref:System.Windows.Forms.TreeView>控制項和<xref:System.Windows.Forms.ListView>在個別的面板上的控制項。</span><span class="sxs-lookup"><span data-stu-id="14060-104">Windows Explorer is, essentially, a <xref:System.Windows.Forms.TreeView> control and a <xref:System.Windows.Forms.ListView> control on separate panels.</span></span> <span data-ttu-id="14060-105">面板是透過分隔器建立可調整大小。</span><span class="sxs-lookup"><span data-stu-id="14060-105">The panels are made resizable by a splitter.</span></span> <span data-ttu-id="14060-106">此控制項的排列方式可有效地顯示和瀏覽資訊。</span><span class="sxs-lookup"><span data-stu-id="14060-106">This arrangement of controls is very effective for displaying and browsing information.</span></span>  
  
 <span data-ttu-id="14060-107">下列步驟示範如何在 Windows 檔案總管類似的表單中排列控制項。</span><span class="sxs-lookup"><span data-stu-id="14060-107">The following steps show how to arrange controls in a Windows Explorer-like form.</span></span> <span data-ttu-id="14060-108">它們不會出現如何新增 Windows 檔案總管應用程式的檔案瀏覽功能。</span><span class="sxs-lookup"><span data-stu-id="14060-108">They do not show how to add the file-browsing functionality of the Windows Explorer application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14060-109">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="14060-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="14060-110">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="14060-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="14060-111">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="14060-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a><span data-ttu-id="14060-112">若要建立 Windows 檔案總管樣式的 Windows 表單</span><span class="sxs-lookup"><span data-stu-id="14060-112">To create a Windows Explorer-style Windows Form</span></span>  
  
1. <span data-ttu-id="14060-113">建立新的 Windows 應用程式專案 (**檔案** > **新增** > **專案** > **Visual C#** 或是**Visual Basic** > **傳統桌面** > **Windows Forms 應用程式**)。</span><span class="sxs-lookup"><span data-stu-id="14060-113">Create a new Windows Application project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2. <span data-ttu-id="14060-114">從**工具箱**:</span><span class="sxs-lookup"><span data-stu-id="14060-114">From the **Toolbox**:</span></span>  
  
    1. <span data-ttu-id="14060-115">拖曳<xref:System.Windows.Forms.SplitContainer>控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="14060-115">Drag a <xref:System.Windows.Forms.SplitContainer> control onto your form.</span></span>  
  
    2. <span data-ttu-id="14060-116">拖曳<xref:System.Windows.Forms.TreeView>程式控制**SplitterPanel1** (的面板<xref:System.Windows.Forms.SplitContainer>控制標記**Panel1**)。</span><span class="sxs-lookup"><span data-stu-id="14060-116">Drag a <xref:System.Windows.Forms.TreeView> control into **SplitterPanel1** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel1**).</span></span>  
  
    3. <span data-ttu-id="14060-117">拖曳<xref:System.Windows.Forms.ListView>程式控制**SplitterPanel2** (的面板<xref:System.Windows.Forms.SplitContainer>控制標記**Panel2**)。</span><span class="sxs-lookup"><span data-stu-id="14060-117">Drag a <xref:System.Windows.Forms.ListView> control into **SplitterPanel2** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel2**).</span></span>  
  
3. <span data-ttu-id="14060-118">按下 CTRL 鍵並依序按一下以選取所有的三個控制項。</span><span class="sxs-lookup"><span data-stu-id="14060-118">Select all three controls by pressing the CTRL key and clicking them in turn.</span></span> <span data-ttu-id="14060-119">當您選取<xref:System.Windows.Forms.SplitContainer>控制項中按一下 分隔器列，而不是面板。</span><span class="sxs-lookup"><span data-stu-id="14060-119">When you select the <xref:System.Windows.Forms.SplitContainer> control, click the splitter bar, rather than the panels.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="14060-120">請勿使用**全選**命令**編輯**功能表。</span><span class="sxs-lookup"><span data-stu-id="14060-120">Do not use the **Select All** command on the **Edit** menu.</span></span> <span data-ttu-id="14060-121">如果您這樣做，請在下一個步驟中所需的屬性不會出現在**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="14060-121">If you do so, the property needed in the next step will not appear in the **Properties** window.</span></span>  
  
4. <span data-ttu-id="14060-122">在 [屬性]  視窗中，將 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="14060-122">In the **Properties** window, set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
5. <span data-ttu-id="14060-123">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="14060-123">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="14060-124">此表單會顯示兩個部分使用者介面，類似於 Windows 檔案總管。</span><span class="sxs-lookup"><span data-stu-id="14060-124">The form displays a two-part user interface, similar to that of the Windows Explorer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="14060-125">當您拖曳分隔器時，重新調整大小的面板本身。</span><span class="sxs-lookup"><span data-stu-id="14060-125">When you drag the splitter, the panels resize themselves.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14060-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14060-126">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="14060-127">如何：利用 Windows Form 建立多窗格使用者介面</span><span class="sxs-lookup"><span data-stu-id="14060-127">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)
- [<span data-ttu-id="14060-128">如何：定義調整大小和位置行為在分隔視窗</span><span class="sxs-lookup"><span data-stu-id="14060-128">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)
- [<span data-ttu-id="14060-129">如何：水平分隔視窗</span><span class="sxs-lookup"><span data-stu-id="14060-129">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)
- [<span data-ttu-id="14060-130">SplitContainer 控制項</span><span class="sxs-lookup"><span data-stu-id="14060-130">SplitContainer Control</span></span>](splitcontainer-control-windows-forms.md)
