---
title: WCF Web HTTP 錯誤處理
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: 834c642e36e1551081dbe1f14529ed7596df1360
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152694"
---
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="303a4-102">WCF Web HTTP 錯誤處理</span><span class="sxs-lookup"><span data-stu-id="303a4-102">WCF Web HTTP Error Handling</span></span>
<span data-ttu-id="303a4-103">Windows Communication Foundation (WCF) Web HTTP 錯誤處理可讓您從指定的 HTTP 狀態碼，並傳回錯誤詳細資料，使用相同的格式與作業 （例如 XML 或 JSON） 的 WCF Web HTTP 服務傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="303a4-103">Windows Communication Foundation (WCF) Web HTTP error handling enables you to return errors from WCF Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="303a4-104">WCF Web HTTP 錯誤處理</span><span class="sxs-lookup"><span data-stu-id="303a4-104">WCF Web HTTP Error Handling</span></span>  
 <span data-ttu-id="303a4-105"><xref:System.ServiceModel.Web.WebFaultException> 類別會定義一個建構函式，供您指定 HTTP 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="303a4-105">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="303a4-106">然後，這個狀態碼會傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="303a4-106">This status code is then returned to the client.</span></span> <span data-ttu-id="303a4-107"><xref:System.ServiceModel.Web.WebFaultException> 類別的泛型版本 <xref:System.ServiceModel.Web.WebFaultException%601> 可讓您傳回使用者定義的型別，其中包含已發生錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="303a4-107">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="303a4-108">此自訂物件會使用作業指定的格式序列化，然後傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="303a4-108">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="303a4-109">下列範例示範如何傳回 HTTP 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="303a4-109">The following example shows how to return an HTTP status code.</span></span>  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 <span data-ttu-id="303a4-110">下列範例示範如何傳回 HTTP 狀態碼，以及使用者定義型別中的額外資訊。</span><span class="sxs-lookup"><span data-stu-id="303a4-110">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> `MyErrorDetail` <span data-ttu-id="303a4-111">是使用者定義型別，其中包含有關發生之錯誤的額外資訊。</span><span class="sxs-lookup"><span data-stu-id="303a4-111">is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
```  
Public string Operation2()  
   // Operation logic  
   // ...   MyErrorDetail detail = new MyErrorDetail  
   {  
      Message = "Error Message",  
      ErrorCode = 123,  
   }  
   throw new WebFaultException<MyErrorDetail>(detail, HttpStatusCode.Forbidden);  
}  
```  
  
 <span data-ttu-id="303a4-112">前一個程式碼會傳回 HTTP 回應，附上禁止狀態碼與本文，而本文中會包含 `MyErrorDetails` 物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="303a4-112">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="303a4-113">`MyErrorDetails` 物件的格式取決於：</span><span class="sxs-lookup"><span data-stu-id="303a4-113">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
-   <span data-ttu-id="303a4-114">服務作業所指定 `ResponseFormat` 或 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性之 <xref:System.ServiceModel.Web.WebInvokeAttribute> 參數的值。</span><span class="sxs-lookup"><span data-stu-id="303a4-114">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
-   <span data-ttu-id="303a4-115"><xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> 的值。</span><span class="sxs-lookup"><span data-stu-id="303a4-115">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
-   <span data-ttu-id="303a4-116">透過存取 <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> 之 <xref:System.ServiceModel.Web.OutgoingWebResponseContext> 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="303a4-116">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 <span data-ttu-id="303a4-117">如需有關這些值如何影響作業的格式設定的詳細資訊，請參閱[WCF Web HTTP 格式化](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)。</span><span class="sxs-lookup"><span data-stu-id="303a4-117">For more information about how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>  
  
 <xref:System.ServiceModel.Web.WebFaultException> <span data-ttu-id="303a4-118">是<xref:System.ServiceModel.FaultException>，因此可以當成錯誤例外狀況的程式設計模型的公開 SOAP 端點，以及 web HTTP 端點的服務。</span><span class="sxs-lookup"><span data-stu-id="303a4-118">is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="303a4-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="303a4-119">See also</span></span>

- [<span data-ttu-id="303a4-120">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="303a4-120">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="303a4-121">WCF Web HTTP 格式化</span><span class="sxs-lookup"><span data-stu-id="303a4-121">WCF Web HTTP Formatting</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)
- [<span data-ttu-id="303a4-122">定義並指定錯誤</span><span class="sxs-lookup"><span data-stu-id="303a4-122">Defining and Specifying Faults</span></span>](../../../../docs/framework/wcf/defining-and-specifying-faults.md)
- [<span data-ttu-id="303a4-123">處理例外狀況和錯誤</span><span class="sxs-lookup"><span data-stu-id="303a4-123">Handling Exceptions and Faults</span></span>](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [<span data-ttu-id="303a4-124">傳送和接收錯誤</span><span class="sxs-lookup"><span data-stu-id="303a4-124">Sending and Receiving Faults</span></span>](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
