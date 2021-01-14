---
title: WCF Data Services 通訊協定實作詳細資訊
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: a9b996671f2d8b57593f80fb13e966c5f03a2801
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190386"
---
# <a name="wcf-data-services-protocol-implementation-details"></a><span data-ttu-id="34b98-102">WCF Data Services 通訊協定實作詳細資訊</span><span class="sxs-lookup"><span data-stu-id="34b98-102">WCF Data Services Protocol Implementation Details</span></span>

## <a name="odata-protocol-implementation-details"></a><span data-ttu-id="34b98-103">OData 通訊協定實作詳細資訊</span><span class="sxs-lookup"><span data-stu-id="34b98-103">OData Protocol Implementation Details</span></span>  

<span data-ttu-id="34b98-104">開放式資料通訊協定 (OData) 要求執行通訊協定的資料服務提供特定一組最基本的功能。</span><span class="sxs-lookup"><span data-stu-id="34b98-104">The Open Data Protocol (OData) requires that a data service that implements the protocol provide a certain minimum set of functionalities.</span></span> <span data-ttu-id="34b98-105">這些功能在「應該」和「必須」方面的通訊協定檔中有所描述。</span><span class="sxs-lookup"><span data-stu-id="34b98-105">These functionalities are described in the protocol documents in terms of "should" and "must".</span></span> <span data-ttu-id="34b98-106">其他選擇性功能則是以「可能」描述。</span><span class="sxs-lookup"><span data-stu-id="34b98-106">Other optional functionality is described in terms of "may".</span></span> <span data-ttu-id="34b98-107">本文描述 WCF Data Services 目前未執行的這些選用功能。</span><span class="sxs-lookup"><span data-stu-id="34b98-107">This article describes these optional functionalities that are not currently implemented by WCF Data Services.</span></span>
  
### <a name="support-for-the-format-query-option"></a><span data-ttu-id="34b98-108">支援 $format 查詢選項</span><span class="sxs-lookup"><span data-stu-id="34b98-108">Support for the $format Query Option</span></span>  

 <span data-ttu-id="34b98-109">OData 通訊協定支援 JavaScript 標記法 (JSON) 和 Atom 摘要，而 OData 則提供 `$format` 系統查詢選項，以允許用戶端要求回應摘要的格式。</span><span class="sxs-lookup"><span data-stu-id="34b98-109">The OData protocol supports both JavaScript Notation (JSON) and Atom feeds, and OData provides the `$format` system query option to allow a client to request the format of the response feed.</span></span> <span data-ttu-id="34b98-110">此系統查詢選項 (如果資料服務支援) 必須覆寫要求之 Accept 標頭的值。</span><span class="sxs-lookup"><span data-stu-id="34b98-110">This system query option, if supported by the data service, must override the value of the Accept header of the request.</span></span> <span data-ttu-id="34b98-111">WCF Data Services 支援同時傳回 JSON 和 Atom 摘要。</span><span class="sxs-lookup"><span data-stu-id="34b98-111">WCF Data Services supports returning both JSON and Atom feeds.</span></span> <span data-ttu-id="34b98-112">不過，預設實作不支援 `$format` 查詢選項，而且僅使用 Accept 標頭的值決定回應的格式。</span><span class="sxs-lookup"><span data-stu-id="34b98-112">However, the default implementation does not support the `$format` query option and uses only the value of the Accept header to determine the format of the response.</span></span> <span data-ttu-id="34b98-113">在某些情況下，您的資料服務可能需要支援 `$format` 查詢選項，例如，用戶端無法設定 Accept 標頭時。</span><span class="sxs-lookup"><span data-stu-id="34b98-113">There are cases when your data service may need to support the `$format` query option, such as when clients cannot set the Accept header.</span></span> <span data-ttu-id="34b98-114">為支援這些案例，您必須擴充資料服務來處理 URI 中的這個選項。</span><span class="sxs-lookup"><span data-stu-id="34b98-114">To support these scenarios, you must extend your data service to handle this option in the URI.</span></span>
  
## <a name="wcf-data-services-behaviors"></a><span data-ttu-id="34b98-115">WCF Data Services 行為</span><span class="sxs-lookup"><span data-stu-id="34b98-115">WCF Data Services Behaviors</span></span>  

 <span data-ttu-id="34b98-116">OData 通訊協定未明確定義下列 WCF Data Services 行為：</span><span class="sxs-lookup"><span data-stu-id="34b98-116">The following WCF Data Services behaviors are not explicitly defined by the OData protocol:</span></span>  
  
### <a name="default-sorting-behavior"></a><span data-ttu-id="34b98-117">預設排序行為</span><span class="sxs-lookup"><span data-stu-id="34b98-117">Default Sorting Behavior</span></span>  

 <span data-ttu-id="34b98-118">當傳送至資料服務的查詢要求包含 `$top` 或 `$skip` 系統查詢選項，但不包含 `$orderby` 系統查詢選項時，傳回的摘要會依索引鍵屬性，以遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="34b98-118">When a query request that is sent to the data service includes a `$top` or `$skip` system query option and does not include the `$orderby` system query option, the returned feed is sorted by the key properties, in ascending order.</span></span> <span data-ttu-id="34b98-119">這是因為您需要排序，才能確保結果分頁正確。</span><span class="sxs-lookup"><span data-stu-id="34b98-119">This is because ordering is required to ensure the correct paging of results.</span></span> <span data-ttu-id="34b98-120">若要這樣做，資料服務要將排序運算式加入至查詢中。</span><span class="sxs-lookup"><span data-stu-id="34b98-120">To do this, the data service adds an ordering expression to the query.</span></span> <span data-ttu-id="34b98-121">在資料服務中啟用伺服器驅動型分頁時，也會發生這個行為。</span><span class="sxs-lookup"><span data-stu-id="34b98-121">This behavior also occurs when server-driven paging is enabled in the data service.</span></span> <span data-ttu-id="34b98-122">如需詳細資訊，請參閱設定 [資料服務](configuring-the-data-service-wcf-data-services.md)。若要控制傳回之摘要的順序，您應該包含 `$orderby` 在查詢 URI 中。</span><span class="sxs-lookup"><span data-stu-id="34b98-122">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).To control the ordering of the returned feed, you should include `$orderby` in the query URI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34b98-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34b98-123">See also</span></span>

- [<span data-ttu-id="34b98-124">定義 WCF 資料服務</span><span class="sxs-lookup"><span data-stu-id="34b98-124">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
- [<span data-ttu-id="34b98-125">WCF 資料服務用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="34b98-125">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
