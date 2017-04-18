---
title: "拖放作業和剪貼簿支援 | Microsoft Docs"
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
  - "剪貼簿, Windows Form"
  - "拖放"
  - "拖放, Windows Form"
ms.assetid: 7cce79b6-5835-46fd-b690-73f12ad368b2
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 拖放作業和剪貼簿支援
若要在 Windows 架構應用程式內啟用使用者拖放作業，您可以處理一系列的事件，最值得注意的是 <xref:System.Windows.Forms.Control.DragEnter>、<xref:System.Windows.Forms.Control.DragLeave> 和 <xref:System.Windows.Forms.Control.DragDrop> 事件。  
  
 您也可以使用簡單的方法呼叫，將使用者剪下\/複製\/貼上支援和使用者資料傳輸實作至 Windows 架構應用程式中的剪貼簿。  
  
## 在本節中  
 [逐步解說：在 Windows Form 中執行拖放作業](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)  
 說明如何開始拖放作業。  
  
 [如何：在應用程式間執行拖放作業](../../../../docs/framework/winforms/advanced/how-to-perform-drag-and-drop-operations-between-applications.md)  
 說明如何跨應用程式完成拖放作業。  
  
 [如何：將資料加入至剪貼簿](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 說明如何以程式設計方式，在剪貼簿上插入資訊。  
  
 [如何：從剪貼簿擷取資料](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 說明如何存取儲存在剪貼簿上的資料。  
  
## 相關章節  
 [Windows Form 中的拖放功能](../../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)  
 說明用來實作拖放行為的方法、事件和類別。  
  
 <xref:System.Windows.Forms.Control.QueryContinueDrag>  
 說明要求權限以繼續拖曳作業之事件的複雜性。  
  
 <xref:System.Windows.Forms.Control.DoDragDrop%2A>  
 說明開始拖曳作業之主要方法的複雜性。  
  
 <xref:System.Windows.Forms.Clipboard>  
 另請參閱[如何：傳送資料至作用中的 MDI 子系](http://msdn.microsoft.com/library/y0hkh2c8%20\(v=vs.110\))。