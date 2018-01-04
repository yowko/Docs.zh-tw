---
title: "如何：建立唯讀文字方塊 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 264ef1a7c1f121f889d57dcb0e36e216610418fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="e675a-102">如何：建立唯讀文字方塊 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="e675a-102">How to: Create a Read-Only Text Box (Windows Forms)</span></span>
<span data-ttu-id="e675a-103">您可以將可編輯的 Windows Form 文字方塊中轉換成唯讀的控制項。</span><span class="sxs-lookup"><span data-stu-id="e675a-103">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="e675a-104">例如，文字方塊可能會顯示值通常編輯，但可能不是目前，因為應用程式的狀態。</span><span class="sxs-lookup"><span data-stu-id="e675a-104">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>  
  
### <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="e675a-105">若要建立唯讀文字方塊</span><span class="sxs-lookup"><span data-stu-id="e675a-105">To create a read-only text box</span></span>  
  
1.  <span data-ttu-id="e675a-106">設定<xref:System.Windows.Forms.TextBox>控制項的<xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="e675a-106">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="e675a-107">屬性設定為`true`，使用者仍可以捲動及反白顯示 不允許變更 在文字方塊中的文字。</span><span class="sxs-lookup"><span data-stu-id="e675a-107">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="e675a-108">A**複製**命令仍在文字方塊中，但**剪下**和**貼上** 命令。</span><span class="sxs-lookup"><span data-stu-id="e675a-108">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e675a-109"><xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>屬性只會影響執行階段的使用者互動。</span><span class="sxs-lookup"><span data-stu-id="e675a-109">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="e675a-110">您仍然可以變更文字方塊內容以程式設計方式在執行階段變更<xref:System.Windows.Forms.TextBox.Text%2A>文字方塊的屬性。</span><span class="sxs-lookup"><span data-stu-id="e675a-110">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e675a-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="e675a-111">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="e675a-112">TextBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="e675a-112">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="e675a-113">操作說明：控制 Windows Forms TextBox 控制項中的插入點</span><span class="sxs-lookup"><span data-stu-id="e675a-113">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="e675a-114">操作說明：使用 Windows Forms TextBox 控制項建立密碼文字方塊</span><span class="sxs-lookup"><span data-stu-id="e675a-114">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="e675a-115">操作說明：將引號放入字串中</span><span class="sxs-lookup"><span data-stu-id="e675a-115">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="e675a-116">操作說明：在 Windows Forms TextBox 控制項中選取文字</span><span class="sxs-lookup"><span data-stu-id="e675a-116">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="e675a-117">操作說明：在 Windows Forms TextBox 控制項中檢視多行</span><span class="sxs-lookup"><span data-stu-id="e675a-117">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="e675a-118">TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="e675a-118">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
