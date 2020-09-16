---
title: 作法：在可靠的工作階段內交換訊息
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 97371f8572d5d0db633ab8dd1ca82067d9d55c3f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550185"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a><span data-ttu-id="10ed6-102">作法：在可靠的工作階段內交換訊息</span><span class="sxs-lookup"><span data-stu-id="10ed6-102">How to: Exchange Messages Within a Reliable Session</span></span>

<span data-ttu-id="10ed6-103">本主題概要說明透過其中一個系統提供的繫結啟用可靠工作階段 (此繫結支援此類工作階段，但非預設) 所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="10ed6-103">This topic outlines the steps required to enable a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="10ed6-104">您可以使用程式碼或以宣告方式在設定檔中啟用可靠會話。</span><span class="sxs-lookup"><span data-stu-id="10ed6-104">You enable a reliable session imperatively using code or declaratively in your configuration file.</span></span> <span data-ttu-id="10ed6-105">此程式會使用用戶端和服務設定檔來啟用可靠會話，並規定訊息以傳送的相同順序送達。</span><span class="sxs-lookup"><span data-stu-id="10ed6-105">This procedure uses the client and service configuration files to enable the reliable session and to stipulate that the messages arrive in the same order in which they were sent.</span></span>

<span data-ttu-id="10ed6-106">此程式的關鍵區段是端點設定元素包含 `bindingConfiguration` 屬性，該屬性會參考名為的系結設定 `Binding1` 。</span><span class="sxs-lookup"><span data-stu-id="10ed6-106">The key part of this procedure is that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="10ed6-107">[**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)設定元素會參考此名稱，藉由將專案的屬性設定為，來啟用可靠會話 `enabled` [**\<reliableSession>**](/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) `true` 。</span><span class="sxs-lookup"><span data-stu-id="10ed6-107">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) element to `true`.</span></span> <span data-ttu-id="10ed6-108">您可以將 `ordered` 屬性設為 `true`，為可靠工作階段指定依序傳遞保證。</span><span class="sxs-lookup"><span data-stu-id="10ed6-108">You specify the ordered delivery assurances for the reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="10ed6-109">如需此範例的來源複本，請參閱 [WS 可靠會話](../samples/ws-reliable-session.md)。</span><span class="sxs-lookup"><span data-stu-id="10ed6-109">For the source copy of this example, see [WS Reliable Session](../samples/ws-reliable-session.md).</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="10ed6-110">使用 WSHttpBinding 設定服務以使用可靠會話</span><span class="sxs-lookup"><span data-stu-id="10ed6-110">Configure the service with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="10ed6-111">定義服務類型的服務合約。</span><span class="sxs-lookup"><span data-stu-id="10ed6-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. <span data-ttu-id="10ed6-112">在服務類別中實作服務合約。</span><span class="sxs-lookup"><span data-stu-id="10ed6-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="10ed6-113">請注意，在服務的執行內不會指定位址或系結資訊。</span><span class="sxs-lookup"><span data-stu-id="10ed6-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="10ed6-114">您不需要撰寫程式碼，就能從設定檔取出位址或系結資訊。</span><span class="sxs-lookup"><span data-stu-id="10ed6-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. <span data-ttu-id="10ed6-115">建立 *Web.config* 檔案，以設定的端點，該端點 `CalculatorService` 會使用 <xref:System.ServiceModel.WSHttpBinding> 已啟用可靠會話且依序傳遞所需的訊息。</span><span class="sxs-lookup"><span data-stu-id="10ed6-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding> with reliable session enabled and ordered delivery of messages required.</span></span>

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. <span data-ttu-id="10ed6-116">建立包含該行的 *服務 .svc* 檔案：</span><span class="sxs-lookup"><span data-stu-id="10ed6-116">Create a *Service.svc* file that contains the line:</span></span>

   ```aspx-csharp
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. <span data-ttu-id="10ed6-117">將 *服務 .svc* 檔案放在 INTERNET INFORMATION SERVICES (IIS) 虛擬目錄中。</span><span class="sxs-lookup"><span data-stu-id="10ed6-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="10ed6-118">使用 WSHttpBinding 設定用戶端以使用可靠會話</span><span class="sxs-lookup"><span data-stu-id="10ed6-118">Configure the client with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="10ed6-119">從命令列使用 [ [System.servicemodel 中繼資料公用程式] 工具 (*Svcutil.exe*) ](../servicemodel-metadata-utility-tool-svcutil-exe.md) ，從服務中繼資料產生程式碼：</span><span class="sxs-lookup"><span data-stu-id="10ed6-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata:</span></span>

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="10ed6-120">產生的用戶端所包含的 `ICalculator` 介面，會定義用戶端執行必須滿足的服務合約。</span><span class="sxs-lookup"><span data-stu-id="10ed6-120">The generated client contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. <span data-ttu-id="10ed6-121">產生的用戶端應用程式也包含 `ClientCalculator` 的實作。</span><span class="sxs-lookup"><span data-stu-id="10ed6-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="10ed6-122">請注意，在服務的任何位置中，都不會指定位址和系結資訊。</span><span class="sxs-lookup"><span data-stu-id="10ed6-122">Note that the address and binding information isn't specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="10ed6-123">您不需要撰寫程式碼，就能從設定檔取出位址或系結資訊。</span><span class="sxs-lookup"><span data-stu-id="10ed6-123">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. <span data-ttu-id="10ed6-124">*Svcutil.exe* 也會產生使用類別之用戶端的設定 <xref:System.ServiceModel.WSHttpBinding> 。</span><span class="sxs-lookup"><span data-stu-id="10ed6-124">*Svcutil.exe* also generates the configuration for the client that uses the <xref:System.ServiceModel.WSHttpBinding> class.</span></span> <span data-ttu-id="10ed6-125">使用 Visual Studio 時，請將設定檔命名為 *App.config* 。</span><span class="sxs-lookup"><span data-stu-id="10ed6-125">Name the configuration file *App.config* when using Visual Studio.</span></span>

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. <span data-ttu-id="10ed6-126">`ClientCalculator`在應用程式中建立的實例，並呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="10ed6-126">Create an instance of the `ClientCalculator` in an application and call the service operations.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. <span data-ttu-id="10ed6-127">請編譯並執行用戶端。</span><span class="sxs-lookup"><span data-stu-id="10ed6-127">Compile and run the client.</span></span>

## <a name="example"></a><span data-ttu-id="10ed6-128">範例</span><span class="sxs-lookup"><span data-stu-id="10ed6-128">Example</span></span>

<span data-ttu-id="10ed6-129">好幾個系統提供的繫結預設都支援可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="10ed6-129">Several of the system-provided bindings support reliable sessions by default.</span></span> <span data-ttu-id="10ed6-130">它們包括：</span><span class="sxs-lookup"><span data-stu-id="10ed6-130">These include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

<span data-ttu-id="10ed6-131">如需如何建立支援可靠會話之自訂系結的範例，請參閱 how [to：使用 HTTPS 建立自訂可靠會話](how-to-create-a-custom-reliable-session-binding-with-https.md)系結。</span><span class="sxs-lookup"><span data-stu-id="10ed6-131">For an example of how to create a custom binding that supports reliable sessions, see [How to: Create a Custom Reliable Session Binding with HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="10ed6-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10ed6-132">See also</span></span>

- [<span data-ttu-id="10ed6-133">可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="10ed6-133">Reliable Sessions</span></span>](reliable-sessions.md)
