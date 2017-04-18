---
title: "裝載工作流程服務概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 裝載工作流程服務概觀
您必須裝載工作流程服務，才能加以執行。<xref:System.ServiceModel.WorkflowServiceHost> 是現成的工作流程主機，它支援多個執行個體、組態和 WCF 訊息 \(不過，這些工作流程不需要使用訊息，就能夠裝載\)。此外，它也會透過一組服務行為，與持續性、追蹤和執行個體控制項整合。就像 WCF 的 <xref:System.ServiceModel.ServiceHost> 一樣，<xref:System.ServiceModel.WorkflowServiceHost> 可以在任何 Managed .NET 應用程式中自我裝載，也可以在 IIS \/ WAS 中 Web 裝載 \(成為 .xamlx 檔案\)。本節中的主題描述如何裝載工作流程服務。  
  
## 在本節中  
 [裝載工作流程服務](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 描述如何裝載工作流程服務。  
  
 [工作流程服務主機內部](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 描述 <xref:System.ServiceModel.WorkflowServiceHost> 如何處理傳入訊息。  
  
 [工作流程服務主機擴充性](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 描述如何擴充工作流程服務主機的功能。  
  
 [工作流程控制端點](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 描述如何定義可讓您建立工作流程執行個體的端點。  
  
 [HOW TO：在 IIS 中裝載非服務工作流程](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
 示範如何在 IIS 中裝載非工作流程服務的工作流程。  
  
 [HOW TO：使用 Windows Server App Fabric 裝載工作流程服務](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 示範如何在 Windows Server App Fabric 中裝載現有的工作流程服務。  
  
 [設定 WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 描述如何控制持續性、追蹤、閒置和未處理的例外狀況行為。  
  
## 參考  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## 相關章節  
 [工作流程服務](../../../../docs/framework/wcf/feature-details/workflow-services.md)