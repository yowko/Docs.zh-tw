---
title: HOW TO：將 WCF 用戶端設為與 WSE3.0 服務交互操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: 62642651516274a27c44abfc19e94dc529690ea9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304541"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a><span data-ttu-id="67317-102">HOW TO：將 WCF 用戶端設為與 WSE3.0 服務交互操作</span><span class="sxs-lookup"><span data-stu-id="67317-102">How to: Configure a WCF Client to interoperate with WSE3.0 Services</span></span>
<span data-ttu-id="67317-103">當 WCF 用戶端會設定為使用 August 2004 版本的 Ws-addressing 規格，Windows Communication Foundation (WCF) 用戶端會將與 Web Services Enhancements 3.0 for Microsoft.NET (WSE) 服務的連線層級相容性。</span><span class="sxs-lookup"><span data-stu-id="67317-103">Windows Communication Foundation (WCF) clients are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) services when WCF clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a><span data-ttu-id="67317-104">將 WCF 用戶端設定為與 WSE 3.0 Web 服務交互操作</span><span class="sxs-lookup"><span data-stu-id="67317-104">To configure a WCF client to interoperate with a WSE 3.0 Web service</span></span>  
  
1. <span data-ttu-id="67317-105">執行[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)建立 WSE 3.0 Web 服務的 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="67317-105">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a WCF client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="67317-106">針對 WSE Web 服務，建立 WCF 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="67317-106">For a WSE Web service, a WCF client class is created.</span></span>  
  
     <span data-ttu-id="67317-107">如需建立 WCF 用戶端的詳細資訊，請參閱[How to:建立用戶端](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="67317-107">For details about creating a WCF client, see the [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2. <span data-ttu-id="67317-108">建立類別，表示可與 WSE 3.0 Web 服務通訊的繫結。</span><span class="sxs-lookup"><span data-stu-id="67317-108">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="67317-109">下列類別是屬於[與 WSE 交互操作](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)範例。</span><span class="sxs-lookup"><span data-stu-id="67317-109">The following class is part of the [Interoperating with WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) sample.</span></span>  
  
    1.  <span data-ttu-id="67317-110">建立從 <xref:System.ServiceModel.Channels.Binding> 類別衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="67317-110">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="67317-111">下列程式碼範例會建立一個名為 `WseHttpBinding` 的類別，此類別衍生自 <xref:System.ServiceModel.Channels.Binding> 類別。</span><span class="sxs-lookup"><span data-stu-id="67317-111">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  <span data-ttu-id="67317-112">將屬性加入至類別，以指定 WSE 通行判斷提示 (Turnkey Assertion)、是否需要衍生金鑰、是否使用安全工作階段、是否需要簽章確認，以及訊息保護設定。</span><span class="sxs-lookup"><span data-stu-id="67317-112">Add properties to the class that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span>  
  
         <span data-ttu-id="67317-113">下列程式碼範例會定義`SecurityAssertion`， `RequireDerivedKeys`， `EstablishSecurityContext`，和`MessageProtectionOrder`屬性。</span><span class="sxs-lookup"><span data-stu-id="67317-113">The following code example defines the `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, and `MessageProtectionOrder` properties.</span></span> <span data-ttu-id="67317-114">它們分別指定 WSE 通行判斷提示、 是否需要衍生的金鑰、 是否使用安全工作階段、 是否需要簽章確認和訊息保護設定。</span><span class="sxs-lookup"><span data-stu-id="67317-114">They specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  <span data-ttu-id="67317-115">覆寫 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> 方法來設定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="67317-115">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="67317-116">下列程式碼範例會藉由取得 `SecurityAssertion` 和 `MessageProtectionOrder` 屬性的值，指定傳輸、訊息編碼和訊息保護設定。</span><span class="sxs-lookup"><span data-stu-id="67317-116">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3. <span data-ttu-id="67317-117">在用戶端應用程式程式碼中，加入程式碼以設定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="67317-117">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="67317-118">下列程式碼範例指定 WCF 用戶端必須使用訊息保護和驗證所定義的 WSE 3.0`AnonymousForCertificate`通行安全性判斷提示。</span><span class="sxs-lookup"><span data-stu-id="67317-118">The following code example specifies that the WCF client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="67317-119">此外，也需要安全工作階段和衍生金鑰。</span><span class="sxs-lookup"><span data-stu-id="67317-119">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="67317-120">範例</span><span class="sxs-lookup"><span data-stu-id="67317-120">Example</span></span>  
 <span data-ttu-id="67317-121">下列程式碼範例會定義自訂的繫結，此繫結會公開 WSE 3.0 通行安全性判斷提示屬性的對應屬性。</span><span class="sxs-lookup"><span data-stu-id="67317-121">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="67317-122">自訂繫結，名為`WseHttpBinding`，然後用來指定 WCF 用戶端的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="67317-122">The custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a WCF client.</span></span>  

[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="67317-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67317-123">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- [<span data-ttu-id="67317-124">與 WSE 交互操作</span><span class="sxs-lookup"><span data-stu-id="67317-124">Interoperating with WSE</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
