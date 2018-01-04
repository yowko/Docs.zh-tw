---
title: "實作服務合約"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b4085e23120ad654121f33111eda68276259096
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-service-contracts"></a><span data-ttu-id="6557e-102">實作服務合約</span><span class="sxs-lookup"><span data-stu-id="6557e-102">Implementing Service Contracts</span></span>
<span data-ttu-id="6557e-103">服務是一種類別，會在一或多個端點公開可供用戶端使用的功能。</span><span class="sxs-lookup"><span data-stu-id="6557e-103">A service is a class that exposes functionality available to clients at one or more endpoints.</span></span> <span data-ttu-id="6557e-104">如果要建立服務，請寫入實作 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 合約的類別。</span><span class="sxs-lookup"><span data-stu-id="6557e-104">To create a service, write a class that implements a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] contract.</span></span> <span data-ttu-id="6557e-105">您可以使用下列其中一種作法：</span><span class="sxs-lookup"><span data-stu-id="6557e-105">You can do this in one of two ways.</span></span> <span data-ttu-id="6557e-106">您可以將合約另外定義為介面，然後建立實作該介面的類別。</span><span class="sxs-lookup"><span data-stu-id="6557e-106">You can define the contract separately as an interface and then create a class that implements that interface.</span></span> <span data-ttu-id="6557e-107">或者，您可以將 <xref:System.ServiceModel.ServiceContractAttribute> 屬性置於類別本身，而將 <xref:System.ServiceModel.OperationContractAttribute> 屬性置於可供服務之用戶端使用的方法上，以直接建立類別和合約。</span><span class="sxs-lookup"><span data-stu-id="6557e-107">Alternatively, you can create the class and contract directly by placing the <xref:System.ServiceModel.ServiceContractAttribute> attribute on the class itself and the <xref:System.ServiceModel.OperationContractAttribute> attribute on the methods available to the clients of the service.</span></span>  
  
## <a name="creating-a-service-class"></a><span data-ttu-id="6557e-108">建立服務類別</span><span class="sxs-lookup"><span data-stu-id="6557e-108">Creating a service class</span></span>  
 <span data-ttu-id="6557e-109">以下是實作已另外定義之 `IMath` 合約的服務範例。</span><span class="sxs-lookup"><span data-stu-id="6557e-109">The following is an example of a service that implements an `IMath` contract that has been defined separately.</span></span>  
  
```csharp  
// Define the IMath contract.  
[ServiceContract]  
public interface IMath  
{  
    [OperationContract]   
    double Add(double A, double B);  
  
    [OperationContract]  
    double Multiply (double A, double B);  
}  
  
// Implement the IMath contract in the MathService class.  
public class MathService : IMath  
{  
    public double Add (double A, double B) { return A + B; }  
    public double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 <span data-ttu-id="6557e-110">或者，服務可以直接公開合約。</span><span class="sxs-lookup"><span data-stu-id="6557e-110">Alternatively, a service can expose a contract directly.</span></span> <span data-ttu-id="6557e-111">以下是定義及實作 `MathService` 合約的服務類別範例。</span><span class="sxs-lookup"><span data-stu-id="6557e-111">The following is an example of a service class that defines and implements a `MathService` contract.</span></span>  
  
```csharp  
// Define the MathService contract directly on the service class.  
[ServiceContract]  
class MathService  
{  
    [OperationContract]  
    public double Add(double A, double B) { return A + B; }  
    [OperationContract]  
    private double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 <span data-ttu-id="6557e-112">請注意，前述服務會公開不同的合約，因為合約名稱不同。</span><span class="sxs-lookup"><span data-stu-id="6557e-112">Note that the preceding services expose different contracts because the contract names are different.</span></span> <span data-ttu-id="6557e-113">在第一個案例中，公開的合約名為 "`IMath`"，而在第二個案例中，合約名為 "`MathService`"。</span><span class="sxs-lookup"><span data-stu-id="6557e-113">In the first case, the exposed contract is named "`IMath`" while in the second case the contract is named "`MathService`".</span></span>  
  
 <span data-ttu-id="6557e-114">您可以在服務和作業實作層級進行一些設定，例如並行和執行個體。</span><span class="sxs-lookup"><span data-stu-id="6557e-114">You can set a few things at the service and operation implementation levels, such as concurrency and instancing.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="6557e-115">[設計和實作服務](../../../docs/framework/wcf/designing-and-implementing-services.md)。</span><span class="sxs-lookup"><span data-stu-id="6557e-115"> [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md).</span></span>  
  
 <span data-ttu-id="6557e-116">在實作服務合約之後，必須為服務建立一或多個端點。</span><span class="sxs-lookup"><span data-stu-id="6557e-116">After implementing a service contract, you must create one or more endpoints for the service.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="6557e-117">[端點建立概觀](../../../docs/framework/wcf/endpoint-creation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="6557e-117"> [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="6557e-118">執行服務，請參閱[裝載服務](../../../docs/framework/wcf/hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="6557e-118"> how to run a service, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6557e-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="6557e-119">See Also</span></span>  
 [<span data-ttu-id="6557e-120">設計與實作服務</span><span class="sxs-lookup"><span data-stu-id="6557e-120">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [<span data-ttu-id="6557e-121">如何：使用合約類別來建立服務</span><span class="sxs-lookup"><span data-stu-id="6557e-121">How to: Create a Service with a Contract Class</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)  
 [<span data-ttu-id="6557e-122">如何：使用合約介面來建立服務</span><span class="sxs-lookup"><span data-stu-id="6557e-122">How to: Create a Service with a Contract Interface</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)  
 [<span data-ttu-id="6557e-123">指定服務執行階段行為</span><span class="sxs-lookup"><span data-stu-id="6557e-123">Specifying Service Run-Time Behavior</span></span>](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
