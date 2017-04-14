---
title: "處理使用者輸入 | Microsoft Docs"
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
  - "自訂控制項 [Windows Form], 使用程式碼的鍵盤事件"
  - "自訂控制項 [Windows Form], 使用程式碼的滑鼠事件"
  - "自訂控制項 [Windows Form], 使用程式碼的使用者輸入"
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 處理使用者輸入
本主題將描述 <xref:System.Windows.Forms.Control?displayProperty=fullName> 所提供的主要鍵盤和滑鼠事件。  在處理事件時，控制項作者應該覆寫保護的 `On`*EventName* 方法，而不是附加委派 \(Delegate\) 至事件。  如需檢視事件，請參閱[從元件引發事件](../Topic/Raising%20Events%20from%20a%20Component.md)。  
  
> [!NOTE]
>  如果沒有與事件相關聯的資料，會將基底類別 \(Base Class\) <xref:System.EventArgs> 的執行個體 \(Instance\) 當做引數傳遞給 `On`*EventName* 方法。  
  
## 鍵盤事件  
 控制項可以處理的一般鍵盤事件為 <xref:System.Windows.Forms.Control.KeyDown>、<xref:System.Windows.Forms.Control.KeyPress> 和 <xref:System.Windows.Forms.Control.KeyUp>。  
  
|事件名稱|要覆寫的方法|事件說明|  
|----------|------------|----------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|只有在按鍵初次按下時引發。|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|每次按鍵被按下時引發。  如果按下按鍵不放，<xref:System.Windows.Forms.Control.KeyPress> 事件會以作業系統定義的重複率來引發。|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|在放開按鍵時引發。|  
  
> [!NOTE]
>  處理鍵盤輸入較覆寫前面表格中的事件更為複雜，而且超出這個主題的範圍。  如需詳細資訊，請參閱 [Windows Form 中的使用者輸入](../../../../docs/framework/winforms/user-input-in-windows-forms.md)。  
  
## 滑鼠事件  
 控制項可以處理的滑鼠事件為 <xref:System.Windows.Forms.Control.MouseDown>、<xref:System.Windows.Forms.Control.MouseEnter>、<xref:System.Windows.Forms.Control.MouseHover>、<xref:System.Windows.Forms.Control.MouseLeave>、<xref:System.Windows.Forms.Control.MouseMove> 和 <xref:System.Windows.Forms.Control.MouseUp>。  
  
|事件名稱|要覆寫的方法|事件說明|  
|----------|------------|----------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|當指標在控制項之上，而按下滑鼠按鈕時引發。|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|在指標第一次進入控制項的區域時引發。|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|在指標停留於控制項時引發。|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|在指標離開控制項的區域時引發。|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|在指標移入控制項的區域時引發。|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|當指標在控制項之上或指標要離開控制項區域，而放開滑鼠按鈕時引發。|  
  
 下列程式碼片段會示範覆寫 <xref:System.Windows.Forms.Control.MouseDown> 事件的範例。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 下列程式碼片段會示範覆寫 <xref:System.Windows.Forms.Control.MouseMove> 事件的範例。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 下列程式碼片段會示範覆寫 <xref:System.Windows.Forms.Control.MouseUp> 事件的範例。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 如需 `FlashTrackBar` 範例的完整原始程式碼，請參閱 [如何：建立顯示進度的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)。  
  
## 請參閱  
 [Windows Form 控制項中的事件](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)   
 [定義事件](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)   
 [事件](../../../../docs/standard/events/index.md)   
 [Windows Form 中的使用者輸入](../../../../docs/framework/winforms/user-input-in-windows-forms.md)