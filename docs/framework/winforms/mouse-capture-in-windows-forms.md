---
title: "Windows Form 中的滑鼠捕捉 | Microsoft Docs"
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
  - "滑鼠, 捕捉"
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Windows Form 中的滑鼠捕捉
*滑鼠捕捉 \(Mouse Capture\)* 會參考控制項何時接收所有滑鼠輸入的命令。  當控制項已捕捉到滑鼠時，它會接收滑鼠輸入，不論指標是否位於控制項的框線內。  
  
## 設定滑鼠捕捉  
 在 Windows Form 中，當使用者在控制項上按下滑鼠按鈕時會由控制項捕捉滑鼠，並且當使用者放開滑鼠按鈕時控制項也隨之釋放滑鼠。  
  
 <xref:System.Windows.Forms.Control> 類別的 <xref:System.Windows.Forms.Control.Capture%2A> 屬性指出控制項是否捕捉到滑鼠。  若要判斷控制項何時遺失滑鼠捕捉，請處理 <xref:System.Windows.Forms.Control.MouseCaptureChanged> 事件。  
  
 唯有前景視窗才能捕捉滑鼠。  當背景視窗嘗試捕捉滑鼠時，視窗接收到的只有當滑鼠指標位於視窗可見部分內而引發的滑鼠事件訊息。  此外，即使前景視窗已捕捉到滑鼠，使用者仍可以按一下其他視窗，即可將之帶至前景。  捕捉到滑鼠之後，快速鍵便無法使用。  
  
## 請參閱  
 [Windows Form 應用程式中的滑鼠輸入](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)