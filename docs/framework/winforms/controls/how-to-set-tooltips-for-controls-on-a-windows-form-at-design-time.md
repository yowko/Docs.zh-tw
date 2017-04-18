---
title: "如何：在設計階段設定 Windows Form 上控制項的工具提示 | Microsoft Docs"
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
  - "工具提示 [Windows Form], 控制項適用"
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 如何：在設計階段設定 Windows Form 上控制項的工具提示
您可以在程式碼或 Windows Form 設計工具中設定 <xref:System.Windows.Forms.ToolTip> 字串。  如需 <xref:System.Windows.Forms.ToolTip> 元件的詳細資訊，請參閱 [ToolTip 元件概觀](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要以程式設計方式設定工具提示  
  
1.  加入要顯示工具提示的控制項。  
  
2.  使用 <xref:System.Windows.Forms.ToolTip> 元件的 <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> 方法。  
  
    ```vb  
    ' In this example, Button1 is the control to display the ToolTip.  
    ToolTip1.SetToolTip(Button1, "Save changes")  
  
    ```  
  
    ```csharp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1.SetToolTip(button1, "Save changes");  
  
    ```  
  
    ```cpp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1->SetToolTip(button1, "Save changes");  
    ```  
  
### 在設計工具中設定工具提示  
  
1.  在表單中加入 <xref:System.Windows.Forms.ToolTip> 元件。  
  
2.  選取顯示工具提示的控制項，或將它加入至表單。  
  
3.  在 \[**屬性**\] 視窗中，將 \[**ToolTip1 的工作提示**\] 值設定為適當的文字字串。  
  
## 請參閱  
 [ToolTip 元件概觀](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)   
 [如何：變更 Windows Form ToolTip 元件的延遲時間](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)   
 [ToolTip 元件](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)