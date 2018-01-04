---
title: "如何：使用 Windows Form Label 控制項建立便捷鍵"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- Label control [Windows Forms], creating access keys
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- Windows Forms controls, access keys
- UseMnemonic property [Windows Forms], Label control
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
ms.assetid: 5ee8f823-80be-4a4f-96a4-412671e2e306
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a856090a76f484c21c1d9982d67e9fdf21e8451
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a><span data-ttu-id="f8bd4-102">如何：使用 Windows Form Label 控制項建立便捷鍵</span><span class="sxs-lookup"><span data-stu-id="f8bd4-102">How to: Create Access Keys with Windows Forms Label Controls</span></span>
<span data-ttu-id="f8bd4-103">Windows Form<xref:System.Windows.Forms.Label>控制項可以用來定義其他控制項的便捷鍵。</span><span class="sxs-lookup"><span data-stu-id="f8bd4-103">Windows Forms <xref:System.Windows.Forms.Label> controls can be used to define access keys for other controls.</span></span> <span data-ttu-id="f8bd4-104">當您定義便捷鍵的標籤控制項中時，使用者可以按 ALT 鍵加上您將焦點移至定位順序中在它後面的控制項，將指定的字元。</span><span class="sxs-lookup"><span data-stu-id="f8bd4-104">When you define an access key in a label control, the user can press the ALT key plus the character you designate to move the focus to the control that follows it in the tab order.</span></span> <span data-ttu-id="f8bd4-105">因為標籤不會收到焦點，焦點會自動移到定位順序中的下一個控制項。</span><span class="sxs-lookup"><span data-stu-id="f8bd4-105">Because labels cannot receive focus, focus automatically moves to the next control in the tab order.</span></span> <span data-ttu-id="f8bd4-106">使用這項技術，將文字方塊、 下拉式方塊、 清單方塊和資料格的存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="f8bd4-106">Use this technique to assign access keys to text boxes, combo boxes, list boxes, and data grids.</span></span>  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a><span data-ttu-id="f8bd4-107">若要指派給具有標籤控制項的便捷鍵</span><span class="sxs-lookup"><span data-stu-id="f8bd4-107">To assign an access key to a control with a label</span></span>  
  
1.  <span data-ttu-id="f8bd4-108">首先，繪製在標籤，然後繪製另一個控制項。</span><span class="sxs-lookup"><span data-stu-id="f8bd4-108">Draw the label first, and then draw the other control.</span></span>  
  
     <span data-ttu-id="f8bd4-109">-或-</span><span class="sxs-lookup"><span data-stu-id="f8bd4-109">-or-</span></span>  
  
     <span data-ttu-id="f8bd4-110">繪製控制項以任何順序，並設定<xref:System.Windows.Forms.Control.TabIndex%2A>屬性的其中一個小於另一個控制項的標籤。</span><span class="sxs-lookup"><span data-stu-id="f8bd4-110">Draw the controls in any order and set the <xref:System.Windows.Forms.Control.TabIndex%2A> property of the label to one less than the other control.</span></span>  
  
2.  <span data-ttu-id="f8bd4-111">設定標籤的<xref:System.Windows.Forms.Label.UseMnemonic%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="f8bd4-111">Set the label's <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`.</span></span>  
  
3.  <span data-ttu-id="f8bd4-112">使用連字號 (&) 中的標籤<xref:System.Windows.Forms.Label.Text%2A>屬性來指定標籤便捷鍵。</span><span class="sxs-lookup"><span data-stu-id="f8bd4-112">Use an ampersand (&) in the label's <xref:System.Windows.Forms.Label.Text%2A> property to assign the access key for the label.</span></span> <span data-ttu-id="f8bd4-113">如需詳細資訊，請參閱[建立存取金鑰的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="f8bd4-113">For more information, see [Creating Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8bd4-114">您可能想要顯示的標籤控制項中的連字號，而不是使用它們來建立便捷鍵。</span><span class="sxs-lookup"><span data-stu-id="f8bd4-114">You may want to display ampersands in a label control, rather than use them to create access keys.</span></span> <span data-ttu-id="f8bd4-115">如果您將標籤控制項繫結至資料錄集中的資料，包括連字號的欄位，也可能會發生。</span><span class="sxs-lookup"><span data-stu-id="f8bd4-115">This may occur if you bind a label control to a field in a recordset where the data includes ampersands.</span></span> <span data-ttu-id="f8bd4-116">若要顯示的標籤控制項中的連字號，將<xref:System.Windows.Forms.Label.UseMnemonic%2A>屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="f8bd4-116">To display ampersands in a label control, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `false`.</span></span> <span data-ttu-id="f8bd4-117">如果您想要顯示連字號和也都有便捷鍵時，設定<xref:System.Windows.Forms.Label.UseMnemonic%2A>屬性`true`，表示一個連字號 ' 的存取金鑰 (&) 和連字號來顯示具有兩個連字號。</span><span class="sxs-lookup"><span data-stu-id="f8bd4-117">If you wish to display ampersands and also have an access key, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true` and indicate the access key with one ampersand (&) and the ampersand to display with two ampersands.</span></span>  
  
    ```vb  
    Label1.UseMnemonic = True  
    Label1.Text = "&Print"  
    Label2.UseMnemonic = True  
    Label2.Text = "&Copy && Paste"  
    ```  
  
    ```csharp  
    label1.UseMnemonic = true;  
    label1.Text = "&Print";  
    label2.UseMnemonic = true;  
    label2.Text = "&Copy && Paste";  
    ```  
  
    ```cpp  
    label1->UseMnemonic = true;  
    label1->Text = "&Print";  
    label2->UseMnemonic = true;  
    label2->Text = "&Copy && Paste";  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f8bd4-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="f8bd4-118">See Also</span></span>  
 [<span data-ttu-id="f8bd4-119">操作說明：調整 Windows Forms Label 控制項大小以適合其內容</span><span class="sxs-lookup"><span data-stu-id="f8bd4-119">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)  
 [<span data-ttu-id="f8bd4-120">Label 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="f8bd4-120">Label Control Overview</span></span>](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [<span data-ttu-id="f8bd4-121">Label 控制項</span><span class="sxs-lookup"><span data-stu-id="f8bd4-121">Label Control</span></span>](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
