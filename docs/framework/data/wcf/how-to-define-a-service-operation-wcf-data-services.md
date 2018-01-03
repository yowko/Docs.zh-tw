---
title: "如何：定義服務作業 (WCF 資料服務)"
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
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03dc0b774fe6c3e077fa539fc14c7df4a1fb448d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a><span data-ttu-id="af95e-102">如何：定義服務作業 (WCF 資料服務)</span><span class="sxs-lookup"><span data-stu-id="af95e-102">How to: Define a Service Operation (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="af95e-103"> 會將伺服器上定義的方法公開為服務作業。</span><span class="sxs-lookup"><span data-stu-id="af95e-103"> expose methods that are defined on the server as service operations.</span></span> <span data-ttu-id="af95e-104">服務作業可讓資料服務，以提供透過 URI 在伺服器上定義的方法存取。</span><span class="sxs-lookup"><span data-stu-id="af95e-104">Service operations allow a data service to provide access through a URI to a method that is defined on the server.</span></span> <span data-ttu-id="af95e-105">若要定義服務作業，請套用 [`WebGet]`或`[WebInvoke]`屬性加入方法。</span><span class="sxs-lookup"><span data-stu-id="af95e-105">To define a service operation, apply the [`WebGet]` or `[WebInvoke]` attribute to the method.</span></span> <span data-ttu-id="af95e-106">若要支援查詢運算子，服務作業必須傳回<xref:System.Linq.IQueryable%601>執行個體。</span><span class="sxs-lookup"><span data-stu-id="af95e-106">To support query operators, the service operation must return an <xref:System.Linq.IQueryable%601> instance.</span></span> <span data-ttu-id="af95e-107">服務作業可以透過 <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> 上的 <xref:System.Data.Services.DataService%601> 屬性存取基礎資料資源。</span><span class="sxs-lookup"><span data-stu-id="af95e-107">Service operations may access the underlying data source through the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> property on the <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="af95e-108">如需詳細資訊，請參閱[服務作業](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="af95e-108">For more information, see [Service Operations](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="af95e-109">本主題的範例定義名為 `GetOrdersByCity` 的服務作業，此服務作業會針對 <xref:System.Linq.IQueryable%601> 執行個體傳回篩選過的 `Orders`，以及相關的 `Order_Details` 物件。</span><span class="sxs-lookup"><span data-stu-id="af95e-109">The example in this topic defines a service operation named `GetOrdersByCity` that returns a filtered <xref:System.Linq.IQueryable%601> instance of `Orders` and related `Order_Details` objects.</span></span> <span data-ttu-id="af95e-110">此範例存取的 <xref:System.Data.Objects.ObjectContext> 執行個體為 Northwind 範例資料服務的資料來源。</span><span class="sxs-lookup"><span data-stu-id="af95e-110">The example accesses the <xref:System.Data.Objects.ObjectContext> instance that is the data source for the Northwind sample data service.</span></span> <span data-ttu-id="af95e-111">當您完成時，此服務會建立[WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="af95e-111">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a><span data-ttu-id="af95e-112">在 Northwind 資料服務中定義服務作業</span><span class="sxs-lookup"><span data-stu-id="af95e-112">To define a service operation in the Northwind data service</span></span>  
  
1.  <span data-ttu-id="af95e-113">在 Northwind 資料服務專案中，開啟 Northwind.svc 檔案。</span><span class="sxs-lookup"><span data-stu-id="af95e-113">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2.  <span data-ttu-id="af95e-114">在 `Northwind` 類別中，定義名為 `GetOrdersByCity` 的服務作業方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="af95e-114">In the `Northwind` class, define a service operation method named `GetOrdersByCity` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
3.  <span data-ttu-id="af95e-115">在 `InitializeService` 類別的`Northwind` 方法中加入下列程式碼，以存取服務作業：</span><span class="sxs-lookup"><span data-stu-id="af95e-115">In the `InitializeService` method of the `Northwind` class, add the following code to enable access to the service operation:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
### <a name="to-query-the-getordersbycity-service-operation"></a><span data-ttu-id="af95e-116">查詢 GetOrdersByCity 服務作業</span><span class="sxs-lookup"><span data-stu-id="af95e-116">To query the GetOrdersByCity service operation</span></span>  
  
-   <span data-ttu-id="af95e-117">在 Web 瀏覽器中輸入下列其中一個 URI，叫用在下列範例中定義的服務作業：</span><span class="sxs-lookup"><span data-stu-id="af95e-117">In a Web browser, enter one of the following URIs to invoke the service operation that is defined in the following example:</span></span>  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`  
  
## <a name="example"></a><span data-ttu-id="af95e-118">範例</span><span class="sxs-lookup"><span data-stu-id="af95e-118">Example</span></span>  
 <span data-ttu-id="af95e-119">下列範例會在 Northwind 資料服務實作名為 `GetOrderByCity` 的服務作業。</span><span class="sxs-lookup"><span data-stu-id="af95e-119">The following example implements a service operation named `GetOrderByCity` on the Northwind data service.</span></span> <span data-ttu-id="af95e-120">此作業使用 ADO.NET Entity Framework，根據所提供的城市名稱傳回一組 `Orders` 和相關的 `Order_Details` 物件，做為 <xref:System.Linq.IQueryable%601> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="af95e-120">This operation uses the ADO.NET Entity Framework to return a set of `Orders` and related `Order_Details` objects as an <xref:System.Linq.IQueryable%601> instance based on the provided city name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af95e-121">此服務作業端點支援查詢運算子，因為方法會傳回 <xref:System.Linq.IQueryable%601> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="af95e-121">Query operators are supported on this service operation endpoint because the method returns an <xref:System.Linq.IQueryable%601> instance.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperation)]
 [!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperation)]  
  
## <a name="see-also"></a><span data-ttu-id="af95e-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="af95e-122">See Also</span></span>  
 [<span data-ttu-id="af95e-123">定義 WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="af95e-123">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
