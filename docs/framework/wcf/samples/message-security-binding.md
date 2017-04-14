---
title: "訊息安全性繫結 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a4570ce7-864e-461b-85d8-0f7bcc53c2c8
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# 訊息安全性繫結
本節包含示範 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中 Windows 服務之訊息安全性繫結的範例。  
  
## 在本節中  
 [訊息安全性匿名](../../../../docs/framework/wcf/samples/message-security-anonymous.md)  
 這個範例會示範如何實作 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 應用程式，這個應用程式所使用的訊息層級安全性並不會透過用戶端驗證，而是要求以伺服器的 X.509 憑證進行伺服器驗證。  
  
 [訊息安全性憑證](../../../../docs/framework/wcf/samples/message-security-certificate.md)  
 這個範例會示範如何實作應用程式，該應用程式會對用戶端使用搭配 X.509 v3 憑證驗證的 WS\-Security，並要求使用伺服器之 X.509 v3 憑證進行驗證的伺服器。  
  
 [訊息安全性使用者名稱](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
 這個範例會示範如何實作應用程式，該應用程式會對用戶端使用搭配使用者名稱驗證的 WS\-Security，並要求使用伺服器之 X.509v3 憑證進行驗證的伺服器驗證。  
  
 [訊息安全性視窗](../../../../docs/framework/wcf/samples/message-security-windows.md)  
 這個範例會示範如何將 <xref:System.ServiceModel.WSHttpBinding> 繫結設定成搭配 Windows 驗證使用的訊息層級安全性。