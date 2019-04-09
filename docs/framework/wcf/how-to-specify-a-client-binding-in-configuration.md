---
title: HOW TO：在組態中指定用戶端繫結
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 81e9b4b5949d3a89749911a30ad199c4f0da300f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091560"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="1b28d-102">HOW TO：在組態中指定用戶端繫結</span><span class="sxs-lookup"><span data-stu-id="1b28d-102">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="1b28d-103">在此範例中，建立了一個使用計算機服務的用戶端主控台應用程式，並在組態中以宣告方式指定用戶端的繫結。</span><span class="sxs-lookup"><span data-stu-id="1b28d-103">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="1b28d-104">用戶端會存取 `CalculatorService` (該服務會實作 `ICalculator` 介面)，而服務和用戶端都會使用 <xref:System.ServiceModel.BasicHttpBinding> 類別。</span><span class="sxs-lookup"><span data-stu-id="1b28d-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="1b28d-105">所述的程序假設計算機服務正在執行中。</span><span class="sxs-lookup"><span data-stu-id="1b28d-105">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="1b28d-106">如需如何建置服務的資訊，請參閱[How to:在組態中指定的服務繫結](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="1b28d-106">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="1b28d-107">它也會使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) Windows Communication Foundation (WCF) 提供自動產生的用戶端元件。</span><span class="sxs-lookup"><span data-stu-id="1b28d-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) that Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="1b28d-108">此工具會產生用戶端程式碼，以及存取服務的組態。</span><span class="sxs-lookup"><span data-stu-id="1b28d-108">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="1b28d-109">用戶端會建置成兩個部分。</span><span class="sxs-lookup"><span data-stu-id="1b28d-109">The client is built in two parts.</span></span> <span data-ttu-id="1b28d-110">Svcutil.exe 會產生 `ClientCalculator`，而該元件會實作 `ICalculator` 介面。</span><span class="sxs-lookup"><span data-stu-id="1b28d-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="1b28d-111">接著會藉由建構 `ClientCalculator` 的執行個體，以建構此用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="1b28d-111">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="1b28d-112">通常最佳作法是在組態中以宣告方式指定繫結和位址資訊，而不是在程式碼中強制指定。</span><span class="sxs-lookup"><span data-stu-id="1b28d-112">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="1b28d-113">在程式碼中定義端點通常不太實用，因為部署之服務的繫結和位址通常與開發服務時所使用的繫結和位址不同。</span><span class="sxs-lookup"><span data-stu-id="1b28d-113">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="1b28d-114">比較一般性的作法是將繫結和位址資訊留在程式碼外面，如此一來，不需要重新編譯或重新部署應用程式，就可以變更繫結和位址資訊。</span><span class="sxs-lookup"><span data-stu-id="1b28d-114">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="1b28d-115">您可以使用來執行所有的下列設定步驟[組態編輯器工具 (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="1b28d-115">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="1b28d-116">如需此範例中的來源複本，請參閱[BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md)範例。</span><span class="sxs-lookup"><span data-stu-id="1b28d-116">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="1b28d-117">指定組態中的用戶端繫結</span><span class="sxs-lookup"><span data-stu-id="1b28d-117">Specifying a client binding in configuration</span></span>  
  
1.  <span data-ttu-id="1b28d-118">從命令列使用 Svcutil.exe 產生取自服務中繼資料的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1b28d-118">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  <span data-ttu-id="1b28d-119">所產生的用戶端會包含 `ICalculator` 介面，其中定義了用戶端實作所必須滿足的服務合約。</span><span class="sxs-lookup"><span data-stu-id="1b28d-119">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3.  <span data-ttu-id="1b28d-120">產生的用戶端也會包含 `ClientCalculator` 的實作。</span><span class="sxs-lookup"><span data-stu-id="1b28d-120">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4.  <span data-ttu-id="1b28d-121">Svcutil.exe 也會為使用 <xref:System.ServiceModel.BasicHttpBinding> 類別的用戶端產生組態。</span><span class="sxs-lookup"><span data-stu-id="1b28d-121">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="1b28d-122">使用 Visual Studio 時，此檔案 App.config 的名稱。請注意，服務的實作內部並未指定位址和繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="1b28d-122">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="1b28d-123">同時，您不需要撰寫可從組態檔擷取該資訊的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1b28d-123">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5.  <span data-ttu-id="1b28d-124">在應用程式內建立 `ClientCalculator` 的執行個體，然後呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="1b28d-124">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6.  <span data-ttu-id="1b28d-125">請編譯並執行用戶端。</span><span class="sxs-lookup"><span data-stu-id="1b28d-125">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b28d-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b28d-126">See also</span></span>

- [<span data-ttu-id="1b28d-127">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="1b28d-127">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
