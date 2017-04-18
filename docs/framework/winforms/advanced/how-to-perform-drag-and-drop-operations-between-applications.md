---
title: "如何：在應用程式間執行拖放作業 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "拖放, 應用程式間"
ms.assetid: fa347436-2b12-4dd6-8507-59d7241f6a06
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：在應用程式間執行拖放作業
在應用程式之間執行拖放作業與在應用程式之內啟用這個動作並無不同，只要涉及的兩個應用程式根據 <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> 和 <xref:System.Windows.Forms.DragEventArgs.Effect%2A> 屬性之間建立的「合約」表現即可。  
  
 在下列程序中，您將使用您建立的 Windows 架構應用程式以及隨附於 Windows 作業系統、用來執行應用程式間拖放作業的 WordPad 文書處理器。  WordPad 具有一組特定的允許拖曳和卸除文字的效果集；您將為其撰寫程式碼的 Windows 架構應用程式將會使用這些效果，如此便可能會成功完成拖放作業。  
  
### 執行應用程式之間的拖放程序  
  
1.  新建 Windows Forms 應用程式  
  
2.  新增 <xref:System.Windows.Forms.TextBox> 控制項至表單。  
  
3.  設定 <xref:System.Windows.Forms.TextBox> 控制項以接收已卸除的資料。  
  
     如需詳細資訊，請參閱[逐步解說：在 Windows Form 中執行拖放作業](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)。  
  
4.  執行 Windows 架構應用程式，並與此同時執行 WordPad。  
  
     WordPad 是由允許拖放作業之 Windows 所安裝的文字編輯器。  它是藉由按下 \[開始\] 按鈕、選取 \[執行\]、然後在 \[執行\] 對話方塊中的文字方塊中輸入 `WordPad` 並按一下 \[確定\]  來存取。  
  
5.  一旦開啟 WordPad，請於其中輸入文字的字串。  
  
6.  使用滑鼠、選取文字，然後再將選取的文字拖曳到 Windows 架構應用程式中的 <xref:System.Windows.Forms.TextBox> 控制項。  
  
     觀察當以滑鼠移過 <xref:System.Windows.Forms.TextBox> 控制項 \(然後因此引發 <xref:System.Windows.Forms.Control.DragEnter> 事件\)，游標會變更，且您可以卸除選取的文字 <xref:System.Windows.Forms.TextBox> 至控制項。  
  
     此外，您可以設定您的 <xref:System.Windows.Forms.TextBox> 控制項，以允許將文字字串拖放到 WordPad。  如需詳細資訊，請參閱[逐步解說：在 Windows Form 中執行拖放作業](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)。  
  
## 請參閱  
 [如何：將資料加入至剪貼簿](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)   
 [如何：從剪貼簿擷取資料](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)   
 [拖放作業和剪貼簿支援](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)