---
title: "如何：錨定 Windows Form 上的控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fcc672dea63bc74980b4829129f530de9cc72ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-anchor-controls-on-windows-forms"></a><span data-ttu-id="7ee2b-102">如何：錨定 Windows Form 上的控制項</span><span class="sxs-lookup"><span data-stu-id="7ee2b-102">How to: Anchor Controls on Windows Forms</span></span>
<span data-ttu-id="7ee2b-103">如果您要設計的表單，使用者可以在執行階段調整大小，將表單上的控制項應調整大小，並適當地重新調整位置。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-103">If you are designing a form that the user can resize at run time, the controls on your form should resize and reposition properly.</span></span> <span data-ttu-id="7ee2b-104">若要調整大小以動態方式使用表單的控制項，您可以使用<xref:System.Windows.Forms.Control.Anchor%2A>Windows Form 控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-104">To resize controls dynamically with the form, you can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of Windows Forms controls.</span></span> <span data-ttu-id="7ee2b-105"><xref:System.Windows.Forms.Control.Anchor%2A>屬性會定義控制項的錨點位置。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-105">The <xref:System.Windows.Forms.Control.Anchor%2A> property defines an anchor position for the control.</span></span> <span data-ttu-id="7ee2b-106">當控制項錨定至表單，並調整表單大小時，控制項就會維護控制項的錨點位置之間的距離。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-106">When a control is anchored to a form and the form is resized, the control maintains the distance between the control and the anchor positions.</span></span> <span data-ttu-id="7ee2b-107">例如，如果您有<xref:System.Windows.Forms.TextBox>錨定的左方、 右方和下邊緣的表單，表單調整大小時，控制項<xref:System.Windows.Forms.TextBox>水平控制項會調整大小，以便保持相同的距離，從表單的左邊和右邊側邊。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-107">For example, if you have a <xref:System.Windows.Forms.TextBox> control that is anchored to the left, right, and bottom edges of the form, as the form is resized, the <xref:System.Windows.Forms.TextBox> control resizes horizontally so that it maintains the same distance from the right and left sides of the form.</span></span> <span data-ttu-id="7ee2b-108">此外，控制項本身也會做垂直定位，因此其位置一律會從表單的邊緣相同的距離。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-108">In addition, the control positions itself vertically so that its location is always the same distance from the bottom edge of the form.</span></span> <span data-ttu-id="7ee2b-109">如果控制項不錨定和調整表單大小時，會變更控制項相對於表單的邊緣的位置。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-109">If a control is not anchored and the form is resized, the position of the control relative to the edges of the form is changed.</span></span>  
  
 <span data-ttu-id="7ee2b-110"><xref:System.Windows.Forms.Control.Anchor%2A>屬性互動<xref:System.Windows.Forms.Control.AutoSize%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-110">The <xref:System.Windows.Forms.Control.Anchor%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="7ee2b-111">如需詳細資訊，請參閱[AutoSize 屬性概觀](../../../../docs/framework/winforms/controls/autosize-property-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-111">For more information, see [AutoSize Property Overview](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ee2b-112">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7ee2b-113">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7ee2b-114">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="7ee2b-114">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-anchor-a-control-on-a-form"></a><span data-ttu-id="7ee2b-115">若要錨定在表單上的控制項</span><span class="sxs-lookup"><span data-stu-id="7ee2b-115">To anchor a control on a form</span></span>  
  
1.  <span data-ttu-id="7ee2b-116">選取您想要錨定的控制項。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-116">Select the control you want to anchor.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7ee2b-117">您可以按住 CTRL 鍵，按一下以選取它，每個控制項，然後遵循此程序的其餘同時錨定多個控制項。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-117">You can anchor multiple controls simultaneously by pressing the CTRL key, clicking each control to select it, and then following the rest of this procedure.</span></span>  
  
2.  <span data-ttu-id="7ee2b-118">在**屬性**視窗中，按一下右邊的箭號<xref:System.Windows.Forms.Control.Anchor%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-118">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span>  
  
     <span data-ttu-id="7ee2b-119">編輯器會隨即出現，顯示交叉。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-119">An editor is displayed that shows a cross.</span></span>  
  
3.  <span data-ttu-id="7ee2b-120">設定錨點，請按一下左上方、 右側或底端交叉區段。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-120">To set an anchor, click the top, left, right, or bottom section of the cross.</span></span>  
  
     <span data-ttu-id="7ee2b-121">控制項可錨定至頂端，而且留下的預設值。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-121">Controls are anchored to the top and left by default.</span></span>  
  
4.  <span data-ttu-id="7ee2b-122">若要清除已錨定的控制項的一邊，請按一下該 arm 的交叉。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-122">To clear a side of the control that has been anchored, click that arm of the cross.</span></span>  
  
5.  <span data-ttu-id="7ee2b-123">若要關閉<xref:System.Windows.Forms.Control.Anchor%2A>屬性編輯器中，按一下<xref:System.Windows.Forms.Control.Anchor%2A>再次屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-123">To close the <xref:System.Windows.Forms.Control.Anchor%2A> property editor, click the <xref:System.Windows.Forms.Control.Anchor%2A> property name again.</span></span>  
  
 <span data-ttu-id="7ee2b-124">當表單出現在執行階段時，控制項會調整大小以便維持在相同的距離，從表單的邊緣。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-124">When your form is displayed at run time, the control resizes to remain positioned at the same distance from the edge of the form.</span></span> <span data-ttu-id="7ee2b-125">錨定的邊緣之間的距離一定會保持相同的距離會定義當控制項放置在 Windows Form 設計工具。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-125">The distance from the anchored edge always remains the same as the distance defined when the control is positioned in the Windows Forms Designer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ee2b-126">特定控制項，例如<xref:System.Windows.Forms.ComboBox>控制項，其高度限制。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-126">Certain controls, such as the <xref:System.Windows.Forms.ComboBox> control, have a limit to their height.</span></span> <span data-ttu-id="7ee2b-127">錨定至底部其表單或容器控制項無法強制控制項超過其高度限制。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-127">Anchoring the control to the bottom of its form or container cannot force the control to exceed its height limit.</span></span>  
  
 <span data-ttu-id="7ee2b-128">繼承的控制項必須是`Protected`能夠錨定。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-128">Inherited controls must be `Protected` to be able to be anchored.</span></span> <span data-ttu-id="7ee2b-129">若要變更控制項的存取層級，設定其`Modifiers`屬性**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="7ee2b-129">To change the access level of a control, set its `Modifiers` property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ee2b-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="7ee2b-130">See Also</span></span>  
 [<span data-ttu-id="7ee2b-131">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="7ee2b-131">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="7ee2b-132">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="7ee2b-132">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="7ee2b-133">AutoSize 屬性概觀</span><span class="sxs-lookup"><span data-stu-id="7ee2b-133">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [<span data-ttu-id="7ee2b-134">操作說明：將控制項停駐在 Windows Forms 上</span><span class="sxs-lookup"><span data-stu-id="7ee2b-134">How to: Dock Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [<span data-ttu-id="7ee2b-135">逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項</span><span class="sxs-lookup"><span data-stu-id="7ee2b-135">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="7ee2b-136">逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="7ee2b-136">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="7ee2b-137">逐步解說：使用邊框距離、邊界和 AutoSize 屬性配置 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="7ee2b-137">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
