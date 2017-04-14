---
title: "在 Windows Form 控制項中的多執行緒 | Microsoft Docs"
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
  - "BackgroundWorker 元件"
  - "BeginInvoke 方法"
  - "執行緒處理 [Windows Form], 控制項"
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 在 Windows Form 控制項中的多執行緒
在許多應用程式中，您都可以利用另一個執行緒來執行耗時的作業，讓您的使用者介面 \(UI\) 有更快的回應。  有許多工具都可以讓您的 Windows Form 控制項具有多執行緒的能力，包括 <xref:System.Threading> 命名空間、<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=fullName> 方法，以及 `BackgroundWorker` 元件。  
  
> [!NOTE]
>  `BackgroundWorker` 元件會取代並加入功能至 <xref:System.Threading> 命名空間以及 <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=fullName> 方法；不過，您可以依選擇為回溯相容性 \(Backward Compatibility\) 和未來使用將其保留。  如需詳細資訊，請參閱 [BackgroundWorker 元件概觀](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)。  
  
## 在本節中  
 [如何：進行對 Windows Form 控制項的安全執行緒呼叫](../../../../docs/framework/winforms/controls/how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 顯示如何進行對 Windows Form 控制項的安全執行緒呼叫  
  
 [如何：使用背景執行緒搜尋檔案](../../../../docs/framework/winforms/controls/how-to-use-a-background-thread-to-search-for-files.md)  
 顯示如何使用 <xref:System.Threading> 命名空間和 <xref:System.Windows.Forms.Control.BeginInvoke%2A> 方法來非同步搜尋檔案。  
  
## 參考  
 <xref:System.ComponentModel.BackgroundWorker>  
 提供以一個封裝了背景工作執行緒的元件來執行非同步作業的文件。  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 提供如何非同步載入音效的文件。  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 提供如何非同步載入影像的文件。  
  
## 相關章節  
 [如何：在背景執行作業](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 顯示如何使用 <xref:System.ComponentModel.BackgroundWorker> 元件來執行耗時的作業。  
  
 [BackgroundWorker 元件概觀](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 提供描述如何使用 <xref:System.ComponentModel.BackgroundWorker> 元件來執行非同步作業的主題