---
title: HOW TO：設定輸入的遮罩
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 53bb8d0e301f83c25ab292b1cb6324dd5f21f100
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702356"
---
# <a name="how-to-set-the-input-mask"></a><span data-ttu-id="f7497-102">HOW TO：設定輸入的遮罩</span><span class="sxs-lookup"><span data-stu-id="f7497-102">How to: Set the Input Mask</span></span>
<span data-ttu-id="f7497-103">遮罩的文字方塊控制項是支援的宣告式語法，以接受或拒絕使用者輸入增強的文字方塊控制項。</span><span class="sxs-lookup"><span data-stu-id="f7497-103">The masked text box control is an enhanced text box control that supports a declarative syntax for accepting or rejecting user input.</span></span> <span data-ttu-id="f7497-104">藉由設定 [遮罩] 屬性，您可以指定允許使用者輸入，而不需要撰寫任何自訂驗證邏輯應用程式中。</span><span class="sxs-lookup"><span data-stu-id="f7497-104">By setting the Mask property, you can specify the allowable user input without writing any custom validation logic in your application.</span></span> <span data-ttu-id="f7497-105">如需詳細資訊，請參閱的 < 備註 > 一節<xref:System.Windows.Forms.MaskedTextBox>類別。</span><span class="sxs-lookup"><span data-stu-id="f7497-105">For more information, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox> class.</span></span>  
  
## <a name="setting-the-mask-property-manually"></a><span data-ttu-id="f7497-106">手動設定遮罩屬性</span><span class="sxs-lookup"><span data-stu-id="f7497-106">Setting the Mask Property Manually</span></span>  
 <span data-ttu-id="f7497-107">如果您已熟悉使用遮罩屬性支援的字元，您可以手動輸入。</span><span class="sxs-lookup"><span data-stu-id="f7497-107">If you are familiar with the characters that the Mask property supports, you can enter it manually.</span></span> <span data-ttu-id="f7497-108">如需摘要的遮罩屬性支援的字元，請參閱 < 備註 > 一節<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="f7497-108">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
#### <a name="to-set-the-mask-property-manually"></a><span data-ttu-id="f7497-109">若要手動設定遮罩屬性</span><span class="sxs-lookup"><span data-stu-id="f7497-109">To set the Mask property manually</span></span>  
  
1.  <span data-ttu-id="f7497-110">在 **設計**檢視中，選取<xref:System.Windows.Forms.MaskedTextBox>。</span><span class="sxs-lookup"><span data-stu-id="f7497-110">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
2.  <span data-ttu-id="f7497-111">在 [**屬性**] 視窗中，找出<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="f7497-111">In the **Properties** window, locate the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
3.  <span data-ttu-id="f7497-112">輸入您想要的遮罩。</span><span class="sxs-lookup"><span data-stu-id="f7497-112">Type the mask that you want.</span></span> <span data-ttu-id="f7497-113">例如，輸入 `###`。</span><span class="sxs-lookup"><span data-stu-id="f7497-113">For example, type `###`.</span></span>  
  
## <a name="using-the-input-mask-dialog-box"></a><span data-ttu-id="f7497-114">使用 [輸入的遮罩] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="f7497-114">Using the Input Mask Dialog Box</span></span>  
 <span data-ttu-id="f7497-115">[輸入遮罩] 對話方塊中提供一些預先定義的輸入的遮罩。</span><span class="sxs-lookup"><span data-stu-id="f7497-115">The Input Mask dialog box provides some predefined input masks.</span></span> <span data-ttu-id="f7497-116">您也可以變更預先定義的遮罩，或以手動方式輸入您自己的遮罩。</span><span class="sxs-lookup"><span data-stu-id="f7497-116">You can also change the predefined masks or enter your own mask manually.</span></span>  
  
#### <a name="to-open-the-input-mask-dialog-box"></a><span data-ttu-id="f7497-117">若要開啟 [輸入遮罩] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="f7497-117">To open the Input Mask dialog box</span></span>  
  
1.  <span data-ttu-id="f7497-118">在 **設計**檢視中，選取<xref:System.Windows.Forms.MaskedTextBox>。</span><span class="sxs-lookup"><span data-stu-id="f7497-118">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
    1.  <span data-ttu-id="f7497-119">按一下以開啟的智慧標籤**MaskedTextBox 工作**面板。</span><span class="sxs-lookup"><span data-stu-id="f7497-119">Click the smart tag to open the **MaskedTextBox Tasks** panel.</span></span>  
  
    2.  <span data-ttu-id="f7497-120">按一下 **設定遮罩**。</span><span class="sxs-lookup"><span data-stu-id="f7497-120">Click **Set Mask**.</span></span>  
  
     <span data-ttu-id="f7497-121">\-或-</span><span class="sxs-lookup"><span data-stu-id="f7497-121">\- or -</span></span>  
  
    1.  <span data-ttu-id="f7497-122">在 **屬性**視窗中，選取<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="f7497-122">In the **Properties** window, select the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
    2.  <span data-ttu-id="f7497-123">按一下省略符號按鈕，在屬性資料行。</span><span class="sxs-lookup"><span data-stu-id="f7497-123">Click the ellipsis button in the property value column.</span></span>  
  
     <span data-ttu-id="f7497-124">**輸入遮罩** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="f7497-124">The **Input Mask** dialog box appears.</span></span>  
  
#### <a name="to-use-the-input-mask-dialog-box"></a><span data-ttu-id="f7497-125">若要使用 [輸入遮罩] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="f7497-125">To use the Input Mask dialog box</span></span>  
  
1.  <span data-ttu-id="f7497-126">（選擇性）按一下其中一個預先定義的遮罩，在清單中。</span><span class="sxs-lookup"><span data-stu-id="f7497-126">(Optional) Click one of the predefined masks in the list.</span></span>  
  
2.  <span data-ttu-id="f7497-127">（選擇性）編輯中的預先定義的遮罩**遮罩** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="f7497-127">(Optional) Edit the predefined mask in the **Mask** box.</span></span>  
  
3.  <span data-ttu-id="f7497-128">（選擇性）輸入新遮罩**遮罩** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="f7497-128">(Optional) Type a new mask in the **Mask** box.</span></span> <span data-ttu-id="f7497-129">也就是說，您不必使用其中一個預先定義的遮罩。</span><span class="sxs-lookup"><span data-stu-id="f7497-129">That is, you do not have to use one of the predefined masks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f7497-130">[預覽] 方塊會顯示在中的使用者會看到的字元<xref:System.Windows.Forms.MaskedTextBox>。</span><span class="sxs-lookup"><span data-stu-id="f7497-130">The Preview box displays the characters that the user sees in the <xref:System.Windows.Forms.MaskedTextBox>.</span></span> <span data-ttu-id="f7497-131">這些字元是幫助使用者輸入正確的資料。</span><span class="sxs-lookup"><span data-stu-id="f7497-131">These characters are a guide to help the user enter the data correctly.</span></span>  
  
4.  <span data-ttu-id="f7497-132">選取或清除**使用 ValidatingType**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f7497-132">Select or clear the **Use ValidatingType** check box.</span></span> <span data-ttu-id="f7497-133">**使用 ValidatingType**核取方塊可讓您指定的資料類型是否用來驗證資料輸入的使用者。</span><span class="sxs-lookup"><span data-stu-id="f7497-133">The **Use ValidatingType** check box specifies whether a data type is used to verify the data input by the user.</span></span> <span data-ttu-id="f7497-134">如需詳細資訊，請參閱 <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="f7497-134">For more information, see the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property.</span></span>  
  
5.  <span data-ttu-id="f7497-135">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="f7497-135">Click **OK**.</span></span>  
  
     <span data-ttu-id="f7497-136">在 輸入遮罩**遮罩**中的屬性**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="f7497-136">The mask is entered in the **Mask** property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7497-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7497-137">See also</span></span>
- [<span data-ttu-id="f7497-138">逐步解說：使用 MaskedTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="f7497-138">Walkthrough: Working with the MaskedTextBox Control</span></span>](walkthrough-working-with-the-maskedtextbox-control.md)
