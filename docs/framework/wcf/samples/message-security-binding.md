---
title: 訊息安全性繫結
ms.date: 03/30/2017
ms.assetid: a4570ce7-864e-461b-85d8-0f7bcc53c2c8
ms.openlocfilehash: 7c4b21a8983884cbb4f8ab77568bd4977563b3b1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584827"
---
# <a name="message-security-binding"></a>訊息安全性繫結
本節包含的範例會示範 WCF 中 Windows 服務的訊息安全性系結。  
  
## <a name="in-this-section"></a>本節內容  
 [訊息安全性匿名](message-security-anonymous.md)  
 這個範例示範如何使用不具用戶端驗證的訊息層級安全性來執行 Windows Communication Foundation （WCF）應用程式，但這需要使用伺服器的 x.509 憑證進行伺服器驗證。  
  
 [訊息安全性憑證](message-security-certificate.md)  
 這個範例會示範如何實作應用程式，該應用程式會對用戶端使用搭配 X.509 v3 憑證驗證的 WS-Security，並要求使用伺服器之 X.509 v3 憑證進行驗證的伺服器。  
  
 [訊息安全性使用者名稱](message-security-user-name.md)  
 這個範例會示範如何實作應用程式，該應用程式會對用戶端使用搭配使用者名稱驗證的 WS-Security，並要求使用伺服器之 X.509v3 憑證進行驗證的伺服器驗證。  
  
 [訊息安全性視窗](message-security-windows.md)  
 這個範例會示範如何將 <xref:System.ServiceModel.WSHttpBinding> 繫結設定成搭配 Windows 驗證使用的訊息層級安全性。
