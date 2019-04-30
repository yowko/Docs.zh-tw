---
title: Label 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- Label
helpviewer_keywords:
- images [Windows Forms], displaying in labels
- labels
- Label control [Windows Forms], about Label control
ms.assetid: dcad7f44-11b7-4c55-b0c0-d984ade43d7d
ms.openlocfilehash: cc38b0f3ded9e3c2a5a4146eb6bb474921d1e19f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012852"
---
# <a name="label-control-overview-windows-forms"></a><span data-ttu-id="a963b-102">Label 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="a963b-102">Label Control Overview (Windows Forms)</span></span>
<span data-ttu-id="a963b-103">Windows Form<xref:System.Windows.Forms.Label>控制項可用來顯示使用者無法編輯的映像或文字。</span><span class="sxs-lookup"><span data-stu-id="a963b-103">Windows Forms <xref:System.Windows.Forms.Label> controls are used to display text or images that cannot be edited by the user.</span></span> <span data-ttu-id="a963b-104">它們用來識別在表單上的物件，提供描述哪些特定的控制項將會執行動作，按一下，比方說，或在執行階段事件或在您的應用程式中的處理序的回應中顯示資訊。</span><span class="sxs-lookup"><span data-stu-id="a963b-104">They are used to identify objects on a form — to provide a description of what a certain control will do if clicked, for example, or to display information in response to a run-time event or process in your application.</span></span> <span data-ttu-id="a963b-105">例如，您可以使用標籤將描述性的原文字幕新增至文字方塊、 清單方塊、 下拉式方塊等等。</span><span class="sxs-lookup"><span data-stu-id="a963b-105">For example, you can use labels to add descriptive captions to text boxes, list boxes, combo boxes, and so on.</span></span> <span data-ttu-id="a963b-106">您也可以撰寫程式碼以變更在執行階段回應事件中的標籤所顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="a963b-106">You can also write code that changes the text displayed by a label in response to events at run time.</span></span> <span data-ttu-id="a963b-107">比方說，如果您的應用程式花幾分鐘的時間處理的變更，您就可以在標籤中顯示的處理狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="a963b-107">For example, if your application takes a few minutes to process a change, you can display a processing-status message in a label.</span></span>  
  
## <a name="working-with-the-label-control"></a><span data-ttu-id="a963b-108">使用標籤控制項</span><span class="sxs-lookup"><span data-stu-id="a963b-108">Working with the Label Control</span></span>  
 <span data-ttu-id="a963b-109">因為<xref:System.Windows.Forms.Label>控制項無法接收焦點，它也可用來建立其他控制項的便捷鍵。</span><span class="sxs-lookup"><span data-stu-id="a963b-109">Because the <xref:System.Windows.Forms.Label> control cannot receive the focus, it can also be used to create access keys for other controls.</span></span> <span data-ttu-id="a963b-110">便捷鍵可讓使用者選取另一個控制項，藉由按下 ALT 鍵以存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="a963b-110">An access key allows a user to select the other control by pressing the ALT key with the access key.</span></span> <span data-ttu-id="a963b-111">如需詳細資訊，請參閱 <<c0> [ 建立存取金鑰的 Windows Forms 控制項](how-to-create-access-keys-for-windows-forms-controls.md)和[How to:使用 Windows Forms Label 控制項建立便捷鍵](how-to-create-access-keys-with-windows-forms-label-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="a963b-111">For more information, see [Creating Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md) and [How to: Create Access Keys with Windows Forms Label Controls](how-to-create-access-keys-with-windows-forms-label-controls.md).</span></span>  
  
 <span data-ttu-id="a963b-112">在標籤中顯示的標題中包含<xref:System.Windows.Forms.Label.Text%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a963b-112">The caption displayed in the label is contained in the <xref:System.Windows.Forms.Label.Text%2A> property.</span></span> <span data-ttu-id="a963b-113"><xref:System.Windows.Forms.Label.TextAlign%2A>屬性可讓您設定在標籤內文字的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="a963b-113">The <xref:System.Windows.Forms.Label.TextAlign%2A> property allows you to set the alignment of the text within the label.</span></span> <span data-ttu-id="a963b-114">如需詳細資訊，請參閱[如何：設定所顯示之文字的 Windows Form 控制項](how-to-set-the-text-displayed-by-a-windows-forms-control.md)。</span><span class="sxs-lookup"><span data-stu-id="a963b-114">For more information, see [How to: Set the Text Displayed by a Windows Forms Control](how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a963b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a963b-115">See also</span></span>

- <xref:System.Windows.Forms.Label>
- [<span data-ttu-id="a963b-116">如何：調整大小以容納其內容的 Windows Form Label 控制項</span><span class="sxs-lookup"><span data-stu-id="a963b-116">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [<span data-ttu-id="a963b-117">如何：使用 Windows Forms Label 控制項建立便捷鍵</span><span class="sxs-lookup"><span data-stu-id="a963b-117">How to: Create Access Keys with Windows Forms Label Controls</span></span>](how-to-create-access-keys-with-windows-forms-label-controls.md)
