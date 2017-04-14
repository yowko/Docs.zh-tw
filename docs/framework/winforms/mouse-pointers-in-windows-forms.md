---
title: "Windows Form 中的滑鼠指標 | Microsoft Docs"
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
  - "游標, 設定 [Windows Form]"
  - "滑鼠游標"
  - "滑鼠指標"
  - "滑鼠指標, 設定 [Windows Form]"
  - "滑鼠, 游標"
  - "指標, 設定 [Windows Form]"
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Windows Form 中的滑鼠指標
滑鼠*指標* \(有時亦稱為游標\) 是一個點陣圖，在螢幕上以滑鼠指定使用者輸入的焦點。  這個主題提供 Windows Form 中滑鼠指標的概觀，並且描述一些修改及控制滑鼠指標的方法。  
  
## 存取滑鼠指標  
 滑鼠指標是以 <xref:System.Windows.Forms.Cursor> 類別表示，而且每一個 <xref:System.Windows.Forms.Control> 都有 <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=fullName> 屬性，指定該控制項的指標。  <xref:System.Windows.Forms.Cursor> 類別包含描述指標的屬性 \(例如 <xref:System.Windows.Forms.Cursor.Position%2A> 和 <xref:System.Windows.Forms.Cursor.HotSpot%2A> 屬性\) 以及可用來修改指標外觀的方法 \(例如 <xref:System.Windows.Forms.Cursor.Show%2A>、<xref:System.Windows.Forms.Cursor.Hide%2A> 和 <xref:System.Windows.Forms.Cursor.DrawStretched%2A> 方法\)。  
  
## 控制滑鼠指標  
 有時候您可能會想要限制滑鼠使用範圍或者變更滑鼠位置。  您可以使用 <xref:System.Windows.Forms.Cursor> 的 <xref:System.Windows.Forms.Cursor.Position%2A> 屬性來取得或設定目前的滑鼠位置。  此外，您還可以藉由設定 <xref:System.Windows.Forms.Cursor.Clip%2A> 屬性來限制滑鼠使用範圍。  根據預設，裁剪範圍是整個螢幕。  
  
## 變更滑鼠指標  
 變更滑鼠指標是提供使用者回應的重要方式。  例如，滑鼠指標可以在 <xref:System.Windows.Forms.Control.MouseEnter> 和 <xref:System.Windows.Forms.Control.MouseLeave> 事件的處理常式中進行修改，以告知使用者正在進行計算並且限制控制項中的使用者互動。  有時候，滑鼠指標會因為系統事件而變更，例如在應用程式發生拖放作業的時候。  
  
 變更滑鼠指標的主要方式即是將控制項的 <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=fullName> 或 <xref:System.Windows.Forms.Control.DefaultCursor%2A> 屬性設為新的 <xref:System.Windows.Forms.Cursor>。  如需變更滑鼠指標的範例，請參考 <xref:System.Windows.Forms.Cursor> 類別中的程式碼範例。  此外，<xref:System.Windows.Forms.Cursors> 類別會公開一組許多不同指標類型的 <xref:System.Windows.Forms.Cursor> 物件，例如手形指標。  當滑鼠指標位於控制項上時，若要顯示等待指標 \(形狀為沙漏\)，請使用 <xref:System.Windows.Forms.Control> 類別的 <xref:System.Windows.Forms.Control.UseWaitCursor%2A> 屬性。  
  
## 請參閱  
 <xref:System.Windows.Forms.Cursor>   
 [Windows Form 應用程式中的滑鼠輸入](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)   
 [Windows Form 中的拖放功能](../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)