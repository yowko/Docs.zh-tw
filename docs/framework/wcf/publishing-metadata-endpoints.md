---
title: 發行中繼資料端點
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 143a46ce18a0d9dee89bbbffac9be9a467e951df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955151"
---
# <a name="publishing-metadata-endpoints"></a><span data-ttu-id="64963-102">發行中繼資料端點</span><span class="sxs-lookup"><span data-stu-id="64963-102">Publishing Metadata Endpoints</span></span>
<span data-ttu-id="64963-103">Windows Communication Foundation (WCF) 服務會發行中繼資料發行一個或多個中繼資料端點。</span><span class="sxs-lookup"><span data-stu-id="64963-103">Windows Communication Foundation (WCF) services publish metadata by publishing one or more metadata endpoints.</span></span> <span data-ttu-id="64963-104">發行服務中繼資料會使用標準化的通訊協定 (例如 WS-MetadataExchange (MEX) 和 HTTP/GET 要求) 來提供中繼資料。</span><span class="sxs-lookup"><span data-stu-id="64963-104">Publishing service metadata makes the metadata available using standardized protocols, such as WS-MetadataExchange (MEX) and HTTP/GET requests.</span></span> <span data-ttu-id="64963-105">中繼資料端點與其他服務端點相似的地方，在於都有位址、繫結和合約，並且能夠透過組態或程式碼新增至服務主機。</span><span class="sxs-lookup"><span data-stu-id="64963-105">Metadata endpoints are similar to other service endpoints in that they have an address, a binding, and a contract, and they can be added to a service host through configuration or in code.</span></span> <span data-ttu-id="64963-106">若要啟用發行中繼資料端點，您必須將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 服務行為新增至服務。</span><span class="sxs-lookup"><span data-stu-id="64963-106">To enable publishing metadata endpoints, you must add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> service behavior to the service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="64963-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="64963-107">In This Section</span></span>  
 [<span data-ttu-id="64963-108">如何：發行服務，使用組態檔的中繼資料</span><span class="sxs-lookup"><span data-stu-id="64963-108">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 <span data-ttu-id="64963-109">示範如何設定 WCF 服務發行中繼資料，讓用戶端可以擷取中繼資料使用 Ws-metadataexchange 或 HTTP/GET 要求使用`?wsdl`查詢字串。</span><span class="sxs-lookup"><span data-stu-id="64963-109">Demonstrates how to configure a WCF service to publish metadata so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
 [<span data-ttu-id="64963-110">如何：發行服務，使用程式碼的中繼資料</span><span class="sxs-lookup"><span data-stu-id="64963-110">How to: Publish Metadata for a Service Using Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 <span data-ttu-id="64963-111">示範如何啟用 WCF 服務程式碼中的中繼資料發行，讓用戶端可以擷取中繼資料使用 Ws-metadataexchange 或 HTTP/GET 要求使用`?wsdl`查詢字串。</span><span class="sxs-lookup"><span data-stu-id="64963-111">Demonstrates how to enable metadata publishing for a WCF service in code so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64963-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64963-112">See also</span></span>

- [<span data-ttu-id="64963-113">發行中繼資料</span><span class="sxs-lookup"><span data-stu-id="64963-113">Publishing Metadata</span></span>](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
