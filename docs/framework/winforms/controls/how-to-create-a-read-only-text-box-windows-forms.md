---
title: 如何：建立唯讀文字方塊
description: 瞭解如何將可編輯的 Windows Forms 文字方塊轉換成隻讀 Windows Forms 文字方塊。
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 5baa7c66d5f16560a4ea23861d563b099592957f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619360"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="b6904-103">如何：建立唯讀文字方塊 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="b6904-103">How to: Create a Read-Only Text Box (Windows Forms)</span></span>

<span data-ttu-id="b6904-104">您可以將可編輯的 Windows Forms 文字方塊轉換成隻讀控制項。</span><span class="sxs-lookup"><span data-stu-id="b6904-104">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="b6904-105">例如，因為應用程式的狀態，文字方塊可能會顯示通常已編輯但目前可能不是的值。</span><span class="sxs-lookup"><span data-stu-id="b6904-105">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>

## <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="b6904-106">若要建立唯讀文字方塊</span><span class="sxs-lookup"><span data-stu-id="b6904-106">To create a read-only text box</span></span>

1. <span data-ttu-id="b6904-107">將 <xref:System.Windows.Forms.TextBox> 控制項的 <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> 屬性設為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="b6904-107">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="b6904-108">當屬性設定為時 `true` ，使用者仍然可以在文字方塊中滾動並反白顯示文字，而不允許變更。</span><span class="sxs-lookup"><span data-stu-id="b6904-108">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="b6904-109">**複製**命令在文字方塊中可正常運作，但**剪**下和**貼**上命令則不會。</span><span class="sxs-lookup"><span data-stu-id="b6904-109">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b6904-110"><xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>屬性只會影響執行時間的使用者互動。</span><span class="sxs-lookup"><span data-stu-id="b6904-110">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="b6904-111">您仍然可以藉由變更文字方塊的屬性，在執行時間以程式設計方式變更文字方塊內容 <xref:System.Windows.Forms.TextBox.Text%2A> 。</span><span class="sxs-lookup"><span data-stu-id="b6904-111">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6904-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6904-112">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="b6904-113">TextBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="b6904-113">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="b6904-114">如何：控制 Windows Forms TextBox 控制項的插入點</span><span class="sxs-lookup"><span data-stu-id="b6904-114">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="b6904-115">如何：使用 Windows Forms TextBox 控制項建立密碼文字方塊</span><span class="sxs-lookup"><span data-stu-id="b6904-115">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="b6904-116">操作說明：將引號放入字串中</span><span class="sxs-lookup"><span data-stu-id="b6904-116">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="b6904-117">如何：在 Windows Form TextBox 控制項中選取文字</span><span class="sxs-lookup"><span data-stu-id="b6904-117">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="b6904-118">如何：檢視 Windows Form TextBox 控制項中的多行</span><span class="sxs-lookup"><span data-stu-id="b6904-118">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="b6904-119">TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="b6904-119">TextBox Control</span></span>](textbox-control-windows-forms.md)
