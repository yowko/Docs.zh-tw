---
title: "ToolTip 元件概觀 (Windows Form) | Microsoft Docs"
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
  - "ToolTip"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ToolTip 元件 [Windows Form], 關於 ToolTip 元件"
  - "工具提示 [Windows Form], 關於工具提示"
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# ToolTip 元件概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.ToolTip> 元件會在使用者指向控制項時顯示文字。  工具提示 \(ToolTip\) 可以和任何控制項建立關聯。  使用這個元件的範例之一是：若要節省表單的空間，您可以在按鈕上顯示小圖示，並利用工具提示說明按鈕的功能。  
  
## 使用 ToolTip 元件  
 <xref:System.Windows.Forms.ToolTip> 元件在 Windows Form 或其他容器 \(Container\) 上提供 `ToolTip` 屬性給多個控制項。  例如，如果在表單上加入 <xref:System.Windows.Forms.ToolTip> 元件，就可以為 <xref:System.Windows.Forms.TextBox> 控制項顯示「在這裡輸入您的姓名」，且為 <xref:System.Windows.Forms.Button> 控制項顯示「按這裡儲存變更」。  
  
 <xref:System.Windows.Forms.ToolTip> 元件的主要方法為 <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> 和 <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>。  您可以使用 <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> 方法設定針對控制項所顯示的工具提示。  如需詳細資訊，請參閱 [如何：在設計階段設定 Windows Form 上控制項的工具提示](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)。  主要屬性包括 <xref:System.Windows.Forms.ToolTip.Active%2A> \(必須設定為 `true` 以便顯示工具提示\) 以及 <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> \(設定工具提示字串顯示的時間長度、使用者必須指向多長的時間控制項才會顯示，以及後續的工具提示視窗出現所需的時間\)。  如需詳細資訊，請參閱 [如何：變更 Windows Form ToolTip 元件的延遲時間](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolTip>   
 [如何：在設計階段設定 Windows Form 上控制項的工具提示](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)   
 [如何：變更 Windows Form ToolTip 元件的延遲時間](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)