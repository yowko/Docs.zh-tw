---
title: "Internet Explorer 與 WCF 執行之服務憑證驗證之間的差異"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12e30d9df9d6bb0a9f8776099951e4354d302ebf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Internet Explorer 與 WCF 執行之服務憑證驗證之間的差異
因為 Internet Explorer 與 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 使用 HTTPS 時，驗證服務憑證的方法不同，所以即使 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端可成功傳送訊息至服務端點，Internet Explorer 還是有可能無法存取說明網頁或服務的 Web 服務描述語言 (WSDL)。 這是因為 Internet Explorer 檢查服務憑證在增強用途旗標中是否擁有 `ServerAuthentication` 物件識別項 (OID)，而 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 並未強制執行這種限制。 如果 Internet Explorer 無法存取服務說明網頁或服務的 WSDL，請使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來存取服務中繼資料。  
  
## <a name="see-also"></a>請參閱  
 [透過 TCP 與 SOAP 安全性的 HTTPS 與 SSL 之間的憑證驗證差異](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [如何：擷取中繼資料並實作相容性服務](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
