---
title: 錨點控制項
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c307d8c5b3bc32e15e6de048c434854ef1bbc65
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747190"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a><span data-ttu-id="9ae72-102">如何：錨定 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="9ae72-102">How to: Anchor controls on Windows Forms</span></span>

<span data-ttu-id="9ae72-103">如果您要設計一個表單，讓使用者可以在執行時間調整其大小，您的表單上的控制項應該會調整大小並正確重新置放。</span><span class="sxs-lookup"><span data-stu-id="9ae72-103">If you're designing a form that the user can resize at run time, the controls on your form should resize and reposition properly.</span></span> <span data-ttu-id="9ae72-104">若要使用表單動態調整控制項大小，您可以使用 Windows Forms 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="9ae72-104">To resize controls dynamically with the form, you can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of Windows Forms controls.</span></span> <span data-ttu-id="9ae72-105"><xref:System.Windows.Forms.Control.Anchor%2A> 屬性會定義控制項的錨點位置。</span><span class="sxs-lookup"><span data-stu-id="9ae72-105">The <xref:System.Windows.Forms.Control.Anchor%2A> property defines an anchor position for the control.</span></span> <span data-ttu-id="9ae72-106">當控制項錨定至表單，且表單已調整大小時，控制項會維持控制項與錨點位置之間的距離。</span><span class="sxs-lookup"><span data-stu-id="9ae72-106">When a control is anchored to a form and the form is resized, the control maintains the distance between the control and the anchor positions.</span></span> <span data-ttu-id="9ae72-107">例如，如果您的 <xref:System.Windows.Forms.TextBox> 控制項已錨定至表單的左、右和下邊緣，則當表單調整大小時，<xref:System.Windows.Forms.TextBox> 控制項會水準調整大小，使其維持與表單右邊和左側相同的距離。</span><span class="sxs-lookup"><span data-stu-id="9ae72-107">For example, if you have a <xref:System.Windows.Forms.TextBox> control that is anchored to the left, right, and bottom edges of the form, as the form is resized, the <xref:System.Windows.Forms.TextBox> control resizes horizontally so that it maintains the same distance from the right and left sides of the form.</span></span> <span data-ttu-id="9ae72-108">此外，控制項的位置會垂直，使其位置一律與表單下邊緣的距離相同。</span><span class="sxs-lookup"><span data-stu-id="9ae72-108">In addition, the control positions itself vertically so that its location is always the same distance from the bottom edge of the form.</span></span> <span data-ttu-id="9ae72-109">如果控制項未錨定，而表單已調整大小，則控制項相對於表單邊緣的位置會變更。</span><span class="sxs-lookup"><span data-stu-id="9ae72-109">If a control is not anchored and the form is resized, the position of the control relative to the edges of the form is changed.</span></span>

<span data-ttu-id="9ae72-110"><xref:System.Windows.Forms.Control.Anchor%2A> 屬性會與 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性互動。</span><span class="sxs-lookup"><span data-stu-id="9ae72-110">The <xref:System.Windows.Forms.Control.Anchor%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="9ae72-111">如需詳細資訊，請參閱[AutoSize 屬性總覽](autosize-property-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9ae72-111">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>

## <a name="anchor-a-control-on-a-form"></a><span data-ttu-id="9ae72-112">錨定表單上的控制項</span><span class="sxs-lookup"><span data-stu-id="9ae72-112">Anchor a control on a form</span></span>

1. <span data-ttu-id="9ae72-113">在 Visual Studio 中，選取您要錨定的控制項。</span><span class="sxs-lookup"><span data-stu-id="9ae72-113">In Visual Studio, select the control you want to anchor.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9ae72-114">您可以按下 CTRL 鍵，按一下每個控制項來選取它，然後遵循此程式的其餘部分，以同時錨定多個控制項。</span><span class="sxs-lookup"><span data-stu-id="9ae72-114">You can anchor multiple controls simultaneously by pressing the CTRL key, clicking each control to select it, and then following the rest of this procedure.</span></span>

2. <span data-ttu-id="9ae72-115">在 [**屬性**] 視窗中，按一下 [<xref:System.Windows.Forms.Control.Anchor%2A>] 屬性右邊的箭號。</span><span class="sxs-lookup"><span data-stu-id="9ae72-115">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span>

     <span data-ttu-id="9ae72-116">隨即顯示一個顯示交叉的編輯器。</span><span class="sxs-lookup"><span data-stu-id="9ae72-116">An editor is displayed that shows a cross.</span></span>

3. <span data-ttu-id="9ae72-117">若要設定錨點，請按一下交叉的頂端、左側、右側或底部區段。</span><span class="sxs-lookup"><span data-stu-id="9ae72-117">To set an anchor, click the top, left, right, or bottom section of the cross.</span></span>

     <span data-ttu-id="9ae72-118">控制項預設會錨定到頂端和左側。</span><span class="sxs-lookup"><span data-stu-id="9ae72-118">Controls are anchored to the top and left by default.</span></span>

4. <span data-ttu-id="9ae72-119">若要清除已錨定之控制項的側邊，請按一下 [交叉] 的 arm。</span><span class="sxs-lookup"><span data-stu-id="9ae72-119">To clear a side of the control that has been anchored, click that arm of the cross.</span></span>

5. <span data-ttu-id="9ae72-120">若要關閉 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性編輯器，請再次按一下 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="9ae72-120">To close the <xref:System.Windows.Forms.Control.Anchor%2A> property editor, click the <xref:System.Windows.Forms.Control.Anchor%2A> property name again.</span></span>

<span data-ttu-id="9ae72-121">當您的表單在執行時間顯示時，控制項會調整大小以維持與表單邊緣相同的距離。</span><span class="sxs-lookup"><span data-stu-id="9ae72-121">When your form is displayed at run time, the control resizes to remain positioned at the same distance from the edge of the form.</span></span> <span data-ttu-id="9ae72-122">距錨定邊緣的距離一律會與控制項位於 Windows Form 設計工具中時所定義的距離保持相同。</span><span class="sxs-lookup"><span data-stu-id="9ae72-122">The distance from the anchored edge always remains the same as the distance defined when the control is positioned in the Windows Forms Designer.</span></span>

> [!NOTE]
> <span data-ttu-id="9ae72-123">某些控制項（例如 <xref:System.Windows.Forms.ComboBox> 控制項）具有其高度的限制。</span><span class="sxs-lookup"><span data-stu-id="9ae72-123">Certain controls, such as the <xref:System.Windows.Forms.ComboBox> control, have a limit to their height.</span></span> <span data-ttu-id="9ae72-124">將控制項錨定到其表單或容器的底部，無法強制控制項超過其高度限制。</span><span class="sxs-lookup"><span data-stu-id="9ae72-124">Anchoring the control to the bottom of its form or container cannot force the control to exceed its height limit.</span></span>

<span data-ttu-id="9ae72-125">繼承的控制項必須 `Protected` 才能夠錨定。</span><span class="sxs-lookup"><span data-stu-id="9ae72-125">Inherited controls must be `Protected` to be able to be anchored.</span></span> <span data-ttu-id="9ae72-126">若要變更控制項的存取層級，請在 [**屬性**] 視窗中設定其 [`Modifiers`] 屬性。</span><span class="sxs-lookup"><span data-stu-id="9ae72-126">To change the access level of a control, set its `Modifiers` property in the **Properties** window.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ae72-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="9ae72-127">See also</span></span>

- [<span data-ttu-id="9ae72-128">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="9ae72-128">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="9ae72-129">AutoSize 屬性概觀</span><span class="sxs-lookup"><span data-stu-id="9ae72-129">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="9ae72-130">如何：將控制項停駐在 Windows Forms 上</span><span class="sxs-lookup"><span data-stu-id="9ae72-130">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="9ae72-131">逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項</span><span class="sxs-lookup"><span data-stu-id="9ae72-131">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="9ae72-132">逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="9ae72-132">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="9ae72-133">逐步解說：使用邊框距離、邊界和 AutoSize 屬性配置 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="9ae72-133">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)
