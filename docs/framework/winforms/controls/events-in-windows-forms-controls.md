---
title: "Windows Form 控制項中的事件 | Microsoft Docs"
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
  - "自訂控制項 [Windows Form], 事件概觀 (使用程式碼)"
  - "事件 [Windows Form], 自訂控制項 (使用程式碼)"
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Windows Form 控制項中的事件
Windows Form 控制項從 <xref:System.Windows.Forms.Control?displayProperty=fullName> 繼承了六十個以上的事件。  其中包含會造成繪製控制項的 <xref:System.Windows.Forms.Control.Paint> 事件，與顯示視窗相關的事件 \(例如 <xref:System.Windows.Forms.Control.Resize> 和 <xref:System.Windows.Forms.Control.Layout> 事件\)，以及低階滑鼠和鍵盤事件。  某些低階事件是由 <xref:System.Windows.Forms.Control> 結合成語意事件，例如 <xref:System.Windows.Forms.Control.Click> 和 <xref:System.Windows.Forms.Control.DoubleClick>。  如需繼承事件的詳細資訊，請參閱 <xref:System.Windows.Forms.Control>。  
  
 如果自訂控制項需要覆寫繼承的事件功能，請覆寫繼承的 `On`*EventName* 方法，而不要附加委派 \(Delegate\)。  如果您不太熟悉 .NET Framework 中的事件模型，請參閱[從元件引發事件](../Topic/Raising%20Events%20from%20a%20Component.md)。  
  
## 請參閱  
 [覆寫 OnPaint 方法](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)   
 [處理使用者輸入](../../../../docs/framework/winforms/controls/handling-user-input.md)   
 [定義事件](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)   
 [事件](../../../../docs/standard/events/index.md)