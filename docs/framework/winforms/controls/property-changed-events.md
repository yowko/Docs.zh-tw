---
title: "屬性變更事件 | Microsoft Docs"
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
  - "自訂控制項 [Windows Form], 屬性變更 (使用程式碼)"
  - "屬性 [Windows Form], 變更"
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 屬性變更事件
如果希望控制項在名為 *PropertyName* 的屬性變更時傳送告知，請定義名為 *PropertyName*`Changed` 的事件，以及引發事件且名為 `On`*PropertyName*`Changed` 的方法。  Windows Form 中的命名慣例是將文字 *Changed* 附加到屬性的名稱。  屬性變更事件的相關事件委派 \(Delegate\) 型別為 <xref:System.EventHandler>，而事件資料型別為 <xref:System.EventArgs>。  基底類別 <xref:System.Windows.Forms.Control> 定義了許多屬性變更事件，例如 <xref:System.Windows.Forms.Control.BackColorChanged>、<xref:System.Windows.Forms.Control.BackgroundImageChanged>、<xref:System.Windows.Forms.Control.FontChanged>、<xref:System.Windows.Forms.Control.LocationChanged> 和其他事件。  如需事件的背景資訊，請參閱[事件](../../../../docs/standard/events/index.md)和 [Windows Form 控制項中的事件](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)。  
  
 屬性變更事件很有用處，因為它們允許控制項的消費者附加會回應變更的事件處理常式。  如果您的控制項需要回應其引發的屬性變更事件，請覆寫對應的 `On`*PropertyName*`Changed` 方法，而不要附加委派至事件。  控制項基本上藉著更新其他屬性或重繪其繪圖平面的局部或全部來回應屬性變更事件。  
  
 下列範例示範 `FlashTrackBar` 自訂控制項如何回應某些繼承自 <xref:System.Windows.Forms.Control> 的屬性變更事件。  如需完整範例，請參閱 [如何：建立顯示進度的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## 請參閱  
 [事件](../../../../docs/standard/events/index.md)   
 [Windows Form 控制項中的事件](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)   
 [Windows Form 控制項中的屬性](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)