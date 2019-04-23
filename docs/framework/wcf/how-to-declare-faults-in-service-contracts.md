---
title: HOW TO：在服務合約中宣告錯誤
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 0e173f71201d5f98a04d2ad922469e4ff6666681
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768588"
---
# <a name="how-to-declare-faults-in-service-contracts"></a><span data-ttu-id="d1abe-102">HOW TO：在服務合約中宣告錯誤</span><span class="sxs-lookup"><span data-stu-id="d1abe-102">How to: Declare Faults in Service Contracts</span></span>
<span data-ttu-id="d1abe-103">在 Managed 程式碼中，發生錯誤狀況時會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d1abe-103">In managed code, exceptions are thrown when error conditions occur.</span></span> <span data-ttu-id="d1abe-104">在 Windows Communication Foundation (WCF) 應用程式，不過，服務合約會指定哪些資訊時發生錯誤，會藉由宣告服務合約中的 SOAP 錯誤傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="d1abe-104">In Windows Communication Foundation (WCF) applications, however, service contracts specify what error information is returned to clients by declaring SOAP faults in the service contract.</span></span> <span data-ttu-id="d1abe-105">如需例外狀況和錯誤之間的關聯性的概觀，請參閱 <<c0> [ 指定及處理合約和服務中的錯誤](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d1abe-105">For an overview of the relationship between exceptions and faults, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
### <a name="create-a-service-contract-that-specifies-a-soap-fault"></a><span data-ttu-id="d1abe-106">建立會指定 SOAP 錯誤的服務合約</span><span class="sxs-lookup"><span data-stu-id="d1abe-106">Create a service contract that specifies a SOAP fault</span></span>  
  
1. <span data-ttu-id="d1abe-107">建立其中至少包含一個作業的服務合約。</span><span class="sxs-lookup"><span data-stu-id="d1abe-107">Create a service contract that contains at least one operation.</span></span> <span data-ttu-id="d1abe-108">如需範例，請參閱[如何：定義服務合約](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="d1abe-108">For an example, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2. <span data-ttu-id="d1abe-109">選取作業，這個作業會指定用戶端預期會收到通知的錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="d1abe-109">Select an operation that can specify an error condition about which clients can expect to be notified.</span></span> <span data-ttu-id="d1abe-110">若要決定哪些錯誤狀況證明將 SOAP 錯誤傳回給用戶端，請參閱[指定及處理合約和服務中的錯誤](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d1abe-110">To decide which error conditions justify returning SOAP faults to clients, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
3. <span data-ttu-id="d1abe-111">將 <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> 套用至選取的作業，並將可序列化的錯誤類型傳遞至建構函式。</span><span class="sxs-lookup"><span data-stu-id="d1abe-111">Apply a <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> to the selected operation and pass a serializable fault type to the constructor.</span></span> <span data-ttu-id="d1abe-112">如需有關建立及使用可序列化類型的詳細資訊，請參閱 < [Specifying Data Transfer in Service Contracts](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="d1abe-112">For details about creating and using serializable types, see [Specifying Data Transfer in Service Contracts](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span></span> <span data-ttu-id="d1abe-113">下列範例將示範如何指定會在 `SampleMethod` 中產生 `GreetingFault` 作業。</span><span class="sxs-lookup"><span data-stu-id="d1abe-113">The following example shows how to specify that the `SampleMethod` operation can result in a `GreetingFault`.</span></span>  
  
     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
4. <span data-ttu-id="d1abe-114">對合約中會與用戶端溝通錯誤狀況的所有作業，重複步驟 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="d1abe-114">Repeat steps 2 and 3 for all operations in the contract that communicate error conditions to clients.</span></span>  
  
## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a><span data-ttu-id="d1abe-115">實作作業以傳回指定的 SOAP 錯誤</span><span class="sxs-lookup"><span data-stu-id="d1abe-115">Implementing an Operation to Return a Specified SOAP Fault</span></span>  
 <span data-ttu-id="d1abe-116">一旦作業已指定可傳回特定 SOAP 錯誤 (如之前的程序所示)，以與呼叫應用程式溝通錯誤狀況，則下一個步驟就是實作該指定項目。</span><span class="sxs-lookup"><span data-stu-id="d1abe-116">Once an operation has specified that a specific SOAP fault can be returned (such as in the preceding procedure) to communicate an error condition to a calling application, the next step is to implement that specification.</span></span>  
  
#### <a name="throw-the-specified-soap-fault-in-the-operation"></a><span data-ttu-id="d1abe-117">在作業中擲回指定的 SOAP 錯誤</span><span class="sxs-lookup"><span data-stu-id="d1abe-117">Throw the specified SOAP fault in the operation</span></span>  
  
1. <span data-ttu-id="d1abe-118">在作業中發生 <xref:System.ServiceModel.FaultContractAttribute> 特定的錯誤狀況時，會擲回新的 <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>，其中指定的 SOAP 錯誤為型別參數。</span><span class="sxs-lookup"><span data-stu-id="d1abe-118">When a <xref:System.ServiceModel.FaultContractAttribute>-specified error condition occurs in an operation, throw a new <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> where the specified SOAP fault is the type parameter.</span></span> <span data-ttu-id="d1abe-119">下列範例會示範如何在之前程序中顯示的 `GreetingFault` 中擲回 `SampleMethod`，以及如何在下列「程式碼」區段中擲回。</span><span class="sxs-lookup"><span data-stu-id="d1abe-119">The following example shows how to throw the `GreetingFault` in the `SampleMethod` shown in the preceding procedure and in the following Code section.</span></span>  
  
     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="d1abe-120">範例</span><span class="sxs-lookup"><span data-stu-id="d1abe-120">Example</span></span>  
 <span data-ttu-id="d1abe-121">下列程式碼範例會顯示對 `GreetingFault` 作業指定 `SampleMethod` 的單一作業實作。</span><span class="sxs-lookup"><span data-stu-id="d1abe-121">The following code example shows an implementation of a single operation that specifies a `GreetingFault` for the `SampleMethod` operation.</span></span>  
  
 [!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
 [!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d1abe-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1abe-122">See also</span></span>

- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
