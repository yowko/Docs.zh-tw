---
title: "如何：使用 Windows Form RichTextBox 控制項設定縮排、首行縮排和分項段落 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - ".rtf 檔案, 在 RichTextBox 制項中格式化"
  - "範例 [Windows Form], 文字方塊"
  - "RichTextBox 控制項 [Windows Form], 設定縮排和項目符號"
  - "RTF 檔案, 在 RichTextBox 制項中格式化"
  - "文字方塊, 項目符號"
  - "文字方塊, 設定縮排"
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：使用 Windows Form RichTextBox 控制項設定縮排、首行縮排和分項段落
Windows Form <xref:System.Windows.Forms.RichTextBox> 控制項有各種選項可格式化其所顯示的文字。  您可藉由設定 <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> 屬性來將選取的段落格式化為項目符號清單。  您也可使用 <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>、<xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> 和 <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> 屬性來相對於控制項的左右邊緣和其他行文字的左邊緣，設定段落的縮排。  
  
### 若要將段落格式化為項目符號清單  
  
1.  將 <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> 屬性設為 `true`。  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### 若要縮排段落  
  
1.  將 <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> 屬性設定為表示控制項左邊緣和文字左邊緣之間像素距離的整數。  
  
2.  將 <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> 屬性設定為表示段落第一行文字左邊緣和同一段落中後續幾行左邊緣之間像素距離的整數。  <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> 屬性的值只會套用至段落中在第一行之下換行的文字。  
  
3.  將 <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> 屬性設定為表示控制項右邊緣和文字右邊緣之間像素距離的整數。  
  
    ```vb  
    RichTextBox1.SelectionIndent = 8  
    RichTextBox1.SelectionHangingIndent = 3  
    RichTextBox1.SelectionRightIndent = 12  
  
    ```  
  
    ```csharp  
    richTextBox1.SelectionIndent = 8;  
    richTextBox1.SelectionHangingIndent = 3;  
    richTextBox1.SelectionRightIndent = 12;  
  
    ```  
  
    ```cpp  
    richTextBox1->SelectionIndent = 8;  
    richTextBox1->SelectionHangingIndent = 3;  
    richTextBox1->SelectionRightIndent = 12;  
    ```  
  
    > [!NOTE]
    >  上述所有屬性都會影響任何包含選取文字的段落，而且也會影響在目前插入點之後輸入的文字。  例如，當使用者選取段落中的一個字並接著調整縮排時，新的設定值會套用至包含這個字的整個段落，以及在選取段落之後輸入的任何後續段落。  如需利用程式設計方式選取文字的詳細資訊，請參閱 [TextBoxBase.Select 方法](frlrfSystemWindowsFormsTextBoxBaseClassSelectTopic)。  
  
## 請參閱  
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox 控制項](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)