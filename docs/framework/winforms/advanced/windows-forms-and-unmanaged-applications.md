---
title: "Windows Form 和 Unmanaged 應用程式 | Microsoft Docs"
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
  - "ActiveX 控制項 [Windows Form]"
  - "COM [Windows Form]"
  - "COM Interop, Windows Form"
  - "Windows Form, Interop"
  - "Windows Form, Unmanaged"
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Windows Form 和 Unmanaged 應用程式
伴隨著某些注意事項，Windows Form 應用程式和控制項能與 Unmanaged 應用程式交互操作。  下列各節描述 Windows Form 應用程式和控制項支援及不支援的案例和組態。  
  
## 在本節中  
 [Windows Form 和 Unmanaged 應用程式概觀](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)  
 針對如何使用及實作 Windows Form 控制項來與 Unmanaged 應用程式搭配運作，提供一般相關資訊。  
  
 [如何：顯示 Windows Form 和 ShowDialog 方法以支援 COM Interop](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 提供程式碼範例，示範如何使用 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=fullName> 方法，在 Unmanaged 應用程式中執行 Windows Form。  
  
 [如何：在自己的執行緒上顯示每個 Windows Form 以支援 COM Interop](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 提供程式碼範例，示範如何讓 Windows Form 在其自己的執行緒上執行。  
  
 另請參閱[逐步解說：在自己的執行緒上顯示每個 Windows Form 以支援 COM Interop](http://msdn.microsoft.com/library/ms233639\(v=vs.110\))。  
  
## 參考  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=fullName>  
 用來為 Windows Form 建立個別的執行緒。  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=fullName>  
 為執行緒啟動訊息迴圈。  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 將呼叫從 Unmanaged 應用程式封送處理至表單。  
  
## 相關章節  
 [將 .NET Framework 元件公開給 COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 針對如何在 Unmanaged 應用程式中使用 .NET Framework 類型，提供一般相關資訊。