---
title: "發行中繼資料端點"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 64032fbc675e30e9f01a5db4d56ecc36574e08de
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="publishing-metadata-endpoints"></a><span data-ttu-id="fe30f-102">發行中繼資料端點</span><span class="sxs-lookup"><span data-stu-id="fe30f-102">Publishing Metadata Endpoints</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="fe30f-103"> 服務會藉由發行一或多個中繼資料端點以發行中繼資料。</span><span class="sxs-lookup"><span data-stu-id="fe30f-103"> services publish metadata by publishing one or more metadata endpoints.</span></span> <span data-ttu-id="fe30f-104">發行服務中繼資料會使用標準化的通訊協定 (例如 WS-MetadataExchange (MEX) 和 HTTP/GET 要求) 來提供中繼資料。</span><span class="sxs-lookup"><span data-stu-id="fe30f-104">Publishing service metadata makes the metadata available using standardized protocols, such as WS-MetadataExchange (MEX) and HTTP/GET requests.</span></span> <span data-ttu-id="fe30f-105">中繼資料端點與其他服務端點相似的地方，在於都有位址、繫結和合約，並且能夠透過組態或程式碼新增至服務主機。</span><span class="sxs-lookup"><span data-stu-id="fe30f-105">Metadata endpoints are similar to other service endpoints in that they have an address, a binding, and a contract, and they can be added to a service host through configuration or in code.</span></span> <span data-ttu-id="fe30f-106">若要啟用發行中繼資料端點，您必須將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 服務行為新增至服務。</span><span class="sxs-lookup"><span data-stu-id="fe30f-106">To enable publishing metadata endpoints, you must add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> service behavior to the service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fe30f-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="fe30f-107">In This Section</span></span>  
 [<span data-ttu-id="fe30f-108">如何： 使用組態檔的服務發行中繼資料</span><span class="sxs-lookup"><span data-stu-id="fe30f-108">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 <span data-ttu-id="fe30f-109">示範如何設定 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務來發行中繼資料，以便讓用戶端能夠使用 `?wsdl` 查詢字串透過 WS-MetadataExchange 或 HTTP/GET 要求擷取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="fe30f-109">Demonstrates how to configure a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service to publish metadata so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
 [<span data-ttu-id="fe30f-110">如何： 使用程式碼的服務發行中繼資料</span><span class="sxs-lookup"><span data-stu-id="fe30f-110">How to: Publish Metadata for a Service Using Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 <span data-ttu-id="fe30f-111">示範如何在程式碼中啟用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務的中繼資料發行，以便讓用戶端能夠使用 `?wsdl` 查詢字串透過 WS-MetadataExchange 或 HTTP/GET 要求擷取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="fe30f-111">Demonstrates how to enable metadata publishing for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service in code so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe30f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe30f-112">See Also</span></span>  
 [<span data-ttu-id="fe30f-113">發行中繼資料</span><span class="sxs-lookup"><span data-stu-id="fe30f-113">Publishing Metadata</span></span>](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
