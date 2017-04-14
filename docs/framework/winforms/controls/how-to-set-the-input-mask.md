---
title: "如何：設定輸入遮罩 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "net.ComponentModel.MaskPropertyEditor"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "MaskedTextBox 控制項 [Windows Form]"
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：設定輸入遮罩
遮罩文字方塊控制是增強型方塊控制項，可支援接受或拒絕使用者輸入的宣告式語法。  您可以設定 \[Mask\] 屬性以指定可允許的使用者輸入，而不需在應用程式中編寫任何自訂的驗證邏輯。  如需詳細資訊，請參閱 <xref:System.Windows.Forms.MaskedTextBox> 類別中的＜備註＞一節。  
  
## 手動設定 Mask 屬性  
 如果您熟悉 Mask 屬性支援的字元，您可以手動輸入它。  如需 Mask 屬性支援的字元摘要，請參閱 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> 屬性的＜備註＞一節。  
  
#### 若要手動設定 Mask 屬性  
  
1.  在 \[**設計**\] 檢視中，選取 <xref:System.Windows.Forms.MaskedTextBox>。  
  
2.  在 \[**屬性**\] 視窗中，找出 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> 屬性。  
  
3.  輸入您要的遮罩。  例如，輸入 `###`。  
  
## 使用輸入遮罩對話方塊  
 \[輸入遮罩\] 對話方塊可提供一些預先定義的輸入遮罩。  您也可以變更預先定義的遮罩，或手動輸入您自己的遮罩。  
  
#### 若要開啟輸入遮罩對話方塊  
  
1.  在 \[**設計**\] 檢視中，選取 <xref:System.Windows.Forms.MaskedTextBox>。  
  
    1.  按一下智慧標籤以開啟 \[**MaskedTextBox 工作**\] 面板。  
  
    2.  按一下 \[**設定遮罩**\]。  
  
     \-或\-  
  
    1.  在 \[**屬性**\] 視窗中選取 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> 屬性。  
  
    2.  按一下屬性值資料行中的省略符號按鈕。  
  
     \[**輸入遮罩**\] 對話方塊隨即出現。  
  
#### 若要使用輸入遮罩對話方塊  
  
1.  \(選擇性\) 按一下清單中預先定義的遮罩。  
  
2.  \(選擇性\) 編輯 \[**遮罩**\] 方塊中預先定義的遮罩。  
  
3.  \(選擇性\) 在 \[**遮罩**\] 方塊中輸入新遮罩。  也就是說，您不必使用其中一個預先定義的遮罩。  
  
    > [!NOTE]
    >  \[預覽\] 方塊會顯示使用者在 <xref:System.Windows.Forms.MaskedTextBox> 中看到的字元。  這些字元是協助使用者正確輸入資料的指引。  
  
4.  選取或清除 \[**使用 ValidatingType**\] 核取方塊。  \[**使用 ValidatingType**\] 核取方塊會指定使用者是否會使用資料類型來驗證資料輸入。  如需詳細資訊，請參閱 <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> 屬性。  
  
5.  按一下 \[**確定**\]。  
  
     該遮罩隨即輸入至 \[**屬性**\] 視窗的 \[**遮罩**\] 屬性中。  
  
## 請參閱  
 [逐步解說：使用 MaskedTextBox 控制項](../../../../docs/framework/winforms/controls/walkthrough-working-with-the-maskedtextbox-control.md)