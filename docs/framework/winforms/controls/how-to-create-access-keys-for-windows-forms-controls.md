---
title: "如何：建立 Windows Form 控制項的便捷鍵 | Microsoft Docs"
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
  - "ALT 鍵"
  - "快速鍵中的連字號 (&) 字元"
  - "Button 控制項 [Windows Form], 便捷鍵"
  - "控制項 [Windows Form], 便捷鍵"
  - "對話方塊控制項, 助憶鍵"
  - "範例 [Windows Form], 控制項"
  - "鍵盤快速鍵, 為控制項建立"
  - "助憶鍵"
  - "助憶鍵, 加入至對話方塊控制項"
  - "Text 屬性, 指定控制項的便捷鍵"
  - "Windows Form 控制項, 便捷鍵"
ms.assetid: 4faa0991-28ec-4eca-91db-51dc2cd6a7ac
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：建立 Windows Form 控制項的便捷鍵
*便捷鍵* \(Access Key\) 指的是功能表文字、功能表項目或是控制項標籤中含有底線的字元 \(例如按鈕\)。  便捷鍵可讓使用者同時按下 ALT 鍵與預先定義便捷鍵，來達到「按一下」按鈕的效果。  例如，如果某按鈕是以執行程序來列印表單，因此該按鈕 `Text` 屬性是設定為 "Print"，在字母 "P" 之前加上連字號 \(&\) 即可讓在執行階段的按鈕文字字母 "P" 加上底線。  使用者可按 ALT\+P 鍵來執行與按鈕關聯的命令。  您不能為無法接受焦點的控制項設定便捷鍵。  
  
### 若要建立控制項的便捷鍵  
  
1.  將 `Text` 屬性設為字串，並且在要成為快速鍵的字母前面加上連字號 \(&\)。  
  
    ```vb  
    ' Set the letter "P" as an access key.  
    Button1.Text = "&Print"  
  
    ```  
  
    ```csharp  
    // Set the letter "P" as an access key.  
    button1.Text = "&Print";  
  
    ```  
  
    ```cpp  
    // Set the letter "P" as an access key.  
    button1->Text = "&Print";  
    ```  
  
    > [!NOTE]
    >  若標題要包含連字號但不建立便捷鍵，則請加上兩個連字號 \(&&\)。  這樣標題中會出現單一連字號，且不會在字元中加上底線。  
  
## 請參閱  
 <xref:System.Windows.Forms.Button>   
 [如何：回應 Windows Form Button 按一下動作](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)   
 [如何：設定由 Windows Form 控制項所顯示的文字](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)   
 [標記個別 Windows Form 控制項並提供其捷徑](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)