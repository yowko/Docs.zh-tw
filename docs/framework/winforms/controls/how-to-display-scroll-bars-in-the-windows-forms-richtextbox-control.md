---
title: "如何：在 Windows Form RichTextBox 控制項中顯示捲軸"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4645e502544072cbc6268ae07e054ea5450d9c5c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a><span data-ttu-id="071b0-102">如何：在 Windows Form RichTextBox 控制項中顯示捲軸</span><span class="sxs-lookup"><span data-stu-id="071b0-102">How to: Display Scroll Bars in the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="071b0-103">根據預設，Windows Form<xref:System.Windows.Forms.RichTextBox>控制項顯示成必要的水平和垂直捲軸。</span><span class="sxs-lookup"><span data-stu-id="071b0-103">By default, the Windows Forms <xref:System.Windows.Forms.RichTextBox> control displays horizontal and vertical scroll bars as necessary.</span></span> <span data-ttu-id="071b0-104">有七個可能的值為<xref:System.Windows.Forms.RichTextBox.ScrollBars%2A>屬性<xref:System.Windows.Forms.RichTextBox>控制項，如下表所述。</span><span class="sxs-lookup"><span data-stu-id="071b0-104">There are seven possible values for the <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> property of the <xref:System.Windows.Forms.RichTextBox> control, which are described in the table below.</span></span>  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a><span data-ttu-id="071b0-105">在 RichTextBox 控制項中顯示捲軸</span><span class="sxs-lookup"><span data-stu-id="071b0-105">To display scroll bars in a RichTextBox control</span></span>  
  
1.  <span data-ttu-id="071b0-106">將 <xref:System.Windows.Forms.RichTextBox.Multiline%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="071b0-106">Set the <xref:System.Windows.Forms.RichTextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="071b0-107">如果沒有類型的捲軸，包括水平的會顯示<xref:System.Windows.Forms.RichTextBox.Multiline%2A>屬性設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="071b0-107">No type of scroll bar, including horizontal, will display if the <xref:System.Windows.Forms.RichTextBox.Multiline%2A> property is set to `false`.</span></span>  
  
2.  <span data-ttu-id="071b0-108">設定<xref:System.Windows.Forms.RichTextBox.ScrollBars%2A>屬性設為適當值的<xref:System.Windows.Forms.RichTextBoxScrollBars>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="071b0-108">Set the <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> property to an appropriate value of the <xref:System.Windows.Forms.RichTextBoxScrollBars> enumeration.</span></span>  
  
    |<span data-ttu-id="071b0-109">值</span><span class="sxs-lookup"><span data-stu-id="071b0-109">Value</span></span>|<span data-ttu-id="071b0-110">描述</span><span class="sxs-lookup"><span data-stu-id="071b0-110">Description</span></span>|  
    |-----------|-----------------|  
    |<span data-ttu-id="071b0-111"><xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (預設值)</span><span class="sxs-lookup"><span data-stu-id="071b0-111"><xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (default)</span></span>|<span data-ttu-id="071b0-112">只會顯示水平或垂直捲軸，或兩者，文字超過控制項長度的寬度。</span><span class="sxs-lookup"><span data-stu-id="071b0-112">Displays horizontal or vertical scroll bars, or both, only when text exceeds the width or length of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|<span data-ttu-id="071b0-113">永遠不會顯示任何捲軸的類型。</span><span class="sxs-lookup"><span data-stu-id="071b0-113">Never displays any type of scroll bar.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|<span data-ttu-id="071b0-114">顯示水平捲軸僅當文字超過控制項的寬度。</span><span class="sxs-lookup"><span data-stu-id="071b0-114">Displays a horizontal scroll bar only when the text exceeds the width of the control.</span></span> <span data-ttu-id="071b0-115">(針對這種情形，<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>屬性必須設定為`false`。)</span><span class="sxs-lookup"><span data-stu-id="071b0-115">(For this to occur, the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property must be set to `false`.)</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|<span data-ttu-id="071b0-116">顯示垂直捲軸僅當文字超過控制項的高度。</span><span class="sxs-lookup"><span data-stu-id="071b0-116">Displays a vertical scroll bar only when the text exceeds the height of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|<span data-ttu-id="071b0-117">顯示在水平捲軸時<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>屬性設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="071b0-117">Displays a horizontal scroll bar when the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property is set to `false`.</span></span> <span data-ttu-id="071b0-118">文字不會超過控制項的寬度時，捲軸呈現暗灰色。</span><span class="sxs-lookup"><span data-stu-id="071b0-118">The scroll bar appears dimmed when text does not exceed the width of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|<span data-ttu-id="071b0-119">永遠顯示垂直捲軸。</span><span class="sxs-lookup"><span data-stu-id="071b0-119">Always displays a vertical scroll bar.</span></span> <span data-ttu-id="071b0-120">當文字未超過控制項的長度時，捲軸呈現暗灰色。</span><span class="sxs-lookup"><span data-stu-id="071b0-120">The scroll bar appears dimmed when text does not exceed the length of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|<span data-ttu-id="071b0-121">永遠顯示垂直捲軸。</span><span class="sxs-lookup"><span data-stu-id="071b0-121">Always displays a vertical scrollbar.</span></span> <span data-ttu-id="071b0-122">顯示在水平捲軸時<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>屬性設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="071b0-122">Displays a horizontal scroll bar when the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property is set to `false`.</span></span> <span data-ttu-id="071b0-123">捲軸會顯示呈現灰色的寬度或控制項的長度不超過文字時。</span><span class="sxs-lookup"><span data-stu-id="071b0-123">The scroll bars appear grayed when text does not exceed the width or length of the control.</span></span>|  
  
3.  <span data-ttu-id="071b0-124">將 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="071b0-124">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="071b0-125">值</span><span class="sxs-lookup"><span data-stu-id="071b0-125">Value</span></span>|<span data-ttu-id="071b0-126">描述</span><span class="sxs-lookup"><span data-stu-id="071b0-126">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="071b0-127">控制項中的文字不會自動調整為超過控制項的寬度，因此它會向右捲動，直到達到分行符號。</span><span class="sxs-lookup"><span data-stu-id="071b0-127">Text in the control is not automatically adjusted to fit the width of the control, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="071b0-128">如果您選擇上方的水平捲軸或兩者，請使用此值。</span><span class="sxs-lookup"><span data-stu-id="071b0-128">Use this value if you chose horizontal scroll bars or both, above.</span></span>|  
    |<span data-ttu-id="071b0-129">`true` (預設值)</span><span class="sxs-lookup"><span data-stu-id="071b0-129">`true` (default)</span></span>|<span data-ttu-id="071b0-130">控制項中的文字會自動調整以配合控制項的寬度。</span><span class="sxs-lookup"><span data-stu-id="071b0-130">Text in the control is automatically adjusted to fit the width of the control.</span></span> <span data-ttu-id="071b0-131">不會出現水平捲軸。</span><span class="sxs-lookup"><span data-stu-id="071b0-131">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="071b0-132">如果您選擇垂直捲軸或 none、 上方，顯示一或多個段落，請使用此值。</span><span class="sxs-lookup"><span data-stu-id="071b0-132">Use this value if you chose vertical scroll bars or none, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="071b0-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="071b0-133">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBoxScrollBars>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="071b0-134">RichTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="071b0-134">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="071b0-135">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="071b0-135">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
