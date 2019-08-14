---
title: HOW TO：建立唯讀文字方塊 (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 18d2f5ed2530957487ac25c3eb6240f8bc50a938
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971948"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="de3ab-102">作法：建立唯讀文字方塊 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="de3ab-102">How to: Create a Read-Only Text Box (Windows Forms)</span></span>

<span data-ttu-id="de3ab-103">您可以將可編輯的 Windows Forms 文字方塊轉換成隻讀控制項。</span><span class="sxs-lookup"><span data-stu-id="de3ab-103">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="de3ab-104">例如, 因為應用程式的狀態, 文字方塊可能會顯示通常已編輯但目前可能不是的值。</span><span class="sxs-lookup"><span data-stu-id="de3ab-104">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>

## <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="de3ab-105">若要建立唯讀文字方塊</span><span class="sxs-lookup"><span data-stu-id="de3ab-105">To create a read-only text box</span></span>

1. <span data-ttu-id="de3ab-106">將控制項的<xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>屬性設為`true`。 <xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="de3ab-106">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="de3ab-107">當屬性設定為`true`時, 使用者仍然可以在文字方塊中滾動並反白顯示文字, 而不允許變更。</span><span class="sxs-lookup"><span data-stu-id="de3ab-107">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="de3ab-108">**複製**命令在文字方塊中可正常運作, 但**剪**下和**貼**上命令則不會。</span><span class="sxs-lookup"><span data-stu-id="de3ab-108">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>

    > [!NOTE]
    > <span data-ttu-id="de3ab-109">屬性<xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>只會影響執行時間的使用者互動。</span><span class="sxs-lookup"><span data-stu-id="de3ab-109">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="de3ab-110">您仍然可以藉由變更文字方塊的<xref:System.Windows.Forms.TextBox.Text%2A>屬性, 在執行時間以程式設計方式變更文字方塊內容。</span><span class="sxs-lookup"><span data-stu-id="de3ab-110">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>

## <a name="see-also"></a><span data-ttu-id="de3ab-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de3ab-111">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="de3ab-112">TextBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="de3ab-112">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="de3ab-113">如何：控制 Windows Forms TextBox 控制項中的插入點</span><span class="sxs-lookup"><span data-stu-id="de3ab-113">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="de3ab-114">如何：使用 Windows Forms TextBox 控制項建立密碼文字方塊</span><span class="sxs-lookup"><span data-stu-id="de3ab-114">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="de3ab-115">如何：將引號放入字串中</span><span class="sxs-lookup"><span data-stu-id="de3ab-115">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="de3ab-116">如何：選取 Windows Forms TextBox 控制項中的文字</span><span class="sxs-lookup"><span data-stu-id="de3ab-116">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="de3ab-117">如何：在 Windows Forms TextBox 控制項中查看多行</span><span class="sxs-lookup"><span data-stu-id="de3ab-117">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="de3ab-118">TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="de3ab-118">TextBox Control</span></span>](textbox-control-windows-forms.md)
