---
title: 作法：設定輸入遮罩
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 06dee48765653ac7a659246cc3dfe865c795ca21
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949139"
---
# <a name="how-to-set-the-input-mask"></a><span data-ttu-id="18670-102">作法：設定輸入遮罩</span><span class="sxs-lookup"><span data-stu-id="18670-102">How to: Set the Input Mask</span></span>
<span data-ttu-id="18670-103">遮罩的文字方塊控制項是增強的文字方塊控制項, 可支援用來接受或拒絕使用者輸入的宣告式語法。</span><span class="sxs-lookup"><span data-stu-id="18670-103">The masked text box control is an enhanced text box control that supports a declarative syntax for accepting or rejecting user input.</span></span> <span data-ttu-id="18670-104">藉由設定 Mask 屬性, 您可以指定允許的使用者輸入, 而不需要在您的應用程式中撰寫任何自訂驗證邏輯。</span><span class="sxs-lookup"><span data-stu-id="18670-104">By setting the Mask property, you can specify the allowable user input without writing any custom validation logic in your application.</span></span> <span data-ttu-id="18670-105">如需詳細資訊, 請參閱<xref:System.Windows.Forms.MaskedTextBox>類別的「備註」一節。</span><span class="sxs-lookup"><span data-stu-id="18670-105">For more information, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox> class.</span></span>  
  
## <a name="setting-the-mask-property-manually"></a><span data-ttu-id="18670-106">手動設定 Mask 屬性</span><span class="sxs-lookup"><span data-stu-id="18670-106">Setting the Mask Property Manually</span></span>  
 <span data-ttu-id="18670-107">如果您熟悉 Mask 屬性所支援的字元, 您可以手動輸入。</span><span class="sxs-lookup"><span data-stu-id="18670-107">If you are familiar with the characters that the Mask property supports, you can enter it manually.</span></span> <span data-ttu-id="18670-108">如需 Mask 屬性支援的字元摘要, 請參閱<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>屬性的「備註」一節。</span><span class="sxs-lookup"><span data-stu-id="18670-108">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
### <a name="to-set-the-mask-property-manually"></a><span data-ttu-id="18670-109">手動設定 Mask 屬性</span><span class="sxs-lookup"><span data-stu-id="18670-109">To set the Mask property manually</span></span>  
  
1. <span data-ttu-id="18670-110">在**設計**視圖中, 選取<xref:System.Windows.Forms.MaskedTextBox>。</span><span class="sxs-lookup"><span data-stu-id="18670-110">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
2. <span data-ttu-id="18670-111">在 [**屬性**] 視窗中, <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>找出屬性。</span><span class="sxs-lookup"><span data-stu-id="18670-111">In the **Properties** window, locate the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
3. <span data-ttu-id="18670-112">輸入您想要的遮罩。</span><span class="sxs-lookup"><span data-stu-id="18670-112">Type the mask that you want.</span></span> <span data-ttu-id="18670-113">例如，輸入 `###`。</span><span class="sxs-lookup"><span data-stu-id="18670-113">For example, type `###`.</span></span>  
  
## <a name="using-the-input-mask-dialog-box"></a><span data-ttu-id="18670-114">使用輸入遮罩對話方塊</span><span class="sxs-lookup"><span data-stu-id="18670-114">Using the Input Mask Dialog Box</span></span>  
 <span data-ttu-id="18670-115">[輸入遮罩] 對話方塊會提供一些預先定義的輸入遮罩。</span><span class="sxs-lookup"><span data-stu-id="18670-115">The Input Mask dialog box provides some predefined input masks.</span></span> <span data-ttu-id="18670-116">您也可以變更預先定義的遮罩, 或手動輸入自己的遮罩。</span><span class="sxs-lookup"><span data-stu-id="18670-116">You can also change the predefined masks or enter your own mask manually.</span></span>  
  
### <a name="to-open-the-input-mask-dialog-box"></a><span data-ttu-id="18670-117">若要開啟輸入遮罩對話方塊</span><span class="sxs-lookup"><span data-stu-id="18670-117">To open the Input Mask dialog box</span></span>  
  
1. <span data-ttu-id="18670-118">在**設計**視圖中, 選取<xref:System.Windows.Forms.MaskedTextBox>。</span><span class="sxs-lookup"><span data-stu-id="18670-118">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
    1. <span data-ttu-id="18670-119">按一下智慧標籤以開啟 [ **MaskedTextBox**工作] 面板。</span><span class="sxs-lookup"><span data-stu-id="18670-119">Click the smart tag to open the **MaskedTextBox Tasks** panel.</span></span>  
  
    2. <span data-ttu-id="18670-120">按一下 [**設定遮罩**]。</span><span class="sxs-lookup"><span data-stu-id="18670-120">Click **Set Mask**.</span></span>  
  
     <span data-ttu-id="18670-121">\-或-</span><span class="sxs-lookup"><span data-stu-id="18670-121">\- or -</span></span>  
  
    1. <span data-ttu-id="18670-122">在 [**屬性**] 視窗中, <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>選取屬性。</span><span class="sxs-lookup"><span data-stu-id="18670-122">In the **Properties** window, select the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
    2. <span data-ttu-id="18670-123">按一下 [屬性值] 資料行中的省略號按鈕。</span><span class="sxs-lookup"><span data-stu-id="18670-123">Click the ellipsis button in the property value column.</span></span>  
  
     <span data-ttu-id="18670-124">[**輸入遮罩**] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="18670-124">The **Input Mask** dialog box appears.</span></span>  
  
### <a name="to-use-the-input-mask-dialog-box"></a><span data-ttu-id="18670-125">若要使用輸入遮罩對話方塊</span><span class="sxs-lookup"><span data-stu-id="18670-125">To use the Input Mask dialog box</span></span>  
  
1. <span data-ttu-id="18670-126">選擇性按一下清單中其中一個預先定義的遮罩。</span><span class="sxs-lookup"><span data-stu-id="18670-126">(Optional) Click one of the predefined masks in the list.</span></span>  
  
2. <span data-ttu-id="18670-127">選擇性在 [**遮罩**] 方塊中編輯預先定義的遮罩。</span><span class="sxs-lookup"><span data-stu-id="18670-127">(Optional) Edit the predefined mask in the **Mask** box.</span></span>  
  
3. <span data-ttu-id="18670-128">選擇性在 [**遮罩**] 方塊中輸入新的遮罩。</span><span class="sxs-lookup"><span data-stu-id="18670-128">(Optional) Type a new mask in the **Mask** box.</span></span> <span data-ttu-id="18670-129">也就是說, 您不需要使用其中一個預先定義的遮罩。</span><span class="sxs-lookup"><span data-stu-id="18670-129">That is, you do not have to use one of the predefined masks.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="18670-130">[預覽] 方塊會顯示使用者在中<xref:System.Windows.Forms.MaskedTextBox>看到的字元。</span><span class="sxs-lookup"><span data-stu-id="18670-130">The Preview box displays the characters that the user sees in the <xref:System.Windows.Forms.MaskedTextBox>.</span></span> <span data-ttu-id="18670-131">這些字元是協助使用者正確輸入資料的指南。</span><span class="sxs-lookup"><span data-stu-id="18670-131">These characters are a guide to help the user enter the data correctly.</span></span>  
  
4. <span data-ttu-id="18670-132">選取或清除 [**使用 ValidatingType** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="18670-132">Select or clear the **Use ValidatingType** check box.</span></span> <span data-ttu-id="18670-133">[**使用 ValidatingType** ] 核取方塊會指定是否使用資料類型來驗證使用者輸入的資料。</span><span class="sxs-lookup"><span data-stu-id="18670-133">The **Use ValidatingType** check box specifies whether a data type is used to verify the data input by the user.</span></span> <span data-ttu-id="18670-134">如需詳細資訊，請參閱 <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="18670-134">For more information, see the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property.</span></span>  
  
5. <span data-ttu-id="18670-135">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="18670-135">Click **OK**.</span></span>  
  
     <span data-ttu-id="18670-136">遮罩會在 [**屬性**] 視窗的 [**遮罩**] 屬性中輸入。</span><span class="sxs-lookup"><span data-stu-id="18670-136">The mask is entered in the **Mask** property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18670-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18670-137">See also</span></span>

- [<span data-ttu-id="18670-138">逐步解說：使用 MaskedTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="18670-138">Walkthrough: Working with the MaskedTextBox Control</span></span>](walkthrough-working-with-the-maskedtextbox-control.md)
