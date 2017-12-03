---
title: "如何：為資料服務結果啟用分頁功能 (WCF 資料服務)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9156ddbe9482683660524898aa0c6ce3673cd75f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a><span data-ttu-id="c5750-102">如何：為資料服務結果啟用分頁功能 (WCF 資料服務)</span><span class="sxs-lookup"><span data-stu-id="c5750-102">How to: Enable Paging of Data Service Results (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="c5750-103"> 可讓您限制資料服務查詢所傳回的實體數目。</span><span class="sxs-lookup"><span data-stu-id="c5750-103"> enables you to limit the number of entities returned by a data service query.</span></span> <span data-ttu-id="c5750-104">當服務已初始化且可針對每個實體集分別設定服務時，分頁限制會定義於所呼叫的方法中。</span><span class="sxs-lookup"><span data-stu-id="c5750-104">Page limits are defined in the method that is called when the service is initialized and can be set separately for each entity set.</span></span>  
  
 <span data-ttu-id="c5750-105">啟用分頁時，摘要中的最後一個項目會包含下一頁資料的連結。</span><span class="sxs-lookup"><span data-stu-id="c5750-105">When paging is enabled, the final entry in the feed contains a link to the next page of data.</span></span> <span data-ttu-id="c5750-106">如需詳細資訊，請參閱[設定資料服務](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c5750-106">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="c5750-107">本主題顯示如何修改資料服務以啟用傳回之 `Customers` 和 `Orders` 實體集之分頁。</span><span class="sxs-lookup"><span data-stu-id="c5750-107">This topic shows how to modify a data service to enable paging of returned `Customers` and `Orders` entity sets.</span></span> <span data-ttu-id="c5750-108">本主題中的範例使用 Northwind 範例資料服務。</span><span class="sxs-lookup"><span data-stu-id="c5750-108">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="c5750-109">當您完成時，此服務會建立[WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c5750-109">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a><span data-ttu-id="c5750-110">如何啟用傳回之 Customers 和 Orders 實體集之分頁</span><span class="sxs-lookup"><span data-stu-id="c5750-110">How to enable paging of returned Customers and Orders entity sets</span></span>  
  
-   <span data-ttu-id="c5750-111">在資料服務的程式碼中，以下列程式碼取代 `InitializeService` 函數中的預留位置程式碼：</span><span class="sxs-lookup"><span data-stu-id="c5750-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a><span data-ttu-id="c5750-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5750-112">See Also</span></span>  
 [<span data-ttu-id="c5750-113">載入延後內容</span><span class="sxs-lookup"><span data-stu-id="c5750-113">Loading Deferred Content</span></span>](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 [<span data-ttu-id="c5750-114">如何： 載入分頁結果</span><span class="sxs-lookup"><span data-stu-id="c5750-114">How to: Load Paged Results</span></span>](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)
