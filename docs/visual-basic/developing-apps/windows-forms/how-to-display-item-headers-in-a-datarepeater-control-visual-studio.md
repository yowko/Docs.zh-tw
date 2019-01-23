---
title: HOW TO：DataRepeater 控制項 (Visual Studio) 中顯示項目標題
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, item headers
- DataRepeater, selection indicators
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
ms.openlocfilehash: eccac1b3b02da41a34d47072be267f6c51a7d490
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504557"
---
# <a name="how-to-display-item-headers-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="b9cd7-102">HOW TO：DataRepeater 控制項 (Visual Studio) 中顯示項目標題</span><span class="sxs-lookup"><span data-stu-id="b9cd7-102">How to: Display Item Headers in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="b9cd7-103">中的項目標題<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項提供視覺指標，當<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>已選取。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-103">The item header in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control provides a visual indicator when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> is selected.</span></span> <span data-ttu-id="b9cd7-104">當<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>屬性設定為<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical>（預設值），顯示項目標題左邊的每個項目。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-104">When the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> (the default), the item header is displayed to the left of each item.</span></span> <span data-ttu-id="b9cd7-105">當<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>屬性設定為<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>，項目標頭會顯示在每個項目頂端。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-105">When the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>, the item header is displayed at the top of each item.</span></span>  
  
 <span data-ttu-id="b9cd7-106">第一次選取時，所指定的色彩顯示項目標題<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>屬性，而白色箭頭圖示會顯示。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-106">When it is first selected, the item header is displayed in the color that is specified by the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> property, and a white arrow icon is displayed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9cd7-107">如果您設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>至<xref:System.Drawing.Color.White%2A>，選取項目符號將不會顯示當第一次選取的項目。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-107">If you set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> to <xref:System.Drawing.Color.White%2A>, the selection symbol will not be visible when the item is first selected.</span></span>  
  
 <span data-ttu-id="b9cd7-108">中的欄位<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>具有焦點的項目標頭變更色彩<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>背景色彩和箭號圖示隨即變更為黑色。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-108">When a field in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> has focus, the color of the item header changes to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> background color and the arrow icon changes to black.</span></span> <span data-ttu-id="b9cd7-109">如果資料已經變更，鉛筆符號會顯示在項目標題中。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-109">If data is changed, a pencil symbol is displayed in the item header.</span></span>  
  
 <span data-ttu-id="b9cd7-110">預設寬度 (或高度時<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>屬性設定為<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>) 項目的標頭是 15 像素為單位。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-110">The default width (or height when the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>) of the item header is 15 pixels.</span></span> <span data-ttu-id="b9cd7-111">您也可以設定來變更 「 寬度<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-111">You can change the width by setting the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9cd7-112">如果<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>屬性設為小於 11 的值，將不會顯示項目標題中的標記符號。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-112">If the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property is set to a value that is less than 11, the indicator symbols in the item header will not be displayed.</span></span>  
  
 <span data-ttu-id="b9cd7-113">您可以藉由設定隱藏項目標題<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>屬性，以**False**。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-113">You can hide the item headers by setting the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> property to **False**.</span></span> <span data-ttu-id="b9cd7-114">當<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>設為**假**，項目已選取的唯一徵兆為點線周圍<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-114">When <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> is set to **False**, the only indication that an item is selected is a dotted line around the perimeter of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9cd7-115">您也可以藉由監視提供您自己的選取範圍指標<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>的屬性<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>中<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件的<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-115">You can also provide your own selection indicator by monitoring the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> property of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="b9cd7-116">如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-116">For more information, see <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.</span></span>  
  
### <a name="to-change-the-appearance-of-item-headers"></a><span data-ttu-id="b9cd7-117">若要變更項目標題的外觀</span><span class="sxs-lookup"><span data-stu-id="b9cd7-117">To change the appearance of item headers</span></span>  
  
1.  <span data-ttu-id="b9cd7-118">在 Windows Form 設計工具中，選取 下方區域的<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-118">In the Windows Forms Designer, select the lower region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b9cd7-119">您必須選取控制項的下方的區域。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-119">You must select the lower region of the control.</span></span> <span data-ttu-id="b9cd7-120">如果您選取 [項目範本] 區段中，一組不同的屬性會出現在 [屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-120">If you select the item template section, a different set of properties will appear in the Properties window.</span></span>  
  
2.  <span data-ttu-id="b9cd7-121">在 [屬性] 視窗中，使用<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>屬性來變更項目標題的色彩。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-121">In the Properties window, use the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> property to change the color of the item headers.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b9cd7-122">如果您設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>至<xref:System.Drawing.Color.White%2A>，選取項目符號將不會顯示當第一次選取的項目。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-122">If you set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> to <xref:System.Drawing.Color.White%2A>, the selection symbol will not be visible when the item is first selected.</span></span>  
  
3.  <span data-ttu-id="b9cd7-123">使用<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>屬性來變更項目標題的寬度 （或高度）。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-123">Use the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property to change the width (or height) of the item headers.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b9cd7-124">如果<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>屬性設為小於 11 的值，將不會顯示項目標題中的標記符號。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-124">If the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property is set to a value that is less than 11, the indicator symbols in the item header will not be displayed.</span></span>  
  
### <a name="to-hide-item-headers"></a><span data-ttu-id="b9cd7-125">若要隱藏項目標題</span><span class="sxs-lookup"><span data-stu-id="b9cd7-125">To hide item headers</span></span>  
  
1.  <span data-ttu-id="b9cd7-126">在 Windows Form 設計工具中，選取 下方區域的<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-126">In the Windows Forms Designer, select the lower region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b9cd7-127">您必須選取控制項的下方的區域。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-127">You must select the lower region of the control.</span></span> <span data-ttu-id="b9cd7-128">如果您選取 [項目範本] 區段中，一組不同的屬性會出現在 [屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-128">If you select the item template section, a different set of properties will appear in the Properties window.</span></span>  
  
2.  <span data-ttu-id="b9cd7-129">在 [屬性] 視窗中，設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>屬性，以**False**。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-129">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> property to **False**.</span></span>  
  
     <span data-ttu-id="b9cd7-130">中的項目<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>已選取，唯一的指示將會點線周圍<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>。</span><span class="sxs-lookup"><span data-stu-id="b9cd7-130">When an item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> is selected, the only indication will be a dotted line around the perimeter of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9cd7-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9cd7-131">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [<span data-ttu-id="b9cd7-132">DataRepeater 控制項簡介</span><span class="sxs-lookup"><span data-stu-id="b9cd7-132">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="b9cd7-133">如何：變更 DataRepeater 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="b9cd7-133">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="b9cd7-134">如何：變更 DataRepeater 控制項的版面配置</span><span class="sxs-lookup"><span data-stu-id="b9cd7-134">How to: Change the Layout of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="b9cd7-135"> DataRepeater 控制項進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="b9cd7-135">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
