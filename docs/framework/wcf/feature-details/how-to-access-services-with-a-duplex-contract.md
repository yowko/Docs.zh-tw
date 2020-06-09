---
title: 如何：使用雙工合約存取服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
ms.openlocfilehash: bc42792b827b49265a0b1addf959de2fa1a041e3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597211"
---
# <a name="how-to-access-services-with-a-duplex-contract"></a><span data-ttu-id="833cc-102">如何：使用雙工合約存取服務</span><span class="sxs-lookup"><span data-stu-id="833cc-102">How to: Access services with a duplex contract</span></span>

<span data-ttu-id="833cc-103">Windows Communication Foundation （WCF）的其中一項功能，就是建立使用雙工訊息模式之服務的能力。</span><span class="sxs-lookup"><span data-stu-id="833cc-103">One feature of Windows Communication Foundation (WCF) is the ability to create a service that uses a duplex messaging pattern.</span></span> <span data-ttu-id="833cc-104">這個模式可讓服務透過回呼與用戶端通訊。</span><span class="sxs-lookup"><span data-stu-id="833cc-104">This pattern allows a service to communicate with the client through a callback.</span></span> <span data-ttu-id="833cc-105">本主題說明在執行回呼介面的用戶端類別中建立 WCF 用戶端的步驟。</span><span class="sxs-lookup"><span data-stu-id="833cc-105">This topic shows the steps to create a WCF client in a client class that implements the callback interface.</span></span>

<span data-ttu-id="833cc-106">雙重繫結會向服務公開用戶端的 IP 位址，</span><span class="sxs-lookup"><span data-stu-id="833cc-106">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="833cc-107">用戶端應該利用安全性來確保它只與信任的服務連接。</span><span class="sxs-lookup"><span data-stu-id="833cc-107">The client should use security to ensure that it connects only to services it trusts.</span></span>

<span data-ttu-id="833cc-108">如需建立基本 WCF 服務和用戶端的教學課程，請參閱[消費者入門教學](../getting-started-tutorial.md)課程。</span><span class="sxs-lookup"><span data-stu-id="833cc-108">For a tutorial on creating a basic WCF service and client, see [Getting Started Tutorial](../getting-started-tutorial.md).</span></span>

## <a name="to-access-a-duplex-service"></a><span data-ttu-id="833cc-109">若要存取雙工服務</span><span class="sxs-lookup"><span data-stu-id="833cc-109">To access a duplex service</span></span>

1. <span data-ttu-id="833cc-110">建立包含兩個介面的服務。</span><span class="sxs-lookup"><span data-stu-id="833cc-110">Create a service that contains two interfaces.</span></span> <span data-ttu-id="833cc-111">第一個介面主要供服務使用，第二個則是供回呼使用。</span><span class="sxs-lookup"><span data-stu-id="833cc-111">The first interface is for the service, the second is for the callback.</span></span> <span data-ttu-id="833cc-112">如需建立雙工服務的詳細資訊，請參閱[如何：建立雙工合約](how-to-create-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="833cc-112">For more information about creating a duplex service, see [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>

2. <span data-ttu-id="833cc-113">執行服務。</span><span class="sxs-lookup"><span data-stu-id="833cc-113">Run the service.</span></span>

3. <span data-ttu-id="833cc-114">使用[System.servicemodel 中繼資料公用程式工具（Svcutil）](../servicemodel-metadata-utility-tool-svcutil-exe.md)來產生用戶端的合約（介面）。</span><span class="sxs-lookup"><span data-stu-id="833cc-114">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate contracts (interfaces) for the client.</span></span> <span data-ttu-id="833cc-115">如需如何執行此動作的詳細資訊，請參閱[如何：建立用戶端](../how-to-create-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="833cc-115">For information about how to do this, see  [How to: Create a Client](../how-to-create-a-wcf-client.md).</span></span>

4. <span data-ttu-id="833cc-116">依下列範例所示，在用戶端類別中實作回呼介面。</span><span class="sxs-lookup"><span data-stu-id="833cc-116">Implement the callback interface in the client class, as shown in the following example.</span></span>

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

5. <span data-ttu-id="833cc-117">建立 <xref:System.ServiceModel.InstanceContext> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="833cc-117">Create an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="833cc-118">建構函式需要用戶端類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="833cc-118">The constructor requires an instance of the client class.</span></span>

    ```csharp
    InstanceContext site = new InstanceContext(new CallbackHandler());
    ```

    ```vb
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())
    ```

6. <span data-ttu-id="833cc-119">使用需要物件的構造函式，建立 WCF 用戶端的實例 <xref:System.ServiceModel.InstanceContext> 。</span><span class="sxs-lookup"><span data-stu-id="833cc-119">Create an instance of the WCF client using the constructor that requires an <xref:System.ServiceModel.InstanceContext> object.</span></span> <span data-ttu-id="833cc-120">建構函式的第二個參數就是組態檔中找到的端點名稱。</span><span class="sxs-lookup"><span data-stu-id="833cc-120">The second parameter of the constructor is the name of an endpoint found in the configuration file.</span></span>

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. <span data-ttu-id="833cc-121">視需要呼叫 WCF 用戶端的方法。</span><span class="sxs-lookup"><span data-stu-id="833cc-121">Call the methods of the WCF client as required.</span></span>

## <a name="example"></a><span data-ttu-id="833cc-122">範例</span><span class="sxs-lookup"><span data-stu-id="833cc-122">Example</span></span>

<span data-ttu-id="833cc-123">下列程式碼範例會示範如何建立會存取雙工合約的用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="833cc-123">The following code example demonstrates how to create a client class that accesses a duplex contract.</span></span>

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a><span data-ttu-id="833cc-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="833cc-124">See also</span></span>

- [<span data-ttu-id="833cc-125">消費者入門教學課程</span><span class="sxs-lookup"><span data-stu-id="833cc-125">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)
- [<span data-ttu-id="833cc-126">HOW TO：建立雙工合約</span><span class="sxs-lookup"><span data-stu-id="833cc-126">How to: Create a Duplex Contract</span></span>](how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="833cc-127">ServiceModel 中繼資料公用程式工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="833cc-127">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="833cc-128">如何：建立用戶端</span><span class="sxs-lookup"><span data-stu-id="833cc-128">How to: Create a Client</span></span>](../how-to-create-a-wcf-client.md)
- [<span data-ttu-id="833cc-129">如何：使用 ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="833cc-129">How to: Use the ChannelFactory</span></span>](how-to-use-the-channelfactory.md)
