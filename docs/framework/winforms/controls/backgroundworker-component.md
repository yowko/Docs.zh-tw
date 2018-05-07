---
title: BackgroundWorker 元件
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: bef7b0ab-ce57-475a-a2d6-fb8a702a9417
ms.openlocfilehash: 38505876e2f944139622a0d7cf7aaab9c510ef89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="backgroundworker-component"></a>BackgroundWorker 元件
`BackgroundWorker`元件可讓您的表單或控制項加入執行非同步作業。  
  
## <a name="in-this-section"></a>本節內容  
 [BackgroundWorker 元件概觀](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 描述`BackgroundWorker`元件，可讓您執行這些耗時的作業，以非同步方式 （「 在背景中 」），不同於您的應用程式的主要 UI 執行緒的執行緒。  
  
 [逐步解說：在背景執行作業](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)  
 示範如何使用`BackgroundWorker`元件在設計工具中執行耗時的作業，另一個執行緒上。  
  
 [操作說明：在背景執行作業](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 示範如何使用`BackgroundWorker`元件來執行耗時的作業，另一個執行緒上。  
  
 [逐步解說：實作使用背景作業的表單](../../../../docs/framework/winforms/controls/walkthrough-implementing-a-form-that-uses-a-background-operation.md)  
 建立使用設計工具會以非同步方式執行算術運算的應用程式。  
  
 [操作說明：實作使用背景作業的表單](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 建立的應用程式，以非同步方式進行算術運算。  
  
 [操作說明：在背景中下載檔案](../../../../docs/framework/winforms/controls/how-to-download-a-file-in-the-background.md)  
 示範如何使用`BackgroundWorker`元件下載個別的執行緒上的檔案。  
  
## <a name="reference"></a>參考資料  
 <xref:System.ComponentModel.BackgroundWorker>  
 描述這個類別，並且提供其所有成員的連結。  
  
 <xref:System.ComponentModel.RunWorkerCompletedEventArgs>  
 描述保留的資料類型<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件。  
  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 描述保留的資料類型<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件。  
  
## <a name="related-sections"></a>相關章節  
 [事件架構非同步模式概觀](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 描述如何以非同步模式提供多執行緒應用程式的優點同時隱藏許多多執行緒設計中原有的複雜問題。
