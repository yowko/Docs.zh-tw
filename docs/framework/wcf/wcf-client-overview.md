---
title: WCF 用戶端概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
ms.openlocfilehash: 4e502b9917e6a99a8526a2314136841140309083
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64582826"
---
# <a name="wcf-client-overview"></a><span data-ttu-id="b0053-102">WCF 用戶端概觀</span><span class="sxs-lookup"><span data-stu-id="b0053-102">WCF Client Overview</span></span>
<span data-ttu-id="b0053-103">本節說明用戶端應用程式做什麼、 如何設定、 建立和使用 Windows Communication Foundation (WCF) 用戶端，以及如何保護用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="b0053-103">This section describes what client applications do, how to configure, create, and use a Windows Communication Foundation (WCF) client, and how to secure client applications.</span></span>  
  
## <a name="using-wcf-client-objects"></a><span data-ttu-id="b0053-104">使用 WCF 用戶端物件</span><span class="sxs-lookup"><span data-stu-id="b0053-104">Using WCF Client Objects</span></span>  
 <span data-ttu-id="b0053-105">用戶端應用程式是受管理的應用程式與其他應用程式，用來通訊的 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="b0053-105">A client application is a managed application that uses a WCF client to communicate with another application.</span></span> <span data-ttu-id="b0053-106">若要建立用戶端為 WCF 服務的應用程式需要下列步驟：</span><span class="sxs-lookup"><span data-stu-id="b0053-106">To create a client application for a WCF service requires the following steps:</span></span>  
  
1. <span data-ttu-id="b0053-107">取得服務端點的服務合約、繫結和位址資訊。</span><span class="sxs-lookup"><span data-stu-id="b0053-107">Obtain the service contract, bindings, and address information for a service endpoint.</span></span>  
  
2. <span data-ttu-id="b0053-108">建立 WCF 用戶端使用該資訊。</span><span class="sxs-lookup"><span data-stu-id="b0053-108">Create a WCF client using that information.</span></span>  
  
3. <span data-ttu-id="b0053-109">呼叫作業。</span><span class="sxs-lookup"><span data-stu-id="b0053-109">Call operations.</span></span>  
  
4. <span data-ttu-id="b0053-110">關閉 WCF 用戶端物件。</span><span class="sxs-lookup"><span data-stu-id="b0053-110">Close the WCF client object.</span></span>  
  
 <span data-ttu-id="b0053-111">下列各節將討論這些步驟，並簡要介紹以下問題：</span><span class="sxs-lookup"><span data-stu-id="b0053-111">The following sections discuss these steps and provide brief introductions to the following issues:</span></span>  
  
- <span data-ttu-id="b0053-112">處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="b0053-112">Handling errors.</span></span>  
  
- <span data-ttu-id="b0053-113">設定和保護用戶端。</span><span class="sxs-lookup"><span data-stu-id="b0053-113">Configuring and securing clients.</span></span>  
  
- <span data-ttu-id="b0053-114">建立雙工服務的回呼物件。</span><span class="sxs-lookup"><span data-stu-id="b0053-114">Creating callback objects for duplex services.</span></span>  
  
- <span data-ttu-id="b0053-115">非同步呼叫服務。</span><span class="sxs-lookup"><span data-stu-id="b0053-115">Calling services asynchronously.</span></span>  
  
- <span data-ttu-id="b0053-116">透過用戶端通道呼叫服務。</span><span class="sxs-lookup"><span data-stu-id="b0053-116">Calling services using client channels.</span></span>  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a><span data-ttu-id="b0053-117">取得服務合約、繫結和位址</span><span class="sxs-lookup"><span data-stu-id="b0053-117">Obtain the Service Contract, Bindings, and Addresses</span></span>  
 <span data-ttu-id="b0053-118">在 WCF 中，服務和用戶端模型合約會使用 managed 的屬性、 介面和方法。</span><span class="sxs-lookup"><span data-stu-id="b0053-118">In WCF, services and clients model contracts using managed attributes, interfaces, and methods.</span></span> <span data-ttu-id="b0053-119">若要在用戶端應用程式中連接到服務，您必須取得服務合約的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="b0053-119">To connect to a service in a client application, you need to obtain the type information for the service contract.</span></span> <span data-ttu-id="b0053-120">一般而言，您可以使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)，下載中繼資料從服務中，將它轉換成在您選擇的語言中的 managed 的原始程式碼檔，並建立用戶端可用來設定您的 WCF 用戶端物件的應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="b0053-120">Typically, you do this by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), which downloads metadata from the service, converts it to a managed source code file in the language of your choice, and creates a client application configuration file that you can use to configure your WCF client object.</span></span> <span data-ttu-id="b0053-121">例如，如果您要建立 WCF 用戶端物件來叫用`MyCalculatorService`，而且您知道該服務的中繼資料已發佈於`http://computerName/MyCalculatorService/Service.svc?wsdl`，則下列程式碼範例示範如何使用 Svcutil.exe 來取得`ClientCode.vb`檔案包含 managed 程式碼中的服務合約。</span><span class="sxs-lookup"><span data-stu-id="b0053-121">For example, if you are going to create an WCF client object to invoke a `MyCalculatorService`, and you know that the metadata for that service is published at `http://computerName/MyCalculatorService/Service.svc?wsdl`, then the following code example shows how to use Svcutil.exe to obtain a `ClientCode.vb` file that contains the service contract in managed code.</span></span>  
  
```  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 <span data-ttu-id="b0053-122">至用戶端應用程式或用戶端應用程式可用來建立 WCF 用戶端物件的另一個組件，您可能可以編譯此合約程式碼。</span><span class="sxs-lookup"><span data-stu-id="b0053-122">You can either compile this contract code into the client application or into another assembly that the client application can then use to create an WCF client object.</span></span> <span data-ttu-id="b0053-123">您可以使用組態檔來設定用戶端物件，以便正確連接到服務。</span><span class="sxs-lookup"><span data-stu-id="b0053-123">You can use the configuration file to configure the client object to properly connect to the service .</span></span>  
  
 <span data-ttu-id="b0053-124">如需此程序的範例，請參閱[How to:建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="b0053-124">For an example of this process, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="b0053-125">如需更完整合約的詳細資訊，請參閱[合約](../../../docs/framework/wcf/feature-details/contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="b0053-125">For more complete information about contracts, see [Contracts](../../../docs/framework/wcf/feature-details/contracts.md).</span></span>  
  
## <a name="create-a-wcf-client-object"></a><span data-ttu-id="b0053-126">建立 WCF 用戶端物件</span><span class="sxs-lookup"><span data-stu-id="b0053-126">Create a WCF Client Object</span></span>  
 <span data-ttu-id="b0053-127">WCF 用戶端是本機物件，表示在表單中的用戶端可用來與遠端服務進行通訊的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="b0053-127">A WCF client is a local object that represents a WCF service in a form that the client can use to communicate with the remote service.</span></span> <span data-ttu-id="b0053-128">WCF 用戶端型別會實作目標服務合約，因此當您建立並設定它，您可以使用用戶端物件直接叫用服務作業。</span><span class="sxs-lookup"><span data-stu-id="b0053-128">WCF client types implement the target service contract, so when you create one and configure it, you can then use the client object directly to invoke service operations.</span></span> <span data-ttu-id="b0053-129">WCF 執行階段方法呼叫轉換為訊息、 將它們傳送至服務、 接聽回覆，並傳回這些值給 WCF 用戶端物件，作為傳回值或`out`或`ref`參數。</span><span class="sxs-lookup"><span data-stu-id="b0053-129">The WCF run time converts the method calls into messages, sends them to the service, listens for the reply, and returns those values to the WCF client object as return values or `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="b0053-130">您也可以使用 WCF 用戶端通道物件來連接及使用服務。</span><span class="sxs-lookup"><span data-stu-id="b0053-130">You can also use WCF client channel objects to connect with and use services.</span></span> <span data-ttu-id="b0053-131">如需詳細資訊，請參閱 < [WCF 用戶端架構](../../../docs/framework/wcf/feature-details/client-architecture.md)。</span><span class="sxs-lookup"><span data-stu-id="b0053-131">For details, see [WCF Client Architecture](../../../docs/framework/wcf/feature-details/client-architecture.md).</span></span>  
  
#### <a name="creating-a-new-wcf-object"></a><span data-ttu-id="b0053-132">建立新的 WCF 物件</span><span class="sxs-lookup"><span data-stu-id="b0053-132">Creating a New WCF Object</span></span>  
 <span data-ttu-id="b0053-133">為說明 <xref:System.ServiceModel.ClientBase%601> 類別的使用方式，請假設已從服務應用程式產生下列簡單服務合約。</span><span class="sxs-lookup"><span data-stu-id="b0053-133">To illustrate the use of a <xref:System.ServiceModel.ClientBase%601> class, assume the following simple service contract has been generated from a service application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0053-134">如果您使用 Visual Studio 建立您的 WCF 用戶端，物件會自動載入物件瀏覽器到當您將新增服務參考加入專案。</span><span class="sxs-lookup"><span data-stu-id="b0053-134">If you are using Visual Studio to create your WCF client, objects are loaded automatically into the object browser when you add a service reference to your project.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 <span data-ttu-id="b0053-135">如果您不使用 Visual Studio，檢查產生的合約程式碼，以尋找擴充的型別<xref:System.ServiceModel.ClientBase%601>和服務合約介面`ISampleService`。</span><span class="sxs-lookup"><span data-stu-id="b0053-135">If you are not using Visual Studio, examine the generated contract code to find the type that extends <xref:System.ServiceModel.ClientBase%601> and the service contract interface `ISampleService`.</span></span> <span data-ttu-id="b0053-136">在這種情況下，該型別看起來類似下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b0053-136">In this case, that type looks like the following code:</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 <span data-ttu-id="b0053-137">您可以將這個類別建立成本機物件，其方式是使用其中一個建構函式，然後加以設定，再用來連接到型別為 `ISampleService` 的服務。</span><span class="sxs-lookup"><span data-stu-id="b0053-137">This class can be created as a local object using one of the constructors, configured, and then used to connect to a service of the type `ISampleService`.</span></span>  
  
 <span data-ttu-id="b0053-138">建議您首先，建立您的 WCF 用戶端物件，然後使用它並關閉單一的 try/catch 區塊內。</span><span class="sxs-lookup"><span data-stu-id="b0053-138">It is recommended that you create your WCF client object first, and then use it and close it inside a single try/catch block.</span></span> <span data-ttu-id="b0053-139">您不應該使用`using`陳述式 (`Using` Visual Basic 中) 因為它可能會遮罩特定失敗模式的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b0053-139">You should not use the `using` statement (`Using` in Visual Basic) because it may mask exceptions in certain failure modes.</span></span> <span data-ttu-id="b0053-140">如需詳細資訊，請參閱下列各節，以及[使用關閉和中止發行 WCF 用戶端資源](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="b0053-140">For more information, see the following sections as well as [Use Close and Abort to release WCF client resources](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).</span></span>  
  
### <a name="contracts-bindings-and-addresses"></a><span data-ttu-id="b0053-141">合約、繫結和位址</span><span class="sxs-lookup"><span data-stu-id="b0053-141">Contracts, Bindings, and Addresses</span></span>  
 <span data-ttu-id="b0053-142">您可以建立 WCF 用戶端物件之前，您必須設定用戶端物件。</span><span class="sxs-lookup"><span data-stu-id="b0053-142">Before you can create a WCF client object, you must configure the client object.</span></span> <span data-ttu-id="b0053-143">具體來說，它必須擁有的服務*端點*使用。</span><span class="sxs-lookup"><span data-stu-id="b0053-143">Specifically, it must have a service *endpoint* to use.</span></span> <span data-ttu-id="b0053-144">端點是服務合約、繫結和位址的組合 </span><span class="sxs-lookup"><span data-stu-id="b0053-144">An endpoint is the combination of a service contract, a binding, and an address.</span></span> <span data-ttu-id="b0053-145">(如需有關端點的詳細資訊，請參閱[端點：位址、 繫結和合約](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)。)一般而言，這項資訊位於[\<端點 >](../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)用戶端應用程式組態檔，例如 Svcutil.exe 工具產生的而且當您建立您的用戶端時自動載入的項目物件。</span><span class="sxs-lookup"><span data-stu-id="b0053-145">(For more information about endpoints, see [Endpoints: Addresses, Bindings, and Contracts](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md).) Typically, this information is located in the [\<endpoint>](../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md) element in a client application configuration file, such as the one the Svcutil.exe tool generates, and is loaded automatically when you create your client object.</span></span> <span data-ttu-id="b0053-146">這兩種 WCF 用戶端類型也會有多載，可讓您以程式設計方式指定這項資訊。</span><span class="sxs-lookup"><span data-stu-id="b0053-146">Both WCF client types also have overloads that enable you to programmatically specify this information.</span></span>  
  
 <span data-ttu-id="b0053-147">例如，針對前面範例中使用的 `ISampleService` 所產生的組態檔會包含下列端點資訊。</span><span class="sxs-lookup"><span data-stu-id="b0053-147">For example, a generated configuration file for an `ISampleService` used in the preceding examples contains the following endpoint information.</span></span>  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 <span data-ttu-id="b0053-148">這個組態檔會在 `<client>` 元素中指定目標端點。</span><span class="sxs-lookup"><span data-stu-id="b0053-148">This configuration file specifies a target endpoint in the `<client>` element.</span></span> <span data-ttu-id="b0053-149">如需使用多個目標端點的詳細資訊，請參閱 <<c0> <xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=nameWithType> 或<xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=nameWithType>建構函式。</span><span class="sxs-lookup"><span data-stu-id="b0053-149">For more information about using multiple target endpoints, see the <xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=nameWithType> constructors.</span></span>  
  
## <a name="calling-operations"></a><span data-ttu-id="b0053-150">呼叫作業</span><span class="sxs-lookup"><span data-stu-id="b0053-150">Calling Operations</span></span>  
 <span data-ttu-id="b0053-151">一旦您已建立的用戶端物件和設定，建立 try/catch 區塊中，相同的方式，就像是本機，如果在呼叫作業並關閉 WCF 用戶端物件。</span><span class="sxs-lookup"><span data-stu-id="b0053-151">Once you have a client object created and configured, create a try/catch block, call operations in the same way that you would if the object were local, and close the WCF client object.</span></span> <span data-ttu-id="b0053-152">當用戶端應用程式呼叫第一項作業時，WCF 會自動開啟基礎通道，並回收物件時，系統會關閉基礎通道。</span><span class="sxs-lookup"><span data-stu-id="b0053-152">When the client application calls the first operation, WCF automatically opens the underlying channel, and the underlying channel is closed when the object is recycled.</span></span> <span data-ttu-id="b0053-153">(或者，您也可以在呼叫其他作業之前或之後明確地開啟和關閉通道)。</span><span class="sxs-lookup"><span data-stu-id="b0053-153">(Alternatively, you can also explicitly open and close the channel prior to or subsequent to calling other operations.)</span></span>  
  
 <span data-ttu-id="b0053-154">例如，您若有下列服務合約：</span><span class="sxs-lookup"><span data-stu-id="b0053-154">For example, if you have the following service contract:</span></span>  
  
```csharp  
namespace Microsoft.ServiceModel.Samples  
{  
    using System;  
    using System.ServiceModel;  
  
    [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
    public interface ICalculator  
   {  
        [OperationContract]  
        double Add(double n1, double n2);  
        [OperationContract]  
        double Subtract(double n1, double n2);  
        [OperationContract]  
        double Multiply(double n1, double n2);  
        [OperationContract]  
        double Divide(double n1, double n2);  
    }  
}  
```  
  
```vb  
Namespace Microsoft.ServiceModel.Samples  
  
    Imports System  
    Imports System.ServiceModel  
  
    <ServiceContract(Namespace:= _  
    "http://Microsoft.ServiceModel.Samples")> _   
   Public Interface ICalculator  
        <OperationContract> _   
        Function Add(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
        Function Subtract(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
        Function Multiply(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
     Function Divide(n1 As Double, n2 As Double) As Double  
End Interface  
```  
  
 <span data-ttu-id="b0053-155">您可以藉由建立 WCF 用戶端物件來呼叫作業，並呼叫其方法，如下列程式碼範例示範。</span><span class="sxs-lookup"><span data-stu-id="b0053-155">You can call operations by creating a WCF client object and calling its methods, as the following code example demonstrates.</span></span> <span data-ttu-id="b0053-156">請注意開啟、 呼叫和 WCF 用戶端物件的結尾，會在單一的 try/catch 區塊內。</span><span class="sxs-lookup"><span data-stu-id="b0053-156">Note that the opening, calling, and closing of the WCF client object occurs within a single try/catch block.</span></span> <span data-ttu-id="b0053-157">如需詳細資訊，請參閱 <<c0> [ 使用 WCF 用戶端存取服務](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)並[使用關閉和中止發行 WCF 用戶端資源](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="b0053-157">For more information, see [Accessing Services Using a WCF Client](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md) and [Use Close and Abort to release WCF client resources](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a><span data-ttu-id="b0053-158">處理錯誤</span><span class="sxs-lookup"><span data-stu-id="b0053-158">Handling Errors</span></span>  
 <span data-ttu-id="b0053-159">當開啟基礎用戶端通道 (無論是明確或是自動呼叫作業)、使用用戶端或通道物件來呼叫作業，或關閉基礎用戶端通道時，都可能會在用戶端應用程式中發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b0053-159">Exceptions can occur in a client application when opening the underlying client channel (whether explicitly or automatically by calling an operation), using the client or channel object to call operations, or when closing the underlying client channel.</span></span> <span data-ttu-id="b0053-160">除了要由作業傳回因 SOAP 錯誤而擲回的任何 <xref:System.TimeoutException?displayProperty=nameWithType> 物件之外，建議您最少還要讓應用程式有能力處理可能發生的 <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> 和 <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b0053-160">It is recommended at a minimum that applications expect to handle possible <xref:System.TimeoutException?displayProperty=nameWithType> and <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> exceptions in addition to any <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> objects thrown as a result of SOAP faults returned by operations.</span></span> <span data-ttu-id="b0053-161">作業合約中指定的 SOAP 錯誤會針對用戶端應用程式引發為 <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>，其中的型別參數是 SOAP 錯誤的詳細類型。</span><span class="sxs-lookup"><span data-stu-id="b0053-161">SOAP faults specified in the operation contract are raised to client applications as a <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> where the type parameter is the detail type of the SOAP fault.</span></span> <span data-ttu-id="b0053-162">如需有關處理用戶端應用程式中的錯誤狀況的詳細資訊，請參閱 < [Sending and Receiving Faults](../../../docs/framework/wcf/sending-and-receiving-faults.md)。</span><span class="sxs-lookup"><span data-stu-id="b0053-162">For more information about handling error conditions in a client application, see [Sending and Receiving Faults](../../../docs/framework/wcf/sending-and-receiving-faults.md).</span></span> <span data-ttu-id="b0053-163">完整範例示範如何在用戶端中處理錯誤，請參閱[預期的例外狀況](../../../docs/framework/wcf/samples/expected-exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="b0053-163">For a complete sample the shows how to handle errors in a client, see [Expected Exceptions](../../../docs/framework/wcf/samples/expected-exceptions.md).</span></span>  
  
## <a name="configuring-and-securing-clients"></a><span data-ttu-id="b0053-164">設定和保護用戶端</span><span class="sxs-lookup"><span data-stu-id="b0053-164">Configuring and Securing Clients</span></span>  
 <span data-ttu-id="b0053-165">設定用戶端時，通常是先從組態檔載入用戶端或通道物件的必要目標端點資訊；儘管可以透過用戶端建構函式和屬性，使用程式設計方式載入這項資訊，</span><span class="sxs-lookup"><span data-stu-id="b0053-165">Configuring a client starts with the required loading of target endpoint information for the client or channel object, usually from a configuration file, although you can also load this information programmatically using the client constructors and properties.</span></span> <span data-ttu-id="b0053-166">但是為了啟用特定用戶端行為，並符合許多安全性案例的需要，您應該另外執行其他必要的設定步驟。</span><span class="sxs-lookup"><span data-stu-id="b0053-166">However, additional configuration steps are required to enable certain client behavior and for many security scenarios.</span></span>  
  
 <span data-ttu-id="b0053-167">例如，服務合約的安全性需求會在服務合約介面中宣告；如果 Svcutil.exe 建立了組態檔，這個檔案通常應包含能夠支援服務安全性需求的繫結。</span><span class="sxs-lookup"><span data-stu-id="b0053-167">For example, security requirements for service contracts are declared in the service contract interface, and if Svcutil.exe created a configuration file, that file usually contains a binding that is capable of supporting the security requirements of the service.</span></span> <span data-ttu-id="b0053-168">不過，在某些情況下，可能需要進行更多的安全性設定，例如設定用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="b0053-168">In some cases, however, more security configuration may be required, such as configuring client credentials.</span></span> <span data-ttu-id="b0053-169">如需 WCF 用戶端安全性組態的完整資訊，請參閱[保護的用戶端](../../../docs/framework/wcf/securing-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="b0053-169">For complete information about the configuration of security for WCF clients, see [Securing Clients](../../../docs/framework/wcf/securing-clients.md).</span></span>  
  
 <span data-ttu-id="b0053-170">此外，還可以在用戶端應用程式中啟用某些自訂修改，例如自訂執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="b0053-170">In addition, some custom modifications can be enabled in client applications, such as custom run-time behaviors.</span></span> <span data-ttu-id="b0053-171">如需如何設定自訂用戶端行為的詳細資訊，請參閱[設定用戶端行為](../../../docs/framework/wcf/configuring-client-behaviors.md)。</span><span class="sxs-lookup"><span data-stu-id="b0053-171">For more information about how to configure a custom client behavior, see [Configuring Client Behaviors](../../../docs/framework/wcf/configuring-client-behaviors.md).</span></span>  
  
## <a name="creating-callback-objects-for-duplex-services"></a><span data-ttu-id="b0053-172">建立雙工服務的回呼物件</span><span class="sxs-lookup"><span data-stu-id="b0053-172">Creating Callback Objects for Duplex Services</span></span>  
 <span data-ttu-id="b0053-173">雙工服務會指定回呼合約，這是用戶端應用程式為了在服務根據合約需求進行呼叫時提供其所需之回呼物件而必須實作的合約。</span><span class="sxs-lookup"><span data-stu-id="b0053-173">Duplex services specify a callback contract that the client application must implement in order to provide a callback object for the service to call according to the requirements of the contract.</span></span> <span data-ttu-id="b0053-174">雖然回呼物件並非完整的服務 (例如，您無法透過回呼物件啟始通道)，但基於實作和組態設定的目的，不妨將它們視為一種服務。</span><span class="sxs-lookup"><span data-stu-id="b0053-174">Although callback objects are not full services (for example, you cannot initiate a channel with a callback object), for the purposes of implementation and configuration they can be thought of as a kind of service.</span></span>  
  
 <span data-ttu-id="b0053-175">雙工服務的用戶端必須：</span><span class="sxs-lookup"><span data-stu-id="b0053-175">Clients of duplex services must:</span></span>  
  
- <span data-ttu-id="b0053-176">實作回呼合約類別。</span><span class="sxs-lookup"><span data-stu-id="b0053-176">Implement a callback contract class.</span></span>  
  
- <span data-ttu-id="b0053-177">建立回呼合約實作類別的執行個體，並使用它來建立<xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>您傳遞至 WCF 用戶端建構函式物件。</span><span class="sxs-lookup"><span data-stu-id="b0053-177">Create an instance of the callback contract implementation class and use it to create the <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> object that you pass to the WCF client constructor.</span></span>  
  
- <span data-ttu-id="b0053-178">叫用作業和處理作業回呼。</span><span class="sxs-lookup"><span data-stu-id="b0053-178">Invoke operations and handle operation callbacks.</span></span>  
  
 <span data-ttu-id="b0053-179">雙工的 WCF 用戶端物件函式，例如其非雙工的對應項目，與例外狀況，其會公開支援回呼，包括回呼服務的組態所需的功能。</span><span class="sxs-lookup"><span data-stu-id="b0053-179">Duplex WCF client objects function like their nonduplex counterparts, with the exception that they expose the functionality necessary to support callbacks, including the configuration of the callback service.</span></span>  
  
 <span data-ttu-id="b0053-180">例如，您可以在回呼類別上使用 <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> 屬性 (Attribute) 的屬性 (Property)，控制回呼物件執行階段行為的各種層面。</span><span class="sxs-lookup"><span data-stu-id="b0053-180">For example, you can control various aspects of callback object runtime behavior by using properties of the <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> attribute on the callback class.</span></span> <span data-ttu-id="b0053-181">此外，還可以使用 <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> 類別，讓例外狀況資訊回傳給呼叫回呼物件的服務。</span><span class="sxs-lookup"><span data-stu-id="b0053-181">Another example is the use of the <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> class to enable the return of exception information to services that call the callback object.</span></span> <span data-ttu-id="b0053-182">如需詳細資訊，請參閱 <<c0> [ 雙工服務](../../../docs/framework/wcf/feature-details/duplex-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b0053-182">For more information, see [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span> <span data-ttu-id="b0053-183">如需完整範例，請參閱 <<c0> [ 雙工](../../../docs/framework/wcf/samples/duplex.md)。</span><span class="sxs-lookup"><span data-stu-id="b0053-183">For a complete sample, see [Duplex](../../../docs/framework/wcf/samples/duplex.md).</span></span>  
  
 <span data-ttu-id="b0053-184">在執行 Internet Information Services (IIS) 5.1 的 Windows XP 電腦上，雙工用戶端必須使用 <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> 類別來指定用戶端基底位址，否則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b0053-184">On Windows XP computers running Internet Information Services (IIS) 5.1, duplex clients must specify a client base address using the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> class or an exception is thrown.</span></span> <span data-ttu-id="b0053-185">下列程式碼範例示範如何在程式碼中執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="b0053-185">The following code example shows how to do this in code.</span></span>  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 <span data-ttu-id="b0053-186">下列程式碼範例示範如何在組態檔中執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="b0053-186">The following code shows how to do this in a configuration file</span></span>  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a><span data-ttu-id="b0053-187">以非同步方式呼叫服務</span><span class="sxs-lookup"><span data-stu-id="b0053-187">Calling Services Asynchronously</span></span>  
 <span data-ttu-id="b0053-188">呼叫作業的方式完全取決於用戶端開發人員。</span><span class="sxs-lookup"><span data-stu-id="b0053-188">How operations are called is entirely up to the client developer.</span></span> <span data-ttu-id="b0053-189">這是因為透過 Managed 程式碼來表達呼叫程序時，您可以將組成作業的訊息對應至同步或非同步的方法。</span><span class="sxs-lookup"><span data-stu-id="b0053-189">This is because the messages that make up an operation can be mapped to either synchronous or asynchronous methods when expressed in managed code.</span></span> <span data-ttu-id="b0053-190">因此，如果要建置以非同步方式呼叫作業的用戶端，您可以透過 Svcutil.exe，使用 `/async` 選項來產生非同步用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="b0053-190">Therefore, if you want to build a client that calls operations asynchronously, you can use Svcutil.exe to generate asynchronous client code using the `/async` option.</span></span> <span data-ttu-id="b0053-191">如需詳細資訊，請參閱[如何：以非同步方式呼叫服務作業](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)。</span><span class="sxs-lookup"><span data-stu-id="b0053-191">For more information, see [How to: Call Service Operations Asynchronously](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span>  
  
## <a name="calling-services-using-wcf-client-channels"></a><span data-ttu-id="b0053-192">使用 WCF 用戶端通道呼叫服務</span><span class="sxs-lookup"><span data-stu-id="b0053-192">Calling Services Using WCF Client Channels</span></span>  
 <span data-ttu-id="b0053-193">WCF 用戶端型別會擴充<xref:System.ServiceModel.ClientBase%601>，而其本身衍生自<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>介面，以公開基礎通道系統。</span><span class="sxs-lookup"><span data-stu-id="b0053-193">WCF client types extend <xref:System.ServiceModel.ClientBase%601>, which itself derives from <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interface to expose the underlying channel system.</span></span> <span data-ttu-id="b0053-194">您可以搭配 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> 類別使用目標服務合約來叫用服務。</span><span class="sxs-lookup"><span data-stu-id="b0053-194">You can invoke services by using the target service contract with the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="b0053-195">如需詳細資訊，請參閱 < [WCF 用戶端架構](../../../docs/framework/wcf/feature-details/client-architecture.md)。</span><span class="sxs-lookup"><span data-stu-id="b0053-195">For details, see [WCF Client Architecture](../../../docs/framework/wcf/feature-details/client-architecture.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0053-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0053-196">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
