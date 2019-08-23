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
# <a name="how-to-set-the-input-mask"></a>作法：設定輸入遮罩
遮罩的文字方塊控制項是增強的文字方塊控制項, 可支援用來接受或拒絕使用者輸入的宣告式語法。 藉由設定 Mask 屬性, 您可以指定允許的使用者輸入, 而不需要在您的應用程式中撰寫任何自訂驗證邏輯。 如需詳細資訊, 請參閱<xref:System.Windows.Forms.MaskedTextBox>類別的「備註」一節。  
  
## <a name="setting-the-mask-property-manually"></a>手動設定 Mask 屬性  
 如果您熟悉 Mask 屬性所支援的字元, 您可以手動輸入。 如需 Mask 屬性支援的字元摘要, 請參閱<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>屬性的「備註」一節。  
  
### <a name="to-set-the-mask-property-manually"></a>手動設定 Mask 屬性  
  
1. 在**設計**視圖中, 選取<xref:System.Windows.Forms.MaskedTextBox>。  
  
2. 在 [**屬性**] 視窗中, <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>找出屬性。  
  
3. 輸入您想要的遮罩。 例如，輸入 `###`。  
  
## <a name="using-the-input-mask-dialog-box"></a>使用輸入遮罩對話方塊  
 [輸入遮罩] 對話方塊會提供一些預先定義的輸入遮罩。 您也可以變更預先定義的遮罩, 或手動輸入自己的遮罩。  
  
### <a name="to-open-the-input-mask-dialog-box"></a>若要開啟輸入遮罩對話方塊  
  
1. 在**設計**視圖中, 選取<xref:System.Windows.Forms.MaskedTextBox>。  
  
    1. 按一下智慧標籤以開啟 [ **MaskedTextBox**工作] 面板。  
  
    2. 按一下 [**設定遮罩**]。  
  
     \-或-  
  
    1. 在 [**屬性**] 視窗中, <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>選取屬性。  
  
    2. 按一下 [屬性值] 資料行中的省略號按鈕。  
  
     [**輸入遮罩**] 對話方塊隨即出現。  
  
### <a name="to-use-the-input-mask-dialog-box"></a>若要使用輸入遮罩對話方塊  
  
1. 選擇性按一下清單中其中一個預先定義的遮罩。  
  
2. 選擇性在 [**遮罩**] 方塊中編輯預先定義的遮罩。  
  
3. 選擇性在 [**遮罩**] 方塊中輸入新的遮罩。 也就是說, 您不需要使用其中一個預先定義的遮罩。  
  
    > [!NOTE]
    > [預覽] 方塊會顯示使用者在中<xref:System.Windows.Forms.MaskedTextBox>看到的字元。 這些字元是協助使用者正確輸入資料的指南。  
  
4. 選取或清除 [**使用 ValidatingType** ] 核取方塊。 [**使用 ValidatingType** ] 核取方塊會指定是否使用資料類型來驗證使用者輸入的資料。 如需詳細資訊，請參閱 <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> 屬性 (Property)。  
  
5. 按一下 [確定]。  
  
     遮罩會在 [**屬性**] 視窗的 [**遮罩**] 屬性中輸入。  
  
## <a name="see-also"></a>另請參閱

- [逐步解說：使用 MaskedTextBox 控制項](walkthrough-working-with-the-maskedtextbox-control.md)
