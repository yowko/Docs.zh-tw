---
title: "BackgroundWorker 元件 | Microsoft Docs"
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
  - "非同步模式"
  - "背景作業"
  - "背景工作"
  - "BackgroundWorker 元件"
  - "元件 [Windows Form], 非同步"
  - "表單, 背景作業"
  - "表單, 多執行緒"
  - "執行緒處理 [Windows Form], 背景作業"
ms.assetid: bef7b0ab-ce57-475a-a2d6-fb8a702a9417
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# BackgroundWorker 元件
`BackgroundWorker` 元件可以讓您的表單或控制項執行非同步作業。  
  
## 在本節中  
 [BackgroundWorker 元件概觀](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 描述 `BackgroundWorker` 元件，這個元件提供您在不同於應用程式主要 UI 執行緒的執行緒上，非同步 \(「在幕後執行」\) 執行耗時作業的能力。  
  
 [逐步解說：在背景執行作業](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)  
 示範如何在設計工具中使用 `BackgroundWorker` 元件在個別的執行緒上執行耗時的作業。  
  
 [如何：在背景執行作業](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 示範如何使用 `BackgroundWorker` 元件在個別的執行緒上執行耗時的作業。  
  
 [逐步解說：實作使用背景作業的表單](../../../../docs/framework/winforms/controls/walkthrough-implementing-a-form-that-uses-a-background-operation.md)  
 使用設計工具建立一個非同步進行算術運算的應用程式。  
  
 [如何：實作使用背景作業的表單](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 建立一個非同步進行算術運算的應用程式。  
  
 [如何：在背景中下載檔案](../../../../docs/framework/winforms/controls/how-to-download-a-file-in-the-background.md)  
 示範如何使用 `BackgroundWorker` 元件在個別的執行緒上下載檔案。  
  
## 參考  
 <xref:System.ComponentModel.BackgroundWorker>  
 描述這個類別並且連結到它所有的成員。  
  
 <xref:System.ComponentModel.RunWorkerCompletedEventArgs>  
 描述為 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件存放資料的型別。  
  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 描述為 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件存放資料的型別。  
  
## 相關章節  
 [Event\-based Asynchronous Pattern Overview](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 描述非同步模式如何提供多執行緒應用程式的優點，同時隱藏了多執行緒設計中許多原有的複雜問題。