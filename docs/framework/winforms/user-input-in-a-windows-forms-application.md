---
title: "Windows Form 應用程式中的使用者輸入 | Microsoft Docs"
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
  - "Windows Form, 使用者輸入"
ms.assetid: 9d61fa96-70f7-4754-885a-49a4a6316bdb
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Windows Form 應用程式中的使用者輸入
在 Windows Form 中，使用者輸入是以 Windows 訊息的形式傳送至應用程式，  有一系列的可覆寫方法會在應用程式、表單和控制項層級處理這些訊息。  當這些方法接收滑鼠和鍵盤訊息時，它們會引發事件，這些事件可在經過處理後取得滑鼠或鍵盤輸入的資訊。  在許多情況中，Windows Form 應用程式只需經由處理這些事件就可以處理所有的使用者輸入。  在其他情況下，應用程式可能需要覆寫其中一個會處理訊息的方法，以便在應用程式、表單或控制項接收某特定訊息之前先將它攔截下來。  
  
## 滑鼠和鍵盤事件  
 所有的 Windows Form 控制項都會繼承一組和滑鼠及鍵盤輸入有關的事件，  例如，某個控制項可以處理 <xref:System.Windows.Forms.Control.KeyPress> 事件以判斷某按鍵的字元碼，或者是某個控制項可以處理 <xref:System.Windows.Forms.Control.MouseClick> 事件以判斷按一下滑鼠的位置。  如需滑鼠和鍵盤事件的詳細資訊，請參閱[使用鍵盤事件](../../../docs/framework/winforms/using-keyboard-events.md)和 [Windows Form 中的滑鼠事件](../../../docs/framework/winforms/mouse-events-in-windows-forms.md)。  
  
## 會處理使用者輸入訊息的方法  
 表單和控制項可以存取 <xref:System.Windows.Forms.IMessageFilter> 介面以及一組可覆寫的方法，這些方法會在訊息佇列中的不同點處理 Windows 訊息。  這些方法全部都具有 <xref:System.Windows.Forms.Message> 參數，此參數會封裝 Windows 訊息的低階資訊。  您可以實作或覆寫這些方法以檢查訊息，然後再使用訊息或是將它傳遞至訊息佇列中的下一個消費者。  下表列出 Windows Form 中會處理所有 Windows 訊息的方法。  
  
|方法|備註|  
|--------|--------|  
|<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A>|這個方法會在應用程式層級攔截已佇列的 \(也稱為已張貼的\) Windows 訊息。|  
|<xref:System.Windows.Forms.Control.PreProcessMessage%2A>|這個方法會在 Windows 訊息被處理之前，在表單和控制項層級將它攔截。|  
|<xref:System.Windows.Forms.Control.WndProc%2A>|這個方法會在表單和控制項層級處理 Windows 訊息。|  
|<xref:System.Windows.Forms.Control.DefWndProc%2A>|這個方法會在表單和控制項層級執行 Windows 訊息的預設處理程序。  這可提供基本的視窗功能。|  
|<xref:System.Windows.Forms.Control.OnNotifyMessage%2A>|這個方法會在訊息被處理之後，在表單和控制項層級將它攔截。  您必須設定 <xref:System.Windows.Forms.ControlStyles> 樣式位元 \(Style Bit\)，才能呼叫這個方法。|  
  
 另一組可覆寫的方法也會處理鍵盤和滑鼠訊息，這些方法是專門用來處理這類訊息。  如需詳細資訊，請參閱[鍵盤輸入的運作方式](../../../docs/framework/winforms/how-keyboard-input-works.md)和[滑鼠輸入在 Windows Form 中的運作方式](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md)。  
  
## 請參閱  
 [Windows Form 中的使用者輸入](../../../docs/framework/winforms/user-input-in-windows-forms.md)   
 [Windows Form 應用程式中的鍵盤輸入](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)   
 [Windows Form 應用程式中的滑鼠輸入](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)