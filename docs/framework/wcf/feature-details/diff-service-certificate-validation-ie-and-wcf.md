---
title: Internet Explorer 與 WCF 執行之服務憑證驗證之間的差異
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: 0bced548cdc9423d1907de09e8b52ebe078d7c19
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225909"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="0ccba-102">Internet Explorer 與 WCF 執行之服務憑證驗證之間的差異</span><span class="sxs-lookup"><span data-stu-id="0ccba-102">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>
<span data-ttu-id="0ccba-103">Internet Explorer 和 Windows Communication Foundation (WCF) 驗證服務憑證使用 HTTPS 時的方法不同，因為它是 Internet Explorer 將不會無法存取 [說明] 頁面或 Web 服務描述語言(WSDL) 的服務即使 WCF 用戶端能夠成功地將訊息傳送至服務端點。</span><span class="sxs-lookup"><span data-stu-id="0ccba-103">Because of difference between the way Internet Explorer and Windows Communication Foundation (WCF) validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a WCF client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="0ccba-104">這是因為 Internet Explorer 會檢查是否有服務憑證`ServerAuthentication`物件識別項 (OID) 在增強的用途旗標，而 WCF 不會強制這類條件約束。</span><span class="sxs-lookup"><span data-stu-id="0ccba-104">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas WCF does not enforce such a constraint.</span></span> <span data-ttu-id="0ccba-105">如果 Internet Explorer 無法存取服務說明網頁或服務的 WSDL，請使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來存取服務中繼資料。</span><span class="sxs-lookup"><span data-stu-id="0ccba-105">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ccba-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ccba-106">See also</span></span>

- [<span data-ttu-id="0ccba-107">透過 TCP 與 SOAP 安全性的 HTTPS 與 SSL 之間的憑證驗證差異</span><span class="sxs-lookup"><span data-stu-id="0ccba-107">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [<span data-ttu-id="0ccba-108">如何：擷取中繼資料，並實作相容服務</span><span class="sxs-lookup"><span data-stu-id="0ccba-108">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
