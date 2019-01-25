---
title: HOW TO：在 Windows Forms TextBox 控制項中檢視多行
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
ms.openlocfilehash: 11047b9308905b153662c5449abeeae8c23af26c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565627"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a><span data-ttu-id="0790a-102">HOW TO：在 Windows Forms TextBox 控制項中檢視多行</span><span class="sxs-lookup"><span data-stu-id="0790a-102">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="0790a-103">根據預設，Windows Forms<xref:System.Windows.Forms.TextBox>控制項顯示單行文字，並不會顯示捲軸。</span><span class="sxs-lookup"><span data-stu-id="0790a-103">By default, the Windows Forms <xref:System.Windows.Forms.TextBox> control displays a single line of text and does not display scroll bars.</span></span> <span data-ttu-id="0790a-104">如果文字是超過可用的空間，只有部分的文字會顯示。</span><span class="sxs-lookup"><span data-stu-id="0790a-104">If the text is longer than the available space, only part of the text is visible.</span></span> <span data-ttu-id="0790a-105">您可以設定來變更此預設行為<xref:System.Windows.Forms.TextBox.Multiline%2A>， <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>，和<xref:System.Windows.Forms.TextBox.ScrollBars%2A>屬性，以適當的值。</span><span class="sxs-lookup"><span data-stu-id="0790a-105">You can change this default behavior by setting the <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, and <xref:System.Windows.Forms.TextBox.ScrollBars%2A> properties to appropriate values.</span></span>  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a><span data-ttu-id="0790a-106">若要顯示在 TextBox 控制項中傳回的歸位字元</span><span class="sxs-lookup"><span data-stu-id="0790a-106">To display a carriage return in the TextBox control</span></span>  
  
-   <span data-ttu-id="0790a-107">若要顯示在多行歸位<xref:System.Windows.Forms.TextBox>，使用<xref:System.Environment.NewLine%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="0790a-107">To display a carriage return in a multi-line <xref:System.Windows.Forms.TextBox>, use the <xref:System.Environment.NewLine%2A> property.</span></span>  
  
     <span data-ttu-id="0790a-108">請注意，逸出字元的解譯 (\\) 是特定語言。</span><span class="sxs-lookup"><span data-stu-id="0790a-108">Be aware that the interpretation of escape characters (\\) is language-specific.</span></span> <span data-ttu-id="0790a-109">Visual Basic 則使用`Chr$(13) & Chr$(10)`歸位字元傳回和換行字元組合。</span><span class="sxs-lookup"><span data-stu-id="0790a-109">Visual Basic uses `Chr$(13) & Chr$(10)` for the carriage return and linefeed character combination.</span></span>  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a><span data-ttu-id="0790a-110">若要檢視多行 TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="0790a-110">To view multiple lines in the TextBox control</span></span>  
  
1.  <span data-ttu-id="0790a-111">將 <xref:System.Windows.Forms.TextBox.Multiline%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="0790a-111">Set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="0790a-112">如果<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>是`true`（預設值），則控制項中的文字會出現以一個或多個段落; 否則它會顯示為清單中，在其中有些行可能會裁剪邊緣的控制項。</span><span class="sxs-lookup"><span data-stu-id="0790a-112">If <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> is `true` (the default), then the text in the control will appear as one or more paragraphs; otherwise it will appear as a list, in which some lines may be clipped at the edge of the control.</span></span>  
  
2.  <span data-ttu-id="0790a-113">將 <xref:System.Windows.Forms.TextBox.ScrollBars%2A> 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="0790a-113">Set the <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="0790a-114">值</span><span class="sxs-lookup"><span data-stu-id="0790a-114">Value</span></span>|<span data-ttu-id="0790a-115">描述</span><span class="sxs-lookup"><span data-stu-id="0790a-115">Description</span></span>|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|<span data-ttu-id="0790a-116">使用此值，如果文字段落，幾乎永遠符合控制項。</span><span class="sxs-lookup"><span data-stu-id="0790a-116">Use this value if the text will be a paragraph that almost always fits the control.</span></span> <span data-ttu-id="0790a-117">使用者可以使用滑鼠指標，如果文字太長而無法顯示全部一次需要移動控制項內。</span><span class="sxs-lookup"><span data-stu-id="0790a-117">The user can use the mouse pointer to move around inside the control if the text is too long to display all at once.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|<span data-ttu-id="0790a-118">如果您想要顯示的行，其中有些可能會超過寬度的清單，請使用此值<xref:System.Windows.Forms.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="0790a-118">Use this value if you want to display a list of lines, some of which may be longer than the width of the <xref:System.Windows.Forms.TextBox> control.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|<span data-ttu-id="0790a-119">如果清單可能會超過控制項的高度，請使用此值。</span><span class="sxs-lookup"><span data-stu-id="0790a-119">Use this value if the list may be longer than the height of the control.</span></span>|  
  
3.  <span data-ttu-id="0790a-120">將 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="0790a-120">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="0790a-121">值</span><span class="sxs-lookup"><span data-stu-id="0790a-121">Value</span></span>|<span data-ttu-id="0790a-122">描述</span><span class="sxs-lookup"><span data-stu-id="0790a-122">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="0790a-123">控制項中的文字會不會自動換行，因此它會向右捲動，直到達到分行符號。</span><span class="sxs-lookup"><span data-stu-id="0790a-123">Text in the control will not automatically be wrapped, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="0790a-124">使用此值，如果您選擇<xref:System.Windows.Forms.ScrollBars.Horizontal>捲軸或<xref:System.Windows.Forms.ScrollBars.Both>上面。</span><span class="sxs-lookup"><span data-stu-id="0790a-124">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Horizontal> scroll bars or <xref:System.Windows.Forms.ScrollBars.Both>, above.</span></span>|  
    |<span data-ttu-id="0790a-125">`true` (預設值)</span><span class="sxs-lookup"><span data-stu-id="0790a-125">`true` (default)</span></span>|<span data-ttu-id="0790a-126">不會出現水平捲軸。</span><span class="sxs-lookup"><span data-stu-id="0790a-126">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="0790a-127">使用此值，如果您選擇<xref:System.Windows.Forms.ScrollBars.Vertical>捲軸或<xref:System.Windows.Forms.ScrollBars.None>上面，來顯示一或多個段落。</span><span class="sxs-lookup"><span data-stu-id="0790a-127">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Vertical> scroll bars or <xref:System.Windows.Forms.ScrollBars.None>, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0790a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0790a-128">See also</span></span>
- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="0790a-129">TextBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="0790a-129">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="0790a-130">如何：控制 Windows Forms TextBox 控制項中的插入點</span><span class="sxs-lookup"><span data-stu-id="0790a-130">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="0790a-131">如何：使用 Windows Forms TextBox 控制項建立密碼文字方塊</span><span class="sxs-lookup"><span data-stu-id="0790a-131">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="0790a-132">如何：建立唯讀文字方塊</span><span class="sxs-lookup"><span data-stu-id="0790a-132">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="0790a-133">如何：將引號放入字串</span><span class="sxs-lookup"><span data-stu-id="0790a-133">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="0790a-134">如何：在 Windows Forms TextBox 控制項中選取文字</span><span class="sxs-lookup"><span data-stu-id="0790a-134">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="0790a-135">TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="0790a-135">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
