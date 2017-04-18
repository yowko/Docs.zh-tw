---
title: "疑難排解：無法安裝服務應用程式 | Microsoft Docs"
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
  - "服務, 偵錯"
  - "服務, 疑難排解"
  - "NT 服務疑難排解"
  - "服務應用程式疑難排解"
  - "Windows NT 服務, 疑難排解"
  - "Windows 服務應用程式, 疑難排解"
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 8
---
# 疑難排解：無法安裝服務應用程式
如果無法正確安裝服務應用程式，請確定該服務類別的 <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> 屬性是設定為與該服務的安裝程式中所顯示的設定值相同。  這兩個執行個體中該屬性值必須相同，才能正確安裝您的服務。  
  
> [!NOTE]
>  您也可以查看安裝記錄檔，取得安裝過程的回應。  
  
 您也應該檢查是否已經安裝了另一個相同名稱的服務。  服務名稱必須是唯一的，才能成功安裝。  
  
## 請參閱  
 [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)