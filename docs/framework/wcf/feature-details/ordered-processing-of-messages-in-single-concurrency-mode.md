---
title: "單一並行模式中訊息的已排序處理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 單一並行模式中訊息的已排序處理
除非基礎通道具有工作階段，否則 WCF 不保證處理訊息的順序。例如，使用沒有工作階段的 MsmqInputChannel 的 WCF 服務將無法依照順序處理訊息。在某些情況下，開發人員可能需要依序處理的行為，但又不想要使用工作階段。本主題說明如何當服務在單一並行模式中執行時，如何設定這種行為。  
  
## 依照順序的訊息處理  
 名為<xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> 的新屬性已加入至 <xref:System.ServiceModel.ServiceBehaviorAttribute>。當 <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> 設為 true 且 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> 設為 <xref:System.ServiceModel.ConcurrencyMode> 時，將會依照順序處理傳送至服務的訊息。下列程式碼片段將說明如何設定這些屬性：  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
  
```  
  
 如果將 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> 設定為任何其他值，則會擲回 <xref:System.InvalidOperationException>。  
  
## 請參閱  
 [工作階段、執行個體與並行](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)   
 [並行](../../../../docs/framework/wcf/samples/concurrency.md)