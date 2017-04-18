---
title: "工作流程管理端點範例 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# 工作流程管理端點範例
這個範例示範如何使用工作流程控制端點，在本機和遠端建立及執行工作流程。此範例也示範如何裝載控制端點，以及撰寫用戶端來呼叫該控制端點以建立及執行工作流程執行個體。此工作流程不是服務。  
  
 在範例的服務端，工作流程裝載於 WorkflowServiceHost，並且加入了一個 WorkflowControlEndpoint，因此用戶端可以執行控制作業 \(暫停、啟動等\)。另也加入使用者定義的 CreationEndpoint，以便建立工作流程。接著該服務會使用這些端點啟動暫停中狀態的工作流程，然後恢復該工作流程。用戶端會執行相同的作業，但會來自用戶端程式碼。[!INCLUDE[crabout](../../../../includes/crabout-md.md)] 這些介面的詳細資訊，請參閱 [工作流程控制端點](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) 和d [HOW TO：在 IIS 中裝載非服務工作流程](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
  
#### 若要執行範例  
  
1.  以系統管理員權限執行 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]。  
  
2.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 ManagementEndpoint.sln 方案。  
  
3.  若要建置方案，請按 CTRL\+SHIFT\+B 或選取 \[**建置**\] 功能表中的 \[**建置方案**\]。  
  
4.  啟動 ManagementEndpoint.exe 應用程式。  
  
5.  啟動 Client.exe 應用程式。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`  
  
## 請參閱