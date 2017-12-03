---
title: "使用 CancellationScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 39c5c338-b316-43d6-b7fe-a543281dd1ec
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2082ab8e0a9736cf56b7b551335ed57d082f7c8a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="using-cancellationscope"></a>使用 CancellationScope
這個範例示範如何使用 <xref:System.Activities.Statements.CancellationScope> 活動取消應用程式中的工作。  
  
 許多中介層元件和服務依賴已知的交易程式設計建構來處理取消作業。  不過，在許多情況下，必須取消交易中無法完成的工作。  使用取消比使用交易更困難，因為必須取消的工作必須先加以追蹤。 [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] 提供 <xref:System.Activities.Statements.CancellationScope> 活動，可協助您進行作業。  
  
 取消可以從活動中或從活動的父系中觸發。  子活動是由父活動排程 (例如 <xref:System.Activities.Statements.Sequence>、<xref:System.Activities.Statements.Parallel>、<xref:System.Activities.Statements.Flowchart> 或自訂複合活動)。  父活動可以取消子活動，不計原因。  例如，有三個子分支的 <xref:System.Activities.Statements.Parallel> 活動會在完成某個分支而且 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 運算式評估為 `true` 時取消其餘子分支。 工作流程也可以由主應用程式呼叫 <xref:System.Activities.WorkflowApplication.Cancel%2A>，從外部取消。  
  
 若要使用 <xref:System.Activities.Statements.CancellationScope> 活動，請將必須取消的工作放在 <xref:System.Activities.Statements.CancellationScope.Body%2A> 屬性中，並將取消後執行的工作放在 <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> 屬性中。  
  
 這個範例示範如何從活動本身取消活動。  
  
 此範例用來示範 <xref:System.Activities.Statements.CancellationScope> 活動的狀況是，客戶想要盡快購買到邁阿密的機票。 有兩家旅行社想要做這筆生意。 此範例在 <xref:System.Activities.Statements.CancellationScope> 活動中使用兩個 <xref:System.Activities.Statements.Parallel>，以建立此商務邏輯的模型。 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 活動的 <xref:System.Activities.Statements.Parallel> 設為 `true`；因為在任何分支完成之後會檢查 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A>，所以在第一個分支完成之後必須取消其餘分支。 用戶端應用程式要求兩家旅行社購買機票，當第一家確認已買到機票時，應用程式會取消另一家的訂單。  
  
## <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 CancelationScopeXAML.sln 方案檔案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行此方案，請按下 CTRL+F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\CancellationScope`