---
title: HOW TO：啟用資料服務結果分頁（WCF Data Services）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 82b4d0fd3531778ab494d6526a56b092edf9481a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780048"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a><span data-ttu-id="4eb1d-102">作法：啟用資料服務結果分頁（WCF Data Services）</span><span class="sxs-lookup"><span data-stu-id="4eb1d-102">How to: Enable Paging of Data Service Results (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] <span data-ttu-id="4eb1d-103">可讓您限制資料服務查詢所傳回的實體數目。</span><span class="sxs-lookup"><span data-stu-id="4eb1d-103">enables you to limit the number of entities returned by a data service query.</span></span> <span data-ttu-id="4eb1d-104">當服務已初始化且可針對每個實體集分別設定服務時，分頁限制會定義於所呼叫的方法中。</span><span class="sxs-lookup"><span data-stu-id="4eb1d-104">Page limits are defined in the method that is called when the service is initialized and can be set separately for each entity set.</span></span>  
  
 <span data-ttu-id="4eb1d-105">啟用分頁時，摘要中的最後一個項目會包含下一頁資料的連結。</span><span class="sxs-lookup"><span data-stu-id="4eb1d-105">When paging is enabled, the final entry in the feed contains a link to the next page of data.</span></span> <span data-ttu-id="4eb1d-106">如需詳細資訊，請參閱設定[資料服務](configuring-the-data-service-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="4eb1d-106">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="4eb1d-107">本主題顯示如何修改資料服務以啟用傳回之 `Customers` 和 `Orders` 實體集之分頁。</span><span class="sxs-lookup"><span data-stu-id="4eb1d-107">This topic shows how to modify a data service to enable paging of returned `Customers` and `Orders` entity sets.</span></span> <span data-ttu-id="4eb1d-108">本主題中的範例使用 Northwind 範例資料服務。</span><span class="sxs-lookup"><span data-stu-id="4eb1d-108">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="4eb1d-109">此服務會在您完成[WCF Data Services 快速入門](quickstart-wcf-data-services.md)時建立。</span><span class="sxs-lookup"><span data-stu-id="4eb1d-109">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a><span data-ttu-id="4eb1d-110">如何啟用傳回之 Customers 和 Orders 實體集之分頁</span><span class="sxs-lookup"><span data-stu-id="4eb1d-110">How to enable paging of returned Customers and Orders entity sets</span></span>  
  
- <span data-ttu-id="4eb1d-111">在資料服務的程式碼中，以下列程式碼取代 `InitializeService` 函數中的預留位置程式碼：</span><span class="sxs-lookup"><span data-stu-id="4eb1d-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a><span data-ttu-id="4eb1d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4eb1d-112">See also</span></span>

- [<span data-ttu-id="4eb1d-113">載入延後內容</span><span class="sxs-lookup"><span data-stu-id="4eb1d-113">Loading Deferred Content</span></span>](loading-deferred-content-wcf-data-services.md)
- [<span data-ttu-id="4eb1d-114">如何：載入已分頁的結果</span><span class="sxs-lookup"><span data-stu-id="4eb1d-114">How to: Load Paged Results</span></span>](how-to-load-paged-results-wcf-data-services.md)
