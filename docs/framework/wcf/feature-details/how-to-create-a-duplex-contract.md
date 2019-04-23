---
title: HOW TO：建立雙面合約
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: c00e5d8e50de89d3d4d346ccddc50282f24735b2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59332127"
---
# <a name="how-to-create-a-duplex-contract"></a><span data-ttu-id="fa234-102">HOW TO：建立雙面合約</span><span class="sxs-lookup"><span data-stu-id="fa234-102">How to: Create a Duplex Contract</span></span>
<span data-ttu-id="fa234-103">本主題說明的基本步驟可用來建立使用雙工 (雙向) 合約的方法。</span><span class="sxs-lookup"><span data-stu-id="fa234-103">This topic shows the basic steps to create methods that use a duplex (two-way) contract.</span></span> <span data-ttu-id="fa234-104">雙工合約可供用戶端與伺服器彼此各自進行通訊，方便任何一方初始化對另一方的呼叫。</span><span class="sxs-lookup"><span data-stu-id="fa234-104">A duplex contract allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="fa234-105">雙工合約是其中一個可用於 Windows Communication Foundation (WCF) 服務的三種訊息模式。</span><span class="sxs-lookup"><span data-stu-id="fa234-105">The duplex contract is one of three message patterns available to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="fa234-106">其他兩種訊息模式分別是單向和要求-回覆。</span><span class="sxs-lookup"><span data-stu-id="fa234-106">The other two message patterns are one-way and request-reply.</span></span> <span data-ttu-id="fa234-107">雙工合約是由用戶端和伺服器之間的兩個單向合約組成，而且不需要相互關聯方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="fa234-107">A duplex contract consists of two one-way contracts between the client and the server and does not require that the method calls be correlated.</span></span> <span data-ttu-id="fa234-108">當您的服務必須查詢用戶端以獲得更多資訊，或是明確地在用戶端上引發事件時，請使用這種合約。</span><span class="sxs-lookup"><span data-stu-id="fa234-108">Use this kind of contract when your service must query the client for more information or explicitly raise events on the client.</span></span> <span data-ttu-id="fa234-109">如需建立雙工合約的用戶端應用程式的詳細資訊，請參閱[How to:使用雙工合約存取服務](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="fa234-109">For more information about creating a client application for a duplex contract, see [How to: Access Services with a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).</span></span> <span data-ttu-id="fa234-110">如需實用範例，請參閱 <<c0> [ 雙工](../../../../docs/framework/wcf/samples/duplex.md)範例。</span><span class="sxs-lookup"><span data-stu-id="fa234-110">For a working sample, see the [Duplex](../../../../docs/framework/wcf/samples/duplex.md) sample.</span></span>  
  
### <a name="to-create-a-duplex-contract"></a><span data-ttu-id="fa234-111">若要建立雙工合約</span><span class="sxs-lookup"><span data-stu-id="fa234-111">To create a duplex contract</span></span>  
  
1. <span data-ttu-id="fa234-112">建立可組成雙工合約伺服器端的介面。</span><span class="sxs-lookup"><span data-stu-id="fa234-112">Create the interface that makes up the server side of the duplex contract.</span></span>  
  
2. <span data-ttu-id="fa234-113">將 <xref:System.ServiceModel.ServiceContractAttribute> 類別套用到介面。</span><span class="sxs-lookup"><span data-stu-id="fa234-113">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3. <span data-ttu-id="fa234-114">在介面中宣告方法簽章。</span><span class="sxs-lookup"><span data-stu-id="fa234-114">Declare the method signatures in the interface.</span></span>  
  
4. <span data-ttu-id="fa234-115">將 <xref:System.ServiceModel.OperationContractAttribute> 類別套用到每個必須是公用合約一部分的方法簽章上。</span><span class="sxs-lookup"><span data-stu-id="fa234-115">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
5. <span data-ttu-id="fa234-116">建立可定義作業集合 (供服務在用戶端上加以叫用) 的回呼介面。</span><span class="sxs-lookup"><span data-stu-id="fa234-116">Create the callback interface that defines the set of operations that the service can invoke on the client.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6. <span data-ttu-id="fa234-117">在回呼介面中宣告方法簽章。</span><span class="sxs-lookup"><span data-stu-id="fa234-117">Declare the method signatures in the callback interface.</span></span>  
  
7. <span data-ttu-id="fa234-118">將 <xref:System.ServiceModel.OperationContractAttribute> 類別套用到每個必須是公用合約一部分的方法簽章上。</span><span class="sxs-lookup"><span data-stu-id="fa234-118">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
8. <span data-ttu-id="fa234-119">將主要介面中的 <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> 屬性設為回呼介面的型別，以將兩個介面連接至雙工合約。</span><span class="sxs-lookup"><span data-stu-id="fa234-119">Link the two interfaces into a duplex contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> property in the primary interface to the type of the callback interface.</span></span>  
  
### <a name="to-call-methods-on-the-client"></a><span data-ttu-id="fa234-120">若要在用戶端上呼叫方法</span><span class="sxs-lookup"><span data-stu-id="fa234-120">To call methods on the client</span></span>  
  
1. <span data-ttu-id="fa234-121">在服務的主要合約實作中，宣告回呼介面的變數。</span><span class="sxs-lookup"><span data-stu-id="fa234-121">In the service's implementation of the primary contract, declare a variable for the callback interface.</span></span>  
  
2. <span data-ttu-id="fa234-122">將變數設為由 <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> 類別之 <xref:System.ServiceModel.OperationContext> 方法傳回的物件參考。</span><span class="sxs-lookup"><span data-stu-id="fa234-122">Set the variable to the object reference returned by the <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> method of the <xref:System.ServiceModel.OperationContext> class.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3. <span data-ttu-id="fa234-123">呼叫回呼介面定義的方法。</span><span class="sxs-lookup"><span data-stu-id="fa234-123">Call the methods defined by the callback interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa234-124">範例</span><span class="sxs-lookup"><span data-stu-id="fa234-124">Example</span></span>  
 <span data-ttu-id="fa234-125">下列程式碼範例會示範雙工通訊。</span><span class="sxs-lookup"><span data-stu-id="fa234-125">The following code example demonstrates duplex communication.</span></span> <span data-ttu-id="fa234-126">服務合約包含可往前與往後的服務作業。</span><span class="sxs-lookup"><span data-stu-id="fa234-126">The service’s contract contains service operations for moving forward and backward.</span></span> <span data-ttu-id="fa234-127">用戶端合約包含可報告自身位置的服務作業。</span><span class="sxs-lookup"><span data-stu-id="fa234-127">The client’s contract contains a service operation for reporting its position.</span></span>  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
-   <span data-ttu-id="fa234-128">套用 <xref:System.ServiceModel.ServiceContractAttribute> 和 <xref:System.ServiceModel.OperationContractAttribute> 屬性可自動產生 Web 服務描述語言 (WSDL) 格式的服務合約定義。</span><span class="sxs-lookup"><span data-stu-id="fa234-128">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes allows the automatic generation of service contract definitions in the Web Services Description Language (WSDL).</span></span>  
  
-   <span data-ttu-id="fa234-129">使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)擷取 WSDL 文件和 （選擇性） 的程式碼和用戶端組態。</span><span class="sxs-lookup"><span data-stu-id="fa234-129">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to retrieve the WSDL document and (optional) code and configuration for a client.</span></span>  
  
-   <span data-ttu-id="fa234-130">您必須保護公開雙工服務的端點安全。</span><span class="sxs-lookup"><span data-stu-id="fa234-130">Endpoints exposing duplex services must be secured.</span></span> <span data-ttu-id="fa234-131">當服務收到雙工訊息時，會查看該傳入訊息中的 ReplyTo 項目，以判斷傳送回覆的位置。</span><span class="sxs-lookup"><span data-stu-id="fa234-131">When a service receives a duplex message, it looks at the ReplyTo in that incoming message to determine where to send the reply.</span></span> <span data-ttu-id="fa234-132">如果通道不安全，那麼未受信任的用戶端可能會傳送惡意訊息，其中包含目標電腦的 ReplyTo，而導致該目標電腦發生阻絕服務。</span><span class="sxs-lookup"><span data-stu-id="fa234-132">If the channel is not secured, then an untrusted client could send a malicious message with a target machine's ReplyTo, leading to a denial of service of the target machine.</span></span> <span data-ttu-id="fa234-133">如果是一般的要求-回覆訊息，這根本不是問題，因為電腦會忽略 ReplyTo 並且在原始傳入訊息所用的通道上傳送回應。</span><span class="sxs-lookup"><span data-stu-id="fa234-133">With regular request-reply messages, this is not an issue, because the ReplyTo is ignored and the response is sent on the channel the original message came in on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa234-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa234-134">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="fa234-135">如何：Access Services 搭配雙工合約</span><span class="sxs-lookup"><span data-stu-id="fa234-135">How to: Access Services with a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="fa234-136">雙面</span><span class="sxs-lookup"><span data-stu-id="fa234-136">Duplex</span></span>](../../../../docs/framework/wcf/samples/duplex.md)
- [<span data-ttu-id="fa234-137">設計與實作服務</span><span class="sxs-lookup"><span data-stu-id="fa234-137">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)
- [<span data-ttu-id="fa234-138">如何：定義服務合約</span><span class="sxs-lookup"><span data-stu-id="fa234-138">How to: Define a Service Contract</span></span>](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="fa234-139">工作階段</span><span class="sxs-lookup"><span data-stu-id="fa234-139">Session</span></span>](../../../../docs/framework/wcf/samples/session.md)
