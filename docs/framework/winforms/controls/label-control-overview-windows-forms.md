---
title: Label 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- Label
helpviewer_keywords:
- images [Windows Forms], displaying in labels
- labels
- Label control [Windows Forms], about Label control
ms.assetid: dcad7f44-11b7-4c55-b0c0-d984ade43d7d
ms.openlocfilehash: 1ca14553c7cb51d2b7a329950aeaec4c0439762a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745280"
---
# <a name="label-control-overview-windows-forms"></a><span data-ttu-id="84522-102">Label 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="84522-102">Label Control Overview (Windows Forms)</span></span>
<span data-ttu-id="84522-103">Windows Forms <xref:System.Windows.Forms.Label> 控制項是用來顯示使用者無法編輯的文字或影像。</span><span class="sxs-lookup"><span data-stu-id="84522-103">Windows Forms <xref:System.Windows.Forms.Label> controls are used to display text or images that cannot be edited by the user.</span></span> <span data-ttu-id="84522-104">它們可用來識別表單上的物件，以提供特定控制項在按一下時會執行的動作，例如，或顯示資訊以回應應用程式中的運行時間事件或進程。</span><span class="sxs-lookup"><span data-stu-id="84522-104">They are used to identify objects on a form — to provide a description of what a certain control will do if clicked, for example, or to display information in response to a run-time event or process in your application.</span></span> <span data-ttu-id="84522-105">例如，您可以使用標籤，將描述性標題加入文字方塊、清單方塊、下拉式方塊等。</span><span class="sxs-lookup"><span data-stu-id="84522-105">For example, you can use labels to add descriptive captions to text boxes, list boxes, combo boxes, and so on.</span></span> <span data-ttu-id="84522-106">您也可以撰寫程式碼來變更標籤所顯示的文字，以回應執行時間的事件。</span><span class="sxs-lookup"><span data-stu-id="84522-106">You can also write code that changes the text displayed by a label in response to events at run time.</span></span> <span data-ttu-id="84522-107">例如，如果您的應用程式需要幾分鐘的時間來處理變更，您可以在標籤中顯示處理狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="84522-107">For example, if your application takes a few minutes to process a change, you can display a processing-status message in a label.</span></span>  
  
## <a name="working-with-the-label-control"></a><span data-ttu-id="84522-108">使用標籤控制項</span><span class="sxs-lookup"><span data-stu-id="84522-108">Working with the Label Control</span></span>  
 <span data-ttu-id="84522-109">因為 <xref:System.Windows.Forms.Label> 控制項無法接收焦點，所以它也可以用來建立其他控制項的存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="84522-109">Because the <xref:System.Windows.Forms.Label> control cannot receive the focus, it can also be used to create access keys for other controls.</span></span> <span data-ttu-id="84522-110">存取金鑰可讓使用者按下 ALT 鍵與存取金鑰來選取另一個控制項。</span><span class="sxs-lookup"><span data-stu-id="84522-110">An access key allows a user to select the other control by pressing the ALT key with the access key.</span></span> <span data-ttu-id="84522-111">如需詳細資訊，請參閱[建立 Windows Forms 控制項的存取金鑰](how-to-create-access-keys-for-windows-forms-controls.md)和[如何：使用 Windows Forms 標籤控制項建立便捷鍵](how-to-create-access-keys-with-windows-forms-label-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="84522-111">For more information, see [Creating Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md) and [How to: Create Access Keys with Windows Forms Label Controls](how-to-create-access-keys-with-windows-forms-label-controls.md).</span></span>  
  
 <span data-ttu-id="84522-112">標籤中顯示的標題會包含在 [<xref:System.Windows.Forms.Label.Text%2A>] 屬性中。</span><span class="sxs-lookup"><span data-stu-id="84522-112">The caption displayed in the label is contained in the <xref:System.Windows.Forms.Label.Text%2A> property.</span></span> <span data-ttu-id="84522-113"><xref:System.Windows.Forms.Label.TextAlign%2A> 屬性可讓您設定標籤中文字的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="84522-113">The <xref:System.Windows.Forms.Label.TextAlign%2A> property allows you to set the alignment of the text within the label.</span></span> <span data-ttu-id="84522-114">如需詳細資訊，請參閱[如何：設定 Windows Forms 控制項所顯示的文字](how-to-set-the-text-displayed-by-a-windows-forms-control.md)。</span><span class="sxs-lookup"><span data-stu-id="84522-114">For more information, see [How to: Set the Text Displayed by a Windows Forms Control](how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84522-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84522-115">See also</span></span>

- <xref:System.Windows.Forms.Label>
- [<span data-ttu-id="84522-116">操作說明：調整 Windows Forms Label 控制項大小以適合其內容</span><span class="sxs-lookup"><span data-stu-id="84522-116">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [<span data-ttu-id="84522-117">操作說明：使用 Windows Forms Label 控制項建立便捷鍵</span><span class="sxs-lookup"><span data-stu-id="84522-117">How to: Create Access Keys with Windows Forms Label Controls</span></span>](how-to-create-access-keys-with-windows-forms-label-controls.md)
