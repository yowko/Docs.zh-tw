---
title: HOW TO：建立唯讀文字方塊 (Windows Form)
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 72dc188993474ad4b39f0cfa74cadffdb99ff46f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59308571"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="f48b5-102">HOW TO：建立唯讀文字方塊 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="f48b5-102">How to: Create a Read-Only Text Box (Windows Forms)</span></span>
<span data-ttu-id="f48b5-103">您可以將可編輯的 Windows Form 文字方塊中轉換成唯讀的控制項。</span><span class="sxs-lookup"><span data-stu-id="f48b5-103">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="f48b5-104">例如，文字方塊可能會顯示值通常進行編輯，但可能不是目前因為應用程式的狀態。</span><span class="sxs-lookup"><span data-stu-id="f48b5-104">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>  
  
### <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="f48b5-105">若要建立唯讀文字方塊</span><span class="sxs-lookup"><span data-stu-id="f48b5-105">To create a read-only text box</span></span>  
  
1. <span data-ttu-id="f48b5-106">設定<xref:System.Windows.Forms.TextBox>控制項的<xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="f48b5-106">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="f48b5-107">屬性設為`true`，使用者仍然可以捲動，並反白顯示 不允許變更 文字 方塊中的文字。</span><span class="sxs-lookup"><span data-stu-id="f48b5-107">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="f48b5-108">A**複製**命令會在文字方塊中中, 運作，但**剪下**並**貼上**命令不是。</span><span class="sxs-lookup"><span data-stu-id="f48b5-108">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f48b5-109"><xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>屬性只會影響在執行階段的使用者互動。</span><span class="sxs-lookup"><span data-stu-id="f48b5-109">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="f48b5-110">您仍然可以變更文字方塊內容以程式設計方式在執行階段變更<xref:System.Windows.Forms.TextBox.Text%2A>文字方塊的屬性。</span><span class="sxs-lookup"><span data-stu-id="f48b5-110">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f48b5-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f48b5-111">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="f48b5-112">TextBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="f48b5-112">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="f48b5-113">HOW TO：控制 Windows Forms TextBox 控制項的插入點</span><span class="sxs-lookup"><span data-stu-id="f48b5-113">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="f48b5-114">HOW TO：使用 Windows Forms TextBox 控制項建立密碼文字方塊</span><span class="sxs-lookup"><span data-stu-id="f48b5-114">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="f48b5-115">HOW TO：將引號放入字串中</span><span class="sxs-lookup"><span data-stu-id="f48b5-115">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="f48b5-116">HOW TO：選取 Windows Forms TextBox 控制項的文字</span><span class="sxs-lookup"><span data-stu-id="f48b5-116">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="f48b5-117">HOW TO：檢視 Windows Forms TextBox 控制項中的多行</span><span class="sxs-lookup"><span data-stu-id="f48b5-117">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="f48b5-118">TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="f48b5-118">TextBox Control</span></span>](textbox-control-windows-forms.md)
