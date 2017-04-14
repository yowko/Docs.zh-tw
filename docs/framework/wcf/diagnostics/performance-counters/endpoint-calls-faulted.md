---
title: "端點：發生錯誤的呼叫數 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 271e6284-9c4b-465f-b619-069e1555a5e4
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 端點：發生錯誤的呼叫數
計數器名稱：發生錯誤的呼叫數。  
  
## 描述  
 對這個端點有傳回錯誤的呼叫數。在 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 應用程式中，服務方法使用 SOAP 錯誤訊息來溝通處理錯誤資訊。SOAP 錯誤是包含在服務作業之中繼資料內的訊息類型，因此會建立錯誤合約，而用戶端可使用該合約來讓其執行作業更強固或更具互動性。由於 SOAP 錯誤會以 XML 表單的形式傳達給用戶端，所以其互通性很高。  
  
## 請參閱  
 [指定與處理合約和服務中的錯誤](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)