---
title: "如何：為 Windows Form RichTextBox 控制項設定字型屬性 | Microsoft Docs"
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
  - "字型, 變更 RichTextBox 控制項中的屬性"
  - "格式化 [Windows Form]"
  - "RichTextBox 控制項 [Windows Form], 設定字型屬性"
  - "RTF 檔案, 在 RichTextBox 制項中格式化"
  - "文字 [Windows Form]"
  - "文字方塊, 格式化文字"
ms.assetid: 2bc23ddb-0529-4489-a1a2-ad253cb43f9a
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：為 Windows Form RichTextBox 控制項設定字型屬性
Windows Form <xref:System.Windows.Forms.RichTextBox> 控制項有各種選項可格式化其所顯示的文字。  您可使用 <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> 屬性將選取的字元以粗體、加上底線或斜體顯示。  您也可使用這個屬性 \(Property\) 來變更選取字元的大小和字樣。  <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> 屬性可讓您變更選取字元的色彩。  
  
### 若要變更字元的外觀  
  
1.  將 <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> 屬性設定至適當字型。  
  
     若要讓使用者能夠在應用程式中設定字型系列、大小和字樣，您通常會使用 <xref:System.Windows.Forms.FontDialog> 元件。  如需概觀說明，請參閱[FontDialog 元件概觀](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md)。  
  
2.  將 <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> 屬性設定至適當色彩。  
  
     若要讓使用者能夠在應用程式中設定色彩，您通常會使用 <xref:System.Windows.Forms.ColorDialog> 元件。  如需概觀說明，請參閱[ColorDialog 元件概觀](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md)。  
  
    ```vb  
    RichTextBox1.SelectionFont = New Font("Tahoma", 12, FontStyle.Bold)  
    RichTextBox1.SelectionColor = System.Drawing.Color.Red  
  
    ```  
  
    ```csharp  
    richTextBox1.SelectionFont = new Font("Tahoma", 12, FontStyle.Bold);  
    richTextBox1.SelectionColor = System.Drawing.Color.Red;  
  
    ```  
  
    ```cpp  
    richTextBox1->SelectionFont =  
       gcnew System::Drawing::Font("Tahoma", 12, FontStyle::Bold);  
    richTextBox1->SelectionColor = System::Drawing::Color::Red;  
    ```  
  
    > [!NOTE]
    >  這些屬性只會影響選取的文字，或是如果未選取文字，就會影響在插入點目前位置輸入的文字。  如需利用程式設計方式選取文字的詳細資訊，請參閱 [TextBoxBase.Select 方法](frlrfSystemWindowsFormsTextBoxBaseClassSelectTopic)。  
  
## 請參閱  
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox 控制項](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)