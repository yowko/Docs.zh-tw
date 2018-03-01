---
title: "HOW TO：使用雙工合約存取服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 425d17fa34b61985ad3600f992e028e156f6adb9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-access-services-with-a-duplex-contract"></a><span data-ttu-id="2a6ce-102">HOW TO：使用雙工合約存取服務</span><span class="sxs-lookup"><span data-stu-id="2a6ce-102">How to: Access Services with a Duplex Contract</span></span>
<span data-ttu-id="2a6ce-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 其中一項功能，就是建立使用雙工訊息模式的服務。</span><span class="sxs-lookup"><span data-stu-id="2a6ce-103">One feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is the ability to create a service that uses a duplex messaging pattern.</span></span> <span data-ttu-id="2a6ce-104">這個模式可讓服務透過回呼與用戶端通訊。</span><span class="sxs-lookup"><span data-stu-id="2a6ce-104">This pattern allows a service to communicate with the client through a callback.</span></span> <span data-ttu-id="2a6ce-105">本主題將說明在會實作回呼介面的用戶端類別中，建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端的步驟。</span><span class="sxs-lookup"><span data-stu-id="2a6ce-105">This topic shows the steps to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client in a client class that implements the callback interface.</span></span>  
  
 <span data-ttu-id="2a6ce-106">雙重繫結會向服務公開用戶端的 IP 位址，</span><span class="sxs-lookup"><span data-stu-id="2a6ce-106">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="2a6ce-107">用戶端應該利用安全性來確保它只與信任的服務連接。</span><span class="sxs-lookup"><span data-stu-id="2a6ce-107">The client should use security to ensure that it connects only to services it trusts.</span></span>  
  
 <span data-ttu-id="2a6ce-108">如需建立基本的教學課程[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務與用戶端，請參閱[入門教學課程](../../../../docs/framework/wcf/getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="2a6ce-108">For a tutorial on creating a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service and client, see [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
### <a name="to-access-a-duplex-service"></a><span data-ttu-id="2a6ce-109">若要存取雙工服務</span><span class="sxs-lookup"><span data-stu-id="2a6ce-109">To access a duplex service</span></span>  
  
1.  <span data-ttu-id="2a6ce-110">建立包含兩個介面的服務。</span><span class="sxs-lookup"><span data-stu-id="2a6ce-110">Create a service that contains two interfaces.</span></span> <span data-ttu-id="2a6ce-111">第一個介面主要供服務使用，第二個則是供回呼使用。</span><span class="sxs-lookup"><span data-stu-id="2a6ce-111">The first interface is for the service, the second is for the callback.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="2a6ce-112">建立雙工服務，請參閱[How to： 建立雙工合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="2a6ce-112"> creating a duplex service, see [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
2.  <span data-ttu-id="2a6ce-113">執行服務。</span><span class="sxs-lookup"><span data-stu-id="2a6ce-113">Run the service.</span></span>  
  
3.  <span data-ttu-id="2a6ce-114">使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來產生用戶端合約 （介面）。</span><span class="sxs-lookup"><span data-stu-id="2a6ce-114">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate contracts (interfaces) for the client.</span></span> <span data-ttu-id="2a6ce-115">如需如何執行這項操作資訊，請參閱[How to： 建立用戶端](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="2a6ce-115">For information about how to do this, see  [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
4.  <span data-ttu-id="2a6ce-116">依下列範例所示，在用戶端類別中實作回呼介面。</span><span class="sxs-lookup"><span data-stu-id="2a6ce-116">Implement the callback interface in the client class, as shown in the following example.</span></span>  
  
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
            Console.Writeline("Equation({0})", equation)  
        End Sub  
    End Class  
    ```  
  
5.  <span data-ttu-id="2a6ce-117">建立 <xref:System.ServiceModel.InstanceContext> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a6ce-117">Create an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="2a6ce-118">建構函式需要用戶端類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a6ce-118">The constructor requires an instance of the client class.</span></span>  
  
    ```csharp  
    InstanceContext site = new InstanceContext(new CallbackHandler());  
    ```  
  
    ```vb  
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())  
    ```  
  
6.  <span data-ttu-id="2a6ce-119">使用需要 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 物件的建構函式來建立 <xref:System.ServiceModel.InstanceContext> 用戶端的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a6ce-119">Create an instance of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client using the constructor that requires an <xref:System.ServiceModel.InstanceContext> object.</span></span> <span data-ttu-id="2a6ce-120">建構函式的第二個參數就是組態檔中找到的端點名稱。</span><span class="sxs-lookup"><span data-stu-id="2a6ce-120">The second parameter of the constructor is the name of an endpoint found in the configuration file.</span></span>  
  
    ```csharp  
    CalculatorDuplexClient wcfClient =   
    new CalculatorDuplexClient(site, "default")  
    ```  
  
    ```vb  
    Dim wcfClient As New CalculatorDuplexClient(site, "default")  
    ```  
  
7.  <span data-ttu-id="2a6ce-121">視需要呼叫 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端的方法。</span><span class="sxs-lookup"><span data-stu-id="2a6ce-121">Call the methods of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client as required.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a6ce-122">範例</span><span class="sxs-lookup"><span data-stu-id="2a6ce-122">Example</span></span>  
 <span data-ttu-id="2a6ce-123">下列程式碼範例會示範如何建立會存取雙工合約的用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="2a6ce-123">The following code example demonstrates how to create a client class that accesses a duplex contract.</span></span>  
  
 [!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
 [!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="2a6ce-124">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="2a6ce-124">.NET Framework Security</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a6ce-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="2a6ce-125">See Also</span></span>  
 [<span data-ttu-id="2a6ce-126">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="2a6ce-126">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [<span data-ttu-id="2a6ce-127">如何：建立雙面合約</span><span class="sxs-lookup"><span data-stu-id="2a6ce-127">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="2a6ce-128">ServiceModel 中繼資料公用程式工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="2a6ce-128">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="2a6ce-129">如何：建立用戶端</span><span class="sxs-lookup"><span data-stu-id="2a6ce-129">How to: Create a Client</span></span>](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="2a6ce-130">如何：使用 ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="2a6ce-130">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
