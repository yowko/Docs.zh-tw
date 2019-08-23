---
title: 作法：設定 Windows Forms 的定位順序
ms.date: 03/30/2017
f1_keywords:
- TabStop
- TabIndex
helpviewer_keywords:
- tab order [Windows Forms], controls on Windows forms
- Windows Forms controls, setting tab order
- controls [Windows Forms], setting tab order
- Windows Forms, setting tab order
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
ms.openlocfilehash: 0a6cd8b16148d28049549b241b568966239b9b01
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923606"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a><span data-ttu-id="09baf-102">HOW TO：設定 Windows Forms 的定位順序</span><span class="sxs-lookup"><span data-stu-id="09baf-102">How to: Set the Tab Order on Windows Forms</span></span>
<span data-ttu-id="09baf-103">定位順序是使用者按下 TAB 鍵將焦點從一個控制項移至另一個控制項的順序。</span><span class="sxs-lookup"><span data-stu-id="09baf-103">The tab order is the order in which a user moves focus from one control to another by pressing the TAB key.</span></span> <span data-ttu-id="09baf-104">每個表單都有自己的定位順序。</span><span class="sxs-lookup"><span data-stu-id="09baf-104">Each form has its own tab order.</span></span> <span data-ttu-id="09baf-105">根據預設, 定位順序與您建立控制項的順序相同。</span><span class="sxs-lookup"><span data-stu-id="09baf-105">By default, the tab order is the same as the order in which you created the controls.</span></span> <span data-ttu-id="09baf-106">定位字元順序編號的開頭為零。</span><span class="sxs-lookup"><span data-stu-id="09baf-106">Tab-order numbering begins with zero.</span></span>

## <a name="to-set-the-tab-order-of-a-control"></a><span data-ttu-id="09baf-107">設定控制項的定位順序</span><span class="sxs-lookup"><span data-stu-id="09baf-107">To set the tab order of a control</span></span>

1. <span data-ttu-id="09baf-108">在 [ **View** ] 功能表上, 按一下 [定位**順序]** 。</span><span class="sxs-lookup"><span data-stu-id="09baf-108">On the **View** menu, click **Tab Order**.</span></span>

     <span data-ttu-id="09baf-109">這會啟動表單上的索引標籤順序選取模式。</span><span class="sxs-lookup"><span data-stu-id="09baf-109">This activates the tab-order selection mode on the form.</span></span> <span data-ttu-id="09baf-110">數位 (代表<xref:System.Windows.Forms.Control.TabIndex%2A>屬性) 會出現在每個控制項的左上角。</span><span class="sxs-lookup"><span data-stu-id="09baf-110">A number (representing the <xref:System.Windows.Forms.Control.TabIndex%2A> property) appears in the upper-left corner of each control.</span></span>

2. <span data-ttu-id="09baf-111">依序按一下控制項, 以建立您想要的定位順序。</span><span class="sxs-lookup"><span data-stu-id="09baf-111">Click the controls sequentially to establish the tab order you want.</span></span>

    > [!NOTE]
    > <span data-ttu-id="09baf-112">控制項在定位順序內的位置可以設定為任何大於或等於0的值。</span><span class="sxs-lookup"><span data-stu-id="09baf-112">A control's place within the tab order can be set to any value greater than or equal to 0.</span></span> <span data-ttu-id="09baf-113">發生重複時, 會評估這兩個控制項的迭置順序, 並將頂端的控制項設為優先。</span><span class="sxs-lookup"><span data-stu-id="09baf-113">When duplicates occur, the z-order of the two controls is evaluated and the control on top is tabbed to first.</span></span> <span data-ttu-id="09baf-114">([迭置順序] 是表單上控制項的視覺分層, 沿著表單的 Z 軸 [深度]。</span><span class="sxs-lookup"><span data-stu-id="09baf-114">(The z-order is the visual layering of controls on a form along the form's z-axis [depth].</span></span> <span data-ttu-id="09baf-115">迭置順序會決定哪些控制項位於其他控制項前面)。如需有關迭置順序的詳細資訊, 請參閱[Windows Forms 上的分層物件](how-to-layer-objects-on-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="09baf-115">The z-order determines which controls are in front of other controls.) For more information on z-order, see [Layering Objects on Windows Forms](how-to-layer-objects-on-windows-forms.md).</span></span>

3. <span data-ttu-id="09baf-116">當您完成時, 請再次按一下 [ **View** ] 功能表上的 [定位**順序]** , 離開定位順序模式。</span><span class="sxs-lookup"><span data-stu-id="09baf-116">When you have finished, click **Tab Order** on the **View** menu again to leave tab order mode.</span></span>

    > [!NOTE]
    > <span data-ttu-id="09baf-117">無法取得焦點的控制項, 以及停用和隱藏的控制項<xref:System.Windows.Forms.Control.TabIndex%2A>都沒有屬性, 而且不會包含在定位順序中。</span><span class="sxs-lookup"><span data-stu-id="09baf-117">Controls that cannot get the focus, as well as disabled and invisible controls, do not have a <xref:System.Windows.Forms.Control.TabIndex%2A> property and are not included in the tab order.</span></span> <span data-ttu-id="09baf-118">當使用者按下 TAB 鍵時, 會略過這些控制項。</span><span class="sxs-lookup"><span data-stu-id="09baf-118">As a user presses the TAB key, these controls are skipped.</span></span>

 <span data-ttu-id="09baf-119">或者, 您可以使用<xref:System.Windows.Forms.Control.TabIndex%2A>屬性, 在屬性視窗中設定定位順序。</span><span class="sxs-lookup"><span data-stu-id="09baf-119">Alternatively, tab order can be set in the Properties window using the <xref:System.Windows.Forms.Control.TabIndex%2A> property.</span></span> <span data-ttu-id="09baf-120">控制項<xref:System.Windows.Forms.Control.TabIndex%2A>的屬性會決定它在定位順序中的位置。</span><span class="sxs-lookup"><span data-stu-id="09baf-120">The <xref:System.Windows.Forms.Control.TabIndex%2A> property of a control determines where it is positioned in the tab order.</span></span> <span data-ttu-id="09baf-121">根據預設, 第一個繪製<xref:System.Windows.Forms.Control.TabIndex%2A>的控制項的值為 0, 第二個<xref:System.Windows.Forms.Control.TabIndex%2A>則為 1, 依此類推。</span><span class="sxs-lookup"><span data-stu-id="09baf-121">By default, the first control drawn has a <xref:System.Windows.Forms.Control.TabIndex%2A> value of 0, the second has a <xref:System.Windows.Forms.Control.TabIndex%2A> of 1, and so on.</span></span>

 <span data-ttu-id="09baf-122">此外, 根據預設, <xref:System.Windows.Forms.GroupBox>控制項有自己<xref:System.Windows.Forms.Control.TabIndex%2A>的值, 也就是整數。</span><span class="sxs-lookup"><span data-stu-id="09baf-122">Additionally, by default, a <xref:System.Windows.Forms.GroupBox> control has its own <xref:System.Windows.Forms.Control.TabIndex%2A> value, which is a whole number.</span></span> <span data-ttu-id="09baf-123"><xref:System.Windows.Forms.GroupBox>控制項本身在執行時間不能有焦點。</span><span class="sxs-lookup"><span data-stu-id="09baf-123">A <xref:System.Windows.Forms.GroupBox> control itself cannot have focus at run time.</span></span> <span data-ttu-id="09baf-124">因此, 中的<xref:System.Windows.Forms.GroupBox>每個控制項都有自己的十進位<xref:System.Windows.Forms.Control.TabIndex%2A>值, 從. 0 開始。</span><span class="sxs-lookup"><span data-stu-id="09baf-124">Thus, each control within a <xref:System.Windows.Forms.GroupBox> has its own decimal <xref:System.Windows.Forms.Control.TabIndex%2A> value, beginning with .0.</span></span> <span data-ttu-id="09baf-125">自然地, 隨著<xref:System.Windows.Forms.Control.TabIndex%2A> <xref:System.Windows.Forms.GroupBox>控制項的遞增, 其內的控制項也會遞增。</span><span class="sxs-lookup"><span data-stu-id="09baf-125">Naturally, as the <xref:System.Windows.Forms.Control.TabIndex%2A> of a <xref:System.Windows.Forms.GroupBox> control is incremented, the controls within it will be incremented accordingly.</span></span> <span data-ttu-id="09baf-126">如果您將<xref:System.Windows.Forms.Control.TabIndex%2A>值從5變更為 6 <xref:System.Windows.Forms.Control.TabIndex%2A> , 則其群組中第一個控制項的值會自動變更為 6.0, 依此類推。</span><span class="sxs-lookup"><span data-stu-id="09baf-126">If you changed a <xref:System.Windows.Forms.Control.TabIndex%2A> value from 5 to 6, the <xref:System.Windows.Forms.Control.TabIndex%2A> value of the first control in its group automatically changes to 6.0, and so on.</span></span>

 <span data-ttu-id="09baf-127">最後, 您可以在定位順序中略過許多表單上的任何控制項。</span><span class="sxs-lookup"><span data-stu-id="09baf-127">Finally, any control of the many on your form can be skipped in the tab order.</span></span> <span data-ttu-id="09baf-128">通常, 在執行時間連續按 TAB 鍵, 會選取定位順序中的每個控制項。</span><span class="sxs-lookup"><span data-stu-id="09baf-128">Usually, pressing TAB successively at run time selects each control in the tab order.</span></span> <span data-ttu-id="09baf-129">藉由關閉屬性, 您可以讓控制項在表單的定位順序中傳遞。 <xref:System.Windows.Forms.Control.TabStop%2A></span><span class="sxs-lookup"><span data-stu-id="09baf-129">By turning off the <xref:System.Windows.Forms.Control.TabStop%2A> property, you can make a control be passed over in the tab order of the form.</span></span>

## <a name="to-remove-a-control-from-the-tab-order"></a><span data-ttu-id="09baf-130">若要從定位順序中移除控制項</span><span class="sxs-lookup"><span data-stu-id="09baf-130">To remove a control from the tab order</span></span>

1. <span data-ttu-id="09baf-131">在屬性視窗中, <xref:System.Windows.Forms.Control.TabStop%2A>將控制項`false`的屬性設定為。</span><span class="sxs-lookup"><span data-stu-id="09baf-131">Set the control's <xref:System.Windows.Forms.Control.TabStop%2A> property to `false` in the Properties window.</span></span>

     <span data-ttu-id="09baf-132">其<xref:System.Windows.Forms.Control.TabStop%2A>屬性已設定為`false`的控制項, 仍然會在定位順序中維持其位置, 即使在使用 tab 鍵迴圈流覽控制項時略過控制項也一樣。</span><span class="sxs-lookup"><span data-stu-id="09baf-132">A control whose <xref:System.Windows.Forms.Control.TabStop%2A> property has been set to `false` still maintains its position in the tab order, even though the control is skipped when you cycle through the controls with the TAB key.</span></span>

    > [!NOTE]
    > <span data-ttu-id="09baf-133">選項按鈕群組在執行時間會有一個定位停駐點。</span><span class="sxs-lookup"><span data-stu-id="09baf-133">A radio button group has a single tab stop at run time.</span></span> <span data-ttu-id="09baf-134">選取的按鈕 (也就<xref:System.Windows.Forms.RadioButton.Checked%2A>是其屬性設為`true`的按鈕) 會自動將<xref:System.Windows.Forms.Control.TabStop%2A>其屬性設<xref:System.Windows.Forms.Control.TabStop%2A>為`true`, 而其他按鈕的屬性會設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="09baf-134">The selected button (that is, the button with its <xref:System.Windows.Forms.RadioButton.Checked%2A> property set to `true`) has its <xref:System.Windows.Forms.Control.TabStop%2A> property automatically set to `true`, while the other buttons have their <xref:System.Windows.Forms.Control.TabStop%2A> property set to `false`.</span></span> <span data-ttu-id="09baf-135">如需群組<xref:System.Windows.Forms.RadioButton>控制項的詳細資訊, 請參閱[群組 Windows Forms 選項按鈕控制項以作為集合](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)。</span><span class="sxs-lookup"><span data-stu-id="09baf-135">For more information about grouping <xref:System.Windows.Forms.RadioButton> controls, see [Grouping Windows Forms RadioButton Controls to Function as a Set](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="09baf-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09baf-136">See also</span></span>

- [<span data-ttu-id="09baf-137">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="09baf-137">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="09baf-138">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="09baf-138">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="09baf-139">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="09baf-139">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="09baf-140">依功能區分 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="09baf-140">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
