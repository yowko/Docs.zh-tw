---
title: 作法：將 WCF 服務設為與 ASP.NET Web 服務用戶端交互操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: 9c241c06f153e4f85c70459ff3c50889057103f5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295037"
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a><span data-ttu-id="deb4e-102">作法：將 WCF 服務設為與 ASP.NET Web 服務用戶端交互操作</span><span class="sxs-lookup"><span data-stu-id="deb4e-102">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>

<span data-ttu-id="deb4e-103">若要設定 Windows Communication Foundation (WCF) 服務端點與 ASP.NET Web 服務用戶端互通，請使用 <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> 類型做為服務端點的系結類型。</span><span class="sxs-lookup"><span data-stu-id="deb4e-103">To configure a Windows Communication Foundation (WCF) service endpoint to be interoperable with ASP.NET Web service clients, use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
 <span data-ttu-id="deb4e-104">您可選擇啟用 HTTPS 支援及對繫結的傳輸層級用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="deb4e-104">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span> <span data-ttu-id="deb4e-105">ASP.NET Web 服務用戶端不支援 MTOM 訊息編碼，因此 <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> 屬性應該保留為其預設值，也就是 <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="deb4e-105">ASP.NET Web service clients do not support MTOM message encoding, so the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property should be left as its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>.</span></span> <span data-ttu-id="deb4e-106">ASP.NET Web 服務用戶端不支援 WS-Security，因此 <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> 應該設定為 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> 。</span><span class="sxs-lookup"><span data-stu-id="deb4e-106">ASP.NET Web Service clients do not support WS-Security, so the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> should be set to <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.</span></span>  
  
 <span data-ttu-id="deb4e-107">若要將 WCF 服務的中繼資料提供給 ASP.NET Web 服務 proxy 產生工具 (也就是 [Web 服務描述語言工具 ( # A0)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))、 [Web 服務探索工具 ( # A1)](/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100))和 Visual Studio) 中的「 **加入 Web 參考** 」功能，您應該公開 HTTP/GET 中繼資料端點。</span><span class="sxs-lookup"><span data-stu-id="deb4e-107">To make the metadata for a WCF service available to ASP.NET Web service proxy generation tools (that is, [Web Services Description Language Tool (Wsdl.exe)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100)), [Web Services Discovery Tool (Disco.exe)](/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100)), and the **Add Web Reference** feature in Visual Studio), you should expose an HTTP/GET metadata endpoint.</span></span>  
  
## <a name="add-an-endpoint-in-code"></a><span data-ttu-id="deb4e-108">在程式碼中新增端點</span><span class="sxs-lookup"><span data-stu-id="deb4e-108">Add an endpoint in code</span></span>  
  
1. <span data-ttu-id="deb4e-109">建立新的 <xref:System.ServiceModel.BasicHttpBinding> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="deb4e-109">Create a new <xref:System.ServiceModel.BasicHttpBinding> instance</span></span>  
  
2. <span data-ttu-id="deb4e-110">設定繫結至 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> 的安全性模式，以選擇性啟用此服務端點繫結的傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="deb4e-110">Optionally enable transport security for this service endpoint binding by setting the security mode for the binding to <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.</span></span> <span data-ttu-id="deb4e-111">如需詳細資訊，請參閱 [傳輸安全性](transport-security.md)。</span><span class="sxs-lookup"><span data-stu-id="deb4e-111">For details, see [Transport Security](transport-security.md).</span></span>  
  
3. <span data-ttu-id="deb4e-112">使用您剛建立的繫結執行個體新增新的應用程式端點到您的服務主機中。</span><span class="sxs-lookup"><span data-stu-id="deb4e-112">Add a new application endpoint to your service host using the binding instance that you just created.</span></span> <span data-ttu-id="deb4e-113">如需如何在程式碼中新增服務端點的詳細資訊，請參閱 [如何：在程式碼中建立服務端點](how-to-create-a-service-endpoint-in-code.md)。</span><span class="sxs-lookup"><span data-stu-id="deb4e-113">For details about how to add a service endpoint in code, see the [How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md).</span></span>  
  
4. <span data-ttu-id="deb4e-114">啟用您的服務的 HTTP/GET 中繼資料端點。</span><span class="sxs-lookup"><span data-stu-id="deb4e-114">Enable an HTTP/GET metadata endpoint for your service.</span></span> <span data-ttu-id="deb4e-115">如需詳細資訊，請參閱 [如何：使用程式碼發行服務的中繼資料](how-to-publish-metadata-for-a-service-using-code.md)。</span><span class="sxs-lookup"><span data-stu-id="deb4e-115">For details see [How to: Publish Metadata for a Service Using Code](how-to-publish-metadata-for-a-service-using-code.md).</span></span>  
  
## <a name="add-an-endpoint-in-a-configuration-file"></a><span data-ttu-id="deb4e-116">在設定檔中新增端點</span><span class="sxs-lookup"><span data-stu-id="deb4e-116">Add an endpoint in a configuration file</span></span>  
  
1. <span data-ttu-id="deb4e-117">建立新的 <xref:System.ServiceModel.BasicHttpBinding> 繫結組態。</span><span class="sxs-lookup"><span data-stu-id="deb4e-117">Create a new <xref:System.ServiceModel.BasicHttpBinding> binding configuration.</span></span> <span data-ttu-id="deb4e-118">如需詳細資訊，請參閱 [如何：在設定中指定服務](../how-to-specify-a-service-binding-in-configuration.md)系結。</span><span class="sxs-lookup"><span data-stu-id="deb4e-118">For details, see the [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
2. <span data-ttu-id="deb4e-119">設定繫結至 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> 的安全性模式，以選擇性啟用此服務端點繫結組態的傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="deb4e-119">Optionally enable transport security for this service endpoint binding configuration by setting the security mode for the binding to <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.</span></span> <span data-ttu-id="deb4e-120">如需詳細資訊，請參閱 [傳輸安全性](transport-security.md)。</span><span class="sxs-lookup"><span data-stu-id="deb4e-120">For details, see [Transport Security](transport-security.md).</span></span>  
  
3. <span data-ttu-id="deb4e-121">使用您剛建立的繫結組態設定您的服務的新應用程式端點。</span><span class="sxs-lookup"><span data-stu-id="deb4e-121">Configure a new application endpoint for your service using the binding configuration that you just created.</span></span> <span data-ttu-id="deb4e-122">如需如何在設定檔中新增服務端點的詳細資訊，請參閱 [如何：在設定中建立服務端點](how-to-create-a-service-endpoint-in-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="deb4e-122">For details about how to add a service endpoint in a configuration file, see the [How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md).</span></span>  
  
4. <span data-ttu-id="deb4e-123">啟用您的服務的 HTTP/GET 中繼資料端點。</span><span class="sxs-lookup"><span data-stu-id="deb4e-123">Enable an HTTP/GET metadata endpoint for your service.</span></span> <span data-ttu-id="deb4e-124">如需詳細資訊，請參閱 [如何：使用設定檔發行服務的中繼資料](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="deb4e-124">For details see the [How to: Publish Metadata for a Service Using a Configuration File](how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="deb4e-125">範例</span><span class="sxs-lookup"><span data-stu-id="deb4e-125">Example</span></span>  

 <span data-ttu-id="deb4e-126">下列範例程式碼示範如何在程式碼中新增與 ASP.NET Web 服務用戶端相容的 WCF 端點，也可以在設定檔中新增。</span><span class="sxs-lookup"><span data-stu-id="deb4e-126">The following example code demonstrates how to add a WCF endpoint that is compatible with ASP.NET Web service clients in code and alternatively in configuration files.</span></span>  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]
  
## <a name="see-also"></a><span data-ttu-id="deb4e-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="deb4e-127">See also</span></span>

- [<span data-ttu-id="deb4e-128">作法：在程式碼中建立服務端點</span><span class="sxs-lookup"><span data-stu-id="deb4e-128">How to: Create a Service Endpoint in Code</span></span>](how-to-create-a-service-endpoint-in-code.md)
- [<span data-ttu-id="deb4e-129">作法：使用程式碼發行服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="deb4e-129">How to: Publish Metadata for a Service Using Code</span></span>](how-to-publish-metadata-for-a-service-using-code.md)
- [<span data-ttu-id="deb4e-130">作法：在組態中指定服務繫結</span><span class="sxs-lookup"><span data-stu-id="deb4e-130">How to: Specify a Service Binding in Configuration</span></span>](../how-to-specify-a-service-binding-in-configuration.md)
- [<span data-ttu-id="deb4e-131">作法：在組態中建立服務端點</span><span class="sxs-lookup"><span data-stu-id="deb4e-131">How to: Create a Service Endpoint in Configuration</span></span>](how-to-create-a-service-endpoint-in-configuration.md)
- [<span data-ttu-id="deb4e-132">作法：使用組態檔發行服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="deb4e-132">How to: Publish Metadata for a Service Using a Configuration File</span></span>](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="deb4e-133">傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="deb4e-133">Transport Security</span></span>](transport-security.md)
- [<span data-ttu-id="deb4e-134">使用中繼資料</span><span class="sxs-lookup"><span data-stu-id="deb4e-134">Using Metadata</span></span>](using-metadata.md)
