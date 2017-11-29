---
title: "要求-回覆服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a38a90d4e9ec249f91e8bfda88c646c006890d8d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="request-reply-services"></a><span data-ttu-id="7f595-102">要求-回覆服務</span><span class="sxs-lookup"><span data-stu-id="7f595-102">Request-Reply Services</span></span>
<span data-ttu-id="7f595-103">要求-回覆服務是 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中作業合約的預設類型。</span><span class="sxs-lookup"><span data-stu-id="7f595-103">Request-reply services are the default type of operation contract in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="7f595-104">用戶端呼叫服務作業然後等候服務回應。</span><span class="sxs-lookup"><span data-stu-id="7f595-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="7f595-105">您可以使用同步 (用戶端會鎖定，直到其接收到來自服務或呼叫階段的回應) 或非同步 (用戶端會呼叫服務作業、繼續工作，然後接收來自其他執行緒服務的回應) 方式呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="7f595-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="7f595-106">若要建立要求-回覆服務合約，請定義服務合約然後將 <xref:System.ServiceModel.OperationContractAttribute> 類別套用至每個作業，如同下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="7f595-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="7f595-107">您不需要將 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 屬性設定為 `false`，因為這是預設行為。</span><span class="sxs-lookup"><span data-stu-id="7f595-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f595-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f595-108">See Also</span></span>  
 [<span data-ttu-id="7f595-109">單向服務</span><span class="sxs-lookup"><span data-stu-id="7f595-109">One-Way Services</span></span>](../../../../docs/framework/wcf/feature-details/one-way-services.md)  
 [<span data-ttu-id="7f595-110">雙工服務</span><span class="sxs-lookup"><span data-stu-id="7f595-110">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
