---
title: "如何：使用設計工具將 Windows Form 按鈕指定為取消按鈕 | Microsoft Docs"
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
  - "Button 控制項 [Windows Form], 指定為取消按鈕"
  - "按鈕, 取消按鈕"
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：使用設計工具將 Windows Form 按鈕指定為取消按鈕
在任何 Windows Form 中，您可以將 <xref:System.Windows.Forms.Button> 控制項指定為取消按鈕。  每當使用者按下 ESC 鍵，則不管表單上的哪個控制項擁有焦點，都會按一下取消按鈕。  這類按鈕通常都利用程式設計，讓使用者不需認可任何動作就能快速結束作業。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要指定取消按鈕  
  
1.  選取按鈕所在的表單  
  
2.  在 \[**屬性**\] 視窗中，將表單的 <xref:System.Windows.Forms.Form.CancelButton%2A> 屬性設為 <xref:System.Windows.Forms.Button> 控制項的名稱。  
  
## 請參閱  
 <xref:System.Windows.Forms.Form.CancelButton%2A>   
 [Button 控制項概觀](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)   
 [選取 Windows Form Button 控制項的方法](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)   
 [如何：回應 Windows Form Button 按一下動作](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)   
 [如何：使用設計工具將 Windows Form 按鈕指定為接受按鈕](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)   
 [Button 控制項](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)