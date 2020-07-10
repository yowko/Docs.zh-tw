---
title: 在 TextBox 控制項中查看多行
description: 藉由設定多行、自動換行和捲軸屬性，瞭解如何在 Windows Forms TextBox 控制項中查看多行。
ms.date: 03/30/2017
helpviewer_keywords:
- newline
- end of line
- ScrollBars property [Windows Forms], in TextBox control
- CRLF
- MultiLine property in TextBox control
- line-feed
- TextBox control [Windows Forms], viewing multiple lines
- carriage return
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
ms.openlocfilehash: e40d720bcd56366f4f06bfe2e2d347aaf9aa9d6c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174467"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a><span data-ttu-id="284ad-103">如何：檢視 Windows Form TextBox 控制項中的多行</span><span class="sxs-lookup"><span data-stu-id="284ad-103">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="284ad-104">根據預設，Windows Forms <xref:System.Windows.Forms.TextBox> 控制項會顯示一行文字，而且不會顯示捲軸。</span><span class="sxs-lookup"><span data-stu-id="284ad-104">By default, the Windows Forms <xref:System.Windows.Forms.TextBox> control displays a single line of text and does not display scroll bars.</span></span> <span data-ttu-id="284ad-105">如果文字長度超過可用空間，則只會顯示部分的文字。</span><span class="sxs-lookup"><span data-stu-id="284ad-105">If the text is longer than the available space, only part of the text is visible.</span></span> <span data-ttu-id="284ad-106">您可以藉由將 <xref:System.Windows.Forms.TextBox.Multiline%2A> 、 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 和屬性設定為適當的值，來變更此預設行為 <xref:System.Windows.Forms.TextBox.ScrollBars%2A> 。</span><span class="sxs-lookup"><span data-stu-id="284ad-106">You can change this default behavior by setting the <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, and <xref:System.Windows.Forms.TextBox.ScrollBars%2A> properties to appropriate values.</span></span>  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a><span data-ttu-id="284ad-107">在 TextBox 控制項中顯示回車</span><span class="sxs-lookup"><span data-stu-id="284ad-107">To display a carriage return in the TextBox control</span></span>  
  
- <span data-ttu-id="284ad-108">若要在多行中顯示回車符 <xref:System.Windows.Forms.TextBox> ，請使用 <xref:System.Environment.NewLine%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="284ad-108">To display a carriage return in a multi-line <xref:System.Windows.Forms.TextBox>, use the <xref:System.Environment.NewLine%2A> property.</span></span>  
  
     <span data-ttu-id="284ad-109">請注意， () 的逸出字元解讀 \\ 是語言特定的。</span><span class="sxs-lookup"><span data-stu-id="284ad-109">Be aware that the interpretation of escape characters (\\) is language-specific.</span></span> <span data-ttu-id="284ad-110">Visual Basic `Chr$(13) & Chr$(10)` 用於回車和換行字元的組合。</span><span class="sxs-lookup"><span data-stu-id="284ad-110">Visual Basic uses `Chr$(13) & Chr$(10)` for the carriage return and linefeed character combination.</span></span>  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a><span data-ttu-id="284ad-111">若要在 TextBox 控制項中查看多行</span><span class="sxs-lookup"><span data-stu-id="284ad-111">To view multiple lines in the TextBox control</span></span>  
  
1. <span data-ttu-id="284ad-112">將 <xref:System.Windows.Forms.TextBox.Multiline%2A> 屬性設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="284ad-112">Set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="284ad-113">如果 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> `true` (預設) ，則控制項中的文字會顯示為一或多個段落，否則會顯示為清單，其中有些線條可能會在控制項的邊緣裁剪。</span><span class="sxs-lookup"><span data-stu-id="284ad-113">If <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> is `true` (the default), then the text in the control will appear as one or more paragraphs; otherwise it will appear as a list, in which some lines may be clipped at the edge of the control.</span></span>  
  
2. <span data-ttu-id="284ad-114">將 <xref:System.Windows.Forms.TextBox.ScrollBars%2A> 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="284ad-114">Set the <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="284ad-115">值</span><span class="sxs-lookup"><span data-stu-id="284ad-115">Value</span></span>|<span data-ttu-id="284ad-116">描述</span><span class="sxs-lookup"><span data-stu-id="284ad-116">Description</span></span>|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|<span data-ttu-id="284ad-117">如果文字將會是幾乎一律符合控制項的段落，請使用此值。</span><span class="sxs-lookup"><span data-stu-id="284ad-117">Use this value if the text will be a paragraph that almost always fits the control.</span></span> <span data-ttu-id="284ad-118">如果文字太長而無法全部顯示時，使用者可以使用滑鼠指標在控制項內四處移動。</span><span class="sxs-lookup"><span data-stu-id="284ad-118">The user can use the mouse pointer to move around inside the control if the text is too long to display all at once.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|<span data-ttu-id="284ad-119">如果您想要顯示行清單，其中有些可能會比控制項的寬度還長，請使用此值 <xref:System.Windows.Forms.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="284ad-119">Use this value if you want to display a list of lines, some of which may be longer than the width of the <xref:System.Windows.Forms.TextBox> control.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|<span data-ttu-id="284ad-120">如果清單可能比控制項的高度長，請使用此值。</span><span class="sxs-lookup"><span data-stu-id="284ad-120">Use this value if the list may be longer than the height of the control.</span></span>|  
  
3. <span data-ttu-id="284ad-121">將 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="284ad-121">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="284ad-122">值</span><span class="sxs-lookup"><span data-stu-id="284ad-122">Value</span></span>|<span data-ttu-id="284ad-123">描述</span><span class="sxs-lookup"><span data-stu-id="284ad-123">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="284ad-124">控制項中的文字不會自動換行，因此它會向右滾動，直到到達分行符號為止。</span><span class="sxs-lookup"><span data-stu-id="284ad-124">Text in the control will not automatically be wrapped, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="284ad-125">如果您選擇 <xref:System.Windows.Forms.ScrollBars.Horizontal> 捲軸或上方的，請使用此值 <xref:System.Windows.Forms.ScrollBars.Both> 。</span><span class="sxs-lookup"><span data-stu-id="284ad-125">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Horizontal> scroll bars or <xref:System.Windows.Forms.ScrollBars.Both>, above.</span></span>|  
    |<span data-ttu-id="284ad-126">`true` (預設值)</span><span class="sxs-lookup"><span data-stu-id="284ad-126">`true` (default)</span></span>|<span data-ttu-id="284ad-127">水準捲軸不會出現。</span><span class="sxs-lookup"><span data-stu-id="284ad-127">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="284ad-128">如果您選擇 <xref:System.Windows.Forms.ScrollBars.Vertical> 捲軸或 <xref:System.Windows.Forms.ScrollBars.None> 上方顯示一個或多個段落，請使用此值。</span><span class="sxs-lookup"><span data-stu-id="284ad-128">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Vertical> scroll bars or <xref:System.Windows.Forms.ScrollBars.None>, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="284ad-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="284ad-129">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="284ad-130">TextBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="284ad-130">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="284ad-131">如何：控制 Windows Forms TextBox 控制項的插入點</span><span class="sxs-lookup"><span data-stu-id="284ad-131">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="284ad-132">如何：使用 Windows Forms TextBox 控制項建立密碼文字方塊</span><span class="sxs-lookup"><span data-stu-id="284ad-132">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="284ad-133">如何：建立唯讀文字方塊</span><span class="sxs-lookup"><span data-stu-id="284ad-133">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="284ad-134">操作說明：將引號放入字串中</span><span class="sxs-lookup"><span data-stu-id="284ad-134">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="284ad-135">如何：在 Windows Form TextBox 控制項中選取文字</span><span class="sxs-lookup"><span data-stu-id="284ad-135">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="284ad-136">TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="284ad-136">TextBox Control</span></span>](textbox-control-windows-forms.md)
