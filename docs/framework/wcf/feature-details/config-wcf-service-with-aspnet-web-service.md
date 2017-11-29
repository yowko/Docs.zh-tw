---
title: "HOW TO：將 WCF 服務設為與 ASP.NET Web 服務用戶端交互操作"
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
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ce9c0ca82803654b2268ff0440bbacec4cb0d0dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a><span data-ttu-id="f3fc4-102">HOW TO：將 WCF 服務設為與 ASP.NET Web 服務用戶端交互操作</span><span class="sxs-lookup"><span data-stu-id="f3fc4-102">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>
<span data-ttu-id="f3fc4-103">若要將 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務端點設定為與 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 服務用戶端交互操作，請使用 <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> 類型做為服務端點的繫結類型。</span><span class="sxs-lookup"><span data-stu-id="f3fc4-103">To configure a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service endpoint to be interoperable with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web service clients, use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
 <span data-ttu-id="f3fc4-104">您可選擇啟用 HTTPS 支援及對繫結的傳輸層級用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="f3fc4-104">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span> [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="f3fc4-105"> Web 服務用戶端不支援 MTOM 訊息編碼，因此應將 <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> 屬性保留為預設值，也就是 <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f3fc4-105"> Web service clients do not support MTOM message encoding, so the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property should be left as its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f3fc4-106">ASP.Net Web 服務用戶端不支援 Web 服務安全性，因此應該將 <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> 設定為 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>。</span><span class="sxs-lookup"><span data-stu-id="f3fc4-106">ASP.Net Web Service clients do not support WS-Security, so the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> should be set to <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.</span></span>  
  
 <span data-ttu-id="f3fc4-107">若要將中繼資料給[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]可用來服務[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web 服務 proxy 產生工具 (也就是[Web 服務描述語言工具 (Wsdl.exe)](http://go.microsoft.com/fwlink/?LinkId=73833)， [Web 服務探索工具 (Disco.exe)](http://go.microsoft.com/fwlink/?LinkId=73834)，和 Visual Studio 中的加入 Web 參考功能)，您應該公開 （expose) 的 HTTP/GET 中繼資料端點。</span><span class="sxs-lookup"><span data-stu-id="f3fc4-107">To make the metadata for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service available to [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web service proxy generation tools (that is, [Web Services Description Language Tool (Wsdl.exe)](http://go.microsoft.com/fwlink/?LinkId=73833), [Web Services Discovery Tool (Disco.exe)](http://go.microsoft.com/fwlink/?LinkId=73834), and the Add Web Reference feature in Visual Studio), you should expose an HTTP/GET metadata endpoint.</span></span>  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-code"></a><span data-ttu-id="f3fc4-108">若要在程式碼中新增與 ASP.NET Web 服務用戶端相容的 WCF 端點</span><span class="sxs-lookup"><span data-stu-id="f3fc4-108">To add a WCF endpoint that is compatible with ASP.NET Web service clients in code</span></span>  
  
1.  <span data-ttu-id="f3fc4-109">建立新的 <xref:System.ServiceModel.BasicHttpBinding> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="f3fc4-109">Create a new <xref:System.ServiceModel.BasicHttpBinding> instance</span></span>  
  
2.  <span data-ttu-id="f3fc4-110">設定繫結至 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> 的安全性模式，以選擇性啟用此服務端點繫結的傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="f3fc4-110">Optionally enable transport security for this service endpoint binding by setting the security mode for the binding to <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.</span></span> <span data-ttu-id="f3fc4-111">如需詳細資訊，請參閱[傳輸安全性](../../../../docs/framework/wcf/feature-details/transport-security.md)。</span><span class="sxs-lookup"><span data-stu-id="f3fc4-111">For details, please see [Transport Security](../../../../docs/framework/wcf/feature-details/transport-security.md).</span></span>  
  
3.  <span data-ttu-id="f3fc4-112">使用您剛建立的繫結執行個體新增新的應用程式端點到您的服務主機中。</span><span class="sxs-lookup"><span data-stu-id="f3fc4-112">Add a new application endpoint to your service host using the binding instance that you just created.</span></span> <span data-ttu-id="f3fc4-113">如需有關如何在程式碼中加入服務端點的詳細資訊，請參閱[How to： 在程式碼中建立服務端點](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)。</span><span class="sxs-lookup"><span data-stu-id="f3fc4-113">For details about how to add a service endpoint in code, see the [How to: Create a Service Endpoint in Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span></span>  
  
4.  <span data-ttu-id="f3fc4-114">啟用您的服務的 HTTP/GET 中繼資料端點。</span><span class="sxs-lookup"><span data-stu-id="f3fc4-114">Enable an HTTP/GET metadata endpoint for your service.</span></span> <span data-ttu-id="f3fc4-115">如需詳細資訊，請參閱[How to： 服務使用程式碼發行中繼資料](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)。</span><span class="sxs-lookup"><span data-stu-id="f3fc4-115">For details see [How to: Publish Metadata for a Service Using Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span></span>  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-a-configuration-file"></a><span data-ttu-id="f3fc4-116">若要在組態檔中新增與 ASP.NET Web 服務用戶端相容的 WCF 端點</span><span class="sxs-lookup"><span data-stu-id="f3fc4-116">To add a WCF endpoint that is compatible with ASP.NET Web service clients in a configuration file</span></span>  
  
1.  <span data-ttu-id="f3fc4-117">建立新的 <xref:System.ServiceModel.BasicHttpBinding> 繫結組態。</span><span class="sxs-lookup"><span data-stu-id="f3fc4-117">Create a new <xref:System.ServiceModel.BasicHttpBinding> binding configuration.</span></span> <span data-ttu-id="f3fc4-118">如需詳細資訊，請參閱[How to： 在組態中指定服務繫結](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="f3fc4-118">For details, see the [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
2.  <span data-ttu-id="f3fc4-119">設定繫結至 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> 的安全性模式，以選擇性啟用此服務端點繫結組態的傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="f3fc4-119">Optionally enable transport security for this service endpoint binding configuration by setting the security mode for the binding to <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.</span></span> <span data-ttu-id="f3fc4-120">如需詳細資訊，請參閱[傳輸安全性](../../../../docs/framework/wcf/feature-details/transport-security.md)。</span><span class="sxs-lookup"><span data-stu-id="f3fc4-120">For details, see [Transport Security](../../../../docs/framework/wcf/feature-details/transport-security.md).</span></span>  
  
3.  <span data-ttu-id="f3fc4-121">使用您剛建立的繫結組態設定您的服務的新應用程式端點。</span><span class="sxs-lookup"><span data-stu-id="f3fc4-121">Configure a new application endpoint for your service using the binding configuration that you just created.</span></span> <span data-ttu-id="f3fc4-122">如需有關如何在組態檔中加入服務端點的詳細資訊，請參閱[How to： 在組態中建立服務端點](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="f3fc4-122">For details about how to add a service endpoint in a configuration file, see the [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span></span>  
  
4.  <span data-ttu-id="f3fc4-123">啟用您的服務的 HTTP/GET 中繼資料端點。</span><span class="sxs-lookup"><span data-stu-id="f3fc4-123">Enable an HTTP/GET metadata endpoint for your service.</span></span> <span data-ttu-id="f3fc4-124">如需詳細資訊，請參閱[How to： 使用組態檔的服務發行中繼資料](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="f3fc4-124">For details see the [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3fc4-125">範例</span><span class="sxs-lookup"><span data-stu-id="f3fc4-125">Example</span></span>  
 <span data-ttu-id="f3fc4-126">下列範例程式碼示範如何在程式碼中，或是組態檔案中新增與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web 服務用戶端相容的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 端點。</span><span class="sxs-lookup"><span data-stu-id="f3fc4-126">The following example code demonstrates how to add a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint that is compatible with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web service clients in code and alternatively in configuration files.</span></span>  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)] 
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)] 
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]     
  
## <a name="see-also"></a><span data-ttu-id="f3fc4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3fc4-127">See Also</span></span>  
 [<span data-ttu-id="f3fc4-128">如何： 在程式碼中建立服務端點</span><span class="sxs-lookup"><span data-stu-id="f3fc4-128">How to: Create a Service Endpoint in Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 [<span data-ttu-id="f3fc4-129">如何： 使用程式碼的服務發行中繼資料</span><span class="sxs-lookup"><span data-stu-id="f3fc4-129">How to: Publish Metadata for a Service Using Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 [<span data-ttu-id="f3fc4-130">如何：在設定中指定服務繫結</span><span class="sxs-lookup"><span data-stu-id="f3fc4-130">How to: Specify a Service Binding in Configuration</span></span>](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [<span data-ttu-id="f3fc4-131">如何： 在組態中建立服務端點</span><span class="sxs-lookup"><span data-stu-id="f3fc4-131">How to: Create a Service Endpoint in Configuration</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 [<span data-ttu-id="f3fc4-132">如何： 使用組態檔的服務發行中繼資料</span><span class="sxs-lookup"><span data-stu-id="f3fc4-132">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="f3fc4-133">傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="f3fc4-133">Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="f3fc4-134">使用中繼資料</span><span class="sxs-lookup"><span data-stu-id="f3fc4-134">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
