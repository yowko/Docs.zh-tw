---
title: RichTextBox 控制項 (Windows Form)
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes
- RichTextBox control [Windows Forms]
- rich edit controls
ms.assetid: 3225f2ef-c6d9-4bd4-9d3e-2219e58edbf2
ms.openlocfilehash: 00f28abeb616006e63a45dd7922f4d5b247e8dd9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540878"
---
# <a name="richtextbox-control-windows-forms"></a><span data-ttu-id="7234d-102">RichTextBox 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="7234d-102">RichTextBox Control (Windows Forms)</span></span>
<span data-ttu-id="7234d-103">Windows Form`RichTextBox`控制項用來顯示、 輸入及管理具有格式的文字。</span><span class="sxs-lookup"><span data-stu-id="7234d-103">The Windows Forms `RichTextBox` control is used for displaying, entering, and manipulating text with formatting.</span></span> <span data-ttu-id="7234d-104">`RichTextBox`控制項執行的所有項目<xref:System.Windows.Forms.TextBox>控制項，但同時，也顯示字型、 色彩和連結; 載入文字和內嵌的影像檔案，則復原和重做的編輯作業，並尋找指定的字元。</span><span class="sxs-lookup"><span data-stu-id="7234d-104">The `RichTextBox` control does everything the <xref:System.Windows.Forms.TextBox> control does, but it can also display fonts, colors, and links; load text and embedded images from a file; undo and redo editing operations; and find specified characters.</span></span> <span data-ttu-id="7234d-105">`RichTextBox`控制項通常用來提供操作文字，並顯示類似於文書處理應用程式，例如 Microsoft Word 的功能。</span><span class="sxs-lookup"><span data-stu-id="7234d-105">The `RichTextBox` control is typically used to provide text manipulation and display features similar to word processing applications such as Microsoft Word.</span></span> <span data-ttu-id="7234d-106">像<xref:System.Windows.Forms.TextBox>控制項，`RichTextBox`控制項可以顯示捲軸，但不同的是<xref:System.Windows.Forms.TextBox>控制項，其中預設會顯示水平與垂直捲軸，而沒有其他的捲軸設定。</span><span class="sxs-lookup"><span data-stu-id="7234d-106">Like the <xref:System.Windows.Forms.TextBox> control, the `RichTextBox` control can display scroll bars; but unlike the <xref:System.Windows.Forms.TextBox> control, it displays both horizontal and vertical scrollbars by default and has additional scrollbar settings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7234d-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="7234d-107">In This Section</span></span>  
 [<span data-ttu-id="7234d-108">RichTextBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="7234d-108">RichTextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md)  
 <span data-ttu-id="7234d-109">導入的一般概念`RichTextBox`控制項，可讓使用者輸入、 顯示和操作文字格式化選項。</span><span class="sxs-lookup"><span data-stu-id="7234d-109">Introduces the general concepts of the `RichTextBox` control, which allows users to enter, display, and manipulate text with formatting options.</span></span>  
  
 [<span data-ttu-id="7234d-110">操作說明：判斷 Windows Forms RichTextBox 控制項中的格式屬性何時變更</span><span class="sxs-lookup"><span data-stu-id="7234d-110">How to: Determine When Formatting Attributes Change in the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/determine-when-formatting-attributes-change-wf-richtextbox-control.md)  
 <span data-ttu-id="7234d-111">說明如何追蹤的字型和中的段落格式化變更`RichTextBox`控制項。</span><span class="sxs-lookup"><span data-stu-id="7234d-111">Explains how to keep track of changes in font and paragraph formatting in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="7234d-112">操作說明：在 Windows Forms RichTextBox 控制項中顯示捲軸</span><span class="sxs-lookup"><span data-stu-id="7234d-112">How to: Display Scroll Bars in the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="7234d-113">描述許多選擇可用的捲軸在`RichTextBox`控制項。</span><span class="sxs-lookup"><span data-stu-id="7234d-113">Describes the many choices available for scroll bars in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="7234d-114">操作說明：使用 Windows Forms RichTextBox 控制項顯示 Web 樣式連結</span><span class="sxs-lookup"><span data-stu-id="7234d-114">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="7234d-115">說明如何連結至網站的`RichTextBox`控制項。</span><span class="sxs-lookup"><span data-stu-id="7234d-115">Explains how to link to Web sites from the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="7234d-116">操作說明：啟用 Windows Forms RichTextBox 控制項的拖放作業</span><span class="sxs-lookup"><span data-stu-id="7234d-116">How to: Enable Drag-and-Drop Operations with the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/enable-drag-and-drop-operations-with-wf-richtextbox-control.md)  
 <span data-ttu-id="7234d-117">提供拖曳到資料的指示`RichTextBox`控制項。</span><span class="sxs-lookup"><span data-stu-id="7234d-117">Provides instructions for dragging data into the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="7234d-118">操作說明：將檔案載入 Windows Forms RichTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="7234d-118">How to: Load Files into the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-load-files-into-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="7234d-119">提供載入到現有檔案的指示`RichTextBox`控制項。</span><span class="sxs-lookup"><span data-stu-id="7234d-119">Provides instructions for loading an existing file into the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="7234d-120">操作說明：使用 Windows Forms RichTextBox 控制項儲存檔案</span><span class="sxs-lookup"><span data-stu-id="7234d-120">How to: Save Files with the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-save-files-with-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="7234d-121">提供的內容儲存指示`RichTextBox`檔案的控制項。</span><span class="sxs-lookup"><span data-stu-id="7234d-121">Provides instructions for saving the contents of the `RichTextBox` control to a file.</span></span>  
  
 [<span data-ttu-id="7234d-122">操作說明：為 Windows Forms RichTextBox 控制項設定字型屬性</span><span class="sxs-lookup"><span data-stu-id="7234d-122">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="7234d-123">描述如何設定字型家族、 大小、 樣式和文字色彩`RichTextBox`控制項。</span><span class="sxs-lookup"><span data-stu-id="7234d-123">Describes how to set the font family, size, style, and color of text in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="7234d-124">操作說明：使用 Windows Forms RichTextBox 控制項設定縮排、首行縮排和分項段落</span><span class="sxs-lookup"><span data-stu-id="7234d-124">How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md)  
 <span data-ttu-id="7234d-125">描述如何格式化的段落`RichTextBox`控制項。</span><span class="sxs-lookup"><span data-stu-id="7234d-125">Describes how to format paragraphs in the `RichTextBox` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7234d-126">參考資料</span><span class="sxs-lookup"><span data-stu-id="7234d-126">Reference</span></span>  
 <span data-ttu-id="7234d-127"><xref:System.Windows.Forms.RichTextBox> 類別</span><span class="sxs-lookup"><span data-stu-id="7234d-127"><xref:System.Windows.Forms.RichTextBox> class</span></span>  
 <span data-ttu-id="7234d-128">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="7234d-128">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7234d-129">相關章節</span><span class="sxs-lookup"><span data-stu-id="7234d-129">Related Sections</span></span>  
 [<span data-ttu-id="7234d-130">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="7234d-130">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="7234d-131">提供 Windows Form 控制項的完整清單，以及其用法的資訊連結。</span><span class="sxs-lookup"><span data-stu-id="7234d-131">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="7234d-132">TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="7234d-132">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)  
 <span data-ttu-id="7234d-133">導入的一般概念<xref:System.Windows.Forms.TextBox>控制項，可讓使用者可以編輯、 多行輸入。</span><span class="sxs-lookup"><span data-stu-id="7234d-133">Introduces the general concepts of the <xref:System.Windows.Forms.TextBox> control, which allows editable, multiline input from the user.</span></span>
