---
title: HOW TO：使用 Windows 認證來確保服務安全
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: c47539e0c614992efd74296171034b8091ba3f15
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183317"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a><span data-ttu-id="6ba96-102">HOW TO：使用 Windows 認證來確保服務安全</span><span class="sxs-lookup"><span data-stu-id="6ba96-102">How to: Secure a Service with Windows Credentials</span></span>
<span data-ttu-id="6ba96-103">本主題說明如何啟用位於 Windows 網域，而且由相同的網域中的用戶端呼叫的 Windows Communication Foundation (WCF) 服務上的傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="6ba96-103">This topic shows how to enable transport security on a Windows Communication Foundation (WCF) service that resides in a Windows domain and is called by clients in the same domain.</span></span> <span data-ttu-id="6ba96-104">如需有關此案例的詳細資訊，請參閱 < [Windows 驗證的傳輸安全性](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="6ba96-104">For more information about this scenario, see [Transport Security with Windows Authentication](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md).</span></span> <span data-ttu-id="6ba96-105">範例應用程式，請參閱[WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md)範例。</span><span class="sxs-lookup"><span data-stu-id="6ba96-105">For a sample application, see the [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span>  
  
 <span data-ttu-id="6ba96-106">這個主題假設您擁有現有的合約介面、已定義了實作 (Implementation)，以及一些附加內容。</span><span class="sxs-lookup"><span data-stu-id="6ba96-106">This topic assumes you have an existing contract interface and implementation already defined, and adds on to that.</span></span> <span data-ttu-id="6ba96-107">您也可以修改現有的服務和用戶端。</span><span class="sxs-lookup"><span data-stu-id="6ba96-107">You can also modify an existing service and client.</span></span>  
  
 <span data-ttu-id="6ba96-108">您可以完全使用程式碼，透過 Windows 認證來確保服務安全。</span><span class="sxs-lookup"><span data-stu-id="6ba96-108">You can secure a service with Windows credentials completely in code.</span></span> <span data-ttu-id="6ba96-109">或者，您也可以使用組態檔來省略部分程式碼。</span><span class="sxs-lookup"><span data-stu-id="6ba96-109">Alternatively, you can omit some of the code by using a configuration file.</span></span> <span data-ttu-id="6ba96-110">這個主題會說明這兩種方式。</span><span class="sxs-lookup"><span data-stu-id="6ba96-110">This topic shows both ways.</span></span> <span data-ttu-id="6ba96-111">請務必只使用其中一種方式，不要兩種都使用。</span><span class="sxs-lookup"><span data-stu-id="6ba96-111">Be sure you only use one of the ways, not both.</span></span>  
  
 <span data-ttu-id="6ba96-112">前三個程序會說明如何使用程式碼來保護服務安全。</span><span class="sxs-lookup"><span data-stu-id="6ba96-112">The first three procedures show how to secure the service using code.</span></span> <span data-ttu-id="6ba96-113">第四和第五個程序會說明如何使用組態檔來執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="6ba96-113">The fourth and fifth procedure shows how to do it with a configuration file.</span></span>  
  
## <a name="using-code"></a><span data-ttu-id="6ba96-114">使用程式碼</span><span class="sxs-lookup"><span data-stu-id="6ba96-114">Using Code</span></span>  
 <span data-ttu-id="6ba96-115">服務和用戶端的完整程式碼已提供於本主題結尾的「範例」一節。</span><span class="sxs-lookup"><span data-stu-id="6ba96-115">The complete code for the service and the client is in the Example section at the end of this topic.</span></span>  
  
 <span data-ttu-id="6ba96-116">第一個程序會逐步解說如何使用程式碼建立和設定 <xref:System.ServiceModel.WSHttpBinding> 類別。</span><span class="sxs-lookup"><span data-stu-id="6ba96-116">The first procedure walks through creating and configuring a <xref:System.ServiceModel.WSHttpBinding> class in code.</span></span> <span data-ttu-id="6ba96-117">繫結會使用 HTTP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="6ba96-117">The binding uses the HTTP transport.</span></span> <span data-ttu-id="6ba96-118">用戶端上會使用相同的繫結。</span><span class="sxs-lookup"><span data-stu-id="6ba96-118">The same binding is used on the client.</span></span>  
  
#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a><span data-ttu-id="6ba96-119">建立會使用 Windows 認證和訊息安全性的 WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="6ba96-119">To create a WSHttpBinding that uses Windows credentials and message security</span></span>  
  
1.  <span data-ttu-id="6ba96-120">這個程序的程式碼會插入至「範例」一節服務程式碼中 `Run` 類別的 `Test` 方法開頭。</span><span class="sxs-lookup"><span data-stu-id="6ba96-120">This procedure's code is inserted at the beginning of the `Run` method of the `Test` class in the service code in the Example section.</span></span>  
  
2.  <span data-ttu-id="6ba96-121">建立 <xref:System.ServiceModel.WSHttpBinding> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6ba96-121">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>  
  
3.  <span data-ttu-id="6ba96-122">將 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> 類別的 <xref:System.ServiceModel.WSHttpSecurity> 屬性設定為 <xref:System.ServiceModel.SecurityMode.Message>。</span><span class="sxs-lookup"><span data-stu-id="6ba96-122">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property of the <xref:System.ServiceModel.WSHttpSecurity> class to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>  
  
4.  <span data-ttu-id="6ba96-123">將 <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> 類別的 <xref:System.ServiceModel.MessageSecurityOverHttp> 屬性設定為 <xref:System.ServiceModel.MessageCredentialType.Windows>。</span><span class="sxs-lookup"><span data-stu-id="6ba96-123">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property of the <xref:System.ServiceModel.MessageSecurityOverHttp> class to <xref:System.ServiceModel.MessageCredentialType.Windows>.</span></span>  
  
5.  <span data-ttu-id="6ba96-124">這項程序的程式碼如下所示：</span><span class="sxs-lookup"><span data-stu-id="6ba96-124">The code for this procedure is as follows:</span></span>  
  
     [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
     [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]  
  
### <a name="using-the-binding-in-a-service"></a><span data-ttu-id="6ba96-125">在服務中使用繫結</span><span class="sxs-lookup"><span data-stu-id="6ba96-125">Using the Binding in a Service</span></span>  
 <span data-ttu-id="6ba96-126">這是第二個程序，說明如何在自我裝載的服務中使用繫結。</span><span class="sxs-lookup"><span data-stu-id="6ba96-126">This is the second procedure, which shows how to use the binding in a self-hosted service.</span></span> <span data-ttu-id="6ba96-127">裝載服務的詳細資訊請參閱 <<c0> [ 裝載的服務](../../../docs/framework/wcf/hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="6ba96-127">For more information about hosting services see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
##### <a name="to-use-a-binding-in-a-service"></a><span data-ttu-id="6ba96-128">在服務中使用繫結</span><span class="sxs-lookup"><span data-stu-id="6ba96-128">To use a binding in a service</span></span>  
  
1.  <span data-ttu-id="6ba96-129">將這個程序的程式碼插入到前一個程序的程式碼後面。</span><span class="sxs-lookup"><span data-stu-id="6ba96-129">Insert this procedure's code after the code from the preceding procedure.</span></span>  
  
2.  <span data-ttu-id="6ba96-130">建立名稱為 <xref:System.Type> 的 `contractType` 變數，並將其類型指派為介面 (`ICalculator`)。</span><span class="sxs-lookup"><span data-stu-id="6ba96-130">Create a <xref:System.Type> variable named `contractType` and assign it the type of the interface (`ICalculator`).</span></span> <span data-ttu-id="6ba96-131">當您使用 Visual Basic，使用`GetType`運算子; 使用 C# 中，使用時`typeof`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="6ba96-131">When using Visual Basic, use the `GetType` operator; when using C#, use the `typeof` keyword.</span></span>  
  
3.  <span data-ttu-id="6ba96-132">建立第二個名稱為 `Type` 的 `serviceType` 變數，並將其類型指派為實作的合約 (`Calculator`)。</span><span class="sxs-lookup"><span data-stu-id="6ba96-132">Create a second `Type` variable named `serviceType` and assign it the type of the implemented contract (`Calculator`).</span></span>  
  
4.  <span data-ttu-id="6ba96-133">使用服務的基底位址，建立名稱為 <xref:System.Uri> 之 `baseAddress` 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6ba96-133">Create an instance of the <xref:System.Uri> class named `baseAddress` with the base address of the service.</span></span> <span data-ttu-id="6ba96-134">基底位址必須具有符合傳輸的配置。</span><span class="sxs-lookup"><span data-stu-id="6ba96-134">The base address must have a scheme that matches the transport.</span></span> <span data-ttu-id="6ba96-135">在此情況下，傳輸配置為 HTTP，而位址中則包含特殊統一資源識別元 (URI)"localhost"與連接埠號碼 (8036)，以及基底的端點位址 ("serviceModelSamples /): `http://localhost:8036/serviceModelSamples/`。</span><span class="sxs-lookup"><span data-stu-id="6ba96-135">In this case, the transport scheme is HTTP, and the address includes the special Uniform Resource Identifier (URI) "localhost" and a port number (8036) as well as a base endpoint address ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/`.</span></span>  
  
5.  <span data-ttu-id="6ba96-136">使用 <xref:System.ServiceModel.ServiceHost> 和 `serviceType` 變數，建立 `baseAddress` 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6ba96-136">Create an instance of the <xref:System.ServiceModel.ServiceHost> class with the `serviceType` and `baseAddress` variables.</span></span>  
  
6.  <span data-ttu-id="6ba96-137">使用 `contractType`、繫結和端點名稱 (secureCalculator)，將端點新增至服務。</span><span class="sxs-lookup"><span data-stu-id="6ba96-137">Add an endpoint to the service using the `contractType`, binding, and an endpoint name (secureCalculator).</span></span> <span data-ttu-id="6ba96-138">初始化服務的呼叫時，用戶端必須串連基底位址和端點名稱。</span><span class="sxs-lookup"><span data-stu-id="6ba96-138">A client must concatenate the base address and the endpoint name when initiating a call to the service.</span></span>  
  
7.  <span data-ttu-id="6ba96-139">呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> 方法啟動服務。</span><span class="sxs-lookup"><span data-stu-id="6ba96-139">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service.</span></span> <span data-ttu-id="6ba96-140">這項程序的程式碼如下所示：</span><span class="sxs-lookup"><span data-stu-id="6ba96-140">The code for this procedure is shown here:</span></span>  
  
     [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
     [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]  
  
### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="6ba96-141">在用戶端中使用繫結</span><span class="sxs-lookup"><span data-stu-id="6ba96-141">Using the Binding in a Client</span></span>  
 <span data-ttu-id="6ba96-142">這項程序會說明如何產生與服務進行通訊的 Proxy。</span><span class="sxs-lookup"><span data-stu-id="6ba96-142">This procedure shows how to generate a proxy that communicates with the service.</span></span> <span data-ttu-id="6ba96-143">Proxy 就會產生含有[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)建立 proxy 的情況下，這在使用的服務中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6ba96-143">The proxy is generated with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) which uses the service metadata to create the proxy.</span></span>  
  
 <span data-ttu-id="6ba96-144">此程序還會建立可與服務進行通訊之 <xref:System.ServiceModel.WSHttpBinding> 類別的執行個體，然後呼叫該服務。</span><span class="sxs-lookup"><span data-stu-id="6ba96-144">This procedure also creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class to communicate with the service, and then calls the service.</span></span>  
  
 <span data-ttu-id="6ba96-145">這個範例只會使用程式碼來建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="6ba96-145">This example uses only code to create the client.</span></span> <span data-ttu-id="6ba96-146">或者，您可以使用組態檔，該檔案會在此程序之後的章節中說明。</span><span class="sxs-lookup"><span data-stu-id="6ba96-146">As an alternative, you can use a configuration file, which is shown in the section following this procedure.</span></span>  
  
##### <a name="to-use-a-binding-in-a-client-with-code"></a><span data-ttu-id="6ba96-147">搭配程式碼在用戶端中使用繫結</span><span class="sxs-lookup"><span data-stu-id="6ba96-147">To use a binding in a client with code</span></span>  
  
1.  <span data-ttu-id="6ba96-148">使用 SvcUtil.exe 工具，從服務的中繼資料產生 Proxy 程式碼。</span><span class="sxs-lookup"><span data-stu-id="6ba96-148">Use the SvcUtil.exe tool to generate the proxy code from the service's metadata.</span></span> <span data-ttu-id="6ba96-149">如需詳細資訊，請參閱 <<c0> [ 如何： 建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="6ba96-149">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="6ba96-150">產生的 proxy 程式碼繼承自<xref:System.ServiceModel.ClientBase%601>類別，可確保每個用戶端具有必要的建構函式、 方法和屬性與 WCF 服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="6ba96-150">The generated proxy code inherits from the <xref:System.ServiceModel.ClientBase%601> class, which ensures that every client has the necessary constructors, methods, and properties to communicate with a WCF service.</span></span> <span data-ttu-id="6ba96-151">在這個範例中，產生的程式碼包含 `CalculatorClient` 類別，這個類別會實作 `ICalculator` 介面，因此就會與服務程式碼相容。</span><span class="sxs-lookup"><span data-stu-id="6ba96-151">In this example, the generated code includes the `CalculatorClient` class, which implements the `ICalculator` interface, enabling compatibility with the service code.</span></span>  
  
2.  <span data-ttu-id="6ba96-152">此程序的程式碼會插入至用戶端程式的 `Main` 方法開頭。</span><span class="sxs-lookup"><span data-stu-id="6ba96-152">This procedure's code is inserted at the beginning of the `Main` method of the client program.</span></span>  
  
3.  <span data-ttu-id="6ba96-153">建立 <xref:System.ServiceModel.WSHttpBinding> 類別的執行個體，將其安全性模式設定為 `Message`，並將其用戶端認證類型設定為 `Windows`。</span><span class="sxs-lookup"><span data-stu-id="6ba96-153">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to `Message` and its client credential type to `Windows`.</span></span> <span data-ttu-id="6ba96-154">這個範例會將變數命名為 `clientBinding`。</span><span class="sxs-lookup"><span data-stu-id="6ba96-154">The example names the variable `clientBinding`.</span></span>  
  
4.  <span data-ttu-id="6ba96-155">建立名稱為 <xref:System.ServiceModel.EndpointAddress> 之 `serviceAddress` 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6ba96-155">Create an instance of the <xref:System.ServiceModel.EndpointAddress> class named `serviceAddress`.</span></span> <span data-ttu-id="6ba96-156">使用與端點名稱串連的基底位址初始化執行個體。</span><span class="sxs-lookup"><span data-stu-id="6ba96-156">Initialize the instance with the base address concatenated with the endpoint name.</span></span>  
  
5.  <span data-ttu-id="6ba96-157">使用 `serviceAddress` 和 `clientBinding` 變數，建立產生之用戶端類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6ba96-157">Create an instance of the generated client class with the `serviceAddress` and the `clientBinding` variables.</span></span>  
  
6.  <span data-ttu-id="6ba96-158">呼叫 <xref:System.ServiceModel.ClientBase%601.Open%2A> 方法，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="6ba96-158">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>  
  
7.  <span data-ttu-id="6ba96-159">呼叫服務並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="6ba96-159">Call the service and display the results.</span></span>  
  
     [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
     [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]  
  
## <a name="using-the-configuration-file"></a><span data-ttu-id="6ba96-160">使用組態檔</span><span class="sxs-lookup"><span data-stu-id="6ba96-160">Using the Configuration File</span></span>  
 <span data-ttu-id="6ba96-161">如果不使用程序程式碼建立繫結，您可以改用下面針對組態檔之繫結區段所顯示的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6ba96-161">Instead of creating the binding with procedural code, you can use the following code shown for the bindings section of the configuration file.</span></span>  
  
 <span data-ttu-id="6ba96-162">如果您還沒有定義的服務，請參閱[設計與實作服務](../../../docs/framework/wcf/designing-and-implementing-services.md)，並[Configuring](../../../docs/framework/wcf/configuring-services.md)。</span><span class="sxs-lookup"><span data-stu-id="6ba96-162">If you do not already have a service defined, see [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md), and [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
 <span data-ttu-id="6ba96-163">**請注意**這個組態程式碼會在服務和用戶端組態檔。</span><span class="sxs-lookup"><span data-stu-id="6ba96-163">**Note** This configuration code is used in both the service and client configuration files.</span></span>  
  
#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a><span data-ttu-id="6ba96-164">使用組態在 Windows 網域的服務上啟用傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="6ba96-164">To enable transfer security on a service in a Windows domain using configuration</span></span>  
  
1.  <span data-ttu-id="6ba96-165">新增[ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)項目[\<繫結 >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)項目區段的組態檔。</span><span class="sxs-lookup"><span data-stu-id="6ba96-165">Add a [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element to the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section of the configuration file.</span></span>  
  
2.  <span data-ttu-id="6ba96-166">將 <`binding`> 項目新增至 <`WSHttpBinding`> 項目，並將 `configurationName` 屬性設定為適用於您應用程式的值。</span><span class="sxs-lookup"><span data-stu-id="6ba96-166">Add a <`binding`> element to the <`WSHttpBinding`> element and set the `configurationName` attribute to a value appropriate to your application.</span></span>  
  
3.  <span data-ttu-id="6ba96-167">新增 <`security`> 項目，並將 `mode` 屬性設定為 Message。</span><span class="sxs-lookup"><span data-stu-id="6ba96-167">Add a <`security`> element and set the `mode` attribute to Message.</span></span>  
  
4.  <span data-ttu-id="6ba96-168">新增 <`message`> 項目，並將 `clientCredentialType` 屬性設定為 Windows。</span><span class="sxs-lookup"><span data-stu-id="6ba96-168">Add a <`message`> element and set the `clientCredentialType` attribute to Windows.</span></span>  
  
5.  <span data-ttu-id="6ba96-169">在服務的組態檔中，將 `<bindings>` 區段取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="6ba96-169">In the service's configuration file, replace the `<bindings>` section with the following code.</span></span> <span data-ttu-id="6ba96-170">如果您還沒有服務組態檔，請參閱[使用的繫結設定服務及用戶端](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="6ba96-170">If you do not already have a service configuration file, see [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>  
  
    ```xml  
    <bindings>  
      <wsHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    ```  
  
### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="6ba96-171">在用戶端中使用繫結</span><span class="sxs-lookup"><span data-stu-id="6ba96-171">Using the Binding in a Client</span></span>  
 <span data-ttu-id="6ba96-172">此程序會說明如何產生兩個檔案：與服務進行通訊的 Proxy 及組態檔。</span><span class="sxs-lookup"><span data-stu-id="6ba96-172">This procedure shows how to generate two files: a proxy that communicates with the service and a configuration file.</span></span> <span data-ttu-id="6ba96-173">此外還會說明用戶端程式的變更，也就是用戶端上使用的第三個檔案。</span><span class="sxs-lookup"><span data-stu-id="6ba96-173">It also describes changes to the client program, which is the third file used on the client.</span></span>  
  
##### <a name="to-use-a-binding-in-a-client-with-configuration"></a><span data-ttu-id="6ba96-174">搭配組態在用戶端中使用繫結</span><span class="sxs-lookup"><span data-stu-id="6ba96-174">To use a binding in a client with configuration</span></span>  
  
1.  <span data-ttu-id="6ba96-175">使用 SvcUtil.exe 工具，從服務的中繼資料產生 Proxy 程式碼和組態檔。</span><span class="sxs-lookup"><span data-stu-id="6ba96-175">Use the SvcUtil.exe tool to generate the proxy code and configuration file from the service's metadata.</span></span> <span data-ttu-id="6ba96-176">如需詳細資訊，請參閱 <<c0> [ 如何： 建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="6ba96-176">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="6ba96-177">取代[\<繫結 >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)為前一個區段的組態程式碼產生的組態檔區段。</span><span class="sxs-lookup"><span data-stu-id="6ba96-177">Replace the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) section of the generated configuration file with the configuration code from the preceding section.</span></span>  
  
3.  <span data-ttu-id="6ba96-178">程序程式碼會插入至用戶端程式的 `Main` 方法開頭。</span><span class="sxs-lookup"><span data-stu-id="6ba96-178">Procedural code is inserted at the beginning of the `Main` method of the client program.</span></span>  
  
4.  <span data-ttu-id="6ba96-179">建立已產生之用戶端類別的執行個體，將組態檔中繫結的名稱當做輸入參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="6ba96-179">Create an instance of the generated client class passing the name of the binding in the configuration file as an input parameter.</span></span>  
  
5.  <span data-ttu-id="6ba96-180">呼叫 <xref:System.ServiceModel.ClientBase%601.Open%2A> 方法，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="6ba96-180">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>  
  
6.  <span data-ttu-id="6ba96-181">呼叫服務並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="6ba96-181">Call the service and display the results.</span></span>  
  
     [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="6ba96-182">範例</span><span class="sxs-lookup"><span data-stu-id="6ba96-182">Example</span></span>  
 [!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]  
  
 [!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)] 
 [!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]      
  
## <a name="see-also"></a><span data-ttu-id="6ba96-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ba96-183">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpBinding>  
 [<span data-ttu-id="6ba96-184">ServiceModel 中繼資料公用程式工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="6ba96-184">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="6ba96-185">如何：建立用戶端</span><span class="sxs-lookup"><span data-stu-id="6ba96-185">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="6ba96-186">保護服務安全</span><span class="sxs-lookup"><span data-stu-id="6ba96-186">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="6ba96-187">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="6ba96-187">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)
