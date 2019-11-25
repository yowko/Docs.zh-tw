---
title: HOW TO：使用 HTTPS 建立自訂可靠工作階段繫結
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: 26466a97ae44e6852c189d0b72bdba1b93d86141
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141730"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a><span data-ttu-id="7b9dc-102">HOW TO：使用 HTTPS 建立自訂可靠工作階段繫結</span><span class="sxs-lookup"><span data-stu-id="7b9dc-102">How to: Create a Custom Reliable Session Binding with HTTPS</span></span>

<span data-ttu-id="7b9dc-103">本主題示範使用 Secure Sockets Layer (SSL) 傳輸安全性來搭配可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-103">This topic demonstrates the use of Secure Sockets Layer (SSL) transport security with reliable sessions.</span></span> <span data-ttu-id="7b9dc-104">若要透過 HTTPS 使用可靠工作階段，您必須建立使用可靠工作階段與 HTTPS 傳輸的自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-104">To use a reliable session over HTTPS, you must create a custom binding that uses a reliable session and the HTTPS transport.</span></span> <span data-ttu-id="7b9dc-105">您可以使用程式碼或以宣告方式在設定檔中啟用可靠會話。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-105">You enable the reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="7b9dc-106">此程式會使用用戶端和服務設定檔來啟用可靠會話和[ **\<HTTPsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md)元素。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-106">This procedure uses the client and service configuration files to enable the reliable session and the [**\<httpsTransport>**](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) element.</span></span>

<span data-ttu-id="7b9dc-107">此程式的重要部分是 **\<端點 >** configuration 元素包含一個 `bindingConfiguration` 屬性，其參考名為 `reliableSessionOverHttps`的自訂系結設定。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-107">The key part of this procedure is that the **\<endpoint>** configuration element contain a `bindingConfiguration` attribute that references a custom binding configuration named `reliableSessionOverHttps`.</span></span> <span data-ttu-id="7b9dc-108">\<系結[ **>** ](../../configure-apps/file-schema/wcf/bindings.md) configuration 專案會參考此名稱，藉由包含 **\<reliableSession >** 和 **\<HTTPsTransport >** 元素，來指定要使用可靠會話和 HTTPS 傳輸。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-108">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element references this name to specify that a reliable session and the HTTPS transport are used by including **\<reliableSession>** and **\<httpsTransport>** elements.</span></span>

<span data-ttu-id="7b9dc-109">如需此範例的來源複本，請參閱透過[HTTPS 自訂系結可靠會話](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md)。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-109">For the source copy of this example, see [Custom Binding Reliable Session over HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).</span></span>

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="7b9dc-110">以 CustomBinding 設定服務，以搭配使用可靠會話與 HTTPS</span><span class="sxs-lookup"><span data-stu-id="7b9dc-110">Configure the service with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="7b9dc-111">定義服務類型的服務合約。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. <span data-ttu-id="7b9dc-112">在服務類別中實作服務合約。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="7b9dc-113">請注意，不會在服務的執行中指定位址或系結資訊。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="7b9dc-114">您不需要撰寫程式碼，就能從設定檔抓取位址或系結資訊。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. <span data-ttu-id="7b9dc-115">建立*web.config*檔案，使用名為 `reliableSessionOverHttps` 的自訂系結來設定 `CalculatorService` 的端點，該系結會使用可靠會話和 HTTPS 傳輸。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` with a custom binding named `reliableSessionOverHttps` that uses a reliable session and the HTTPS transport.</span></span>

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. <span data-ttu-id="7b9dc-116">建立包含這一行的*服務 .svc*檔案：</span><span class="sxs-lookup"><span data-stu-id="7b9dc-116">Create a *Service.svc* file that contains the line:</span></span>

   `<%@ServiceHost language=c# Service="CalculatorService" %>`

1. <span data-ttu-id="7b9dc-117">將*服務 .svc*檔案放在您的 INTERNET INFORMATION SERVICES （IIS）虛擬目錄中。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="7b9dc-118">設定具有 CustomBinding 的用戶端，以搭配使用可靠會話與 HTTPS</span><span class="sxs-lookup"><span data-stu-id="7b9dc-118">Configure the client with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="7b9dc-119">從命令列使用[System.servicemodel 中繼資料公用程式工具（*Svcutil*）](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ，以從服務中繼資料產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="7b9dc-120">產生的用戶端會包含 `ICalculator` 介面，以定義用戶端執行必須滿足的服務合約。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-120">The client that's generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. <span data-ttu-id="7b9dc-121">產生的用戶端應用程式也包含 `ClientCalculator` 的實作。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="7b9dc-122">請注意，不會在服務的執行中指定位址和系結資訊。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-122">Note that the address and binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="7b9dc-123">您不需要撰寫程式碼，就能從設定檔抓取位址和系結資訊。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-123">You aren't required to write code to retrieve the address and binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. <span data-ttu-id="7b9dc-124">設定名為 `reliableSessionOverHttps` 的自訂系結，以使用 HTTPS 傳輸和可靠會話。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-124">Configure a custom binding named `reliableSessionOverHttps` to use the HTTPS transport and reliable sessions.</span></span>

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. <span data-ttu-id="7b9dc-125">在應用程式中建立 `ClientCalculator` 的執行個體，然後呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-125">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. <span data-ttu-id="7b9dc-126">請編譯並執行用戶端。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-126">Compile and run the client.</span></span>  

## <a name="net-framework-security"></a><span data-ttu-id="7b9dc-127">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="7b9dc-127">.NET Framework security</span></span>

<span data-ttu-id="7b9dc-128">因為此範例中使用的憑證是使用*Makecert*建立的測試憑證，所以當您嘗試從瀏覽器存取 HTTPS 位址（例如 `https://localhost/servicemodelsamples/service.svc`）時，就會出現安全性警示。</span><span class="sxs-lookup"><span data-stu-id="7b9dc-128">Because the certificate used in this sample is a test certificate created with *Makecert.exe*, a security alert appears when you try to access an HTTPS address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b9dc-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="7b9dc-129">See also</span></span>

- [<span data-ttu-id="7b9dc-130">可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="7b9dc-130">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
