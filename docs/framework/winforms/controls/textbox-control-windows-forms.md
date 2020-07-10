---
title: TextBox 控制項
description: 瞭解 Windows Forms TextBox 控制項的各個層面，包括將它用於可編輯的文字，並將它設為唯讀。
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes
- TextBox control [Windows Forms]
ms.assetid: e5a06987-8aec-4271-b196-2245ba992d62
ms.openlocfilehash: 026f6d2653e41dabd3db7490660b6ce19846d397
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174441"
---
# <a name="textbox-control-windows-forms"></a><span data-ttu-id="472a0-103">TextBox 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="472a0-103">TextBox Control (Windows Forms)</span></span>
<span data-ttu-id="472a0-104">Windows Forms 文字方塊可用來取得使用者的輸入或顯示文字。</span><span class="sxs-lookup"><span data-stu-id="472a0-104">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="472a0-105">`TextBox`控制項通常用於可編輯的文字，不過它也可以設為唯讀。</span><span class="sxs-lookup"><span data-stu-id="472a0-105">The `TextBox` control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="472a0-106">文字方塊可以顯示多行、將文字換成控制項的大小，以及新增基本格式。</span><span class="sxs-lookup"><span data-stu-id="472a0-106">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="472a0-107">`TextBox`控制項允許在控制項中顯示或輸入文字的單一格式。</span><span class="sxs-lookup"><span data-stu-id="472a0-107">The `TextBox` control allows a single format for text displayed or entered in the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="472a0-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="472a0-108">In This Section</span></span>  
 [<span data-ttu-id="472a0-109">TextBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="472a0-109">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)  
 <span data-ttu-id="472a0-110">說明此控制項是什麼，並說明其重要功能與屬性。</span><span class="sxs-lookup"><span data-stu-id="472a0-110">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="472a0-111">如何：控制 Windows Forms TextBox 控制項的插入點</span><span class="sxs-lookup"><span data-stu-id="472a0-111">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 <span data-ttu-id="472a0-112">說明如何指定當編輯控制項第一次取得焦點時，插入點出現的位置。</span><span class="sxs-lookup"><span data-stu-id="472a0-112">Gives directions for specifying where the insertion point appears when an edit control first gets the focus.</span></span>  
  
 [<span data-ttu-id="472a0-113">如何：使用 Windows Forms TextBox 控制項建立密碼文字方塊</span><span class="sxs-lookup"><span data-stu-id="472a0-113">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="472a0-114">說明如何隱藏在文字方塊中輸入的內容。</span><span class="sxs-lookup"><span data-stu-id="472a0-114">Explains how to conceal what is typed into a text box.</span></span>  
  
 [<span data-ttu-id="472a0-115">如何：建立唯讀文字方塊</span><span class="sxs-lookup"><span data-stu-id="472a0-115">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)  
 <span data-ttu-id="472a0-116">描述如何防止文字方塊的內容遭到變更。</span><span class="sxs-lookup"><span data-stu-id="472a0-116">Describes how to prevent the contents of a text box from being changed.</span></span>  
  
 [<span data-ttu-id="472a0-117">操作說明：將引號放入字串中</span><span class="sxs-lookup"><span data-stu-id="472a0-117">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 <span data-ttu-id="472a0-118">說明如何將引號加入文字方塊中的字串。</span><span class="sxs-lookup"><span data-stu-id="472a0-118">Explains adding quotation marks to a string in a text box.</span></span>  
  
 [<span data-ttu-id="472a0-119">如何：在 Windows Form TextBox 控制項中選取文字</span><span class="sxs-lookup"><span data-stu-id="472a0-119">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="472a0-120">說明如何反白顯示文字方塊中的文字。</span><span class="sxs-lookup"><span data-stu-id="472a0-120">Explains how to highlight text in a text box.</span></span>  
  
 [<span data-ttu-id="472a0-121">如何：檢視 Windows Form TextBox 控制項中的多行</span><span class="sxs-lookup"><span data-stu-id="472a0-121">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="472a0-122">描述如何讓文字方塊成為可滾動的。</span><span class="sxs-lookup"><span data-stu-id="472a0-122">Describes how to make a text box scrollable.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="472a0-123">參考</span><span class="sxs-lookup"><span data-stu-id="472a0-123">Reference</span></span>  
 <span data-ttu-id="472a0-124"><xref:System.Windows.Forms.TextBox> 類別</span><span class="sxs-lookup"><span data-stu-id="472a0-124"><xref:System.Windows.Forms.TextBox> class</span></span>  
 <span data-ttu-id="472a0-125">說明這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="472a0-125">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="472a0-126">相關章節</span><span class="sxs-lookup"><span data-stu-id="472a0-126">Related Sections</span></span>  
 [<span data-ttu-id="472a0-127">在 Windows Form 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="472a0-127">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="472a0-128">提供 Windows Form 控制項的完整清單，以及其用法的資訊連結。</span><span class="sxs-lookup"><span data-stu-id="472a0-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
