---
title: RichTextBox 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes
- RichTextBox control [Windows Forms]
- rich edit controls
ms.assetid: 3225f2ef-c6d9-4bd4-9d3e-2219e58edbf2
ms.openlocfilehash: 9d26ec7bfc4d75b304bbc9dc98dbbeaed64effe7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743129"
---
# <a name="richtextbox-control-windows-forms"></a><span data-ttu-id="2846f-102">RichTextBox 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="2846f-102">RichTextBox Control (Windows Forms)</span></span>
<span data-ttu-id="2846f-103">Windows Forms `RichTextBox` 控制項用於顯示、輸入和操作格式化的文字。</span><span class="sxs-lookup"><span data-stu-id="2846f-103">The Windows Forms `RichTextBox` control is used for displaying, entering, and manipulating text with formatting.</span></span> <span data-ttu-id="2846f-104">`RichTextBox` 控制項會執行 <xref:System.Windows.Forms.TextBox> 控制項的所有工作，但也可以顯示字型、色彩和連結;從檔案載入文字和內嵌影像;復原和重做編輯作業;並尋找指定的字元。</span><span class="sxs-lookup"><span data-stu-id="2846f-104">The `RichTextBox` control does everything the <xref:System.Windows.Forms.TextBox> control does, but it can also display fonts, colors, and links; load text and embedded images from a file; undo and redo editing operations; and find specified characters.</span></span> <span data-ttu-id="2846f-105">`RichTextBox` 控制項通常用來提供文字操作和顯示功能，類似于 word 處理應用程式（例如 Microsoft Word）。</span><span class="sxs-lookup"><span data-stu-id="2846f-105">The `RichTextBox` control is typically used to provide text manipulation and display features similar to word processing applications such as Microsoft Word.</span></span> <span data-ttu-id="2846f-106">就像 <xref:System.Windows.Forms.TextBox> 控制項一樣，`RichTextBox` 控制項也可以顯示捲軸;但與 <xref:System.Windows.Forms.TextBox> 控制項不同的是，它預設會顯示水準和垂直捲動條，而且有其他捲軸設定。</span><span class="sxs-lookup"><span data-stu-id="2846f-106">Like the <xref:System.Windows.Forms.TextBox> control, the `RichTextBox` control can display scroll bars; but unlike the <xref:System.Windows.Forms.TextBox> control, it displays both horizontal and vertical scrollbars by default and has additional scrollbar settings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2846f-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="2846f-107">In This Section</span></span>  
 [<span data-ttu-id="2846f-108">RichTextBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="2846f-108">RichTextBox Control Overview</span></span>](richtextbox-control-overview-windows-forms.md)  
 <span data-ttu-id="2846f-109">介紹 `RichTextBox` 控制項的一般概念，可讓使用者使用格式選項來輸入、顯示及操作文字。</span><span class="sxs-lookup"><span data-stu-id="2846f-109">Introduces the general concepts of the `RichTextBox` control, which allows users to enter, display, and manipulate text with formatting options.</span></span>  
  
 [<span data-ttu-id="2846f-110">操作說明：判斷 Windows Forms RichTextBox 控制項中的格式屬性何時變更</span><span class="sxs-lookup"><span data-stu-id="2846f-110">How to: Determine When Formatting Attributes Change in the Windows Forms RichTextBox Control</span></span>](determine-when-formatting-attributes-change-wf-richtextbox-control.md)  
 <span data-ttu-id="2846f-111">說明如何追蹤 `RichTextBox` 控制項中字型和段落格式的變更。</span><span class="sxs-lookup"><span data-stu-id="2846f-111">Explains how to keep track of changes in font and paragraph formatting in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="2846f-112">操作說明：在 Windows Forms RichTextBox 控制項中顯示捲軸</span><span class="sxs-lookup"><span data-stu-id="2846f-112">How to: Display Scroll Bars in the Windows Forms RichTextBox Control</span></span>](how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="2846f-113">描述 `RichTextBox` 控制項中捲軸可用的許多選項。</span><span class="sxs-lookup"><span data-stu-id="2846f-113">Describes the many choices available for scroll bars in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="2846f-114">操作說明：使用 Windows Forms RichTextBox 控制項顯示 Web 樣式連結</span><span class="sxs-lookup"><span data-stu-id="2846f-114">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>](how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="2846f-115">說明如何從 `RichTextBox` 控制項連結至網站。</span><span class="sxs-lookup"><span data-stu-id="2846f-115">Explains how to link to Web sites from the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="2846f-116">操作說明：啟用 Windows Forms RichTextBox 控制項的拖放作業</span><span class="sxs-lookup"><span data-stu-id="2846f-116">How to: Enable Drag-and-Drop Operations with the Windows Forms RichTextBox Control</span></span>](enable-drag-and-drop-operations-with-wf-richtextbox-control.md)  
 <span data-ttu-id="2846f-117">提供將資料拖曳至 `RichTextBox` 控制項的指示。</span><span class="sxs-lookup"><span data-stu-id="2846f-117">Provides instructions for dragging data into the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="2846f-118">操作說明：將檔案載入 Windows Forms RichTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="2846f-118">How to: Load Files into the Windows Forms RichTextBox Control</span></span>](how-to-load-files-into-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="2846f-119">提供將現有檔案載入 `RichTextBox` 控制項的指示。</span><span class="sxs-lookup"><span data-stu-id="2846f-119">Provides instructions for loading an existing file into the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="2846f-120">操作說明：使用 Windows Forms RichTextBox 控制項儲存檔案</span><span class="sxs-lookup"><span data-stu-id="2846f-120">How to: Save Files with the Windows Forms RichTextBox Control</span></span>](how-to-save-files-with-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="2846f-121">提供將 `RichTextBox` 控制項的內容儲存至檔案的指示。</span><span class="sxs-lookup"><span data-stu-id="2846f-121">Provides instructions for saving the contents of the `RichTextBox` control to a file.</span></span>  
  
 [<span data-ttu-id="2846f-122">操作說明：為 Windows Forms RichTextBox 控制項設定字型屬性</span><span class="sxs-lookup"><span data-stu-id="2846f-122">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>](how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="2846f-123">描述如何設定 `RichTextBox` 控制項中文字的字型系列、大小、樣式和色彩。</span><span class="sxs-lookup"><span data-stu-id="2846f-123">Describes how to set the font family, size, style, and color of text in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="2846f-124">操作說明：使用 Windows Forms RichTextBox 控制項設定縮排、首行縮排和分項段落</span><span class="sxs-lookup"><span data-stu-id="2846f-124">How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control</span></span>](set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md)  
 <span data-ttu-id="2846f-125">描述如何格式化 `RichTextBox` 控制項中的段落。</span><span class="sxs-lookup"><span data-stu-id="2846f-125">Describes how to format paragraphs in the `RichTextBox` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2846f-126">參考資料</span><span class="sxs-lookup"><span data-stu-id="2846f-126">Reference</span></span>  
 <span data-ttu-id="2846f-127"><xref:System.Windows.Forms.RichTextBox> 類別</span><span class="sxs-lookup"><span data-stu-id="2846f-127"><xref:System.Windows.Forms.RichTextBox> class</span></span>  
 <span data-ttu-id="2846f-128">說明這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="2846f-128">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2846f-129">相關章節</span><span class="sxs-lookup"><span data-stu-id="2846f-129">Related Sections</span></span>  
 [<span data-ttu-id="2846f-130">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="2846f-130">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="2846f-131">提供 Windows Form 控制項的完整清單，以及其用法的資訊連結。</span><span class="sxs-lookup"><span data-stu-id="2846f-131">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="2846f-132">TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="2846f-132">TextBox Control</span></span>](textbox-control-windows-forms.md)  
 <span data-ttu-id="2846f-133">介紹 <xref:System.Windows.Forms.TextBox> 控制項的一般概念，可讓使用者進行可編輯的多行輸入。</span><span class="sxs-lookup"><span data-stu-id="2846f-133">Introduces the general concepts of the <xref:System.Windows.Forms.TextBox> control, which allows editable, multiline input from the user.</span></span>
