---
title: 建立具有標籤控制項的存取金鑰
ms.date: 03/30/2017
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
ms.openlocfilehash: 800afc03e71435e2721456b93bb9704af01f714a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731045"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a><span data-ttu-id="2fdbe-102">如何：使用 Windows Form Label 控制項建立便捷鍵</span><span class="sxs-lookup"><span data-stu-id="2fdbe-102">How to: Create Access Keys with Windows Forms Label Controls</span></span>
<span data-ttu-id="2fdbe-103">Windows Forms <xref:System.Windows.Forms.Label> 控制項可以用來定義其他控制項的存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="2fdbe-103">Windows Forms <xref:System.Windows.Forms.Label> controls can be used to define access keys for other controls.</span></span> <span data-ttu-id="2fdbe-104">當您在 [標籤] 控制項中定義存取金鑰時，使用者可以按下 ALT 鍵加上您指定的字元，將焦點移至定位順序中後面的控制項。</span><span class="sxs-lookup"><span data-stu-id="2fdbe-104">When you define an access key in a label control, the user can press the ALT key plus the character you designate to move the focus to the control that follows it in the tab order.</span></span> <span data-ttu-id="2fdbe-105">因為標籤無法接收焦點，所以焦點會自動移至定位順序中的下一個控制項。</span><span class="sxs-lookup"><span data-stu-id="2fdbe-105">Because labels cannot receive focus, focus automatically moves to the next control in the tab order.</span></span> <span data-ttu-id="2fdbe-106">使用這項技術可將存取金鑰指派給文字方塊、下拉式方塊、清單方塊和資料格。</span><span class="sxs-lookup"><span data-stu-id="2fdbe-106">Use this technique to assign access keys to text boxes, combo boxes, list boxes, and data grids.</span></span>  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a><span data-ttu-id="2fdbe-107">若要將存取金鑰指派給具有標籤的控制項</span><span class="sxs-lookup"><span data-stu-id="2fdbe-107">To assign an access key to a control with a label</span></span>  
  
1. <span data-ttu-id="2fdbe-108">先繪製標籤，然後再繪製另一個控制項。</span><span class="sxs-lookup"><span data-stu-id="2fdbe-108">Draw the label first, and then draw the other control.</span></span>  
  
     <span data-ttu-id="2fdbe-109">-或-</span><span class="sxs-lookup"><span data-stu-id="2fdbe-109">-or-</span></span>  
  
     <span data-ttu-id="2fdbe-110">以任何順序繪製控制項，並將標籤的 <xref:System.Windows.Forms.Control.TabIndex%2A> 屬性設定為小於另一個控制項。</span><span class="sxs-lookup"><span data-stu-id="2fdbe-110">Draw the controls in any order and set the <xref:System.Windows.Forms.Control.TabIndex%2A> property of the label to one less than the other control.</span></span>  
  
2. <span data-ttu-id="2fdbe-111">將標籤的 [<xref:System.Windows.Forms.Label.UseMnemonic%2A>] 屬性設定為 [`true`]。</span><span class="sxs-lookup"><span data-stu-id="2fdbe-111">Set the label's <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`.</span></span>  
  
3. <span data-ttu-id="2fdbe-112">在標籤的 <xref:System.Windows.Forms.Label.Text%2A> 屬性中使用連字號（&），以指派標籤的存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="2fdbe-112">Use an ampersand (&) in the label's <xref:System.Windows.Forms.Label.Text%2A> property to assign the access key for the label.</span></span> <span data-ttu-id="2fdbe-113">如需詳細資訊，請參閱[建立 Windows Forms 控制項的存取金鑰](how-to-create-access-keys-for-windows-forms-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="2fdbe-113">For more information, see [Creating Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2fdbe-114">您可能想要在標籤控制項中顯示符號，而不是使用它們來建立存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="2fdbe-114">You may want to display ampersands in a label control, rather than use them to create access keys.</span></span> <span data-ttu-id="2fdbe-115">如果您將標籤控制項系結至資料集記錄集中的欄位（其中包含了符號），就可能發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="2fdbe-115">This may occur if you bind a label control to a field in a recordset where the data includes ampersands.</span></span> <span data-ttu-id="2fdbe-116">若要在標籤控制項中顯示符號，請將 [<xref:System.Windows.Forms.Label.UseMnemonic%2A>] 屬性設定為 [`false`]。</span><span class="sxs-lookup"><span data-stu-id="2fdbe-116">To display ampersands in a label control, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `false`.</span></span> <span data-ttu-id="2fdbe-117">如果您想要顯示符號，而且也有存取金鑰，請將 <xref:System.Windows.Forms.Label.UseMnemonic%2A> 屬性設定為 `true`，並使用一個連字號（&）和連字號來顯示具有兩個符號的存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="2fdbe-117">If you wish to display ampersands and also have an access key, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true` and indicate the access key with one ampersand (&) and the ampersand to display with two ampersands.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2fdbe-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="2fdbe-118">See also</span></span>

- [<span data-ttu-id="2fdbe-119">操作說明：調整 Windows Forms Label 控制項大小以適合其內容</span><span class="sxs-lookup"><span data-stu-id="2fdbe-119">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [<span data-ttu-id="2fdbe-120">Label 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="2fdbe-120">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="2fdbe-121">Label 控制項</span><span class="sxs-lookup"><span data-stu-id="2fdbe-121">Label Control</span></span>](label-control-windows-forms.md)
