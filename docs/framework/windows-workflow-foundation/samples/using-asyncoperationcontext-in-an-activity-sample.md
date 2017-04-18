---
title: "使用活動中的 AsyncOperationContext 範例 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# 使用活動中的 AsyncOperationContext 範例
這個範例示範如何開發自訂的 <xref:System.Activities.CodeActivity>，該活動會使用 <xref:System.Activities.AsyncOperationContext> 在工作流程之外以非同步方式執行工作。  
  
## 範例詳細資料  
 範例活動會使用 <xref:System.IO.FileStream> 類別上的 <xref:System.IO.FileStream.BeginWrite> 和 <xref:System.IO.FileStream.EndWrite> 方法，以非同步方式將資料寫入檔案中。此處介紹的模式可加以調整，以應用於其他非同步方法。非同步作業執行時，工作流程中的其他活動也可以執行，不過工作流程無法保存。  
  
#### 若要安裝、建置及執行範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 \[Async.sln\] 範例方案。  
  
2.  建置和執行方案。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`  
  
## 請參閱