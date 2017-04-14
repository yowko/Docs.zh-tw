---
title: "如何：使用 Windows Form Label 控制項建立便捷鍵 | Microsoft Docs"
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
  - "便捷鍵, 為控制項建立"
  - "便捷鍵, Windows Form"
  - "控制項 [Windows Form], 便捷鍵"
  - "對話方塊控制項, 助憶鍵"
  - "鍵盤快速鍵, 為控制項建立"
  - "Label 控制項 [Windows Form], 建立便捷鍵"
  - "助憶鍵"
  - "助憶鍵, 加入至對話方塊控制項"
  - "UseMnemonic 屬性, Label 控制項"
  - "Windows Form 控制項, 便捷鍵"
ms.assetid: 5ee8f823-80be-4a4f-96a4-412671e2e306
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：使用 Windows Form Label 控制項建立便捷鍵
Windows Form <xref:System.Windows.Forms.Label> 控制項可用來定義其他控制項的便捷鍵 \(Access Key\)。  當您在 Label 控制項定義便捷鍵時，使用者可按下 ALT 鍵加上您指定的字元，此字元是用來將焦點移到定位順序中尾隨其後的控制項中。  由於標籤不會收到焦點，所以焦點會自動移到定位順序的下一個控制項。  您可使用此技術將便捷鍵指派給文字方塊、下拉式方塊、清單方塊和資料格。  
  
### 若要使用標籤將便捷鍵指派給控制項  
  
1.  請先繪製標籤，再繪製其他控制項。  
  
     \-或\-  
  
     以任何順序繪製控制項，並將標籤的 <xref:System.Windows.Forms.Control.TabIndex%2A> 屬性設定為小於其他控制項的內容。  
  
2.  將標籤的 <xref:System.Windows.Forms.Label.UseMnemonic%2A> 屬性設定為 `true`。  
  
3.  在標籤的 <xref:System.Windows.Forms.Label.Text%2A> 屬性中使用連字號 \(&\) 來指派標籤的便捷鍵。  如需詳細資訊，請參閱[建立 Windows Form 控制項的便捷鍵](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)。  
  
    > [!NOTE]
    >  您可能會想顯示標籤控制項中的連字號，而非使用它們來建立便捷鍵。  當您將 label 控制項繫結到資料錄集的欄位，而此欄位所包括的資料又有連字號時，便可能發生這種狀況。  若要顯示標籤控制項中的連字號，請將 <xref:System.Windows.Forms.Label.UseMnemonic%2A> 屬性設定為 `false`。  若要顯示連字號以及一個便捷鍵，請將 <xref:System.Windows.Forms.Label.UseMnemonic%2A> 屬性設定為 `true`，並指示含一個連字號 \(&\) 的便捷鍵以及連字號，以使用兩個連字號來顯示。  
  
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
  
## 請參閱  
 [如何：調整 Windows Form Label 控制項大小以適合其內容](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)   
 [Label 控制項概觀](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)   
 [Label 控制項](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)