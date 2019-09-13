---
title: 服務作業 (WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: 583a690a-e60f-4990-8991-d6efce069d76
ms.openlocfilehash: 4f36081ef1a3eec84f3cc2ced3c629109acd6a38
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894278"
---
# <a name="service-operations-wcf-data-services"></a><span data-ttu-id="729ce-102">服務作業 (WCF 資料服務)</span><span class="sxs-lookup"><span data-stu-id="729ce-102">Service Operations (WCF Data Services)</span></span>

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] <span data-ttu-id="729ce-103">可以讓您定義資料服務上的服務作業，以公開伺服器上的方法。</span><span class="sxs-lookup"><span data-stu-id="729ce-103">enables you to define service operations on a data service to expose methods on the server.</span></span> <span data-ttu-id="729ce-104">如同其他資料服務資源，服務作業依 URI 定址。</span><span class="sxs-lookup"><span data-stu-id="729ce-104">Like other data service resources, service operations are addressed by URIs.</span></span> <span data-ttu-id="729ce-105">服務作業可讓您公開資料服務中的業務邏輯，例如實作驗證邏輯、套用以角色為基礎的安全性，或公開特殊的查詢功能。</span><span class="sxs-lookup"><span data-stu-id="729ce-105">Service operations enable you to expose business logic in a data service, such as to implement validation logic, to apply role-based security, or to expose specialized querying capabilities.</span></span> <span data-ttu-id="729ce-106">服務作業是加入至資料服務類別的方法，衍生自 <xref:System.Data.Services.DataService%601>。</span><span class="sxs-lookup"><span data-stu-id="729ce-106">Service operations are methods added to the data service class that derives from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="729ce-107">如同所有其他資料服務資源，您可以將參數提供給服務作業方法。</span><span class="sxs-lookup"><span data-stu-id="729ce-107">Like all other data service resources, you can supply parameters to the service operation method.</span></span> <span data-ttu-id="729ce-108">例如，下列服務作業 URI （以[快速入門](quickstart-wcf-data-services.md)資料服務為基礎）會將值`London`傳遞給`city`參數：</span><span class="sxs-lookup"><span data-stu-id="729ce-108">For example, the following service operation URI (based on the [quickstart](quickstart-wcf-data-services.md) data service) passes the value `London` to the `city` parameter:</span></span>

```http
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'
```

<span data-ttu-id="729ce-109">此服務作業的定義如下：</span><span class="sxs-lookup"><span data-stu-id="729ce-109">The definition for this service operation is as follows:</span></span>

[!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
[!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

<span data-ttu-id="729ce-110">您可以使用 <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> 的 <xref:System.Data.Services.DataService%601>，直接存取資料服務所使用的資料來源。</span><span class="sxs-lookup"><span data-stu-id="729ce-110">You can use the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> of the <xref:System.Data.Services.DataService%601> to directly access the data source that the data service is using.</span></span> <span data-ttu-id="729ce-111">如需詳細資訊，請參閱[如何：定義服務](how-to-define-a-service-operation-wcf-data-services.md)作業。</span><span class="sxs-lookup"><span data-stu-id="729ce-111">For more information, see [How to: Define a Service Operation](how-to-define-a-service-operation-wcf-data-services.md).</span></span>

<span data-ttu-id="729ce-112">如需如何從 .NET Framework 用戶端應用程式呼叫服務作業的詳細資訊，請參閱[呼叫服務作業](calling-service-operations-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="729ce-112">For information on how to call a service operation from a .NET Framework client application, see [Calling Service Operations](calling-service-operations-wcf-data-services.md).</span></span>

## <a name="service-operation-requirements"></a><span data-ttu-id="729ce-113">服務作業需求</span><span class="sxs-lookup"><span data-stu-id="729ce-113">Service Operation Requirements</span></span>

<span data-ttu-id="729ce-114">定義資料服務的服務作業時，適用下列需求。</span><span class="sxs-lookup"><span data-stu-id="729ce-114">The following requirements apply when defining service operations on the data service.</span></span> <span data-ttu-id="729ce-115">如果方法不符合這些需求，就不會公開成資料服務的服務作業。</span><span class="sxs-lookup"><span data-stu-id="729ce-115">If a method does not meet these requirements, it will not be exposed as a service operation for the data service.</span></span>

- <span data-ttu-id="729ce-116">該作業必須是屬於資料服務類別成員的公開執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="729ce-116">The operation must be a public instance method that is a member of the data service class.</span></span>

- <span data-ttu-id="729ce-117">該作業方法只能接受輸入參數。</span><span class="sxs-lookup"><span data-stu-id="729ce-117">The operation method may only accept input parameters.</span></span> <span data-ttu-id="729ce-118">資料服務無法存取訊息主體中傳送的資料。</span><span class="sxs-lookup"><span data-stu-id="729ce-118">Data sent in the message body cannot be accessed by the data service.</span></span>

- <span data-ttu-id="729ce-119">如果定義了參數，每個參數的類型都必須是基本類型。</span><span class="sxs-lookup"><span data-stu-id="729ce-119">If parameters are defined, the type of each parameter must be a primitive type.</span></span> <span data-ttu-id="729ce-120">非基本類型的任何資料都必須先序列化，然後再傳遞到字串參數中。</span><span class="sxs-lookup"><span data-stu-id="729ce-120">Any data of a non-primitive type must be serialized and passed into a string parameter.</span></span>

- <span data-ttu-id="729ce-121">該方法必須傳回下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="729ce-121">The method must return one of the following:</span></span>

  - <span data-ttu-id="729ce-122">`void` (在 Visual Basic 中為 `Nothing`)</span><span class="sxs-lookup"><span data-stu-id="729ce-122">`void` (`Nothing` in Visual Basic)</span></span>

  - <xref:System.Collections.Generic.IEnumerable%601>

  - <xref:System.Linq.IQueryable%601>

  - <span data-ttu-id="729ce-123">資料服務在資料模型中所公開的實體類型。</span><span class="sxs-lookup"><span data-stu-id="729ce-123">An entity type in the data model that the data service exposes.</span></span>

  - <span data-ttu-id="729ce-124">基本類別，例如整數或字串。</span><span class="sxs-lookup"><span data-stu-id="729ce-124">A primitive class such as integer or string.</span></span>

- <span data-ttu-id="729ce-125">為了支援排序、分頁和篩選等查詢選項，服務作業方法應該傳回 <xref:System.Linq.IQueryable%601>。</span><span class="sxs-lookup"><span data-stu-id="729ce-125">In order to support query options such as sorting, paging, and filtering, service operation methods should return <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="729ce-126">只傳回 <xref:System.Collections.Generic.IEnumerable%601> 的作業會拒絕對服務作業的要求 (包括查詢選項)。</span><span class="sxs-lookup"><span data-stu-id="729ce-126">Requests to service operations that include query options are rejected for operations that only return <xref:System.Collections.Generic.IEnumerable%601>.</span></span>

- <span data-ttu-id="729ce-127">服務作業必須傳回 <xref:System.Linq.IQueryable%601>，才能支援使用，導覽屬性存取相關實體。</span><span class="sxs-lookup"><span data-stu-id="729ce-127">In order to support accessing related entities by using navigation properties, the service operation must return <xref:System.Linq.IQueryable%601>.</span></span>

- <span data-ttu-id="729ce-128">此方法必須以 `[WebGet]` 或 `[WebInvoke]` 屬性標註。</span><span class="sxs-lookup"><span data-stu-id="729ce-128">The method must be annotated with the `[WebGet]` or `[WebInvoke]` attribute.</span></span>

  - <span data-ttu-id="729ce-129">`[WebGet]` 可讓您使用 GET 要求來叫用方法。</span><span class="sxs-lookup"><span data-stu-id="729ce-129">`[WebGet]` enables the method to be invoked by using a GET request.</span></span>

  - <span data-ttu-id="729ce-130">`[WebInvoke(Method = "POST")]` 可讓您使用 POST 要求來叫用方法。</span><span class="sxs-lookup"><span data-stu-id="729ce-130">`[WebInvoke(Method = "POST")]` enables the method to be invoked by using a POST request.</span></span> <span data-ttu-id="729ce-131">不支援其他 <xref:System.ServiceModel.Web.WebInvokeAttribute> 方法。</span><span class="sxs-lookup"><span data-stu-id="729ce-131">Other <xref:System.ServiceModel.Web.WebInvokeAttribute> methods are not supported.</span></span>

- <span data-ttu-id="729ce-132">服務作業可能會以 <xref:System.Data.Services.SingleResultAttribute> 加上附註，以便指定此方法的傳回值是單一實體而非實體的集合。</span><span class="sxs-lookup"><span data-stu-id="729ce-132">A service operation may be annotated with the <xref:System.Data.Services.SingleResultAttribute> that specifies that the return value from the method is a single entity rather than a collection of entities.</span></span> <span data-ttu-id="729ce-133">此項差異表示 URI 中會顯示所產生的回應序列化，以及其他導覽屬性周遊的方法。</span><span class="sxs-lookup"><span data-stu-id="729ce-133">This distinction dictates the resulting serialization of the response and the manner in which additional navigation property traversals are represented in the URI.</span></span> <span data-ttu-id="729ce-134">例如，使用 AtomPub 序列化時，單一資源類型執行個體會表示成 entry 項目，而一組執行個體則表示成 feed 項目。</span><span class="sxs-lookup"><span data-stu-id="729ce-134">For example, when using AtomPub serialization, a single resource type instance is represented as an entry element and a set of instances as a feed element.</span></span>

## <a name="addressing-service-operations"></a><span data-ttu-id="729ce-135">定址服務作業</span><span class="sxs-lookup"><span data-stu-id="729ce-135">Addressing Service Operations</span></span>

<span data-ttu-id="729ce-136">您可以將方法的名稱放入 URI 的第一個路徑區段中，以定址服務作業。</span><span class="sxs-lookup"><span data-stu-id="729ce-136">You can address service operations by placing the name of the method in the first path segment of a URI.</span></span> <span data-ttu-id="729ce-137">例如，下列 URI 會存取傳回 `GetOrdersByState` 物件之 <xref:System.Linq.IQueryable%601> 集合的 `Orders` 作業。</span><span class="sxs-lookup"><span data-stu-id="729ce-137">As an example, the following URI accesses a `GetOrdersByState` operation that returns an <xref:System.Linq.IQueryable%601> collection of `Orders` objects.</span></span>

```http
http://localhost:12345/Northwind.svc/GetOrdersByState?state='CA'&includeItems=true
```

<span data-ttu-id="729ce-138">呼叫服務作業時，系統會將參數當做查詢選項提供。</span><span class="sxs-lookup"><span data-stu-id="729ce-138">When calling a service operation, parameters are supplied as query options.</span></span> <span data-ttu-id="729ce-139">先前的服務作業會同時接受字串參數 `state` 和布林值參數 `includeItems`，以指出是否在回應中包含相關的 `Order_Detail` 物件。</span><span class="sxs-lookup"><span data-stu-id="729ce-139">The previous service operation accepts both a string parameter `state` and a Boolean parameter `includeItems` that indicates whether to include related `Order_Detail` objects in the response.</span></span>

<span data-ttu-id="729ce-140">以下是服務作業的有效傳回型別：</span><span class="sxs-lookup"><span data-stu-id="729ce-140">The following are valid return types for a service operation:</span></span>

|<span data-ttu-id="729ce-141">有效傳回類型</span><span class="sxs-lookup"><span data-stu-id="729ce-141">Valid Return Types</span></span>|<span data-ttu-id="729ce-142">URI 規則</span><span class="sxs-lookup"><span data-stu-id="729ce-142">URI Rules</span></span>|
|------------------------|---------------|
|<span data-ttu-id="729ce-143">`void` (在 Visual Basic 中為 `Nothing`)</span><span class="sxs-lookup"><span data-stu-id="729ce-143">`void` (`Nothing` in Visual Basic)</span></span><br /><br /> <span data-ttu-id="729ce-144">-或-</span><span class="sxs-lookup"><span data-stu-id="729ce-144">-or-</span></span><br /><br /> <span data-ttu-id="729ce-145">實體類型</span><span class="sxs-lookup"><span data-stu-id="729ce-145">Entity types</span></span><br /><br /> <span data-ttu-id="729ce-146">-或-</span><span class="sxs-lookup"><span data-stu-id="729ce-146">-or-</span></span><br /><br /> <span data-ttu-id="729ce-147">基本類型</span><span class="sxs-lookup"><span data-stu-id="729ce-147">Primitive types</span></span>|<span data-ttu-id="729ce-148">URI 必須是單一路徑區段，且為服務作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="729ce-148">The URI must be a single path segment that is the name of the service operation.</span></span> <span data-ttu-id="729ce-149">不允許使用查詢選項。</span><span class="sxs-lookup"><span data-stu-id="729ce-149">Query options are not allowed.</span></span>|
|<xref:System.Collections.Generic.IEnumerable%601>|<span data-ttu-id="729ce-150">URI 必須是單一路徑區段，且為服務作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="729ce-150">The URI must be a single path segment that is the name of the service operation.</span></span> <span data-ttu-id="729ce-151">因為結果類型不是 <xref:System.Linq.IQueryable%601> 類型，因此不允許查詢選項。</span><span class="sxs-lookup"><span data-stu-id="729ce-151">Because the result type is not an <xref:System.Linq.IQueryable%601> type, query options are not allowed.</span></span>|
|<xref:System.Linq.IQueryable%601>|<span data-ttu-id="729ce-152">除了為服務作業名稱的路徑外，允許查詢其他路徑區段。</span><span class="sxs-lookup"><span data-stu-id="729ce-152">Query path segments in addition to the path that is the name of the service operation are allowed.</span></span> <span data-ttu-id="729ce-153">亦允許使用查詢選項。</span><span class="sxs-lookup"><span data-stu-id="729ce-153">Query options are also allowed.</span></span>|

<span data-ttu-id="729ce-154">此外，您可以將其他路徑區段或查詢選項加入至 URI，端視服務作業的傳回類型而定。</span><span class="sxs-lookup"><span data-stu-id="729ce-154">Additional path segments or query options may be added to the URI depending on the return type of the service operation.</span></span> <span data-ttu-id="729ce-155">例如，下列 URI 會存取傳回 `GetOrdersByCity` 物件之 <xref:System.Linq.IQueryable%601> 集合的 `Orders` 作業 (以 `RequiredDate` 遞減方式排序) 以及相關的 `Order_Details` 物件：</span><span class="sxs-lookup"><span data-stu-id="729ce-155">For example, the following URI accesses a `GetOrdersByCity` operation that returns an <xref:System.Linq.IQueryable%601> collection of `Orders` objects, ordered by `RequiredDate` in descending order, along with the related `Order_Details` objects:</span></span>

```http
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc
```

## <a name="service-operations-access-control"></a><span data-ttu-id="729ce-156">服務作業存取控制</span><span class="sxs-lookup"><span data-stu-id="729ce-156">Service Operations Access Control</span></span>

<span data-ttu-id="729ce-157">服務作業的服務範圍可視性由 <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> 類別的 <xref:System.Data.Services.IDataServiceConfiguration> 方法控制，與使用 <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A> 方法控制實體集可視性的方式非常相似。</span><span class="sxs-lookup"><span data-stu-id="729ce-157">Service-wide visibility of service operations is controlled by the <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> method on the <xref:System.Data.Services.IDataServiceConfiguration> class in much the same way that entity set visibility is controlled by using the <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A> method.</span></span> <span data-ttu-id="729ce-158">例如，資料服務定義中的下列程式碼行可讓您存取 `CustomersByCity` 服務作業。</span><span class="sxs-lookup"><span data-stu-id="729ce-158">For example, the following line of code in the data service definition enables access to the `CustomersByCity` service operation.</span></span>

[!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
[!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

> [!NOTE]
> <span data-ttu-id="729ce-159">如果服務作業具有已透過現制存取基礎實體集隱藏的傳回型別，則用戶端應用程式就無法使用服務作業。</span><span class="sxs-lookup"><span data-stu-id="729ce-159">If a service operation has a return type that has been hidden by restricting access on the underlying entity sets, then the service operation will not be available to client applications.</span></span>

<span data-ttu-id="729ce-160">如需詳細資訊，請參閱[如何：定義服務](how-to-define-a-service-operation-wcf-data-services.md)作業。</span><span class="sxs-lookup"><span data-stu-id="729ce-160">For more information, see [How to: Define a Service Operation](how-to-define-a-service-operation-wcf-data-services.md).</span></span>

## <a name="raising-exceptions"></a><span data-ttu-id="729ce-161">引發例外狀況</span><span class="sxs-lookup"><span data-stu-id="729ce-161">Raising Exceptions</span></span>

<span data-ttu-id="729ce-162">每當您在資料服務執行中引發例外狀況時，建議您使用 <xref:System.Data.Services.DataServiceException> 類別。</span><span class="sxs-lookup"><span data-stu-id="729ce-162">We recommend that you use the <xref:System.Data.Services.DataServiceException> class whenever you raise an exception in the data service execution.</span></span> <span data-ttu-id="729ce-163">這是因為資料服務執行階段知道如何將此例外狀況物件的屬性正確對應到 HTTP 回應訊息。</span><span class="sxs-lookup"><span data-stu-id="729ce-163">This is because the data service runtime knows how to map properties of this exception object correctly to the HTTP response message.</span></span> <span data-ttu-id="729ce-164">當您在服務作業中引發 <xref:System.Data.Services.DataServiceException> 時，傳回的例外狀況會以 <xref:System.Reflection.TargetInvocationException> 包裝。</span><span class="sxs-lookup"><span data-stu-id="729ce-164">When you raise a <xref:System.Data.Services.DataServiceException> in a service operation, the returned exception is wrapped in a <xref:System.Reflection.TargetInvocationException>.</span></span> <span data-ttu-id="729ce-165">若要傳回沒有以 <xref:System.Data.Services.DataServiceException> 括住的基礎 <xref:System.Reflection.TargetInvocationException>，您必須覆寫 <xref:System.Data.Services.DataService%601.HandleException%2A> 中的 <xref:System.Data.Services.DataService%601> 方法、從 <xref:System.Data.Services.DataServiceException> 擷取 <xref:System.Reflection.TargetInvocationException>，然後將其當做最上層錯誤傳回，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="729ce-165">To return the base <xref:System.Data.Services.DataServiceException> without the enclosing <xref:System.Reflection.TargetInvocationException>, you must override the <xref:System.Data.Services.DataService%601.HandleException%2A> method in the <xref:System.Data.Services.DataService%601>, extract the <xref:System.Data.Services.DataServiceException> from the <xref:System.Reflection.TargetInvocationException>, and return it as the top-level error, as in the following example:</span></span>

[!code-csharp[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#handleexceptions)]
[!code-vb[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#handleexceptions)]

## <a name="see-also"></a><span data-ttu-id="729ce-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="729ce-166">See also</span></span>

- [<span data-ttu-id="729ce-167">攔截器</span><span class="sxs-lookup"><span data-stu-id="729ce-167">Interceptors</span></span>](interceptors-wcf-data-services.md)
