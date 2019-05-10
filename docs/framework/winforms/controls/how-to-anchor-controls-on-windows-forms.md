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
ms.openlocfilehash: b48761bda2baad4f7d1e6db9b41d73d6d54bc081
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211281"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a><span data-ttu-id="789eb-102">HOW TO：錨定 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="789eb-102">How to: Anchor Controls on Windows Forms</span></span>

<span data-ttu-id="789eb-103">如果您正在設計的表單，使用者可以在執行階段調整大小，您的表單上的控制項應該調整大小，並正確重新定位。</span><span class="sxs-lookup"><span data-stu-id="789eb-103">If you're designing a form that the user can resize at run time, the controls on your form should resize and reposition properly.</span></span> <span data-ttu-id="789eb-104">若要調整大小以動態方式與所在表單的控制項，您可以使用<xref:System.Windows.Forms.Control.Anchor%2A>Windows Form 控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="789eb-104">To resize controls dynamically with the form, you can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of Windows Forms controls.</span></span> <span data-ttu-id="789eb-105"><xref:System.Windows.Forms.Control.Anchor%2A>屬性會定義控制項的錨點位置。</span><span class="sxs-lookup"><span data-stu-id="789eb-105">The <xref:System.Windows.Forms.Control.Anchor%2A> property defines an anchor position for the control.</span></span> <span data-ttu-id="789eb-106">當控制項錨定至表單和表單的大小時，控制項就會維護控制項的錨點位置之間的距離。</span><span class="sxs-lookup"><span data-stu-id="789eb-106">When a control is anchored to a form and the form is resized, the control maintains the distance between the control and the anchor positions.</span></span> <span data-ttu-id="789eb-107">例如，如果您有<xref:System.Windows.Forms.TextBox>表單會調整大小時，left、 right 和表單的下邊緣錨定的控制項<xref:System.Windows.Forms.TextBox>水平控制項調整大小，使它可以維持相同的距離，從表單的左邊和右邊側邊。</span><span class="sxs-lookup"><span data-stu-id="789eb-107">For example, if you have a <xref:System.Windows.Forms.TextBox> control that is anchored to the left, right, and bottom edges of the form, as the form is resized, the <xref:System.Windows.Forms.TextBox> control resizes horizontally so that it maintains the same distance from the right and left sides of the form.</span></span> <span data-ttu-id="789eb-108">此外，控制項本身也會做垂直定位，使其位置一律相同從表單的下邊緣的距離。</span><span class="sxs-lookup"><span data-stu-id="789eb-108">In addition, the control positions itself vertically so that its location is always the same distance from the bottom edge of the form.</span></span> <span data-ttu-id="789eb-109">如果控制項不會錨定和表單的大小時，會變更控制項相對於表單的邊緣的位置。</span><span class="sxs-lookup"><span data-stu-id="789eb-109">If a control is not anchored and the form is resized, the position of the control relative to the edges of the form is changed.</span></span>

<span data-ttu-id="789eb-110"><xref:System.Windows.Forms.Control.Anchor%2A>屬性互動<xref:System.Windows.Forms.Control.AutoSize%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="789eb-110">The <xref:System.Windows.Forms.Control.Anchor%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="789eb-111">如需詳細資訊，請參閱 < [AutoSize 屬性概觀](autosize-property-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="789eb-111">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>

## <a name="anchor-a-control-on-a-form"></a><span data-ttu-id="789eb-112">在表單上的將控制項錨定</span><span class="sxs-lookup"><span data-stu-id="789eb-112">Anchor a control on a form</span></span>

1. <span data-ttu-id="789eb-113">在 Visual Studio 中，選取您想要錨定的控制項。</span><span class="sxs-lookup"><span data-stu-id="789eb-113">In Visual Studio, select the control you want to anchor.</span></span>

    > [!NOTE]
    > <span data-ttu-id="789eb-114">您可以藉由按下 CTRL 鍵，按一下每個控制項以選取它，然後遵循此程序的其餘同時錨定多個控制項。</span><span class="sxs-lookup"><span data-stu-id="789eb-114">You can anchor multiple controls simultaneously by pressing the CTRL key, clicking each control to select it, and then following the rest of this procedure.</span></span>

2. <span data-ttu-id="789eb-115">在 [**屬性**] 視窗中，按一下右邊的箭號<xref:System.Windows.Forms.Control.Anchor%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="789eb-115">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span>

     <span data-ttu-id="789eb-116">編輯器隨即出現，顯示交叉。</span><span class="sxs-lookup"><span data-stu-id="789eb-116">An editor is displayed that shows a cross.</span></span>

3. <span data-ttu-id="789eb-117">若要設定錨點，按一下 上、 左、 右、 或交叉的底部區段。</span><span class="sxs-lookup"><span data-stu-id="789eb-117">To set an anchor, click the top, left, right, or bottom section of the cross.</span></span>

     <span data-ttu-id="789eb-118">控制項錨定至頂端，而且留下的預設值。</span><span class="sxs-lookup"><span data-stu-id="789eb-118">Controls are anchored to the top and left by default.</span></span>

4. <span data-ttu-id="789eb-119">若要清除的控制項已經錨定的側邊，按一下 跨該部門。</span><span class="sxs-lookup"><span data-stu-id="789eb-119">To clear a side of the control that has been anchored, click that arm of the cross.</span></span>

5. <span data-ttu-id="789eb-120">若要關閉<xref:System.Windows.Forms.Control.Anchor%2A>屬性編輯器中，按一下 <xref:System.Windows.Forms.Control.Anchor%2A>再次屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="789eb-120">To close the <xref:System.Windows.Forms.Control.Anchor%2A> property editor, click the <xref:System.Windows.Forms.Control.Anchor%2A> property name again.</span></span>

<span data-ttu-id="789eb-121">當您的表單顯示在執行階段時，控制項調整大小以維持在相同的距離，從表單的邊緣。</span><span class="sxs-lookup"><span data-stu-id="789eb-121">When your form is displayed at run time, the control resizes to remain positioned at the same distance from the edge of the form.</span></span> <span data-ttu-id="789eb-122">錨定邊緣之間的距離永遠維持不變的距離會定義當控制項位於 Windows Form 設計工具。</span><span class="sxs-lookup"><span data-stu-id="789eb-122">The distance from the anchored edge always remains the same as the distance defined when the control is positioned in the Windows Forms Designer.</span></span>

> [!NOTE]
> <span data-ttu-id="789eb-123">特定控制項，例如<xref:System.Windows.Forms.ComboBox>控制項，其高度的限制。</span><span class="sxs-lookup"><span data-stu-id="789eb-123">Certain controls, such as the <xref:System.Windows.Forms.ComboBox> control, have a limit to their height.</span></span> <span data-ttu-id="789eb-124">錨定到底部的其表單或容器控制項，無法強制控制項超過其高度限制。</span><span class="sxs-lookup"><span data-stu-id="789eb-124">Anchoring the control to the bottom of its form or container cannot force the control to exceed its height limit.</span></span>

<span data-ttu-id="789eb-125">繼承的控制項必須`Protected`能夠錨定。</span><span class="sxs-lookup"><span data-stu-id="789eb-125">Inherited controls must be `Protected` to be able to be anchored.</span></span> <span data-ttu-id="789eb-126">若要變更控制項的存取層級，設定其`Modifiers`中的屬性**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="789eb-126">To change the access level of a control, set its `Modifiers` property in the **Properties** window.</span></span>

## <a name="see-also"></a><span data-ttu-id="789eb-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="789eb-127">See also</span></span>

- [<span data-ttu-id="789eb-128">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="789eb-128">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="789eb-129">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="789eb-129">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="789eb-130">AutoSize 屬性概觀</span><span class="sxs-lookup"><span data-stu-id="789eb-130">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="789eb-131">如何：停駐在 Windows Forms 上控制項</span><span class="sxs-lookup"><span data-stu-id="789eb-131">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="789eb-132">逐步解說：排列 Windows Form 使用 FlowLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="789eb-132">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="789eb-133">逐步解說：排列 Windows Form 使用 TableLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="789eb-133">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="789eb-134">逐步解說：配置 Windows Form 控制項和邊框距離、 邊界和 AutoSize 屬性</span><span class="sxs-lookup"><span data-stu-id="789eb-134">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)
