---
title: "如何：使用設計工具設定由 Windows Form 控制項所顯示的文字 | Microsoft Docs"
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
  - "控制項 [Windows Form], 設定標題"
  - "Windows Form, 設定顯示的文字"
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：使用設計工具設定由 Windows Form 控制項所顯示的文字
Windows Form 控制項通常會顯示與控制項主要功能相關的一些文字。  例如，<xref:System.Windows.Forms.Button> 控制項通常會顯示標題，指出按一下按鈕時所會執行的動作。  對於所有的控制項，您可以使用 <xref:System.Windows.Forms.Control.Text%2A> 屬性來設定或傳回文字。  您可以藉由使用 <xref:System.Windows.Forms.Control.Font%2A> 屬性以變更字型，  
  
### 若要使用設計工具設定文字和字型  
  
1.  在 \[屬性\] 視窗中，將控制項的 <xref:System.Windows.Forms.Control.Text%2A> 屬性設定為適當字串。  
  
     若要建立含有底線的快速鍵，請在快速鍵字母前面加上連字號 \(&\)。  
  
2.  在 \[屬性\] 視窗中，按一下 <xref:System.Windows.Forms.Control.Font%2A> 屬性旁邊的省略號按鈕 \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\)。  
  
     在標準的字型對話方塊中，選取您要的字型、字型樣式、大小、效果 \(例如刪除線或底線\) 和指令碼。  
  
## 請參閱  
 [如何：設定由 Windows Form 控制項所顯示的文字](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)   
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)   
 [標記個別 Windows Form 控制項並提供其捷徑](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)