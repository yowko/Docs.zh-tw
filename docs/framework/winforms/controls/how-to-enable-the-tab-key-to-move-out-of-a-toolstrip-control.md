---
title: "如何：啟用 TAB 鍵來移至 ToolStrip 控制項之外 | Microsoft Docs"
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
  - "控制項 [Windows Form], 在之間移動"
  - "TAB 鍵, 啟用"
  - "ToolStrip 控制項 [Windows Forms], 移動來源"
ms.assetid: 40f9e88b-09a3-428e-8da8-c00bb65079c6
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：啟用 TAB 鍵來移至 ToolStrip 控制項之外
請使用下列程序，讓使用者按 TAB 鍵便能依定位順序從 <xref:System.Windows.Forms.ToolStrip> 移至下一個控制項。  
  
 <xref:System.Windows.Forms.ToolStrip> 可接受第一次按下 TAB 鍵，而方向鍵則可選取 <xref:System.Windows.Forms.ToolStrip> 內的項目。  當使用者第二次按下 TAB 鍵時，會依定位順序將使用者帶至下一個控制項。  
  
### 若要啟用按 TAB 鍵即將使用者從 ToolStrip 移至下一個控制項  
  
-   將 <xref:System.Windows.Forms.ToolStrip> 的 <xref:System.Windows.Forms.ToolStrip.TabStop%2A> 屬性設為 `true`。  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStrip.TabStop%2A>   
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)