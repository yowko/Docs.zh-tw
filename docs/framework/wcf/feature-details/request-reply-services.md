---
title: 要求-回覆服務
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: 1ff11b1cae4ec8f6fe886a55cb0add27831048d0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177810"
---
# <a name="request-reply-services"></a><span data-ttu-id="c3e9e-102">要求-回覆服務</span><span class="sxs-lookup"><span data-stu-id="c3e9e-102">Request-Reply Services</span></span>
<span data-ttu-id="c3e9e-103">要求-回覆服務是 Windows Communication Foundation (WCF) 中的作業合約的預設類型。</span><span class="sxs-lookup"><span data-stu-id="c3e9e-103">Request-reply services are the default type of operation contract in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="c3e9e-104">用戶端呼叫服務作業然後等候服務回應。</span><span class="sxs-lookup"><span data-stu-id="c3e9e-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="c3e9e-105">您可以使用同步 (用戶端會鎖定，直到其接收到來自服務或呼叫階段的回應) 或非同步 (用戶端會呼叫服務作業、繼續工作，然後接收來自其他執行緒服務的回應) 方式呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="c3e9e-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="c3e9e-106">若要建立要求-回覆服務合約，請定義服務合約然後將 <xref:System.ServiceModel.OperationContractAttribute> 類別套用至每個作業，如同下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="c3e9e-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="c3e9e-107">您不需要將 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 屬性設定為 `false`，因為這是預設行為。</span><span class="sxs-lookup"><span data-stu-id="c3e9e-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3e9e-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3e9e-108">See also</span></span>

- [<span data-ttu-id="c3e9e-109">單向服務</span><span class="sxs-lookup"><span data-stu-id="c3e9e-109">One-Way Services</span></span>](../../../../docs/framework/wcf/feature-details/one-way-services.md)
- [<span data-ttu-id="c3e9e-110">雙工服務</span><span class="sxs-lookup"><span data-stu-id="c3e9e-110">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
