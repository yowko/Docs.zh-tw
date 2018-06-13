---
title: Internet Explorer 與 WCF 執行之服務憑證驗證之間的差異
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: ecc2b16eae5428e305f5f6096d6d7994256d86c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488682"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="b0363-102">Internet Explorer 與 WCF 執行之服務憑證驗證之間的差異</span><span class="sxs-lookup"><span data-stu-id="b0363-102">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>
<span data-ttu-id="b0363-103">由於 Internet Explorer 和 Windows Communication Foundation (WCF) 驗證服務憑證使用 HTTPS 時的方式之間的差異，所以 Internet Explorer 不能存取說明網頁或 Web 服務描述語言(WSDL) 的服務即使 WCF 用戶端便能成功地將訊息傳送至服務端點。</span><span class="sxs-lookup"><span data-stu-id="b0363-103">Because of difference between the way Internet Explorer and Windows Communication Foundation (WCF) validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a WCF client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="b0363-104">這是因為 Internet Explorer 檢查服務憑證是否具有`ServerAuthentication`物件識別項 (OID) 在增強的用途旗標，而 WCF 不會強制執行這類條件約束。</span><span class="sxs-lookup"><span data-stu-id="b0363-104">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas WCF does not enforce such a constraint.</span></span> <span data-ttu-id="b0363-105">如果 Internet Explorer 無法存取服務說明網頁或服務的 WSDL，請使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來存取服務中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b0363-105">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0363-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0363-106">See Also</span></span>  
 [<span data-ttu-id="b0363-107">透過 TCP 與 SOAP 安全性的 HTTPS 與 SSL 之間的憑證驗證差異</span><span class="sxs-lookup"><span data-stu-id="b0363-107">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [<span data-ttu-id="b0363-108">如何：擷取中繼資料並實作相容性服務</span><span class="sxs-lookup"><span data-stu-id="b0363-108">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
