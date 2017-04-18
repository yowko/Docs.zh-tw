---
title: "疑難排解：對 Windows 服務進行偵錯 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯 [Visual Studio], Windows 服務"
  - "對 Windows 服務應用程式進行偵錯"
  - "服務, 偵錯"
  - "服務, 疑難排解"
  - "偵錯疑難排解, Windows 服務"
  - "服務應用程式疑難排解"
  - "Windows 服務應用程式, 偵錯"
  - "Windows 服務應用程式, 疑難排解"
ms.assetid: cf859d4c-f04c-4cb7-81e3-bc7de8bea190
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 8
---
# 疑難排解：對 Windows 服務進行偵錯
當您對 Windows 服務應用程式進行偵錯時，您的服務會與 Windows 的 \[**服務管理員**\] 進行互動。  \[**服務管理員**\] 會藉由呼叫 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法來啟動服務，接著等候 30 秒，等待 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法傳回。  如果此方法沒有在這段時間內傳回結果，管理員會顯示服務無法啟動的錯誤。  
  
 當您依照 [如何：偵錯 Windows 服務應用程式](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md) 中的說明，對 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法進行偵錯時，您必須注意這個 30 秒期間的限制。  如果您在 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法中設定中斷點，而沒有在 30 秒內逐步執行，則管理員不會啟動此服務。  
  
## 請參閱  
 [如何：偵錯 Windows 服務應用程式](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)   
 [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)