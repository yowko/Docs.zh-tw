---
title: HOW TO：將合約公開給 SOAP 和 Web 用戶端
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
ms.openlocfilehash: d82c5e3fc33528eadc3c404cca59a3dcf905e0e2
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2018
ms.locfileid: "47396951"
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a><span data-ttu-id="24222-102">HOW TO：將合約公開給 SOAP 和 Web 用戶端</span><span class="sxs-lookup"><span data-stu-id="24222-102">How to: Expose a Contract to SOAP and Web Clients</span></span>

<span data-ttu-id="24222-103">根據預設，Windows Communication Foundation (WCF) 提供端點只給 SOAP 用戶端。</span><span class="sxs-lookup"><span data-stu-id="24222-103">By default, Windows Communication Foundation (WCF) makes endpoints available only to SOAP clients.</span></span> <span data-ttu-id="24222-104">在 [如何： 建立基本的 WCF Web HTTP 服務](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)，端點可供非 SOAP 用戶端。</span><span class="sxs-lookup"><span data-stu-id="24222-104">In [How to: Create a Basic WCF Web HTTP Service](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md), an endpoint is made available to non-SOAP clients.</span></span> <span data-ttu-id="24222-105">有時候您可能會想要讓兩者都有機會使用相同合約，也就是同時當做 Web 端點和 SOAP 端點。</span><span class="sxs-lookup"><span data-stu-id="24222-105">There may be times when you want to make the same contract available both ways, as a Web endpoint and as a SOAP endpoint.</span></span> <span data-ttu-id="24222-106">本主題說明如何執行此操作的範例。</span><span class="sxs-lookup"><span data-stu-id="24222-106">This topic shows an example of how to do this.</span></span>

## <a name="to-define-the-service-contract"></a><span data-ttu-id="24222-107">若要定義服務合約</span><span class="sxs-lookup"><span data-stu-id="24222-107">To define the service contract</span></span>

1. <span data-ttu-id="24222-108">定義服務合約使用標示的介面<xref:System.ServiceModel.ServiceContractAttribute>，<xref:System.ServiceModel.Web.WebInvokeAttribute>而<xref:System.ServiceModel.Web.WebGetAttribute>屬性，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="24222-108">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes, as shown in the following code:</span></span>

    [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
    [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]

    > [!NOTE]
    > <span data-ttu-id="24222-109">根據預設，<xref:System.ServiceModel.Web.WebInvokeAttribute> 會將 POST 呼叫對應至作業。</span><span class="sxs-lookup"><span data-stu-id="24222-109">By default <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="24222-110">但是，您可以指定 "method=" 參數，以指定要對應至作業的方法。</span><span class="sxs-lookup"><span data-stu-id="24222-110">You can, however, specify the method to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="24222-111"><xref:System.ServiceModel.Web.WebGetAttribute> 沒有 "method=" 參數，只能將 GET 呼叫對應至服務作業。</span><span class="sxs-lookup"><span data-stu-id="24222-111"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>

2. <span data-ttu-id="24222-112">實作服務合約，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="24222-112">Implement the service contract, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]

## <a name="to-host-the-service"></a><span data-ttu-id="24222-113">若要裝載服務</span><span class="sxs-lookup"><span data-stu-id="24222-113">To host the service</span></span>

1. <span data-ttu-id="24222-114">建立<xref:System.ServiceModel.ServiceHost>物件，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="24222-114">Create a <xref:System.ServiceModel.ServiceHost> object, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]

2. <span data-ttu-id="24222-115">新增<xref:System.ServiceModel.Description.ServiceEndpoint>與<xref:System.ServiceModel.BasicHttpBinding>針對 SOAP 端點，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="24222-115">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.BasicHttpBinding> for the SOAP endpoint, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]

3. <span data-ttu-id="24222-116">新增<xref:System.ServiceModel.Description.ServiceEndpoint>具有<xref:System.ServiceModel.WebHttpBinding>針對非 SOAP 端點，並新增<xref:System.ServiceModel.Description.WebHttpBehavior>到端點，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="24222-116">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.WebHttpBinding> for the non-SOAP endpoint and add the <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]

4. <span data-ttu-id="24222-117">呼叫`Open()`上<xref:System.ServiceModel.ServiceHost>執行個體，以開啟服務主機，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="24222-117">Call `Open()` on a <xref:System.ServiceModel.ServiceHost> instance to open the service host, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="24222-118">若要在 Internet Explorer 中呼叫對應至 GET 的服務作業</span><span class="sxs-lookup"><span data-stu-id="24222-118">To call service operations mapped to GET in Internet Explorer</span></span>

1. <span data-ttu-id="24222-119">開啟 Internet Explorer 並輸入"`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`"按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="24222-119">Open Internet Explorer and type "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="24222-120">URL 包含服務的基底位址 (`http://localhost:8000/`)，端點的相對位址 ("")，後面跟著以連字號分隔的具名參數清單的服務作業呼叫 ("EchoWithGet") 和問號 (&)。</span><span class="sxs-lookup"><span data-stu-id="24222-120">The URL contains the base address of the service (`http://localhost:8000/`), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>

## <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a><span data-ttu-id="24222-121">若要透過程式碼呼叫 Web 端點上的服務作業</span><span class="sxs-lookup"><span data-stu-id="24222-121">To call service operations on the Web endpoint in code</span></span>

1. <span data-ttu-id="24222-122">在 <xref:System.ServiceModel.Web.WebChannelFactory%601> 區塊內建立 `using` 的執行個體，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="24222-122">Create an instance of <xref:System.ServiceModel.Web.WebChannelFactory%601> within a `using` block, as shown in the following code.</span></span>

     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]

> [!NOTE]
> <span data-ttu-id="24222-123">在 `Close()` 區塊結尾，會在通道上自動呼叫 `using`。</span><span class="sxs-lookup"><span data-stu-id="24222-123">`Close()` is automatically called on the channel at the end of the `using` block.</span></span>

1. <span data-ttu-id="24222-124">建立通道並呼叫服務，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="24222-124">Create the channel and call the service, as shown in the following code.</span></span>

     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]

## <a name="to-call-service-operations-on-the-soap-endpoint"></a><span data-ttu-id="24222-125">若要在 SOAP 端點上呼叫服務作業</span><span class="sxs-lookup"><span data-stu-id="24222-125">To call service operations on the SOAP endpoint</span></span>

1. <span data-ttu-id="24222-126">在 <xref:System.ServiceModel.ChannelFactory> 區塊內建立 `using` 的執行個體，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="24222-126">Create an instance of <xref:System.ServiceModel.ChannelFactory> within a `using` block, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
    [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]

2. <span data-ttu-id="24222-127">建立通道並呼叫服務，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="24222-127">Create the channel and call the service, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
    [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]

## <a name="to-close-the-service-host"></a><span data-ttu-id="24222-128">若要關閉服務主機</span><span class="sxs-lookup"><span data-stu-id="24222-128">To close the service host</span></span>

1. <span data-ttu-id="24222-129">關閉服務主機，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="24222-129">Close the service host, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
    [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]

## <a name="example"></a><span data-ttu-id="24222-130">範例</span><span class="sxs-lookup"><span data-stu-id="24222-130">Example</span></span>

<span data-ttu-id="24222-131">以下是本主題中列出的完整程式碼：</span><span class="sxs-lookup"><span data-stu-id="24222-131">The following is the full code listing for this topic:</span></span>

[!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
[!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]

## <a name="compiling-the-code"></a><span data-ttu-id="24222-132">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="24222-132">Compiling the code</span></span>

 <span data-ttu-id="24222-133">編譯 Service.cs 時，請參考 System.ServiceModel.dll 和 System.ServiceModel.Web.dll。</span><span class="sxs-lookup"><span data-stu-id="24222-133">When compiling Service.cs, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>

## <a name="see-also"></a><span data-ttu-id="24222-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24222-134">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.ChannelFactory>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="24222-135">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="24222-135">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)