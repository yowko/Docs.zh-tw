---
title: 作業格式器和作業選取器
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: a814de7433f2d06491245dc1d6e6e637b514118a
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45589261"
---
# <a name="operation-formatter-and-operation-selector"></a><span data-ttu-id="d7b79-102">作業格式器和作業選取器</span><span class="sxs-lookup"><span data-stu-id="d7b79-102">Operation Formatter and Operation Selector</span></span>
<span data-ttu-id="d7b79-103">這個範例會示範如何使用 Windows Communication Foundation (WCF) 擴充性點，以允許在不同的格式，從 WCF 所預期的內容中的訊息資料。</span><span class="sxs-lookup"><span data-stu-id="d7b79-103">This sample demonstrates how Windows Communication Foundation (WCF) extensibility points can be used to allow message data in a different format from what WCF expects.</span></span> <span data-ttu-id="d7b79-104">根據預設，WCF 格式器預期方法參數包含`soap:body`項目。</span><span class="sxs-lookup"><span data-stu-id="d7b79-104">By default, WCF formatters expect method parameters to be included under the `soap:body` element.</span></span> <span data-ttu-id="d7b79-105">此範例會示範如何實作自訂作業格式器，而這個作業格式器會剖析 HTTP GET 查詢字串中的參數資料，然後使用該資料叫用方法。</span><span class="sxs-lookup"><span data-stu-id="d7b79-105">The sample shows how to implement a custom operation formatter that parses parameter data from an HTTP GET query string instead and invokes methods using that data.</span></span>  
  
 <span data-ttu-id="d7b79-106">此樣本根據[快速入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，它會實作`ICalculator`服務合約。</span><span class="sxs-lookup"><span data-stu-id="d7b79-106">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="d7b79-107">它會示範如何將 Add、Subtract、Multiply 和 Divide 訊息變更為針對用戶端對伺服器的要求使用 HTTP GET，以及針對伺服器對用戶端的回應使用具有 POX 訊息的 HTTP POST。</span><span class="sxs-lookup"><span data-stu-id="d7b79-107">It shows how Add, Subtract, Multiply, and Divide messages can be changed to use HTTP GET for client-to-server requests and HTTP POST with POX messages for server-to-client responses.</span></span>  
  
 <span data-ttu-id="d7b79-108">為了此示範，範例提供下列各項：</span><span class="sxs-lookup"><span data-stu-id="d7b79-108">To do so, the sample provides the following:</span></span>  
  
-   <span data-ttu-id="d7b79-109">`QueryStringFormatter`，會分別對用戶端和伺服器實作 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> 和 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>，並處理查詢字串中的資料。</span><span class="sxs-lookup"><span data-stu-id="d7b79-109">`QueryStringFormatter`, which implements <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> for the client and server, respectively, and processes the data in the query string.</span></span>  
  
-   <span data-ttu-id="d7b79-110">`UriOperationSelector`，會在伺服器上實作 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>，以根據 GET 要求中的作業名稱執行作業分派。</span><span class="sxs-lookup"><span data-stu-id="d7b79-110">`UriOperationSelector`, which implements <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> on the server to perform operation dispatch based on the operation name in the GET request.</span></span>  
  
-   <span data-ttu-id="d7b79-111">`EnableHttpGetRequestsBehavior` 端點行為 (以及對應的組態)，會將必要的作業選取器加入至執行階段。</span><span class="sxs-lookup"><span data-stu-id="d7b79-111">`EnableHttpGetRequestsBehavior` endpoint behavior (and corresponding configuration), which adds the necessary operation selector to the runtime.</span></span>  
  
-   <span data-ttu-id="d7b79-112">示範如何將新作業格式器插入至執行階段。</span><span class="sxs-lookup"><span data-stu-id="d7b79-112">Shows how to insert a new operation formatter into the runtime.</span></span>  
  
-   <span data-ttu-id="d7b79-113">在這個範例中，用戶端和服務都是主控台應用程式 (.exe)。</span><span class="sxs-lookup"><span data-stu-id="d7b79-113">In this sample, both the client and the service are console applications (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7b79-114">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="d7b79-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="key-concepts"></a><span data-ttu-id="d7b79-115">重要概念</span><span class="sxs-lookup"><span data-stu-id="d7b79-115">Key Concepts</span></span>  
 <span data-ttu-id="d7b79-116">`QueryStringFormatter` -作業格式器會負責將訊息轉換的參數物件陣列和訊息參數物件的陣列的 WCF 中的元件。</span><span class="sxs-lookup"><span data-stu-id="d7b79-116">`QueryStringFormatter` - The operation formatter is the component in WCF that is responsible for converting a message into an array of parameter objects and an array of parameter objects into a message.</span></span> <span data-ttu-id="d7b79-117">此轉換是透過用戶端上的 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> 介面和伺服器上的 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> 介面來完成。</span><span class="sxs-lookup"><span data-stu-id="d7b79-117">This is done on the client using the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface and on the server with the <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface.</span></span> <span data-ttu-id="d7b79-118">這些介面都可讓使用者從 `Serialize` 和 `Deserialize` 方法中取得要求和回應訊息。</span><span class="sxs-lookup"><span data-stu-id="d7b79-118">These interfaces enable users to get the request and response messages from the `Serialize` and `Deserialize` methods.</span></span>  
  
 <span data-ttu-id="d7b79-119">在這個範例中，`QueryStringFormatter` 會實作這兩個介面，並且在用戶端和伺服器上實作。</span><span class="sxs-lookup"><span data-stu-id="d7b79-119">In this sample, `QueryStringFormatter` implements both of these interfaces and is implemented on the client and server.</span></span>  
  
 <span data-ttu-id="d7b79-120">要求：</span><span class="sxs-lookup"><span data-stu-id="d7b79-120">Request:</span></span>  
  
-   <span data-ttu-id="d7b79-121">此範例會使用 <xref:System.ComponentModel.TypeConverter> 類別，將要求訊息中的參數資料與字串互相轉換。</span><span class="sxs-lookup"><span data-stu-id="d7b79-121">The sample uses the <xref:System.ComponentModel.TypeConverter> class to convert parameter data in the request message to and from strings.</span></span> <span data-ttu-id="d7b79-122">如果特定型別無法使用 <xref:System.ComponentModel.TypeConverter>，則範例格式器會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d7b79-122">If a <xref:System.ComponentModel.TypeConverter> is not available for a specific type, the sample formatter throws an exception.</span></span>  
  
-   <span data-ttu-id="d7b79-123">在用戶端的 `IClientMessageFormatter.SerializeRequest` 方法中，格式器會使用適當的收件者地址來建立 URI，並將作業名稱附加為後置字元。</span><span class="sxs-lookup"><span data-stu-id="d7b79-123">In the `IClientMessageFormatter.SerializeRequest` method on the client, the formatter creates a URI with the appropriate To address and appends the operation name as a suffix.</span></span> <span data-ttu-id="d7b79-124">這個名稱會分派至伺服器上的適當作業。</span><span class="sxs-lookup"><span data-stu-id="d7b79-124">This name is used to dispatch to the appropriate operation on the server.</span></span> <span data-ttu-id="d7b79-125">接著會採用參數物件的陣列，並使用 <xref:System.ComponentModel.TypeConverter> 類別轉換的參數名稱和值，將參數資料序列化為 URI 查詢字串。</span><span class="sxs-lookup"><span data-stu-id="d7b79-125">It then takes the array of parameter objects and serializes the parameter data to the URI query string using parameter names and the values converted by the <xref:System.ComponentModel.TypeConverter> class.</span></span> <span data-ttu-id="d7b79-126">然後會將 <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> 和 <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> 屬性設定為這個 URI。</span><span class="sxs-lookup"><span data-stu-id="d7b79-126">The <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> and <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> properties are then set to this URI.</span></span> <span data-ttu-id="d7b79-127"><xref:System.ServiceModel.Channels.MessageProperties> 是透過 <xref:System.ServiceModel.Channels.Message.Properties%2A> 屬性來存取。</span><span class="sxs-lookup"><span data-stu-id="d7b79-127"><xref:System.ServiceModel.Channels.MessageProperties> is accessed through the <xref:System.ServiceModel.Channels.Message.Properties%2A> property.</span></span>  
  
-   <span data-ttu-id="d7b79-128">在伺服器的 `IDispatchMessageFormatter.DeserializeRequest` 方法中，格式器會在傳入要求訊息屬性中擷取 `Via` URI。</span><span class="sxs-lookup"><span data-stu-id="d7b79-128">In the `IDispatchMessageFormatter.DeserializeRequest` method on the server, the formatter retrieves the `Via` URI in the incoming request message properties.</span></span> <span data-ttu-id="d7b79-129">這個格式器會將 URI 查詢字串中的名稱/值組剖析為參數名稱和值，並使用參數名稱和值填入 (Populate) 傳遞至方法的參數陣列。</span><span class="sxs-lookup"><span data-stu-id="d7b79-129">It parses the name-value pairs in the URI query string into parameter names and values and uses the parameter names and values to populate the array of parameters passed into the method.</span></span> <span data-ttu-id="d7b79-130">請注意，已進行作業分派，因此這個方法會忽略作業名稱後置字元。</span><span class="sxs-lookup"><span data-stu-id="d7b79-130">Note that operation dispatch has already occurred, so the operation name suffix is ignored in this method.</span></span>  
  
 <span data-ttu-id="d7b79-131">回應：</span><span class="sxs-lookup"><span data-stu-id="d7b79-131">Response:</span></span>  
  
-   <span data-ttu-id="d7b79-132">在這個範例中，HTTP GET 只能用於要求。</span><span class="sxs-lookup"><span data-stu-id="d7b79-132">In this sample, HTTP GET is used only for the request.</span></span> <span data-ttu-id="d7b79-133">格式器會將傳送回應的職責委派給原始格式器，但已使用原始格式器來產生 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="d7b79-133">The formatter delegates the sending of the response to the original formatter that would have been used to generate an XML message.</span></span> <span data-ttu-id="d7b79-134">這個範例的其中一個目標就是告訴您如何實作此種委派格式器。</span><span class="sxs-lookup"><span data-stu-id="d7b79-134">One of the goals of this sample is to show how such a delegating formatter can be implemented.</span></span>  
  
### <a name="uripathsuffixoperationselector-class"></a><span data-ttu-id="d7b79-135">UriPathSuffixOperationSelector 類別</span><span class="sxs-lookup"><span data-stu-id="d7b79-135">UriPathSuffixOperationSelector Class</span></span>  
 <span data-ttu-id="d7b79-136"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> 介面可讓使用者實作自己的邏輯，而這是特定訊息應該分派的作業。</span><span class="sxs-lookup"><span data-stu-id="d7b79-136">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface enables users to implement their own logic for which operation a particular message should be dispatched.</span></span>  
  
 <span data-ttu-id="d7b79-137">在這個範例中，由於作業名稱是包含在 HTTP GET URI，而非訊息的動作標頭中，因此必須在伺服器上實作 `UriPathSuffixOperationSelector` 才能選取適當的作業。</span><span class="sxs-lookup"><span data-stu-id="d7b79-137">In this sample, `UriPathSuffixOperationSelector` must be implemented on the server to select the appropriate operation because the operation name is included in the HTTP GET URI rather than an action header in the message.</span></span> <span data-ttu-id="d7b79-138">會將範例設定為僅允許不會區分大小寫的作業名稱。</span><span class="sxs-lookup"><span data-stu-id="d7b79-138">The sample is set up to allow only case-insensitive operation names.</span></span>  
  
 <span data-ttu-id="d7b79-139">`SelectOperation` 方法接著採用傳入訊息，並在其訊息屬性中查詢 `Via` URI。</span><span class="sxs-lookup"><span data-stu-id="d7b79-139">The `SelectOperation` method takes the incoming message and looks up the `Via` URI in its message properties.</span></span> <span data-ttu-id="d7b79-140">該方法會從 URI 中擷取作業名稱後置字元、查閱內部表格以取得應將訊息分派至的作業名稱，然後傳回該作業名稱。</span><span class="sxs-lookup"><span data-stu-id="d7b79-140">It extracts the operation name suffix from the URI, looks up an internal table to get the operation name that the message should be dispatched to, and returns that operation name.</span></span>  
  
### <a name="enablehttpgetrequestsbehavior-class"></a><span data-ttu-id="d7b79-141">EnableHttpGetRequestsBehavior 類別</span><span class="sxs-lookup"><span data-stu-id="d7b79-141">EnableHttpGetRequestsBehavior Class</span></span>  
 <span data-ttu-id="d7b79-142">您可以透過程式設計的方法或端點行為來設定 `UriPathSuffixOperationSelector` 元件。</span><span class="sxs-lookup"><span data-stu-id="d7b79-142">The `UriPathSuffixOperationSelector` component can be set up programmatically or through an endpoint behavior.</span></span> <span data-ttu-id="d7b79-143">此範例會實作 `EnableHttpGetRequestsBehavior` 行為，而這個行為是在服務的應用程式組態檔中指定。</span><span class="sxs-lookup"><span data-stu-id="d7b79-143">The sample implements the `EnableHttpGetRequestsBehavior` behavior, which is specified in service’s application configuration file.</span></span>  
  
 <span data-ttu-id="d7b79-144">在伺服器上：</span><span class="sxs-lookup"><span data-stu-id="d7b79-144">On the server:</span></span>  
  
 <span data-ttu-id="d7b79-145">將 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> 設定為 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> 實作。</span><span class="sxs-lookup"><span data-stu-id="d7b79-145">The <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> is set to the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementation.</span></span>  
  
 <span data-ttu-id="d7b79-146">根據預設，WCF 會使用完全符合的位址篩選器。</span><span class="sxs-lookup"><span data-stu-id="d7b79-146">By default, WCF uses an exact-match address filter.</span></span> <span data-ttu-id="d7b79-147">傳入訊息上的 URI 包含作業名稱後置字元，後面跟著包含參數資料的查詢字串，因此端點行為也會將位址篩選條件變更為開頭相符的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="d7b79-147">The URI on the incoming message contains an operation name suffix followed by a query string that contains parameter data, so the endpoint behavior also changes the address filter to be a prefix match filter.</span></span> <span data-ttu-id="d7b79-148">它會使用 WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>針對此目的。</span><span class="sxs-lookup"><span data-stu-id="d7b79-148">It uses the WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> for this purpose.</span></span>  
  
### <a name="installing-operation-formatters"></a><span data-ttu-id="d7b79-149">安裝作業格式器</span><span class="sxs-lookup"><span data-stu-id="d7b79-149">Installing operation formatters</span></span>  
 <span data-ttu-id="d7b79-150">指定格式器的作業行為都是獨一無二。</span><span class="sxs-lookup"><span data-stu-id="d7b79-150">Operation behaviors that specify formatters are unique.</span></span> <span data-ttu-id="d7b79-151">預設一定會對每個作業實作一個這樣的行為，以建立所需的作業格式器。</span><span class="sxs-lookup"><span data-stu-id="d7b79-151">One such behavior is always implemented by default for every operation to create the necessary operation formatter.</span></span> <span data-ttu-id="d7b79-152">不過，這些行為看起來就像其他作業行為，其他屬性無法識別這些行為。</span><span class="sxs-lookup"><span data-stu-id="d7b79-152">However, these behaviors look like just another operation behavior; they are not identifiable by any other attribute.</span></span> <span data-ttu-id="d7b79-153">若要安裝取代行為，實作必須尋找特定的格式器行為，根據預設，而且不是 WCF 型別載入器會安裝取代它，或新增相容的預設行為之後執行的行為。</span><span class="sxs-lookup"><span data-stu-id="d7b79-153">To install a replacement behavior, the implementation must look for specific formatter behaviors that are installed by the WCF type loader by default and either replace it or add a compatible behavior to run after the default behavior.</span></span>  
  
 <span data-ttu-id="d7b79-154">在呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> 之前，可以透過程式設計方式設定這些作業格式器行為，或在預設行為之後指定要執行的作業行為來設定。</span><span class="sxs-lookup"><span data-stu-id="d7b79-154">These operation formatters behaviors can be set up programmatically prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> or by specifying an operation behavior that is executed after the default one.</span></span> <span data-ttu-id="d7b79-155">不過，無法輕易地透過端點行為 (以及組態) 來設定作業格式器行為，因為行為模型不允許取代其他行為，否則會修改描述樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="d7b79-155">However, it cannot easily be set up by an endpoint behavior (and therefore by configuration) because the behavior model does not allow a behavior to replace other behaviors or otherwise modify the description tree.</span></span>  
  
 <span data-ttu-id="d7b79-156">在用戶端上：</span><span class="sxs-lookup"><span data-stu-id="d7b79-156">On the client:</span></span>  
  
 <span data-ttu-id="d7b79-157">必須實作 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> 實作，因此可將要求轉換為 HTTP GET 要求，並針對回應委派至原始格式器。</span><span class="sxs-lookup"><span data-stu-id="d7b79-157">The <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementation must be implemented so that it can convert the requests into HTTP GET requests and delegate to the original formatter for responses.</span></span> <span data-ttu-id="d7b79-158">呼叫 `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` Helper 方法即可完成此動作。</span><span class="sxs-lookup"><span data-stu-id="d7b79-158">This is done by calling the `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method.</span></span>  
  
 <span data-ttu-id="d7b79-159">這個動作必須在呼叫 `CreateChannel` 之前完成。</span><span class="sxs-lookup"><span data-stu-id="d7b79-159">This must be done before calling `CreateChannel`.</span></span>  
  
```  
void ReplaceFormatterBehavior(OperationDescription operationDescription, EndpointAddress address)  
{  
    // Remove the DataContract behavior if it is present.  
    IOperationBehavior formatterBehavior = operationDescription.Behaviors.Remove<DataContractSerializerOperationBehavior>();  
    if (formatterBehavior == null)  
    {  
        // Remove the XmlSerializer behavior if it is present.  
        formatterBehavior = operationDescription.Behaviors.Remove<XmlSerializerOperationBehavior>();  
        ...  
    }  
  
    // Remember what the innerFormatterBehavior was.  
    DelegatingFormatterBehavior delegatingFormatterBehavior = new DelegatingFormatterBehavior(address);  
    delegatingFormatterBehavior.InnerFormatterBehavior = formatterBehavior;  
   operationDescription.Behaviors.Add(delegatingFormatterBehavior);  
}  
```  
  
 <span data-ttu-id="d7b79-160">在伺服器上：</span><span class="sxs-lookup"><span data-stu-id="d7b79-160">On the server:</span></span>  
  
-   <span data-ttu-id="d7b79-161">必須實作 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> 介面，因此可讀取 HTTP GET 要求並委派至原始格式器以撰寫回應。</span><span class="sxs-lookup"><span data-stu-id="d7b79-161">The <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface must be implemented so that it can read HTTP GET requests and delegate to the original formatter for writing responses.</span></span> <span data-ttu-id="d7b79-162">呼叫相同 `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` Helper 方法以做為用戶端 (請參閱先前的程式碼範例)，即可完成此動作。</span><span class="sxs-lookup"><span data-stu-id="d7b79-162">This is done by calling the same `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method as the client (see the previous code sample).</span></span>  
  
-   <span data-ttu-id="d7b79-163">這個動作必須在呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> 之前完成。</span><span class="sxs-lookup"><span data-stu-id="d7b79-163">This must be done before <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="d7b79-164">在此範例中，會顯示如何在呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> 之前，以手動方式修改格式器。</span><span class="sxs-lookup"><span data-stu-id="d7b79-164">In this sample, we show how the formatter is manually modified before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="d7b79-165">其他一種可達到相同目標的方法為，從 <xref:System.ServiceModel.ServiceHost> (會在開啟之前呼叫 `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior`) 衍生類別 (如需範例，請參閱裝載文件和範例)。</span><span class="sxs-lookup"><span data-stu-id="d7b79-165">Another way to achieve the same thing is to derive a class from <xref:System.ServiceModel.ServiceHost> that makes the calls to `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` before opening (please see hosting documentation and samples for examples).</span></span>  
  
### <a name="user-experience"></a><span data-ttu-id="d7b79-166">使用者經歷</span><span class="sxs-lookup"><span data-stu-id="d7b79-166">User experience</span></span>  
 <span data-ttu-id="d7b79-167">在伺服器上：</span><span class="sxs-lookup"><span data-stu-id="d7b79-167">On the server:</span></span>  
  
-   <span data-ttu-id="d7b79-168">您不需要變更伺服器 `ICalculator` 實作。</span><span class="sxs-lookup"><span data-stu-id="d7b79-168">The server `ICalculator` implementation does not need to change.</span></span>  
  
-   <span data-ttu-id="d7b79-169">服務的 App.config 必須使用自訂 POX 繫結，而這個繫結會將 `messageVersion` 項目的 `textMessageEncoding` 屬性設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="d7b79-169">The App.config for the service must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
-   <span data-ttu-id="d7b79-170">服務的 App.config 也必須指定自訂 `EnableHttpGetRequestsBehavior`，方法是新增至行為延伸區段之後再使用即可。</span><span class="sxs-lookup"><span data-stu-id="d7b79-170">The App.config for the service also must specify the custom `EnableHttpGetRequestsBehavior` by adding it to the behavior extensions section and using it.</span></span>  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="enableHttpGetRequestsBehavior">  
          <enableHttpGetRequests />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
    <extensions>  
      <behaviorExtensions>  
        <!-- Enabling HTTP GET requests: Behavior Extension -->  
        <add   
          name="enableHttpGetRequests"           type="Microsoft.ServiceModel.Samples.EnableHttpGetRequestsBehaviorElement, QueryStringFormatter, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
    ```  
  
-   <span data-ttu-id="d7b79-171">呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> 之前新增作業格式器。</span><span class="sxs-lookup"><span data-stu-id="d7b79-171">Add operation formatters before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
 <span data-ttu-id="d7b79-172">在用戶端上：</span><span class="sxs-lookup"><span data-stu-id="d7b79-172">On the client:</span></span>  
  
-   <span data-ttu-id="d7b79-173">您不需要變更用戶端實作。</span><span class="sxs-lookup"><span data-stu-id="d7b79-173">The client implementation does not need to change.</span></span>  
  
-   <span data-ttu-id="d7b79-174">用戶端的 App.config 必須使用自訂 POX 繫結，而這個繫結會將 `messageVersion` 項目的 `textMessageEncoding` 屬性設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="d7b79-174">The App.config for the client must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span> <span data-ttu-id="d7b79-175">與服務的某項差異為用戶端必須啟用手動定址，這樣才能修改傳出的收件者地址。</span><span class="sxs-lookup"><span data-stu-id="d7b79-175">One difference from the service is that the client must enable manual addressing so that the outgoing To address can be modified.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport manualAddressing="True" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
-   <span data-ttu-id="d7b79-176">用戶端的 App.config 必須指定和伺服器一樣的自訂 `EnableHttpGetRequestsBehavior`。</span><span class="sxs-lookup"><span data-stu-id="d7b79-176">The App.config for the client must specify the same custom `EnableHttpGetRequestsBehavior` as the server.</span></span>  
  
-   <span data-ttu-id="d7b79-177">呼叫 <xref:System.ServiceModel.ChannelFactory%601.CreateChannel> 之前新增作業格式器。</span><span class="sxs-lookup"><span data-stu-id="d7b79-177">Add operation formatters before calling <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span></span>  
  
 <span data-ttu-id="d7b79-178">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="d7b79-178">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="d7b79-179">這四個作業 (Add、Subtract、Multiply 和 Divide) 都必須成功。</span><span class="sxs-lookup"><span data-stu-id="d7b79-179">All four operations (Add, Subtract, Multiply, and Divide) must succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d7b79-180">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="d7b79-180">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d7b79-181">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="d7b79-181">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d7b79-182">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="d7b79-182">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d7b79-183">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="d7b79-183">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QuieryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d7b79-184">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="d7b79-184">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d7b79-185">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="d7b79-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d7b79-186">若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="d7b79-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d7b79-187">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="d7b79-187">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7b79-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7b79-188">See Also</span></span>
