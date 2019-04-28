---
title: HOW TO：Access services 搭配雙工合約
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
ms.openlocfilehash: 366fd9d6aa220bcbec1ee8fb2a04d1b84755800a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855136"
---
# <a name="how-to-access-services-with-a-duplex-contract"></a><span data-ttu-id="1b7b4-102">HOW TO：Access services 搭配雙工合約</span><span class="sxs-lookup"><span data-stu-id="1b7b4-102">How to: Access services with a duplex contract</span></span>

<span data-ttu-id="1b7b4-103">Windows Communication Foundation (WCF) 的一項功能是能夠建立使用雙工訊息模式的服務。</span><span class="sxs-lookup"><span data-stu-id="1b7b4-103">One feature of Windows Communication Foundation (WCF) is the ability to create a service that uses a duplex messaging pattern.</span></span> <span data-ttu-id="1b7b4-104">這個模式可讓服務透過回呼與用戶端通訊。</span><span class="sxs-lookup"><span data-stu-id="1b7b4-104">This pattern allows a service to communicate with the client through a callback.</span></span> <span data-ttu-id="1b7b4-105">本主題說明建立 WCF 用戶端實作回呼介面的用戶端類別中的步驟。</span><span class="sxs-lookup"><span data-stu-id="1b7b4-105">This topic shows the steps to create a WCF client in a client class that implements the callback interface.</span></span>

<span data-ttu-id="1b7b4-106">雙重繫結會向服務公開用戶端的 IP 位址，</span><span class="sxs-lookup"><span data-stu-id="1b7b4-106">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="1b7b4-107">用戶端應該利用安全性來確保它只與信任的服務連接。</span><span class="sxs-lookup"><span data-stu-id="1b7b4-107">The client should use security to ensure that it connects only to services it trusts.</span></span>

<span data-ttu-id="1b7b4-108">如需建立基本的 WCF 服務和用戶端的教學課程，請參閱 <<c0> [ 入門教學課程](../../../../docs/framework/wcf/getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="1b7b4-108">For a tutorial on creating a basic WCF service and client, see [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>

## <a name="to-access-a-duplex-service"></a><span data-ttu-id="1b7b4-109">若要存取雙工服務</span><span class="sxs-lookup"><span data-stu-id="1b7b4-109">To access a duplex service</span></span>

1. <span data-ttu-id="1b7b4-110">建立包含兩個介面的服務。</span><span class="sxs-lookup"><span data-stu-id="1b7b4-110">Create a service that contains two interfaces.</span></span> <span data-ttu-id="1b7b4-111">第一個介面主要供服務使用，第二個則是供回呼使用。</span><span class="sxs-lookup"><span data-stu-id="1b7b4-111">The first interface is for the service, the second is for the callback.</span></span> <span data-ttu-id="1b7b4-112">如需建立雙工服務的詳細資訊，請參閱[How to:建立雙工合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="1b7b4-112">For more information about creating a duplex service, see [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>

2. <span data-ttu-id="1b7b4-113">執行服務。</span><span class="sxs-lookup"><span data-stu-id="1b7b4-113">Run the service.</span></span>

3. <span data-ttu-id="1b7b4-114">使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)用戶端產生合約 （介面）。</span><span class="sxs-lookup"><span data-stu-id="1b7b4-114">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate contracts (interfaces) for the client.</span></span> <span data-ttu-id="1b7b4-115">如需如何執行這項操作的資訊，請參閱[How to:建立用戶端](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="1b7b4-115">For information about how to do this, see  [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>

4. <span data-ttu-id="1b7b4-116">依下列範例所示，在用戶端類別中實作回呼介面。</span><span class="sxs-lookup"><span data-stu-id="1b7b4-116">Implement the callback interface in the client class, as shown in the following example.</span></span>

    ```csharp
    public class CallbackHandler : ICalculatorDuplexCallback
    {
        public void Result(double result)
        {
            Console.WriteLine("Result ({0})", result);
        }
        public void Equation(string equation)
        {
            Console.WriteLine("Equation({0})", equation);
        }
    }
    ```

    ```vb
    Public Class CallbackHandler
    Implements ICalculatorDuplexCallback
       Public Sub Result (ByVal result As Double)
          Console.WriteLine("Result ({0})", result)
       End Sub
        Public Sub Equation(ByVal equation As String)
            Console.WriteLine("Equation({0})", equation)
        End Sub
    End Class
    ```

5. <span data-ttu-id="1b7b4-117">建立 <xref:System.ServiceModel.InstanceContext> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1b7b4-117">Create an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="1b7b4-118">建構函式需要用戶端類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1b7b4-118">The constructor requires an instance of the client class.</span></span>

    ```csharp
    InstanceContext site = new InstanceContext(new CallbackHandler());
    ```

    ```vb
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())
    ```

6. <span data-ttu-id="1b7b4-119">建立 WCF 用戶端會使用需要的建構函式的執行個體<xref:System.ServiceModel.InstanceContext>物件。</span><span class="sxs-lookup"><span data-stu-id="1b7b4-119">Create an instance of the WCF client using the constructor that requires an <xref:System.ServiceModel.InstanceContext> object.</span></span> <span data-ttu-id="1b7b4-120">建構函式的第二個參數就是組態檔中找到的端點名稱。</span><span class="sxs-lookup"><span data-stu-id="1b7b4-120">The second parameter of the constructor is the name of an endpoint found in the configuration file.</span></span>

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. <span data-ttu-id="1b7b4-121">呼叫的 WCF 用戶端所需的方法。</span><span class="sxs-lookup"><span data-stu-id="1b7b4-121">Call the methods of the WCF client as required.</span></span>

## <a name="example"></a><span data-ttu-id="1b7b4-122">範例</span><span class="sxs-lookup"><span data-stu-id="1b7b4-122">Example</span></span>

<span data-ttu-id="1b7b4-123">下列程式碼範例會示範如何建立會存取雙工合約的用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="1b7b4-123">The following code example demonstrates how to create a client class that accesses a duplex contract.</span></span>

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a><span data-ttu-id="1b7b4-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b7b4-124">See also</span></span>

- [<span data-ttu-id="1b7b4-125">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="1b7b4-125">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="1b7b4-126">如何：建立雙工合約</span><span class="sxs-lookup"><span data-stu-id="1b7b4-126">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="1b7b4-127">ServiceModel 中繼資料公用程式工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="1b7b4-127">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="1b7b4-128">如何：建立用戶端</span><span class="sxs-lookup"><span data-stu-id="1b7b4-128">How to: Create a Client</span></span>](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="1b7b4-129">如何：使用 ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="1b7b4-129">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
