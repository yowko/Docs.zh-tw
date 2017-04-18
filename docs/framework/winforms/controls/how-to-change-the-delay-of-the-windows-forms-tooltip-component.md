---
title: "如何：變更 Windows Form ToolTip 元件的延遲時間 | Microsoft Docs"
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
  - "範例 [Windows Form], 工具提示"
  - "ToolTip 元件 [Windows Form], 延遲值"
  - "工具提示 [Windows Form], 延遲值"
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：變更 Windows Form ToolTip 元件的延遲時間
您可以設定 Windows Form <xref:System.Windows.Forms.ToolTip> 元件的多個延遲時間值。  這些屬性的度量單位都是毫秒。  <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> 屬性決定使用者必須將滑鼠指標移至相關聯的控制項之後多久才會顯示工具提示字串。  <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> 屬性設定當滑鼠從一工具提示關聯控制項移動到另一工具提示關聯控制項時，下一工具提示字串出現所需的毫秒數間隔。  <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> 決定顯示工具提示字串的時間長短。  您可個別設定這些值，或是設定 <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> 屬性的值來進行；其他延遲屬性是根據指定給 <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> 屬性的值所設定的。  例如，當 <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> 的值設為 N，<xref:System.Windows.Forms.ToolTip.InitialDelay%2A> 的值設為 N，<xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> 設為 <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> 的值除以 5 \(或 N\/5\)，而 <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> 的值設為 <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> 屬性值的 5 倍 \(或 5N\)。  
  
### 若要設定延遲時間  
  
1.  將屬性設定如以下範例所示。  
  
    ```vb  
    ToolTip1.InitialDelay = 500  
    ToolTip1.ReshowDelay = 100  
    ToolTip1.AutoPopDelay = 5000  
  
    ```  
  
    ```csharp  
    ToolTip1.InitialDelay = 500;  
    ToolTip1.ReshowDelay = 100;  
    ToolTip1.AutoPopDelay = 5000;  
  
    ```  
  
    ```cpp  
    toolTip1->InitialDelay = 500;  
    toolTip1->ReshowDelay = 100;  
    toolTip1->AutoPopDelay = 5000;  
    ```  
  
## 請參閱  
 [ToolTip 元件概觀](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)   
 [如何：在設計階段設定 Windows Form 上控制項的工具提示](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)   
 [ToolTip 元件](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)