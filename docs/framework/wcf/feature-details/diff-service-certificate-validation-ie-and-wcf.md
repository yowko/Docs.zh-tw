---
title: Internet Explorer 與 WCF 執行之服務憑證驗證之間的差異
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: 0bced548cdc9423d1907de09e8b52ebe078d7c19
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225909"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Internet Explorer 與 WCF 執行之服務憑證驗證之間的差異
Internet Explorer 和 Windows Communication Foundation (WCF) 驗證服務憑證使用 HTTPS 時的方法不同，因為它是 Internet Explorer 將不會無法存取 [說明] 頁面或 Web 服務描述語言(WSDL) 的服務即使 WCF 用戶端能夠成功地將訊息傳送至服務端點。 這是因為 Internet Explorer 會檢查是否有服務憑證`ServerAuthentication`物件識別項 (OID) 在增強的用途旗標，而 WCF 不會強制這類條件約束。 如果 Internet Explorer 無法存取服務說明網頁或服務的 WSDL，請使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來存取服務中繼資料。  
  
## <a name="see-also"></a>另請參閱

- [透過 TCP 與 SOAP 安全性的 HTTPS 與 SSL 之間的憑證驗證差異](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [HOW TO：擷取中繼資料並實作相容性服務](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
