---
title: "HOW TO：將 WCF 用戶端設為與 WSE3.0 服務交互操作"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 214e0de13ba362bf4f101a665e943a424c56363c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a><span data-ttu-id="ddfbf-102">HOW TO：將 WCF 用戶端設為與 WSE3.0 服務交互操作</span><span class="sxs-lookup"><span data-stu-id="ddfbf-102">How to: Configure a WCF Client to interoperate with WSE3.0 Services</span></span>
<span data-ttu-id="ddfbf-103">當 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 用戶端設定為使用 WS-Addressing August 2004 版本規格時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端的連線層級與 Microsoft .NET 服務的 Web Services Enhancements (WSE) 3.0 相容。</span><span class="sxs-lookup"><span data-stu-id="ddfbf-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] clients are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) services when [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a><span data-ttu-id="ddfbf-104">將 WCF 用戶端設定為與 WSE 3.0 Web 服務交互操作</span><span class="sxs-lookup"><span data-stu-id="ddfbf-104">To configure a WCF client to interoperate with a WSE 3.0 Web service</span></span>  
  
1.  <span data-ttu-id="ddfbf-105">執行[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)建立[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]WSE 3.0 Web 服務用戶端。</span><span class="sxs-lookup"><span data-stu-id="ddfbf-105">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="ddfbf-106">針對 WSE Web 服務，會建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="ddfbf-106">For a WSE Web service, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class is created.</span></span>  
  
     <span data-ttu-id="ddfbf-107">如需詳細資訊，關於建立[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]用戶端，請參閱[How to： 建立用戶端](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="ddfbf-107">For details about creating a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, see the [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="ddfbf-108">建立類別，表示可與 WSE 3.0 Web 服務通訊的繫結。</span><span class="sxs-lookup"><span data-stu-id="ddfbf-108">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="ddfbf-109">下列類別是一部分[與 WSE 互通](http://msdn.microsoft.com/en-us/f6816861-96a0-45f9-8736-8e4e82cd3a41)範例。</span><span class="sxs-lookup"><span data-stu-id="ddfbf-109">The following class is part of the [Interoperating with WSE](http://msdn.microsoft.com/en-us/f6816861-96a0-45f9-8736-8e4e82cd3a41) sample.</span></span>  
  
    1.  <span data-ttu-id="ddfbf-110">建立從 <xref:System.ServiceModel.Channels.Binding> 類別衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="ddfbf-110">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="ddfbf-111">下列程式碼範例會建立一個名為 `WseHttpBinding` 的類別，此類別衍生自 <xref:System.ServiceModel.Channels.Binding> 類別。</span><span class="sxs-lookup"><span data-stu-id="ddfbf-111">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  <span data-ttu-id="ddfbf-112">將屬性加入至類別，以指定 WSE 通行判斷提示 (Turnkey Assertion)、是否需要衍生金鑰、是否使用安全工作階段、是否需要簽章確認，以及訊息保護設定。</span><span class="sxs-lookup"><span data-stu-id="ddfbf-112">Add properties to the class that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span>  
  
         <span data-ttu-id="ddfbf-113">下列程式碼範例會定義`SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder`指定 WSE 通行判斷提示、 是否需要衍生的金鑰、 是否使用安全工作階段、 是否需要簽章確認和訊息保護設定，屬性分別。</span><span class="sxs-lookup"><span data-stu-id="ddfbf-113">The following code example defines `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` properties that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  <span data-ttu-id="ddfbf-114">覆寫 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> 方法來設定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="ddfbf-114">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="ddfbf-115">下列程式碼範例會藉由取得 `SecurityAssertion` 和 `MessageProtectionOrder` 屬性的值，指定傳輸、訊息編碼和訊息保護設定。</span><span class="sxs-lookup"><span data-stu-id="ddfbf-115">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  <span data-ttu-id="ddfbf-116">在用戶端應用程式程式碼中，加入程式碼以設定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="ddfbf-116">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="ddfbf-117">下列程式碼範例會指定 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端必須依照 WSE 3.0 `AnonymousForCertificate` 通行安全性判斷提示所定義，使用訊息保護和驗證。</span><span class="sxs-lookup"><span data-stu-id="ddfbf-117">The following code example specifies that the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="ddfbf-118">此外，也需要安全工作階段和衍生金鑰。</span><span class="sxs-lookup"><span data-stu-id="ddfbf-118">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="ddfbf-119">範例</span><span class="sxs-lookup"><span data-stu-id="ddfbf-119">Example</span></span>  
 <span data-ttu-id="ddfbf-120">下列程式碼範例會定義自訂的繫結，此繫結會公開 WSE 3.0 通行安全性判斷提示屬性的對應屬性。</span><span class="sxs-lookup"><span data-stu-id="ddfbf-120">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="ddfbf-121">接著會使用名為 `WseHttpBinding` 的自訂繫結，指定 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="ddfbf-121">The custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span>  
  
  
[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="ddfbf-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="ddfbf-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 [<span data-ttu-id="ddfbf-123">與 WSE 互通</span><span class="sxs-lookup"><span data-stu-id="ddfbf-123">Interoperating with WSE</span></span>](http://msdn.microsoft.com/en-us/f6816861-96a0-45f9-8736-8e4e82cd3a41)
