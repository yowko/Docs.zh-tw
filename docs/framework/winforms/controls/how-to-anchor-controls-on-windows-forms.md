---
title: HOW TO：錨定 Windows Forms 上的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
ms.openlocfilehash: b5550aef220ece09d5486421275b19a37bfe9011
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59329774"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a><span data-ttu-id="40fba-102">HOW TO：錨定 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="40fba-102">How to: Anchor Controls on Windows Forms</span></span>
<span data-ttu-id="40fba-103">如果您要設計的表單，使用者可以在執行階段調整大小，您的表單上的控制項應該調整大小，並適當地重新調整位置。</span><span class="sxs-lookup"><span data-stu-id="40fba-103">If you are designing a form that the user can resize at run time, the controls on your form should resize and reposition properly.</span></span> <span data-ttu-id="40fba-104">若要調整大小以動態方式與所在表單的控制項，您可以使用<xref:System.Windows.Forms.Control.Anchor%2A>Windows Form 控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="40fba-104">To resize controls dynamically with the form, you can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of Windows Forms controls.</span></span> <span data-ttu-id="40fba-105"><xref:System.Windows.Forms.Control.Anchor%2A>屬性會定義控制項的錨點位置。</span><span class="sxs-lookup"><span data-stu-id="40fba-105">The <xref:System.Windows.Forms.Control.Anchor%2A> property defines an anchor position for the control.</span></span> <span data-ttu-id="40fba-106">當控制項錨定至表單和表單的大小時，控制項就會維護控制項的錨點位置之間的距離。</span><span class="sxs-lookup"><span data-stu-id="40fba-106">When a control is anchored to a form and the form is resized, the control maintains the distance between the control and the anchor positions.</span></span> <span data-ttu-id="40fba-107">例如，如果您有<xref:System.Windows.Forms.TextBox>表單會調整大小時，left、 right 和表單的下邊緣錨定的控制項<xref:System.Windows.Forms.TextBox>水平控制項調整大小，使它可以維持相同的距離，從表單的左邊和右邊側邊。</span><span class="sxs-lookup"><span data-stu-id="40fba-107">For example, if you have a <xref:System.Windows.Forms.TextBox> control that is anchored to the left, right, and bottom edges of the form, as the form is resized, the <xref:System.Windows.Forms.TextBox> control resizes horizontally so that it maintains the same distance from the right and left sides of the form.</span></span> <span data-ttu-id="40fba-108">此外，控制項本身也會做垂直定位，使其位置一律相同從表單的下邊緣的距離。</span><span class="sxs-lookup"><span data-stu-id="40fba-108">In addition, the control positions itself vertically so that its location is always the same distance from the bottom edge of the form.</span></span> <span data-ttu-id="40fba-109">如果控制項不會錨定和表單的大小時，會變更控制項相對於表單的邊緣的位置。</span><span class="sxs-lookup"><span data-stu-id="40fba-109">If a control is not anchored and the form is resized, the position of the control relative to the edges of the form is changed.</span></span>  
  
 <span data-ttu-id="40fba-110"><xref:System.Windows.Forms.Control.Anchor%2A>屬性互動<xref:System.Windows.Forms.Control.AutoSize%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="40fba-110">The <xref:System.Windows.Forms.Control.Anchor%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="40fba-111">如需詳細資訊，請參閱 < [AutoSize 屬性概觀](autosize-property-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="40fba-111">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40fba-112">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="40fba-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="40fba-113">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="40fba-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="40fba-114">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="40fba-114">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-anchor-a-control-on-a-form"></a><span data-ttu-id="40fba-115">若要錨定在表單上的控制項</span><span class="sxs-lookup"><span data-stu-id="40fba-115">To anchor a control on a form</span></span>  
  
1. <span data-ttu-id="40fba-116">選取您想要錨定的控制項。</span><span class="sxs-lookup"><span data-stu-id="40fba-116">Select the control you want to anchor.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="40fba-117">您可以藉由按下 CTRL 鍵，按一下每個控制項以選取它，然後遵循此程序的其餘同時錨定多個控制項。</span><span class="sxs-lookup"><span data-stu-id="40fba-117">You can anchor multiple controls simultaneously by pressing the CTRL key, clicking each control to select it, and then following the rest of this procedure.</span></span>  
  
2. <span data-ttu-id="40fba-118">在 [**屬性**] 視窗中，按一下右邊的箭號<xref:System.Windows.Forms.Control.Anchor%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="40fba-118">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span>  
  
     <span data-ttu-id="40fba-119">編輯器隨即出現，顯示交叉。</span><span class="sxs-lookup"><span data-stu-id="40fba-119">An editor is displayed that shows a cross.</span></span>  
  
3. <span data-ttu-id="40fba-120">若要設定錨點，按一下 上、 左、 右、 或交叉的底部區段。</span><span class="sxs-lookup"><span data-stu-id="40fba-120">To set an anchor, click the top, left, right, or bottom section of the cross.</span></span>  
  
     <span data-ttu-id="40fba-121">控制項錨定至頂端，而且留下的預設值。</span><span class="sxs-lookup"><span data-stu-id="40fba-121">Controls are anchored to the top and left by default.</span></span>  
  
4. <span data-ttu-id="40fba-122">若要清除的控制項已經錨定的側邊，按一下 跨該部門。</span><span class="sxs-lookup"><span data-stu-id="40fba-122">To clear a side of the control that has been anchored, click that arm of the cross.</span></span>  
  
5. <span data-ttu-id="40fba-123">若要關閉<xref:System.Windows.Forms.Control.Anchor%2A>屬性編輯器中，按一下 <xref:System.Windows.Forms.Control.Anchor%2A>再次屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="40fba-123">To close the <xref:System.Windows.Forms.Control.Anchor%2A> property editor, click the <xref:System.Windows.Forms.Control.Anchor%2A> property name again.</span></span>  
  
 <span data-ttu-id="40fba-124">當您的表單顯示在執行階段時，控制項調整大小以維持在相同的距離，從表單的邊緣。</span><span class="sxs-lookup"><span data-stu-id="40fba-124">When your form is displayed at run time, the control resizes to remain positioned at the same distance from the edge of the form.</span></span> <span data-ttu-id="40fba-125">錨定邊緣之間的距離永遠維持不變的距離會定義當控制項位於 Windows Form 設計工具。</span><span class="sxs-lookup"><span data-stu-id="40fba-125">The distance from the anchored edge always remains the same as the distance defined when the control is positioned in the Windows Forms Designer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40fba-126">特定控制項，例如<xref:System.Windows.Forms.ComboBox>控制項，其高度的限制。</span><span class="sxs-lookup"><span data-stu-id="40fba-126">Certain controls, such as the <xref:System.Windows.Forms.ComboBox> control, have a limit to their height.</span></span> <span data-ttu-id="40fba-127">錨定到底部的其表單或容器控制項，無法強制控制項超過其高度限制。</span><span class="sxs-lookup"><span data-stu-id="40fba-127">Anchoring the control to the bottom of its form or container cannot force the control to exceed its height limit.</span></span>  
  
 <span data-ttu-id="40fba-128">繼承的控制項必須`Protected`能夠錨定。</span><span class="sxs-lookup"><span data-stu-id="40fba-128">Inherited controls must be `Protected` to be able to be anchored.</span></span> <span data-ttu-id="40fba-129">若要變更控制項的存取層級，設定其`Modifiers`中的屬性**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="40fba-129">To change the access level of a control, set its `Modifiers` property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40fba-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40fba-130">See also</span></span>

- [<span data-ttu-id="40fba-131">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="40fba-131">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="40fba-132">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="40fba-132">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="40fba-133">AutoSize 屬性概觀</span><span class="sxs-lookup"><span data-stu-id="40fba-133">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="40fba-134">如何：停駐在 Windows Forms 上控制項</span><span class="sxs-lookup"><span data-stu-id="40fba-134">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="40fba-135">逐步解說：排列 Windows Form 使用 FlowLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="40fba-135">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="40fba-136">逐步解說：排列 Windows Form 使用 TableLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="40fba-136">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="40fba-137">逐步解說：配置 Windows Form 控制項和邊框距離、 邊界和 AutoSize 屬性</span><span class="sxs-lookup"><span data-stu-id="40fba-137">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)
