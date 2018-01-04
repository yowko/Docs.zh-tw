---
title: "Label 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Label
helpviewer_keywords:
- images [Windows Forms], displaying in labels
- labels
- Label control [Windows Forms], about Label control
ms.assetid: dcad7f44-11b7-4c55-b0c0-d984ade43d7d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f68642eb5f996722097976e042006afbf366ae39
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="label-control-overview-windows-forms"></a><span data-ttu-id="a6c3e-102">Label 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="a6c3e-102">Label Control Overview (Windows Forms)</span></span>
<span data-ttu-id="a6c3e-103">Windows Form<xref:System.Windows.Forms.Label>控制項用來顯示文字或影像，使用者無法編輯。</span><span class="sxs-lookup"><span data-stu-id="a6c3e-103">Windows Forms <xref:System.Windows.Forms.Label> controls are used to display text or images that cannot be edited by the user.</span></span> <span data-ttu-id="a6c3e-104">它們可用來識別表單的物件，提供特定控制項的描述按一下將執行動作，例如，或在執行階段事件或應用程式中的處理序的回應中顯示資訊。</span><span class="sxs-lookup"><span data-stu-id="a6c3e-104">They are used to identify objects on a form — to provide a description of what a certain control will do if clicked, for example, or to display information in response to a run-time event or process in your application.</span></span> <span data-ttu-id="a6c3e-105">例如，您可以使用標籤，加入文字方塊、 清單方塊、 下拉式方塊和等等的描述性標題。</span><span class="sxs-lookup"><span data-stu-id="a6c3e-105">For example, you can use labels to add descriptive captions to text boxes, list boxes, combo boxes, and so on.</span></span> <span data-ttu-id="a6c3e-106">您也可以撰寫程式碼以變更在執行階段顯示的標籤，以回應事件的文字。</span><span class="sxs-lookup"><span data-stu-id="a6c3e-106">You can also write code that changes the text displayed by a label in response to events at run time.</span></span> <span data-ttu-id="a6c3e-107">例如，如果您的應用程式在幾分鐘的時間來處理變更，您可以在標籤中顯示處理狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="a6c3e-107">For example, if your application takes a few minutes to process a change, you can display a processing-status message in a label.</span></span>  
  
## <a name="working-with-the-label-control"></a><span data-ttu-id="a6c3e-108">使用標籤控制項</span><span class="sxs-lookup"><span data-stu-id="a6c3e-108">Working with the Label Control</span></span>  
 <span data-ttu-id="a6c3e-109">因為<xref:System.Windows.Forms.Label>控制項無法接收焦點，它也可用來建立其他控制項的便捷鍵。</span><span class="sxs-lookup"><span data-stu-id="a6c3e-109">Because the <xref:System.Windows.Forms.Label> control cannot receive the focus, it can also be used to create access keys for other controls.</span></span> <span data-ttu-id="a6c3e-110">便捷鍵可讓使用者選取另一個控制項，藉由按下 ALT 鍵及存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="a6c3e-110">An access key allows a user to select the other control by pressing the ALT key with the access key.</span></span> <span data-ttu-id="a6c3e-111">如需詳細資訊，請參閱[建立存取金鑰的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)和[How to： 使用 Windows Form Label 控制項建立便捷鍵](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="a6c3e-111">For more information, see [Creating Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md) and [How to: Create Access Keys with Windows Forms Label Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md).</span></span>  
  
 <span data-ttu-id="a6c3e-112">在標籤中顯示的標題位於<xref:System.Windows.Forms.Label.Text%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a6c3e-112">The caption displayed in the label is contained in the <xref:System.Windows.Forms.Label.Text%2A> property.</span></span> <span data-ttu-id="a6c3e-113"><xref:System.Windows.Forms.Label.TextAlign%2A>屬性可讓您設定標籤內文字的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="a6c3e-113">The <xref:System.Windows.Forms.Label.TextAlign%2A> property allows you to set the alignment of the text within the label.</span></span> <span data-ttu-id="a6c3e-114">如需詳細資訊，請參閱[How to： 設定 Windows Form 控制項所顯示的文字](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)。</span><span class="sxs-lookup"><span data-stu-id="a6c3e-114">For more information, see [How to: Set the Text Displayed by a Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6c3e-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="a6c3e-115">See Also</span></span>  
 <xref:System.Windows.Forms.Label>  
 [<span data-ttu-id="a6c3e-116">操作說明：調整 Windows Forms Label 控制項大小以適合其內容</span><span class="sxs-lookup"><span data-stu-id="a6c3e-116">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)  
 [<span data-ttu-id="a6c3e-117">操作說明：使用 Windows Forms Label 控制項建立便捷鍵</span><span class="sxs-lookup"><span data-stu-id="a6c3e-117">How to: Create Access Keys with Windows Forms Label Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)
