---
title: WCF 用戶端概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
ms.openlocfilehash: b314b61584e45ac5e80a248e639bdac427ba4a57
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "82021732"
---
# <a name="wcf-client-overview"></a><span data-ttu-id="768cd-102">WCF 用戶端概述</span><span class="sxs-lookup"><span data-stu-id="768cd-102">WCF client overview</span></span>

<span data-ttu-id="768cd-103">本節介紹用戶端應用程式執行哪些操作、如何配置、創建和使用 Windows 通信基礎 (WCF) 用戶端以及如何保護用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="768cd-103">This section describes what client applications do, how to configure, create, and use a Windows Communication Foundation (WCF) client, and how to secure client applications.</span></span>  
  
## <a name="using-wcf-client-objects"></a><span data-ttu-id="768cd-104">使用 WCF 用戶端物件</span><span class="sxs-lookup"><span data-stu-id="768cd-104">Using WCF Client Objects</span></span>  
 <span data-ttu-id="768cd-105">用戶端應用程式是使用 WCF 用戶端與另一個應用程式進行通信的託管應用程式。</span><span class="sxs-lookup"><span data-stu-id="768cd-105">A client application is a managed application that uses a WCF client to communicate with another application.</span></span> <span data-ttu-id="768cd-106">為 WCF 服務建立客戶端應用程式需要以下步驟:</span><span class="sxs-lookup"><span data-stu-id="768cd-106">Creating a client application for a WCF service requires the following steps:</span></span>  
  
1. <span data-ttu-id="768cd-107">取得服務端點的服務合約、繫結和位址資訊。</span><span class="sxs-lookup"><span data-stu-id="768cd-107">Obtain the service contract, bindings, and address information for a service endpoint.</span></span>  
  
2. <span data-ttu-id="768cd-108">使用該資訊創建 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="768cd-108">Create a WCF client using that information.</span></span>  
  
3. <span data-ttu-id="768cd-109">呼叫作業。</span><span class="sxs-lookup"><span data-stu-id="768cd-109">Call operations.</span></span>  
  
4. <span data-ttu-id="768cd-110">關閉 WCF 用戶端物件。</span><span class="sxs-lookup"><span data-stu-id="768cd-110">Close the WCF client object.</span></span>  
  
<span data-ttu-id="768cd-111">下列各節將討論這些步驟，並簡要介紹以下問題：</span><span class="sxs-lookup"><span data-stu-id="768cd-111">The following sections discuss these steps and provide brief introductions to the following issues:</span></span>  
  
- <span data-ttu-id="768cd-112">處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="768cd-112">Handling errors.</span></span>  
  
- <span data-ttu-id="768cd-113">設定和保護用戶端。</span><span class="sxs-lookup"><span data-stu-id="768cd-113">Configuring and securing clients.</span></span>  
  
- <span data-ttu-id="768cd-114">建立雙工服務的回呼物件。</span><span class="sxs-lookup"><span data-stu-id="768cd-114">Creating callback objects for duplex services.</span></span>  
  
- <span data-ttu-id="768cd-115">非同步呼叫服務。</span><span class="sxs-lookup"><span data-stu-id="768cd-115">Calling services asynchronously.</span></span>  
  
- <span data-ttu-id="768cd-116">透過用戶端通道呼叫服務。</span><span class="sxs-lookup"><span data-stu-id="768cd-116">Calling services using client channels.</span></span>  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a><span data-ttu-id="768cd-117">取得服務合約、繫結和位址</span><span class="sxs-lookup"><span data-stu-id="768cd-117">Obtain the Service Contract, Bindings, and Addresses</span></span>  
 <span data-ttu-id="768cd-118">在 WCF 中,服務和用戶端使用託管屬性、介面和方法對協定建模。</span><span class="sxs-lookup"><span data-stu-id="768cd-118">In WCF, services and clients model contracts using managed attributes, interfaces, and methods.</span></span> <span data-ttu-id="768cd-119">若要在用戶端應用程式中連接到服務，您必須取得服務合約的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="768cd-119">To connect to a service in a client application, you need to obtain the type information for the service contract.</span></span> <span data-ttu-id="768cd-120">通常,您可以使用[服務模型中數據實用程式工具 (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)獲取服務協定的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="768cd-120">Typically, you obtain type information for the service contract by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="768cd-121">實用程式從服務下載中繼資料,以您選擇的語言將其轉換為託管原始碼檔,並創建可用於設定 WCF 用戶端物件的用戶端應用程式設定檔。</span><span class="sxs-lookup"><span data-stu-id="768cd-121">The utility downloads metadata from the service, converts it to a managed source code file in the language of your choice, and creates a client application configuration file that you can use to configure your WCF client object.</span></span> <span data-ttu-id="768cd-122">例如,如果要創建 WCF 用戶端物件以呼`MyCalculatorService`叫, 並且知道該服務的中繼`http://computerName/MyCalculatorService/Service.svc?wsdl`資料是在發表於的,則以下代碼範例展示如何使用 Svcutil.exe 獲取包含`ClientCode.vb`託管代碼中的服務協定的檔。</span><span class="sxs-lookup"><span data-stu-id="768cd-122">For example, if you are going to create a WCF client object to invoke a `MyCalculatorService`, and you know that the metadata for that service is published at `http://computerName/MyCalculatorService/Service.svc?wsdl`, then the following code example shows how to use Svcutil.exe to obtain a `ClientCode.vb` file that contains the service contract in managed code.</span></span>  
  
```console  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 <span data-ttu-id="768cd-123">您可以將此協定代碼編譯到用戶端應用程式中或用戶端應用程式隨後可用於創建 WCF 用戶端物件的另一個程式集中。</span><span class="sxs-lookup"><span data-stu-id="768cd-123">You can either compile this contract code into the client application or into another assembly that the client application can then use to create a WCF client object.</span></span> <span data-ttu-id="768cd-124">您可以使用組態檔來設定用戶端物件，以便正確連接到服務。</span><span class="sxs-lookup"><span data-stu-id="768cd-124">You can use the configuration file to configure the client object to properly connect to the service .</span></span>  
  
 <span data-ttu-id="768cd-125">有關此過程的範例,請參閱[如何:建立用戶端](how-to-create-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="768cd-125">For an example of this process, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="768cd-126">有關合約的更多完整資訊,請參閱[合約](./feature-details/contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="768cd-126">For more complete information about contracts, see [Contracts](./feature-details/contracts.md).</span></span>  
  
## <a name="create-a-wcf-client-object"></a><span data-ttu-id="768cd-127">建立 WCF 用戶端物件</span><span class="sxs-lookup"><span data-stu-id="768cd-127">Create a WCF Client Object</span></span>  
 <span data-ttu-id="768cd-128">WCF 用戶端是一個本地物件,它表示 WCF 服務的形式,用戶端可以使用該形式與遠端服務通訊。</span><span class="sxs-lookup"><span data-stu-id="768cd-128">A WCF client is a local object that represents a WCF service in a form that the client can use to communicate with the remote service.</span></span> <span data-ttu-id="768cd-129">WCF 用戶端類型實現目標服務協定,因此,當您創建一個協定並對其進行配置時,可以直接使用用戶端物件調用服務操作。</span><span class="sxs-lookup"><span data-stu-id="768cd-129">WCF client types implement the target service contract, so when you create one and configure it, you can then use the client object directly to invoke service operations.</span></span> <span data-ttu-id="768cd-130">WCF 執行時將方法調用轉換為消息,將它們發送到服務,偵聽答覆,並將這些值作為返回值`out`或`ref`或 參數返回給 WCF 用戶端物件。</span><span class="sxs-lookup"><span data-stu-id="768cd-130">The WCF run time converts the method calls into messages, sends them to the service, listens for the reply, and returns those values to the WCF client object as return values or `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="768cd-131">您還可以使用 WCF 用戶端通道對象來連接和使用服務。</span><span class="sxs-lookup"><span data-stu-id="768cd-131">You can also use WCF client channel objects to connect with and use services.</span></span> <span data-ttu-id="768cd-132">有關詳細資訊,請參閱[WCF 用戶端體系結構](./feature-details/client-architecture.md)。</span><span class="sxs-lookup"><span data-stu-id="768cd-132">For details, see [WCF Client Architecture](./feature-details/client-architecture.md).</span></span>  
  
#### <a name="creating-a-new-wcf-object"></a><span data-ttu-id="768cd-133">建立新的 WCF 物件</span><span class="sxs-lookup"><span data-stu-id="768cd-133">Creating a New WCF Object</span></span>  
 <span data-ttu-id="768cd-134">為說明 <xref:System.ServiceModel.ClientBase%601> 類別的使用方式，請假設已從服務應用程式產生下列簡單服務合約。</span><span class="sxs-lookup"><span data-stu-id="768cd-134">To illustrate the use of a <xref:System.ServiceModel.ClientBase%601> class, assume the following simple service contract has been generated from a service application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="768cd-135">如果使用 Visual Studio 創建 WCF 用戶端,則物件在向專案添加服務引用時會自動載入到物件瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="768cd-135">If you are using Visual Studio to create your WCF client, objects are loaded automatically into the object browser when you add a service reference to your project.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 <span data-ttu-id="768cd-136">如果不使用 Visual Studio,請檢查產生的協定代碼以尋找<xref:System.ServiceModel.ClientBase%601>擴充的類型和服務`ISampleService`協定介面 。</span><span class="sxs-lookup"><span data-stu-id="768cd-136">If you are not using Visual Studio, examine the generated contract code to find the type that extends <xref:System.ServiceModel.ClientBase%601> and the service contract interface `ISampleService`.</span></span> <span data-ttu-id="768cd-137">在這種情況下，該型別看起來類似下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="768cd-137">In this case, that type looks like the following code:</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 <span data-ttu-id="768cd-138">您可以將這個類別建立成本機物件，其方式是使用其中一個建構函式，然後加以設定，再用來連接到型別為 `ISampleService` 的服務。</span><span class="sxs-lookup"><span data-stu-id="768cd-138">This class can be created as a local object using one of the constructors, configured, and then used to connect to a service of the type `ISampleService`.</span></span>  
  
 <span data-ttu-id="768cd-139">建議您首先創建 WCF 用戶端物件,然後使用它並在單個 try/catch 塊內將其關閉。</span><span class="sxs-lookup"><span data-stu-id="768cd-139">It is recommended that you create your WCF client object first, and then use it and close it inside a single try/catch block.</span></span> <span data-ttu-id="768cd-140">不要使用 語`using`句`Using`( 在 Visual Basic 中),因為它可以掩蓋某些失敗模式下的異常。</span><span class="sxs-lookup"><span data-stu-id="768cd-140">Don't use the `using` statement (`Using` in Visual Basic) because it can mask exceptions in certain failure modes.</span></span> <span data-ttu-id="768cd-141">有關詳細資訊,請參閱以下部分以及[使用關閉和中止來釋放 WCF 用戶端資源](./samples/use-close-abort-release-wcf-client-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="768cd-141">For more information, see the following sections as well as [Use Close and Abort to release WCF client resources](./samples/use-close-abort-release-wcf-client-resources.md).</span></span>  
  
### <a name="contracts-bindings-and-addresses"></a><span data-ttu-id="768cd-142">合約、繫結和位址</span><span class="sxs-lookup"><span data-stu-id="768cd-142">Contracts, Bindings, and Addresses</span></span>  
 <span data-ttu-id="768cd-143">在創建 WCF 用戶端物件之前,必須配置用戶端物件。</span><span class="sxs-lookup"><span data-stu-id="768cd-143">Before you can create a WCF client object, you must configure the client object.</span></span> <span data-ttu-id="768cd-144">具體而言,它必須有一個服務*終結點*要使用。</span><span class="sxs-lookup"><span data-stu-id="768cd-144">Specifically, it must have a service *endpoint* to use.</span></span> <span data-ttu-id="768cd-145">端點是服務合約、繫結和位址的組合 </span><span class="sxs-lookup"><span data-stu-id="768cd-145">An endpoint is the combination of a service contract, a binding, and an address.</span></span> <span data-ttu-id="768cd-146">(有關終結點的詳細資訊,請參閱[終結點:位址、綁定和協定](./feature-details/endpoints-addresses-bindings-and-contracts.md)。通常,此資訊位於用戶端應用程式配置檔[\<中的終結點>](../configure-apps/file-schema/wcf/endpoint-of-client.md)元素中,例如 Svcutil.exe 工具生成的終結點,並在創建用戶端物件時自動載入。</span><span class="sxs-lookup"><span data-stu-id="768cd-146">(For more information about endpoints, see [Endpoints: Addresses, Bindings, and Contracts](./feature-details/endpoints-addresses-bindings-and-contracts.md).) Typically, this information is located in the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-of-client.md) element in a client application configuration file, such as the one the Svcutil.exe tool generates, and is loaded automatically when you create your client object.</span></span> <span data-ttu-id="768cd-147">這兩種 WCF 用戶端類型都有重載,使您能夠以程式設計方式指定此資訊。</span><span class="sxs-lookup"><span data-stu-id="768cd-147">Both WCF client types also have overloads that enable you to programmatically specify this information.</span></span>  
  
 <span data-ttu-id="768cd-148">例如，針對前面範例中使用的 `ISampleService` 所產生的組態檔會包含下列端點資訊。</span><span class="sxs-lookup"><span data-stu-id="768cd-148">For example, a generated configuration file for an `ISampleService` used in the preceding examples contains the following endpoint information.</span></span>  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 <span data-ttu-id="768cd-149">這個組態檔會在 `<client>` 元素中指定目標端點。</span><span class="sxs-lookup"><span data-stu-id="768cd-149">This configuration file specifies a target endpoint in the `<client>` element.</span></span> <span data-ttu-id="768cd-150">有關使用多個目標終結點的詳細資訊,請參閱<xref:System.ServiceModel.ClientBase%601.%23ctor%2A><xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A>或構造函數。</span><span class="sxs-lookup"><span data-stu-id="768cd-150">For more information about using multiple target endpoints, see the <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> or the <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> constructors.</span></span>  
  
## <a name="calling-operations"></a><span data-ttu-id="768cd-151">呼叫作業</span><span class="sxs-lookup"><span data-stu-id="768cd-151">Calling Operations</span></span>  
 <span data-ttu-id="768cd-152">創建並配置客戶端物件後,創建 try/catch 塊,調用操作的方式與物件為本地時相同,並關閉 WCF 用戶端物件。</span><span class="sxs-lookup"><span data-stu-id="768cd-152">Once you have a client object created and configured, create a try/catch block, call operations in the same way that you would if the object were local, and close the WCF client object.</span></span> <span data-ttu-id="768cd-153">當用戶端應用程式調用第一個操作時,WCF 會自動打開基礎通道,並且當回收物件時關閉基礎通道。</span><span class="sxs-lookup"><span data-stu-id="768cd-153">When the client application calls the first operation, WCF automatically opens the underlying channel, and the underlying channel is closed when the object is recycled.</span></span> <span data-ttu-id="768cd-154">(或者，您也可以在呼叫其他作業之前或之後明確地開啟和關閉通道)。</span><span class="sxs-lookup"><span data-stu-id="768cd-154">(Alternatively, you can also explicitly open and close the channel prior to or subsequent to calling other operations.)</span></span>  
  
 <span data-ttu-id="768cd-155">例如，您若有下列服務合約：</span><span class="sxs-lookup"><span data-stu-id="768cd-155">For example, if you have the following service contract:</span></span>  
  
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
  
 <span data-ttu-id="768cd-156">可以通過創建 WCF 用戶端物件並調用其方法來調用操作,如下代碼示例所示。</span><span class="sxs-lookup"><span data-stu-id="768cd-156">You can call operations by creating a WCF client object and calling its methods, as the following code example demonstrates.</span></span> <span data-ttu-id="768cd-157">WCF 用戶端物件的打開、調用和關閉發生在單個 try/catch 塊中。</span><span class="sxs-lookup"><span data-stu-id="768cd-157">The opening, calling, and closing of the WCF client object occurs within a single try/catch block.</span></span> <span data-ttu-id="768cd-158">有關詳細資訊,請參閱使用[WCF 用戶端存取服務](./feature-details/accessing-services-using-a-client.md)[,並使用關閉和中止來釋放 WCF 客戶端資源](./samples/use-close-abort-release-wcf-client-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="768cd-158">For more information, see [Accessing Services Using a WCF Client](./feature-details/accessing-services-using-a-client.md) and [Use Close and Abort to release WCF client resources](./samples/use-close-abort-release-wcf-client-resources.md).</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a><span data-ttu-id="768cd-159">處理錯誤</span><span class="sxs-lookup"><span data-stu-id="768cd-159">Handling Errors</span></span>  
 <span data-ttu-id="768cd-160">當開啟基礎用戶端通道 (無論是明確或是自動呼叫作業)、使用用戶端或通道物件來呼叫作業，或關閉基礎用戶端通道時，都可能會在用戶端應用程式中發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="768cd-160">Exceptions can occur in a client application when opening the underlying client channel (whether explicitly or automatically by calling an operation), using the client or channel object to call operations, or when closing the underlying client channel.</span></span> <span data-ttu-id="768cd-161">除了要由作業傳回因 SOAP 錯誤而擲回的任何 <xref:System.TimeoutException?displayProperty=nameWithType> 物件之外，建議您最少還要讓應用程式有能力處理可能發生的 <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> 和 <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="768cd-161">It is recommended at a minimum that applications expect to handle possible <xref:System.TimeoutException?displayProperty=nameWithType> and <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> exceptions in addition to any <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> objects thrown as a result of SOAP faults returned by operations.</span></span> <span data-ttu-id="768cd-162">作業合約中指定的 SOAP 錯誤會針對用戶端應用程式引發為 <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>，其中的型別參數是 SOAP 錯誤的詳細類型。</span><span class="sxs-lookup"><span data-stu-id="768cd-162">SOAP faults specified in the operation contract are raised to client applications as a <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> where the type parameter is the detail type of the SOAP fault.</span></span> <span data-ttu-id="768cd-163">有關處理客戶端應用程式中的錯誤條件的詳細資訊,請參閱[傳送和接收錯誤](sending-and-receiving-faults.md)。</span><span class="sxs-lookup"><span data-stu-id="768cd-163">For more information about handling error conditions in a client application, see [Sending and Receiving Faults](sending-and-receiving-faults.md).</span></span> <span data-ttu-id="768cd-164">有關完整範例,請參閱如何處理用戶端中的錯誤,請參閱[預期異常](./samples/expected-exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="768cd-164">For a complete sample the shows how to handle errors in a client, see [Expected Exceptions](./samples/expected-exceptions.md).</span></span>  
  
## <a name="configuring-and-securing-clients"></a><span data-ttu-id="768cd-165">設定和保護用戶端</span><span class="sxs-lookup"><span data-stu-id="768cd-165">Configuring and Securing Clients</span></span>  
 <span data-ttu-id="768cd-166">設定用戶端時，通常是先從組態檔載入用戶端或通道物件的必要目標端點資訊；儘管可以透過用戶端建構函式和屬性，使用程式設計方式載入這項資訊，</span><span class="sxs-lookup"><span data-stu-id="768cd-166">Configuring a client starts with the required loading of target endpoint information for the client or channel object, usually from a configuration file, although you can also load this information programmatically using the client constructors and properties.</span></span> <span data-ttu-id="768cd-167">但是為了啟用特定用戶端行為，並符合許多安全性案例的需要，您應該另外執行其他必要的設定步驟。</span><span class="sxs-lookup"><span data-stu-id="768cd-167">However, additional configuration steps are required to enable certain client behavior and for many security scenarios.</span></span>  
  
 <span data-ttu-id="768cd-168">例如，服務合約的安全性需求會在服務合約介面中宣告；如果 Svcutil.exe 建立了組態檔，這個檔案通常應包含能夠支援服務安全性需求的繫結。</span><span class="sxs-lookup"><span data-stu-id="768cd-168">For example, security requirements for service contracts are declared in the service contract interface, and if Svcutil.exe created a configuration file, that file usually contains a binding that is capable of supporting the security requirements of the service.</span></span> <span data-ttu-id="768cd-169">不過，在某些情況下，可能需要進行更多的安全性設定，例如設定用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="768cd-169">In some cases, however, more security configuration may be required, such as configuring client credentials.</span></span> <span data-ttu-id="768cd-170">有關 WCF 用戶端的安全設定的完整資訊,請參閱[保護用戶端](securing-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="768cd-170">For complete information about the configuration of security for WCF clients, see [Securing Clients](securing-clients.md).</span></span>  
  
 <span data-ttu-id="768cd-171">此外，還可以在用戶端應用程式中啟用某些自訂修改，例如自訂執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="768cd-171">In addition, some custom modifications can be enabled in client applications, such as custom run-time behaviors.</span></span> <span data-ttu-id="768cd-172">有關如何設定自訂客戶端行為的詳細資訊,請參閱[設定客戶端行為](configuring-client-behaviors.md)。</span><span class="sxs-lookup"><span data-stu-id="768cd-172">For more information about how to configure a custom client behavior, see [Configuring Client Behaviors](configuring-client-behaviors.md).</span></span>  
  
## <a name="creating-callback-objects-for-duplex-services"></a><span data-ttu-id="768cd-173">建立雙工服務的回呼物件</span><span class="sxs-lookup"><span data-stu-id="768cd-173">Creating Callback Objects for Duplex Services</span></span>  
 <span data-ttu-id="768cd-174">雙工服務會指定回呼合約，這是用戶端應用程式為了在服務根據合約需求進行呼叫時提供其所需之回呼物件而必須實作的合約。</span><span class="sxs-lookup"><span data-stu-id="768cd-174">Duplex services specify a callback contract that the client application must implement in order to provide a callback object for the service to call according to the requirements of the contract.</span></span> <span data-ttu-id="768cd-175">雖然回呼物件並非完整的服務 (例如，您無法透過回呼物件啟始通道)，但基於實作和組態設定的目的，不妨將它們視為一種服務。</span><span class="sxs-lookup"><span data-stu-id="768cd-175">Although callback objects are not full services (for example, you cannot initiate a channel with a callback object), for the purposes of implementation and configuration they can be thought of as a kind of service.</span></span>  
  
 <span data-ttu-id="768cd-176">雙工服務的用戶端必須：</span><span class="sxs-lookup"><span data-stu-id="768cd-176">Clients of duplex services must:</span></span>  
  
- <span data-ttu-id="768cd-177">實作回呼合約類別。</span><span class="sxs-lookup"><span data-stu-id="768cd-177">Implement a callback contract class.</span></span>  
  
- <span data-ttu-id="768cd-178">創建回調協定實現類的實例,並用它來創建傳遞給 WCF<xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>用戶端構造函數的物件。</span><span class="sxs-lookup"><span data-stu-id="768cd-178">Create an instance of the callback contract implementation class and use it to create the <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> object that you pass to the WCF client constructor.</span></span>  
  
- <span data-ttu-id="768cd-179">叫用作業和處理作業回呼。</span><span class="sxs-lookup"><span data-stu-id="768cd-179">Invoke operations and handle operation callbacks.</span></span>  
  
 <span data-ttu-id="768cd-180">雙工 WCF 用戶端物件的功能與非雙工物件類似,但它們公開支援回調所需的功能(包括回調服務的配置)除外。</span><span class="sxs-lookup"><span data-stu-id="768cd-180">Duplex WCF client objects function like their nonduplex counterparts, with the exception that they expose the functionality necessary to support callbacks, including the configuration of the callback service.</span></span>  
  
 <span data-ttu-id="768cd-181">例如，您可以在回呼類別上使用 <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> 屬性 (Attribute) 的屬性 (Property)，控制回呼物件執行階段行為的各種層面。</span><span class="sxs-lookup"><span data-stu-id="768cd-181">For example, you can control various aspects of callback object runtime behavior by using properties of the <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> attribute on the callback class.</span></span> <span data-ttu-id="768cd-182">此外，還可以使用 <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> 類別，讓例外狀況資訊回傳給呼叫回呼物件的服務。</span><span class="sxs-lookup"><span data-stu-id="768cd-182">Another example is the use of the <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> class to enable the return of exception information to services that call the callback object.</span></span> <span data-ttu-id="768cd-183">有關詳細資訊,請參閱[雙工服務](./feature-details/duplex-services.md)。</span><span class="sxs-lookup"><span data-stu-id="768cd-183">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span> <span data-ttu-id="768cd-184">有關完整範例,請參閱[雙工](./samples/duplex.md)。</span><span class="sxs-lookup"><span data-stu-id="768cd-184">For a complete sample, see [Duplex](./samples/duplex.md).</span></span>  
  
 <span data-ttu-id="768cd-185">在執行 Internet Information Services (IIS) 5.1 的 Windows XP 電腦上，雙工用戶端必須使用 <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> 類別來指定用戶端基底位址，否則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="768cd-185">On Windows XP computers running Internet Information Services (IIS) 5.1, duplex clients must specify a client base address using the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> class or an exception is thrown.</span></span> <span data-ttu-id="768cd-186">下列程式碼範例示範如何在程式碼中執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="768cd-186">The following code example shows how to do this in code.</span></span>  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 <span data-ttu-id="768cd-187">下列程式碼範例示範如何在組態檔中執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="768cd-187">The following code shows how to do this in a configuration file</span></span>  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a><span data-ttu-id="768cd-188">以非同步方式呼叫服務</span><span class="sxs-lookup"><span data-stu-id="768cd-188">Calling Services Asynchronously</span></span>  
 <span data-ttu-id="768cd-189">呼叫作業的方式完全取決於用戶端開發人員。</span><span class="sxs-lookup"><span data-stu-id="768cd-189">How operations are called is entirely up to the client developer.</span></span> <span data-ttu-id="768cd-190">這是因為透過 Managed 程式碼來表達呼叫程序時，您可以將組成作業的訊息對應至同步或非同步的方法。</span><span class="sxs-lookup"><span data-stu-id="768cd-190">This is because the messages that make up an operation can be mapped to either synchronous or asynchronous methods when expressed in managed code.</span></span> <span data-ttu-id="768cd-191">因此，如果要建置以非同步方式呼叫作業的用戶端，您可以透過 Svcutil.exe，使用 `/async` 選項來產生非同步用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="768cd-191">Therefore, if you want to build a client that calls operations asynchronously, you can use Svcutil.exe to generate asynchronous client code using the `/async` option.</span></span> <span data-ttu-id="768cd-192">有關詳細資訊,請參閱[如何:非同步調用服務操作](./feature-details/how-to-call-wcf-service-operations-asynchronously.md)。</span><span class="sxs-lookup"><span data-stu-id="768cd-192">For more information, see [How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span>  
  
## <a name="calling-services-using-wcf-client-channels"></a><span data-ttu-id="768cd-193">使用 WCF 用戶端通道呼叫服務</span><span class="sxs-lookup"><span data-stu-id="768cd-193">Calling Services Using WCF Client Channels</span></span>  
 <span data-ttu-id="768cd-194">WCF 用戶端<xref:System.ServiceModel.ClientBase%601>類型 擴展 ,它<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>本身派生 自介面來公開基礎通道系統。</span><span class="sxs-lookup"><span data-stu-id="768cd-194">WCF client types extend <xref:System.ServiceModel.ClientBase%601>, which itself derives from <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interface to expose the underlying channel system.</span></span> <span data-ttu-id="768cd-195">您可以搭配 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> 類別使用目標服務合約來叫用服務。</span><span class="sxs-lookup"><span data-stu-id="768cd-195">You can invoke services by using the target service contract with the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="768cd-196">有關詳細資訊,請參閱[WCF 用戶端體系結構](./feature-details/client-architecture.md)。</span><span class="sxs-lookup"><span data-stu-id="768cd-196">For details, see [WCF Client Architecture](./feature-details/client-architecture.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="768cd-197">另請參閱</span><span class="sxs-lookup"><span data-stu-id="768cd-197">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
