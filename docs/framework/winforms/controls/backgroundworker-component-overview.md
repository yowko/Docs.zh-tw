---
title: "BackgroundWorker 元件概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BackgroundWorker"
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
ms.assetid: 64e9b3ab-7443-4a77-ab17-b8b8c0cb3f62
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# BackgroundWorker 元件概觀
有許多經常執行的作業都需要長時間執行。  例如：  
  
-   映像下載  
  
-   Web 服務叫用  
  
-   檔案下載及上傳 \(包括對等應用程式\)  
  
-   複雜的本機運算  
  
-   資料庫交易  
  
-   本機磁碟存取 \(假設因為存取記憶體導致速度變慢\)  
  
 當這類作業執行時，可能會導致您的使用者介面無回應。  當您需要 UI 即時回應，但 UI 卻受到這些作業拖累，導致回應時間拉長時，<xref:System.ComponentModel.BackgroundWorker> 元件可以提供合宜的解決方法。  
  
 <xref:System.ComponentModel.BackgroundWorker> 元件可以非同步 \(在背景中\) 的方式，透過不同於應用程式之主要 UI 執行緒的執行緒來執行這些耗時的作業。  若要使用 <xref:System.ComponentModel.BackgroundWorker>，只須告知此函式要在背景中執行哪一個工作者方法，然後再呼叫 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 方法就可以了。  您呼叫的執行緒會如常執行，而工作者方法也會以非同步的方式同時執行。  當方法結束時，<xref:System.ComponentModel.BackgroundWorker> 會引發 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件來提示您呼叫的執行緒，並視情況在事件中包含作業的結果。  
  
 <xref:System.ComponentModel.BackgroundWorker> 元件會在 \[元件\] 索引標籤的 \[工具箱\] 中提供。  若要將 <xref:System.ComponentModel.BackgroundWorker> 加入表單，可將 <xref:System.ComponentModel.BackgroundWorker> 元件拖曳至表單中。  其本身會顯示在元件匣中，而其屬性則會出現在 \[屬性\] 視窗中。  
  
 若要啟動非同步作業，請使用 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 方法。  <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 可接受選用的 `object` 參數將引數傳遞給您的工作者方法。  <xref:System.ComponentModel.BackgroundWorker> 類別會引發 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件，而您的工作者執行緒會經由 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式連結至此事件。  
  
 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式可接受具有 <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> 屬性的 <xref:System.ComponentModel.DoWorkEventArgs> 參數。  此屬性會從 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 接收參數，並可傳遞給 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式中所呼叫的工作者方法。  下列範例示範如何指派工作者方法 `ComputeFibonacci` 所產生的結果。  此範例僅包含局部內容，如需完整範例，請參閱 [如何：實作使用背景作業的表單](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)。  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 如需使用事件處理常式的詳細資訊，請參閱 [事件](../../../../docs/standard/events/index.md)。  
  
> [!CAUTION]
>  無論使用何種多執行緒作業，您都可能會面臨嚴重而複雜的錯誤。  實作任何會使用多執行緒的方案前，請先參閱 [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md)。  
  
 如需使用 <xref:System.ComponentModel.BackgroundWorker> 類別的詳細資訊，請參閱 [如何：在背景執行作業](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)。  
  
## 請參閱  
 [NOT IN BUILD: Multithreading in Visual Basic](http://msdn.microsoft.com/zh-tw/c731a50c-09c1-4468-9646-54c86b75d269)   
 [如何：實作使用背景作業的表單](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)