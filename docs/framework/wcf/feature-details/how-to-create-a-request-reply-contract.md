---
title: HOW TO：建立要求-回覆合約
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 76a3bbb9415a34218896bc561066c7ac4a30e6b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489569"
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="5e689-102">HOW TO：建立要求-回覆合約</span><span class="sxs-lookup"><span data-stu-id="5e689-102">How to: Create a Request-Reply Contract</span></span>
<span data-ttu-id="5e689-103">要求-回覆合約會指定一個方法以傳回回覆。</span><span class="sxs-lookup"><span data-stu-id="5e689-103">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="5e689-104">回覆必須在此合約條件下進行傳送並與要求相互關聯。</span><span class="sxs-lookup"><span data-stu-id="5e689-104">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="5e689-105">即便該方法未傳回任何回覆 (在 C# 為 `void`，在 Visual Basic 為 `Sub`)，基礎結構還是會建立空訊息並傳送給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="5e689-105">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="5e689-106">若要避免傳送空的回覆訊息，請使用單向作業合約。</span><span class="sxs-lookup"><span data-stu-id="5e689-106">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="5e689-107">若要建立要求-回覆合約</span><span class="sxs-lookup"><span data-stu-id="5e689-107">To create a request-reply contract</span></span>  
  
1.  <span data-ttu-id="5e689-108">使用您選擇的程式語言建立一個介面。</span><span class="sxs-lookup"><span data-stu-id="5e689-108">Create an interface in the programming language of your choice.</span></span>  
  
2.  <span data-ttu-id="5e689-109">將 <xref:System.ServiceModel.ServiceContractAttribute> 屬性套用至該介面。</span><span class="sxs-lookup"><span data-stu-id="5e689-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3.  <span data-ttu-id="5e689-110">將 <xref:System.ServiceModel.OperationContractAttribute> 屬性套用至用戶端可能叫用的每個方法。</span><span class="sxs-lookup"><span data-stu-id="5e689-110">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4.  <span data-ttu-id="5e689-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="5e689-111">Optional.</span></span> <span data-ttu-id="5e689-112">將 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 屬性設定為 `true` 值，以免傳送空的回覆訊息。</span><span class="sxs-lookup"><span data-stu-id="5e689-112">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="5e689-113">預設情況下，所有各項作業都是要求-回覆合約。</span><span class="sxs-lookup"><span data-stu-id="5e689-113">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e689-114">範例</span><span class="sxs-lookup"><span data-stu-id="5e689-114">Example</span></span>  
 <span data-ttu-id="5e689-115">下列範例針對可提供 `Add` 和 `Subtract` 方法的計算機服務定義合約。</span><span class="sxs-lookup"><span data-stu-id="5e689-115">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="5e689-116">`Multiply` 方法不是合約的一部分，因為它未加上 <xref:System.ServiceModel.OperationContractAttribute> 類別標示，因此無法由用戶端來存取。</span><span class="sxs-lookup"><span data-stu-id="5e689-116">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
```
using System.ServiceModel;

[ServiceContract]
public interface ICalculator
{
    [OperationContract]
    // It would be equivalent to write explicitly:
    // [OperationContract(IsOneWay=false)]
    int Add(int a, int b);
    
    [OperationContract]
    int Subtract(int a, int b);
    
    int Multiply(int a, int b)
}
```
  
-   <span data-ttu-id="5e689-117">如需如何指定作業合約的詳細資訊，請參閱<xref:System.ServiceModel.OperationContractAttribute>類別和<xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="5e689-117">For more information about how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
-   <span data-ttu-id="5e689-118">藉由套用 <xref:System.ServiceModel.ServiceContractAttribute> 和 <xref:System.ServiceModel.OperationContractAttribute> 屬性，部署服務時就會自動產生服務合約定義，亦即 Web 服務描述語言 (WSDL) 文件。</span><span class="sxs-lookup"><span data-stu-id="5e689-118">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="5e689-119">只要將 `?wsdl` 附加至服務的 HTTP 基底位址，便能夠下載這份文件。</span><span class="sxs-lookup"><span data-stu-id="5e689-119">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="5e689-120">例如：`http://microsoft/CalculatorService?wsdl`</span><span class="sxs-lookup"><span data-stu-id="5e689-120">For example, `http://microsoft/CalculatorService?wsdl`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e689-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e689-121">See Also</span></span>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [<span data-ttu-id="5e689-122">設計服務合約</span><span class="sxs-lookup"><span data-stu-id="5e689-122">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)  
 [<span data-ttu-id="5e689-123">如何：建立雙面合約</span><span class="sxs-lookup"><span data-stu-id="5e689-123">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
