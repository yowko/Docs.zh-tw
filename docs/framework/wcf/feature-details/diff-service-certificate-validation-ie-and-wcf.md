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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a58ea9f84571ede9943769e1f187a242383a88f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="5488e-102">Internet Explorer 與 WCF 執行之服務憑證驗證之間的差異</span><span class="sxs-lookup"><span data-stu-id="5488e-102">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>
<span data-ttu-id="5488e-103">因為 Internet Explorer 與 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 使用 HTTPS 時，驗證服務憑證的方法不同，所以即使 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端可成功傳送訊息至服務端點，Internet Explorer 還是有可能無法存取說明網頁或服務的 Web 服務描述語言 (WSDL)。</span><span class="sxs-lookup"><span data-stu-id="5488e-103">Because of difference between the way Internet Explorer and [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="5488e-104">這是因為 Internet Explorer 檢查服務憑證在增強用途旗標中是否擁有 `ServerAuthentication` 物件識別項 (OID)，而 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 並未強制執行這種限制。</span><span class="sxs-lookup"><span data-stu-id="5488e-104">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not enforce such a constraint.</span></span> <span data-ttu-id="5488e-105">如果 Internet Explorer 無法存取服務說明網頁或服務的 WSDL，請使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來存取服務中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5488e-105">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5488e-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5488e-106">See Also</span></span>  
 [<span data-ttu-id="5488e-107">憑證驗證差異 HTTPS、 SSL over TCP 與 SOAP 安全性</span><span class="sxs-lookup"><span data-stu-id="5488e-107">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [<span data-ttu-id="5488e-108">如何： 擷取中繼資料，並實作相容服務</span><span class="sxs-lookup"><span data-stu-id="5488e-108">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
