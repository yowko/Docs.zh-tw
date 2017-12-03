---
title: "HOW TO：使用 HTTPS 建立自訂可靠工作階段繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 87a27bb3e33b0dd78fdb2dfa206bbde098c8b769
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a><span data-ttu-id="22fec-102">HOW TO：使用 HTTPS 建立自訂可靠工作階段繫結</span><span class="sxs-lookup"><span data-stu-id="22fec-102">How to: Create a Custom Reliable Session Binding with HTTPS</span></span>

<span data-ttu-id="22fec-103">本主題示範使用 Secure Sockets Layer (SSL) 傳輸安全性來搭配可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="22fec-103">This topic demonstrates the use of Secure Sockets Layer (SSL) transport security with reliable sessions.</span></span> <span data-ttu-id="22fec-104">若要透過 HTTPS 使用可靠工作階段，您必須建立使用可靠工作階段與 HTTPS 傳輸的自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="22fec-104">To use a reliable session over HTTPS, you must create a custom binding that uses a reliable session and the HTTPS transport.</span></span> <span data-ttu-id="22fec-105">透過命令式程式碼或是宣告式組態檔中，您就會啟用可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="22fec-105">You enable the reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="22fec-106">此程序會使用用戶端和服務組態檔來啟用可靠工作階段和[  **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md)項目。</span><span class="sxs-lookup"><span data-stu-id="22fec-106">This procedure uses the client and service configuration files to enable the reliable session and the [**\<httpsTransport>**](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) element.</span></span>

<span data-ttu-id="22fec-107">此程序的重要部分在於**\<端點 >**組態項目包含`bindingConfiguration`屬性必須參考名為自訂繫結組態`reliableSessionOverHttps`。</span><span class="sxs-lookup"><span data-stu-id="22fec-107">The key part of this procedure is that the **\<endpoint>** configuration element contain a `bindingConfiguration` attribute that references a custom binding configuration named `reliableSessionOverHttps`.</span></span> <span data-ttu-id="22fec-108">[ **\<繫結 >** ](../../../../docs/framework/misc/binding.md)組態項目會參考此名稱來指定使用可靠工作階段與 HTTPS 傳輸，藉由 **\<reliableSession >**和 **\<httpsTransport >**項目。</span><span class="sxs-lookup"><span data-stu-id="22fec-108">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element references this name to specify that a reliable session and the HTTPS transport are used by including **\<reliableSession>** and **\<httpsTransport>** elements.</span></span>

<span data-ttu-id="22fec-109">此範例的來源副本，請參閱[自訂繫結可靠工作階段透過 HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md)。</span><span class="sxs-lookup"><span data-stu-id="22fec-109">For the source copy of this example, see [Custom Binding Reliable Session over HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).</span></span>

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="22fec-110">設定包含 CustomBinding 來使用搭配 HTTPS 的可靠工作階段的服務</span><span class="sxs-lookup"><span data-stu-id="22fec-110">Configure the service with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="22fec-111">定義服務類型的服務合約。</span><span class="sxs-lookup"><span data-stu-id="22fec-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. <span data-ttu-id="22fec-112">在服務類別中實作服務合約。</span><span class="sxs-lookup"><span data-stu-id="22fec-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="22fec-113">請注意，位址或繫結資訊不指定服務的實作內部。</span><span class="sxs-lookup"><span data-stu-id="22fec-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="22fec-114">您不需要撰寫程式碼以擷取組態檔中的位址或繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="22fec-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. <span data-ttu-id="22fec-115">建立*Web.config*檔案來設定的端點`CalculatorService`名為的自訂繫結`reliableSessionOverHttps`使用可靠工作階段和 HTTPS 傳輸。</span><span class="sxs-lookup"><span data-stu-id="22fec-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` with a custom binding named `reliableSessionOverHttps` that uses a reliable session and the HTTPS transport.</span></span>

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. <span data-ttu-id="22fec-116">建立*Service.svc*檔案包含行：</span><span class="sxs-lookup"><span data-stu-id="22fec-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. <span data-ttu-id="22fec-117">位置*Service.svc*網際網路資訊服務 (IIS) 虛擬目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="22fec-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="22fec-118">將用戶端設定包含 CustomBinding 來使用搭配 HTTPS 的可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="22fec-118">Configure the client with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="22fec-119">使用[ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)從命令列從服務中繼資料產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="22fec-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="22fec-120">產生的用戶端包含`ICalculator`定義用戶端實作所必須滿足的服務合約的介面。</span><span class="sxs-lookup"><span data-stu-id="22fec-120">The client that's generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. <span data-ttu-id="22fec-121">產生的用戶端應用程式也包含 `ClientCalculator` 的實作。</span><span class="sxs-lookup"><span data-stu-id="22fec-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="22fec-122">請注意，位址和繫結資訊不指定服務的實作內部。</span><span class="sxs-lookup"><span data-stu-id="22fec-122">Note that the address and binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="22fec-123">您不需要撰寫程式碼以擷取組態檔中的位址和繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="22fec-123">You aren't required to write code to retrieve the address and binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. <span data-ttu-id="22fec-124">設定自訂繫結，名為`reliableSessionOverHttps`使用 HTTPS 傳輸和可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="22fec-124">Configure a custom binding named `reliableSessionOverHttps` to use the HTTPS transport and reliable sessions.</span></span>

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. <span data-ttu-id="22fec-125">在應用程式中建立 `ClientCalculator` 的執行個體，然後呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="22fec-125">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. <span data-ttu-id="22fec-126">請編譯並執行用戶端。</span><span class="sxs-lookup"><span data-stu-id="22fec-126">Compile and run the client.</span></span>  

## <a name="net-framework-security"></a><span data-ttu-id="22fec-127">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="22fec-127">.NET Framework security</span></span>

<span data-ttu-id="22fec-128">因為此範例中使用的憑證是使用建立的測試憑證*Makecert.exe*，當您嘗試存取 HTTPS 位址，例如，會顯示安全性警示`https://localhost/servicemodelsamples/service.svc`，從您的瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="22fec-128">Because the certificate used in this sample is a test certificate created with *Makecert.exe*, a security alert appears when you try to access an HTTPS address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="22fec-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="22fec-129">See also</span></span>

[<span data-ttu-id="22fec-130">可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="22fec-130">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
