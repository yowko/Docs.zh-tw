---
title: "HOW TO：在可靠的工作階段內交換訊息"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c0465f50de37d7276cad5920c4b9fb9e544caf57
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a><span data-ttu-id="ece8f-102">HOW TO：在可靠的工作階段內交換訊息</span><span class="sxs-lookup"><span data-stu-id="ece8f-102">How to: Exchange Messages Within a Reliable Session</span></span>

<span data-ttu-id="ece8f-103">本主題概要說明透過其中一個系統提供的繫結啟用可靠工作階段 (此繫結支援此類工作階段，但非預設) 所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="ece8f-103">This topic outlines the steps required to enable a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="ece8f-104">啟用可靠工作階段命令式程式碼或是宣告式組態檔。</span><span class="sxs-lookup"><span data-stu-id="ece8f-104">You enable a reliable session imperatively using code or declaratively in your configuration file.</span></span> <span data-ttu-id="ece8f-105">若要啟用可靠工作階段，並規定訊息到達其傳送的順序相同，此程序會使用用戶端和服務組態檔。</span><span class="sxs-lookup"><span data-stu-id="ece8f-105">This procedure uses the client and service configuration files to enable the reliable session and to stipulate that the messages arrive in the same order in which they were sent.</span></span>

<span data-ttu-id="ece8f-106">此程序的重要部分為端點組態項目包含`bindingConfiguration`屬性必須參考名為繫結組態`Binding1`。</span><span class="sxs-lookup"><span data-stu-id="ece8f-106">The key part of this procedure is that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="ece8f-107">[ **\<繫結 >** ](../../../../docs/framework/misc/binding.md)組態項目會參考此名稱，藉此啟用可靠工作階段`enabled`屬性[ **\<reliableSession >** ](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)元素`true`。</span><span class="sxs-lookup"><span data-stu-id="ece8f-107">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) element to `true`.</span></span> <span data-ttu-id="ece8f-108">您可以將 `ordered` 屬性設為 `true`，為可靠工作階段指定依序傳遞保證。</span><span class="sxs-lookup"><span data-stu-id="ece8f-108">You specify the ordered delivery assurances for the reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="ece8f-109">此範例的來源副本，請參閱[WS 可靠工作階段](../../../../docs/framework/wcf/samples/ws-reliable-session.md)。</span><span class="sxs-lookup"><span data-stu-id="ece8f-109">For the source copy of this example, see [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="ece8f-110">透過 WSHttpBinding 使用可靠工作階段設定服務</span><span class="sxs-lookup"><span data-stu-id="ece8f-110">Configure the service with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="ece8f-111">定義服務類型的服務合約。</span><span class="sxs-lookup"><span data-stu-id="ece8f-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. <span data-ttu-id="ece8f-112">在服務類別中實作服務合約。</span><span class="sxs-lookup"><span data-stu-id="ece8f-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="ece8f-113">請注意，位址或繫結資訊不指定服務的實作內部。</span><span class="sxs-lookup"><span data-stu-id="ece8f-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="ece8f-114">您不需要撰寫程式碼以擷取組態檔中的位址或繫結資訊的資訊。</span><span class="sxs-lookup"><span data-stu-id="ece8f-114">You aren't required to write code to retrieve the address or binding information information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. <span data-ttu-id="ece8f-115">建立*Web.config*檔案來設定的端點`CalculatorService`使用<xref:System.ServiceModel.WSHttpBinding>與可靠工作階段啟用和排序的傳遞所需的訊息。</span><span class="sxs-lookup"><span data-stu-id="ece8f-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding> with reliable session enabled and ordered delivery of messages required.</span></span>

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. <span data-ttu-id="ece8f-116">建立*Service.svc*檔案包含行：</span><span class="sxs-lookup"><span data-stu-id="ece8f-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1.  <span data-ttu-id="ece8f-117">位置*Service.svc*網際網路資訊服務 (IIS) 虛擬目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="ece8f-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="ece8f-118">設定用戶端透過 WSHttpBinding 使用可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="ece8f-118">Configure the client with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="ece8f-119">使用[ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)從命令列從服務中繼資料產生程式碼：</span><span class="sxs-lookup"><span data-stu-id="ece8f-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata:</span></span>

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="ece8f-120">產生的用戶端包含`ICalculator`定義用戶端實作所必須滿足的服務合約的介面。</span><span class="sxs-lookup"><span data-stu-id="ece8f-120">The generated client contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. <span data-ttu-id="ece8f-121">產生的用戶端應用程式也包含 `ClientCalculator` 的實作。</span><span class="sxs-lookup"><span data-stu-id="ece8f-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="ece8f-122">請注意，位址和繫結資訊不內部指定服務的實作。</span><span class="sxs-lookup"><span data-stu-id="ece8f-122">Note that the address and binding information isn't specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="ece8f-123">您不需要撰寫程式碼以擷取組態檔中的位址或繫結資訊的資訊。</span><span class="sxs-lookup"><span data-stu-id="ece8f-123">You aren't required to write code to retrieve the address or binding information information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. <span data-ttu-id="ece8f-124">*Svcutil.exe*也會產生的組態會使用用戶端<xref:System.ServiceModel.WSHttpBinding>類別。</span><span class="sxs-lookup"><span data-stu-id="ece8f-124">*Svcutil.exe* also generates the configuration for the client that uses the <xref:System.ServiceModel.WSHttpBinding> class.</span></span> <span data-ttu-id="ece8f-125">組態檔命名*App.config*時使用[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ece8f-125">Name the configuration file *App.config* when using [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. <span data-ttu-id="ece8f-126">建立的執行個體`ClientCalculator`應用程式中呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="ece8f-126">Create an instance of the `ClientCalculator` in an application and call the service operations.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. <span data-ttu-id="ece8f-127">請編譯並執行用戶端。</span><span class="sxs-lookup"><span data-stu-id="ece8f-127">Compile and run the client.</span></span>

## <a name="example"></a><span data-ttu-id="ece8f-128">範例</span><span class="sxs-lookup"><span data-stu-id="ece8f-128">Example</span></span>

<span data-ttu-id="ece8f-129">好幾個系統提供的繫結預設都支援可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="ece8f-129">Several of the system-provided bindings support reliable sessions by default.</span></span> <span data-ttu-id="ece8f-130">這些活動包括：</span><span class="sxs-lookup"><span data-stu-id="ece8f-130">These include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

<span data-ttu-id="ece8f-131">如需如何建立支援可靠工作階段的自訂繫結的範例，請參閱[How to： 使用 HTTPS 建立自訂可靠工作階段繫結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)。</span><span class="sxs-lookup"><span data-stu-id="ece8f-131">For an example of how to create a custom binding that supports reliable sessions, see [How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ece8f-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="ece8f-132">See also</span></span>

[<span data-ttu-id="ece8f-133">可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="ece8f-133">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
