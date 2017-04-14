---
title: "最佳做法：媒介 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 最佳做法：媒介
當呼叫媒介以確保正確關閉媒介上的服務端通道時，必須特別小心才能正確處理錯誤。  
  
 請考量下列情節。用戶端呼叫媒介，而這個媒介又接著呼叫後端服務。後端服務沒有定義錯誤合約，因此任何從該服務擲回的錯誤都將視為不具型別的錯誤。後端服務會擲回 <xref:System.ApplicationException>，而 WCF 會正確中止服務端通道。然後 <xref:System.ApplicationException> 呈現為擲回給媒介的 <xref:System.ServiceModel.FaultException>。媒介重新擲回 <xref:System.ApplicationException>。WCF 將此解譯為來自媒介的不具型別錯誤，並將其轉送至用戶端。收到錯誤時，媒介和用戶端都會將各自的用戶端通道置於錯誤狀態。不過，WCF 不知道錯誤是嚴重的，因此媒介的服務端通道仍會保持開啟。  
  
 在此情節中，最佳做法是偵測來自服務的錯誤是否為嚴重錯誤，若然則判斷媒介是否應使其服務端通道進入錯誤狀態，如下列程式碼片段所示。  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    Else  
    {  
        throw;  
    }  
}  
  
```  
  
## 請參閱  
 [WCF 錯誤處理](../../../docs/framework/wcf/wcf-error-handling.md)   
 [指定與處理合約和服務中的錯誤](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)