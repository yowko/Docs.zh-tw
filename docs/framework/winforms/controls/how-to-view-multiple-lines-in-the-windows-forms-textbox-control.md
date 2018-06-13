---
title: 如何：檢視 Windows Form TextBox 控制項中的多行
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
ms.openlocfilehash: c826a519d8be05430eb6e2434209424514347b5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538563"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a><span data-ttu-id="a3323-102">如何：檢視 Windows Form TextBox 控制項中的多行</span><span class="sxs-lookup"><span data-stu-id="a3323-102">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="a3323-103">根據預設，Windows Form<xref:System.Windows.Forms.TextBox>控制項顯示單行文字，並不會顯示捲軸。</span><span class="sxs-lookup"><span data-stu-id="a3323-103">By default, the Windows Forms <xref:System.Windows.Forms.TextBox> control displays a single line of text and does not display scroll bars.</span></span> <span data-ttu-id="a3323-104">文字的長度超過可用的空間，部分文字可見。</span><span class="sxs-lookup"><span data-stu-id="a3323-104">If the text is longer than the available space, only part of the text is visible.</span></span> <span data-ttu-id="a3323-105">您可以變更此預設行為，藉由設定<xref:System.Windows.Forms.TextBox.Multiline%2A>， <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>，和<xref:System.Windows.Forms.TextBox.ScrollBars%2A>屬性，以適當的值。</span><span class="sxs-lookup"><span data-stu-id="a3323-105">You can change this default behavior by setting the <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, and <xref:System.Windows.Forms.TextBox.ScrollBars%2A> properties to appropriate values.</span></span>  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a><span data-ttu-id="a3323-106">若要顯示在文字方塊控制項中所傳回的歸位字元</span><span class="sxs-lookup"><span data-stu-id="a3323-106">To display a carriage return in the TextBox control</span></span>  
  
-   <span data-ttu-id="a3323-107">若要顯示多行中換<xref:System.Windows.Forms.TextBox>，使用<xref:System.Environment.NewLine%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a3323-107">To display a carriage return in a multi-line <xref:System.Windows.Forms.TextBox>, use the <xref:System.Environment.NewLine%2A> property.</span></span>  
  
     <span data-ttu-id="a3323-108">請注意，逸出字元的解譯 (\\) 是特定語言。</span><span class="sxs-lookup"><span data-stu-id="a3323-108">Be aware that the interpretation of escape characters (\\) is language-specific.</span></span> <span data-ttu-id="a3323-109">Visual Basic 會使用`Chr$(13) & Chr$(10)`的歸位字元與換行字元組合。</span><span class="sxs-lookup"><span data-stu-id="a3323-109">Visual Basic uses `Chr$(13) & Chr$(10)` for the carriage return and linefeed character combination.</span></span>  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a><span data-ttu-id="a3323-110">若要檢視多行文字方塊控制項中</span><span class="sxs-lookup"><span data-stu-id="a3323-110">To view multiple lines in the TextBox control</span></span>  
  
1.  <span data-ttu-id="a3323-111">將 <xref:System.Windows.Forms.TextBox.Multiline%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a3323-111">Set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="a3323-112">如果<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>是`true`（預設值），然後在控制項中的文字會出現以一個或多個段落; 否則它將會顯示為清單中，可能會在控制項的邊緣裁剪數行程式中。</span><span class="sxs-lookup"><span data-stu-id="a3323-112">If <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> is `true` (the default), then the text in the control will appear as one or more paragraphs; otherwise it will appear as a list, in which some lines may be clipped at the edge of the control.</span></span>  
  
2.  <span data-ttu-id="a3323-113">將 <xref:System.Windows.Forms.TextBox.ScrollBars%2A> 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="a3323-113">Set the <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="a3323-114">值</span><span class="sxs-lookup"><span data-stu-id="a3323-114">Value</span></span>|<span data-ttu-id="a3323-115">描述</span><span class="sxs-lookup"><span data-stu-id="a3323-115">Description</span></span>|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|<span data-ttu-id="a3323-116">使用此值，如果文字段落，幾乎永遠符合控制項。</span><span class="sxs-lookup"><span data-stu-id="a3323-116">Use this value if the text will be a paragraph that almost always fits the control.</span></span> <span data-ttu-id="a3323-117">如果文字太長而無法顯示一次，四處移動控制項內，使用者可以使用滑鼠指標。</span><span class="sxs-lookup"><span data-stu-id="a3323-117">The user can use the mouse pointer to move around inside the control if the text is too long to display all at once.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|<span data-ttu-id="a3323-118">如果您想要顯示的行，其中有些可能會超過寬度的清單，請使用這個值<xref:System.Windows.Forms.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="a3323-118">Use this value if you want to display a list of lines, some of which may be longer than the width of the <xref:System.Windows.Forms.TextBox> control.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|<span data-ttu-id="a3323-119">如果清單可能會超過控制項的高度，請使用此值。</span><span class="sxs-lookup"><span data-stu-id="a3323-119">Use this value if the list may be longer than the height of the control.</span></span>|  
  
3.  <span data-ttu-id="a3323-120">將 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="a3323-120">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="a3323-121">值</span><span class="sxs-lookup"><span data-stu-id="a3323-121">Value</span></span>|<span data-ttu-id="a3323-122">描述</span><span class="sxs-lookup"><span data-stu-id="a3323-122">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="a3323-123">控制項中的文字將不會自動換行，因此它會向右捲動，直到達到分行符號。</span><span class="sxs-lookup"><span data-stu-id="a3323-123">Text in the control will not automatically be wrapped, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="a3323-124">使用此值，如果您選擇<xref:System.Windows.Forms.ScrollBars.Horizontal>捲軸或<xref:System.Windows.Forms.ScrollBars.Both>上述。</span><span class="sxs-lookup"><span data-stu-id="a3323-124">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Horizontal> scroll bars or <xref:System.Windows.Forms.ScrollBars.Both>, above.</span></span>|  
    |<span data-ttu-id="a3323-125">`true` (預設值)</span><span class="sxs-lookup"><span data-stu-id="a3323-125">`true` (default)</span></span>|<span data-ttu-id="a3323-126">不會出現水平捲軸。</span><span class="sxs-lookup"><span data-stu-id="a3323-126">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="a3323-127">使用此值，如果您選擇<xref:System.Windows.Forms.ScrollBars.Vertical>捲軸或<xref:System.Windows.Forms.ScrollBars.None>上述，以顯示一或多個段落。</span><span class="sxs-lookup"><span data-stu-id="a3323-127">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Vertical> scroll bars or <xref:System.Windows.Forms.ScrollBars.None>, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3323-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3323-128">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="a3323-129">TextBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="a3323-129">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="a3323-130">操作說明：控制 Windows Forms TextBox 控制項中的插入點</span><span class="sxs-lookup"><span data-stu-id="a3323-130">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="a3323-131">操作說明：使用 Windows Forms TextBox 控制項建立密碼文字方塊</span><span class="sxs-lookup"><span data-stu-id="a3323-131">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="a3323-132">操作說明：建立唯讀文字方塊</span><span class="sxs-lookup"><span data-stu-id="a3323-132">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="a3323-133">操作說明：將引號放入字串中</span><span class="sxs-lookup"><span data-stu-id="a3323-133">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="a3323-134">操作說明：在 Windows Forms TextBox 控制項中選取文字</span><span class="sxs-lookup"><span data-stu-id="a3323-134">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="a3323-135">TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="a3323-135">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
