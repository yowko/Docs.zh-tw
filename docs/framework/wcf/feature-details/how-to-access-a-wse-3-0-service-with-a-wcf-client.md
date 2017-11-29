---
title: "HOW TO：使用 WCF 用戶端來存取 WSE 3.0 服務"
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
ms.assetid: 1f9bcd9b-8f8f-47fa-8f1e-0d47236eb800
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cd6ad4ed735cb94321adad8fd2e4cf396e2221fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-a-wse-30-service-with-a-wcf-client"></a><span data-ttu-id="62dfd-102">HOW TO：使用 WCF 用戶端來存取 WSE 3.0 服務</span><span class="sxs-lookup"><span data-stu-id="62dfd-102">How to: Access a WSE 3.0 Service with a WCF Client</span></span>
<span data-ttu-id="62dfd-103">當 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 用戶端設定為使用 WS-Addressing August 2004 版本規格時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端的連線層級與 Microsoft .NET 服務的 Web Services Enhancements (WSE) 3.0 相容。</span><span class="sxs-lookup"><span data-stu-id="62dfd-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] clients are wire-level compatible with Web Services Enhancements (WSE) 3.0 for Microsoft .NET services when [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span> <span data-ttu-id="62dfd-104">不過，WSE 3.0 服務不支援中繼資料交換 (MEX) 通訊協定，因此當您使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)建立[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]用戶端類別的安全性設定不會套用至產生[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]用戶端。</span><span class="sxs-lookup"><span data-stu-id="62dfd-104">However, WSE 3.0 services do not support the metadata exchange (MEX) protocol, so when you use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class, the security settings are not applied to the generated [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span> <span data-ttu-id="62dfd-105">因此，在產生 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端之後，您必須指定 WSE 3.0 服務所需的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="62dfd-105">Therefore, you must specify the security settings that the WSE 3.0 service requires after the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client is generated.</span></span>  
  
 <span data-ttu-id="62dfd-106">您可以使用自訂繫結來套用這些安全性設定，將 WSE 3.0 服務的需求，以及 WSE 3.0 服務和 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端之間的互通需求納入考量。</span><span class="sxs-lookup"><span data-stu-id="62dfd-106">You can apply these security settings by using a custom binding to take into account the WSE 3.0 service's requirements and the interoperable requirements between a WSE 3.0 service and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span> <span data-ttu-id="62dfd-107">這些互通性需求包含上述的 WS-Addressing August 2004 規格使用和 WSE 3.0 預設訊息保護 <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>。</span><span class="sxs-lookup"><span data-stu-id="62dfd-107">These interoperability requirements include the aforementioned use of the August 2004 WS-Addressing specification and the  WSE 3.0default message protection of <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.</span></span> <span data-ttu-id="62dfd-108">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的預設訊息保護為 <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>。</span><span class="sxs-lookup"><span data-stu-id="62dfd-108">The default message protection for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>.</span></span> <span data-ttu-id="62dfd-109">本主題詳細說明如何建立與 WSE 3.0 服務相互操作的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 繫結。</span><span class="sxs-lookup"><span data-stu-id="62dfd-109">This topic details how to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binding that interoperates with a WSE 3.0 service.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62dfd-110"> 也會提供包含這個繫結的範例。</span><span class="sxs-lookup"><span data-stu-id="62dfd-110"> also provides a sample that incorporates this binding.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="62dfd-111">此範例中，請參閱[與 ASMX Web 服務互通](../../../../docs/framework/wcf/samples/interoperating-with-asmx-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="62dfd-111"> this sample, see [Interoperating with ASMX Web Services](../../../../docs/framework/wcf/samples/interoperating-with-asmx-web-services.md).</span></span>  
  
### <a name="to-access-a-wse-30-web-service-with-a-wcf-client"></a><span data-ttu-id="62dfd-112">若要使用 WCF 用戶端來存取 WSE 3.0 Web 服務</span><span class="sxs-lookup"><span data-stu-id="62dfd-112">To access a WSE 3.0 Web service with a WCF client</span></span>  
  
1.  <span data-ttu-id="62dfd-113">執行[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)建立[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]WSE 3.0 Web 服務用戶端。</span><span class="sxs-lookup"><span data-stu-id="62dfd-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="62dfd-114">隨即建立 WSE 3.0 Web 服務的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端。</span><span class="sxs-lookup"><span data-stu-id="62dfd-114">For a WSE 3.0 Web service, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client is created.</span></span> <span data-ttu-id="62dfd-115">因為 WSE 3.0 不支援 MEX 通訊協定，所以您無法使用此工具擷取 Web 服務的安全性需求。</span><span class="sxs-lookup"><span data-stu-id="62dfd-115">Because WSE 3.0 does not support the MEX protocol, you cannot use the tool to retrieve the security requirements for the Web service.</span></span> <span data-ttu-id="62dfd-116">應用程式開發人員必須為用戶端加入安全性設定。</span><span class="sxs-lookup"><span data-stu-id="62dfd-116">The application developer must add the security settings for the client.</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="62dfd-117">建立[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]用戶端，請參閱[How to： 建立用戶端](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="62dfd-117"> creating a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, see the [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="62dfd-118">建立類別，表示可與 WSE 3.0 Web 服務通訊的繫結。</span><span class="sxs-lookup"><span data-stu-id="62dfd-118">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="62dfd-119">下列類別是一部分[與 WSE 互通](http://msdn.microsoft.com/en-us/f6816861-96a0-45f9-8736-8e4e82cd3a41)範例：</span><span class="sxs-lookup"><span data-stu-id="62dfd-119">The following class is part of the [Interoperating with WSE](http://msdn.microsoft.com/en-us/f6816861-96a0-45f9-8736-8e4e82cd3a41) sample:</span></span>  
  
    1.  <span data-ttu-id="62dfd-120">建立從 <xref:System.ServiceModel.Channels.Binding> 類別衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="62dfd-120">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="62dfd-121">下列程式碼範例會建立一個名為 `WseHttpBinding` 的類別，此類別衍生自 <xref:System.ServiceModel.Channels.Binding> 類別。</span><span class="sxs-lookup"><span data-stu-id="62dfd-121">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  <span data-ttu-id="62dfd-122">將屬性加入至類別，這些屬性會指定 WSE 服務所使用的 WSE 通行判斷提示 (Turnkey Assertion)、是否需要衍生金鑰、是否使用安全工作階段、是否需要簽章確認，以及訊息保護設定。</span><span class="sxs-lookup"><span data-stu-id="62dfd-122">Add properties to the class that specify the WSE turnkey assertion used by the WSE service, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span> <span data-ttu-id="62dfd-123">在 WSE 3.0 中，通行判斷提示會指定用戶端或 Web 服務的安全性需求，這與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的繫結驗證模式類似。</span><span class="sxs-lookup"><span data-stu-id="62dfd-123">In WSE 3.0, a turnkey assertion specifies the security requirements for a client or Web service—similar to the authentication mode of a binding in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
         <span data-ttu-id="62dfd-124">下列程式碼範例會定義 `SecurityAssertion`、`RequireDerivedKeys`、`EstablishSecurityContext` 和 `MessageProtectionOrder` 屬性，這些屬性會分別指定 WSE 通行判斷提示、是否需要衍生金鑰、是否使用安全工作階段、是否需要簽章確認，以及訊息保護設定。</span><span class="sxs-lookup"><span data-stu-id="62dfd-124">The following code example defines the `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, and `MessageProtectionOrder` properties that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  <span data-ttu-id="62dfd-125">覆寫 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> 方法來設定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="62dfd-125">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="62dfd-126">下列程式碼範例會藉由取得 `SecurityAssertion` 和 `MessageProtectionOrder` 屬性的值，指定傳輸、訊息編碼和訊息保護設定。</span><span class="sxs-lookup"><span data-stu-id="62dfd-126">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  <span data-ttu-id="62dfd-127">在用戶端應用程式程式碼中，加入程式碼以設定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="62dfd-127">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="62dfd-128">下列程式碼範例會指定 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端必須依照 WSE 3.0 `AnonymousForCertificate` 通行安全性判斷提示所定義，使用訊息保護和驗證。</span><span class="sxs-lookup"><span data-stu-id="62dfd-128">The following code example specifies that the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="62dfd-129">此外，也需要安全工作階段和衍生金鑰。</span><span class="sxs-lookup"><span data-stu-id="62dfd-129">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="62dfd-130">範例</span><span class="sxs-lookup"><span data-stu-id="62dfd-130">Example</span></span>  
 <span data-ttu-id="62dfd-131">下列程式碼範例會定義自訂的繫結，此繫結會公開 WSE 3.0 通行安全性判斷提示屬性的對應屬性。</span><span class="sxs-lookup"><span data-stu-id="62dfd-131">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="62dfd-132">此自訂繫結 (名為 `WseHttpBinding`) 接著會用來指定可與 WSSecurityAnonymous WSE 3.0 快速入門範例通訊的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="62dfd-132">That custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that communicates with the WSSecurityAnonymous WSE 3.0 QuickStart sample.</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="62dfd-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62dfd-133">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 [<span data-ttu-id="62dfd-134">與 WSE 互通</span><span class="sxs-lookup"><span data-stu-id="62dfd-134">Interoperating with WSE</span></span>](http://msdn.microsoft.com/en-us/f6816861-96a0-45f9-8736-8e4e82cd3a41)
