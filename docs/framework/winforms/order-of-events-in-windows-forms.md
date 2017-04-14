---
title: "Windows Form 中事件的順序 | Microsoft Docs"
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
  - "應用程式關閉事件順序"
  - "應用程式啟動事件順序"
  - "事件 [Windows Form], 順序"
  - "焦點事件順序"
  - "序列, 事件"
  - "驗證事件, 順序"
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Windows Form 中事件的順序
關於 Windows Form 應用程式中被引發的事件，程式開發人員會特別關注他們的順序，並且盡力依次處理每個事件。  當遇到需要謹慎處理事件的狀況，例如當您重新繪製部分表單時，對於在執行階段時被引發的事件，感知其精確的順序是必需的。  本主題提供一些有關在應用程式以及控制項存留期中，幾個重要階段裡事件順序的詳細資料。  如需有關滑鼠輸入事件之順序的特定詳細資訊，請參閱 [Windows Form 中的滑鼠事件](../../../docs/framework/winforms/mouse-events-in-windows-forms.md)。  如需 Windows Form 中事件的概觀，請參閱[事件概觀](../../../docs/framework/winforms/events-overview-windows-forms.md)。  如需事件處理常式實體架構的詳細資訊，請參閱 [事件處理常式概觀](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)。  
  
## 應用程式啟動和關閉事件  
 <xref:System.Windows.Forms.Form> 和 <xref:System.Windows.Forms.Control> 類別會公開一組關於應用程式啟動和關閉的事件。  當 Windows Form 應用程式啟動時，主要表單的啟動事件會依照下列順序引發：  
  
-   <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Form.Load?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Form.Activated?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Form.Shown?displayProperty=fullName>  
  
 當 Windows Form 應用程式關閉時，主要表單的關閉事件會依照下列順序引發：  
  
-   <xref:System.Windows.Forms.Form.Closing?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Form.FormClosing?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Form.Closed?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Form.FormClosed?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Form.Deactivate?displayProperty=fullName>  
  
 <xref:System.Windows.Forms.Application> 類別的 <xref:System.Windows.Forms.Application.ApplicationExit> 事件會在主要表單的關閉事件之後引發。  
  
> [!NOTE]
>  Visual Basic 2005 包含其他應用程式事件，例如 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=fullName> 和 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=fullName>。  
  
## 焦點和驗證事件。  
 當您使用鍵盤 \(TAB、SHIFT \+ TAB 等等\) 變更焦點時，藉由呼叫 <xref:System.Windows.Forms.Control.Select%2A> 或 <xref:System.Windows.Forms.Control.SelectNextControl%2A> 方法，或藉由設定 <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> 屬性到目前表單， <xref:System.Windows.Forms.Control> 類別的焦點事件會以下列順序發生：  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
 當您使用滑鼠或藉由呼叫 <xref:System.Windows.Forms.Control.Focus%2A> 方法來變更焦點， <xref:System.Windows.Forms.Control> 類別的焦點事件會以下列順序發生：  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
## 請參閱  
 [在 Windows Form 中建立事件處理常式](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)