---
title: 攔截器 (WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
ms.openlocfilehash: 7decfdd738e71a01afa8cb32604953142b46e588
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790434"
---
# <a name="interceptors-wcf-data-services"></a><span data-ttu-id="37024-102">攔截器 (WCF 資料服務)</span><span class="sxs-lookup"><span data-stu-id="37024-102">Interceptors (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="37024-103">讓應用程式攔截要求訊息，讓您可以將自訂邏輯加入至作業。</span><span class="sxs-lookup"><span data-stu-id="37024-103">enables an application to intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="37024-104">您可以使用這個自訂邏輯來驗證傳入訊息中的資料。</span><span class="sxs-lookup"><span data-stu-id="37024-104">You can use this custom logic to validate data in incoming messages.</span></span> <span data-ttu-id="37024-105">您還可以使用它進一步限制查詢要求的範圍，例如，以根據要求來插入自訂授權原則。</span><span class="sxs-lookup"><span data-stu-id="37024-105">You can also use it to further restrict the scope of a query request, such as to insert a custom authorization policy on a per request basis.</span></span>  
  
 <span data-ttu-id="37024-106">攔截由資料服務中特別屬性化的方法執行。</span><span class="sxs-lookup"><span data-stu-id="37024-106">Interception is performed by specially attributed methods in the data service.</span></span> <span data-ttu-id="37024-107">在訊息處理期間的適當時間點，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 會呼叫這些方法。</span><span class="sxs-lookup"><span data-stu-id="37024-107">These methods are called by [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] at the appropriate point in message processing.</span></span> <span data-ttu-id="37024-108">攔截器是根據每個實體集來定義，而攔截器方法則無法接受來自要求的參數，例如服務作業可以。</span><span class="sxs-lookup"><span data-stu-id="37024-108">Interceptors are defined on a per-entity set basis, and interceptor methods cannot accept parameters from the request like service operations can.</span></span> <span data-ttu-id="37024-109">查詢攔截器方法（在處理 HTTP GET 要求時呼叫）必須傳回 lambda 運算式，以判斷查詢結果是否應傳回攔截器實體集的實例。</span><span class="sxs-lookup"><span data-stu-id="37024-109">Query interceptor methods, which are called when processing an HTTP GET request, must return a lambda expression that determines whether an instance of the interceptor's entity set should be returned by the query results.</span></span> <span data-ttu-id="37024-110">資料服務會使用此運算式進一步精簡所要求的作業。</span><span class="sxs-lookup"><span data-stu-id="37024-110">This expression is used by the data service to further refine the requested operation.</span></span> <span data-ttu-id="37024-111">以下是查詢攔截器的定義範例。</span><span class="sxs-lookup"><span data-stu-id="37024-111">The following is an example definition of a query interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 <span data-ttu-id="37024-112">如需詳細資訊，請參閱[如何：攔截資料服務訊息](how-to-intercept-data-service-messages-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="37024-112">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="37024-113">變更處理非查詢作業時呼叫的攔截器，必須傳回 `void` (在 Visual Basic 為 `Nothing`)。</span><span class="sxs-lookup"><span data-stu-id="37024-113">Change interceptors, which are called when processing non-query operations, must return `void` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="37024-114">變更攔截器方法必須接受下列兩個參數：</span><span class="sxs-lookup"><span data-stu-id="37024-114">Change interceptor methods must accept the following two parameters:</span></span>  
  
1. <span data-ttu-id="37024-115">其類型相容於實體集實體類型的參數。</span><span class="sxs-lookup"><span data-stu-id="37024-115">A parameter of a type that is compatible with the entity type of the entity set.</span></span> <span data-ttu-id="37024-116">資料服務叫用變更攔截器時，此參數的值會反映出要求所傳送的實體資訊。</span><span class="sxs-lookup"><span data-stu-id="37024-116">When the data service invokes the change interceptor, the value of this parameter will reflect the entity information that is sent by the request.</span></span>  
  
2. <span data-ttu-id="37024-117">類型為 <xref:System.Data.Services.UpdateOperations> 的參數。</span><span class="sxs-lookup"><span data-stu-id="37024-117">A parameter of type <xref:System.Data.Services.UpdateOperations>.</span></span> <span data-ttu-id="37024-118">資料服務叫用變更攔截器時，此參數的值會反映出要求嘗試執行的作業。</span><span class="sxs-lookup"><span data-stu-id="37024-118">When the data service invokes the change interceptor, the value of this parameter will reflect the operation that the request is trying to perform.</span></span>  
  
 <span data-ttu-id="37024-119">以下是變更攔截器的定義範例。</span><span class="sxs-lookup"><span data-stu-id="37024-119">The following is an example definition of a change interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 <span data-ttu-id="37024-120">如需詳細資訊，請參閱[如何：攔截資料服務訊息](how-to-intercept-data-service-messages-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="37024-120">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="37024-121">攔截支援的屬性如下。</span><span class="sxs-lookup"><span data-stu-id="37024-121">The following attributes are supported for interception.</span></span>  
  
 <span data-ttu-id="37024-122">**[QueryInterceptor(** *EntitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="37024-122">**[QueryInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="37024-123">收到目標實體集資源的 HTTP GET 要求時，會呼叫套用 <xref:System.Data.Services.QueryInterceptorAttribute> 屬性的方法。</span><span class="sxs-lookup"><span data-stu-id="37024-123">Methods with the <xref:System.Data.Services.QueryInterceptorAttribute> attribute applied are called when an HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="37024-124">這些方法必須永遠以 `Expression<Func<T,bool>>` 形式傳回 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="37024-124">These methods must always return a lambda expression in the form of `Expression<Func<T,bool>>`.</span></span>  
  
 <span data-ttu-id="37024-125">**[ChangeInterceptor(** *EntitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="37024-125">**[ChangeInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="37024-126">當目標實體集資源收到 HTTP GET 要求以外的 HTTP 要求時，會呼叫套用 <xref:System.Data.Services.ChangeInterceptorAttribute> 屬性的方法。</span><span class="sxs-lookup"><span data-stu-id="37024-126">Methods with the <xref:System.Data.Services.ChangeInterceptorAttribute> attribute applied are called when an HTTP request other than HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="37024-127">這些方法必須永遠傳回 `void` (在 Visual Basic 中為 `Nothing`)。</span><span class="sxs-lookup"><span data-stu-id="37024-127">These methods must always return `void` (`Nothing` in Visual Basic).</span></span>  
  
 <span data-ttu-id="37024-128">如需詳細資訊，請參閱[如何：攔截資料服務訊息](how-to-intercept-data-service-messages-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="37024-128">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37024-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37024-129">See also</span></span>

- [<span data-ttu-id="37024-130">服務作業</span><span class="sxs-lookup"><span data-stu-id="37024-130">Service Operations</span></span>](service-operations-wcf-data-services.md)
