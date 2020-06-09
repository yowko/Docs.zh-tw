---
title: Internet Explorer 與 WCF 執行之服務憑證驗證之間的差異
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: 151075f2894b895ab90418748df9face3aa70252
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599187"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="b7a78-102">Internet Explorer 與 WCF 執行之服務憑證驗證之間的差異</span><span class="sxs-lookup"><span data-stu-id="b7a78-102">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>
<span data-ttu-id="b7a78-103">因為 Internet Explorer 與 Windows Communication Foundation （WCF）在使用 HTTPS 時驗證服務憑證的方式不同，所以即使 WCF 用戶端能夠成功地將訊息傳送至服務端點，Internet Explorer 還是有可能無法存取服務的說明頁面或 Web 服務描述語言（WSDL）。</span><span class="sxs-lookup"><span data-stu-id="b7a78-103">Because of difference between the way Internet Explorer and Windows Communication Foundation (WCF) validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a WCF client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="b7a78-104">這是因為 Internet Explorer 會 `ServerAuthentication` 在增強的使用旗標中檢查服務憑證是否具有物件識別碼（OID），而 WCF 不會強制執行這類條件約束。</span><span class="sxs-lookup"><span data-stu-id="b7a78-104">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas WCF does not enforce such a constraint.</span></span> <span data-ttu-id="b7a78-105">如果 Internet Explorer 無法存取服務的服務說明頁面或 WSDL，請使用[System.servicemodel 中繼資料公用程式工具（Svcutil）](../servicemodel-metadata-utility-tool-svcutil-exe.md)來存取服務中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b7a78-105">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7a78-106">請參閱</span><span class="sxs-lookup"><span data-stu-id="b7a78-106">See also</span></span>

- [<span data-ttu-id="b7a78-107">透過 TCP 與 SOAP 安全性的 HTTPS 與 SSL 之間的憑證驗證差異</span><span class="sxs-lookup"><span data-stu-id="b7a78-107">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [<span data-ttu-id="b7a78-108">如何：擷取中繼資料並實作相容性服務</span><span class="sxs-lookup"><span data-stu-id="b7a78-108">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](how-to-retrieve-metadata-and-implement-a-compliant-service.md)
