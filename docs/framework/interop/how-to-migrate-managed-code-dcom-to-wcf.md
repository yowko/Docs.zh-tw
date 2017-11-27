---
title: "如何：將 Managed 程式碼 DCOM 移轉至 WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: af401cafe0740dcd9a313ae9143f9772605137d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a><span data-ttu-id="5d2ee-102">如何：將 Managed 程式碼 DCOM 移轉至 WCF</span><span class="sxs-lookup"><span data-stu-id="5d2ee-102">How to: Migrate Managed-Code DCOM to WCF</span></span>
<span data-ttu-id="5d2ee-103">對於分散式環境中伺服器與用戶端之間的 Managed 程式碼呼叫，Windows Communication Foundation (WCF) 是比分散式元件物件模型 (DCOM) 更建議使用的安全選擇。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-103">Windows Communication Foundation (WCF) is the recommended and secure choice over Distributed Component Object Model (DCOM) for managed code calls between servers and clients in a distributed environment.</span></span> <span data-ttu-id="5d2ee-104">本文將說明如何在下列情節中將程式碼從 DCOM 移轉至 WCF。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-104">This article shows how you to migrate code from DCOM to WCF for the following scenarios.</span></span>  
  
-   <span data-ttu-id="5d2ee-105">遠端服務以傳值方式將物件傳回給用戶端</span><span class="sxs-lookup"><span data-stu-id="5d2ee-105">The remote service returns an object by-value to the client</span></span>  
  
-   <span data-ttu-id="5d2ee-106">用戶端以傳值方式將物件傳送至遠端服務</span><span class="sxs-lookup"><span data-stu-id="5d2ee-106">The client sends an object by-value to the remote service</span></span>  
  
-   <span data-ttu-id="5d2ee-107">遠端服務以傳址方式將物件傳回給用戶端</span><span class="sxs-lookup"><span data-stu-id="5d2ee-107">The remote service returns an object by-reference to the client</span></span>  
  
 <span data-ttu-id="5d2ee-108">基於安全性理由，在 WCF 中不允許以傳址方式將物件從用戶端傳送至服務。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-108">For security reasons, sending an object by-reference from the client to the service is not allowed in WCF.</span></span> <span data-ttu-id="5d2ee-109">如果需要在用戶端與伺服器之間來回溝通，可透過雙工服務在 WCF 中達成。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-109">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span>  <span data-ttu-id="5d2ee-110">如需雙工服務的詳細資訊，請參閱[雙工服務](../../../docs/framework/wcf/feature-details/duplex-services.md)。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-110">For more information about duplex services, see [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="5d2ee-111">如需為那些服務建立 WCF 服務和用戶端的詳細資料，請參閱[基本 WCF 程式設計](../../../docs/framework/wcf/basic-wcf-programming.md)、[設計與實作服務](../../../docs/framework/wcf/designing-and-implementing-services.md)和[建置用戶端](../../../docs/framework/wcf/building-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-111">For more details about creating WCF services and clients for those services, see [Basic WCF Programming](../../../docs/framework/wcf/basic-wcf-programming.md), [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md), and [Building Clients](../../../docs/framework/wcf/building-clients.md).</span></span>  
  
## <a name="dcom-example-code"></a><span data-ttu-id="5d2ee-112">DCOM 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="5d2ee-112">DCOM example code</span></span>  
 <span data-ttu-id="5d2ee-113">針對這些情節，使用 WCF 說明的 DCOM 介面有下列結構：</span><span class="sxs-lookup"><span data-stu-id="5d2ee-113">For these scenarios, the DCOM interfaces that are illustrated using WCF have the following structure:</span></span>  
  
```  
[ComVisible(true)]  
[Guid("AA9C4CDB-55EA-4413-90D2-843F1A49E6E6")]  
public interface IRemoteService  
{  
   Customer GetObjectByValue();  
   IRemoteObject GetObjectByReference();  
   void SendObjectByValue(Customer customer);  
}  
  
[ComVisible(true)]  
[Guid("A12C98DE-B6A1-463D-8C24-81E4BBC4351B")]  
public interface IRemoteObject  
{  
}  
  
public class Customer  
{  
}  
```  
  
## <a name="the-service-returns-an-object-by-value"></a><span data-ttu-id="5d2ee-114">服務以傳值方式傳回物件</span><span class="sxs-lookup"><span data-stu-id="5d2ee-114">The service returns an object by-value</span></span>  
 <span data-ttu-id="5d2ee-115">在此情節中，您呼叫服務，而它的物件會從伺服器以傳值方式將物件傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-115">For this scenario, you make a call to a service and it method returns an object, which is passed by-value from the server to the client.</span></span> <span data-ttu-id="5d2ee-116">此情節代表下列 COM 呼叫：</span><span class="sxs-lookup"><span data-stu-id="5d2ee-116">This scenario represents the following COM call:</span></span>  
  
```  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 <span data-ttu-id="5d2ee-117">在此情節中，用戶端會收到來自遠端服務的已還原序列化物件複本。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-117">In this scenario, the client receives a deserialized copy of an object from the remote service.</span></span> <span data-ttu-id="5d2ee-118">用戶端可以與這個本機複本互動，而無需回呼服務。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-118">The client can interact with this local copy without calling back to the service.</span></span>  <span data-ttu-id="5d2ee-119">換句話說，用戶端保證在呼叫本機複本上的方法時，將不會以任何方式影響到服務。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-119">In other words, the client is guaranteed the service will not be involved in any way when methods on the local copy are called.</span></span> <span data-ttu-id="5d2ee-120">WCF 一律會以傳值方式從服務傳回物件，因此下列步驟說明如何建立一般 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-120">WCF always returns objects from the service by value, so the following steps describe creating a regular WCF service.</span></span>  
  
### <a name="step-1-define-the-wcf-service-interface"></a><span data-ttu-id="5d2ee-121">步驟 1：定義 WCF 服務介面</span><span class="sxs-lookup"><span data-stu-id="5d2ee-121">Step 1: Define the WCF service interface</span></span>  
 <span data-ttu-id="5d2ee-122">定義 WCF 服務的公用介面並以 [<xref:System.ServiceModel.ServiceContractAttribute>] 屬性標記。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-122">Define a public interface for the WCF service and mark it with the [<xref:System.ServiceModel.ServiceContractAttribute>] attribute.</span></span>  <span data-ttu-id="5d2ee-123">將您想要公開給用戶端的方法以 [<xref:System.ServiceModel.OperationContractAttribute>] 屬性標記。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-123">Mark the methods you want to expose to clients with the [<xref:System.ServiceModel.OperationContractAttribute>] attribute.</span></span> <span data-ttu-id="5d2ee-124">下列範例顯示使用這些屬性來識別伺服器端介面，以及用戶端可以呼叫的介面方法。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-124">The following example shows using these attributes to identify the server-side interface and interface methods a client can call.</span></span> <span data-ttu-id="5d2ee-125">此情節中所使用的方法是以粗體顯示。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-125">The method used for this scenario is shown in bold.</span></span>  
  
```  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Web;   
. . .  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]  
    void StoreCustomer(Customer customer);  
  
    [OperationContract]     Customer GetCustomer(string firstName, string lastName);   
  
}  
```  
  
### <a name="step-2-define-the-data-contract"></a><span data-ttu-id="5d2ee-126">步驟 2：定義資料合約</span><span class="sxs-lookup"><span data-stu-id="5d2ee-126">Step 2: Define the data contract</span></span>  
 <span data-ttu-id="5d2ee-127">接下來，您應該建立服務的資料合約，它將說明如何在服務及其用戶端之間交換資料。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-127">Next you should create a data contract for the service, which will describe how the data will be exchanged between the service and its clients.</span></span>  <span data-ttu-id="5d2ee-128">資料合約中所述的類別應該以 [<xref:System.Runtime.Serialization.DataContractAttribute>] 屬性標記。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-128">Classes described in the data contract should be marked with the [<xref:System.Runtime.Serialization.DataContractAttribute>] attribute.</span></span> <span data-ttu-id="5d2ee-129">您想讓用戶端和伺服器所看到的個別屬性或欄位應該以 [<xref:System.Runtime.Serialization.DataMemberAttribute>] 屬性標記。如果您想允許從資料合約中的類別所衍生的類型，您必須以 [<xref:System.Runtime.Serialization.KnownTypeAttribute>] 屬性標記它們。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-129">The individual properties or fields you want visible to both client and server should be marked with the [<xref:System.Runtime.Serialization.DataMemberAttribute>] attribute.If you want types derived from a class in the data contract to be allowed, you must identify them with the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute.</span></span> <span data-ttu-id="5d2ee-130">WCF 只會序列化或還原序列化服務介面中的類型和已識別為已知類型的類型。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-130">WCF will only serialize or deserialize types in the service interface and types identified as known types.</span></span> <span data-ttu-id="5d2ee-131">如果您嘗試使用的類型不是已知的類型，會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-131">If you attempt to use a type that is not a known type, an exception will occur.</span></span>  
  
 <span data-ttu-id="5d2ee-132">如需資料合約的詳細資訊，請參閱[資料合約](../../../docs/framework/wcf/samples/data-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-132">For more information about data contracts, see [Data Contracts](../../../docs/framework/wcf/samples/data-contracts.md).</span></span>  
  
```  
[DataContract]  
[KnownType(typeof(PremiumCustomer))]  
public class Customer  
{  
    [DataMember]  
    public string Firstname;  
    [DataMember]  
    public string Lastname;  
    [DataMember]  
    public Address DefaultDeliveryAddress;  
    [DataMember]  
    public Address DefaultBillingAddress;  
}  
 [DataContract]  
public class PremiumCustomer : Customer  
{  
    [DataMember]  
    public int AccountID;  
}  
  
 [DataContract]  
public class Address  
{  
    [DataMember]  
    public string Street;  
    [DataMember]  
    public string Zipcode;  
    [DataMember]  
    public string City;  
    [DataMember]  
    public string State;  
    [DataMember]  
    public string Country;  
}  
```  
  
### <a name="step-3-implement-the-wcf-service"></a><span data-ttu-id="5d2ee-133">步驟 3：實作 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="5d2ee-133">Step 3: Implement the WCF service</span></span>  
 <span data-ttu-id="5d2ee-134">接下來，您應該實作 WCF 服務類別，以實作您在上個步驟中定義的介面。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-134">Next, you should implement the WCF service class that implements the interface you defined in the previous step.</span></span>  
  
```  
public class CustomerService: ICustomerManager    
{  
    public void StoreCustomer(Customer customer)  
    {  
        // write to a database  
    }  
    public Customer GetCustomer(string firstName, string lastName)  
    {  
        // read from a database  
    }  
}  
```  
  
### <a name="step-4-configure-the-service-and-the-client"></a><span data-ttu-id="5d2ee-135">步驟 4：設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="5d2ee-135">Step 4: Configure the service and the client</span></span>  
 <span data-ttu-id="5d2ee-136">若要執行 WCF 服務，您需要宣告一個端點，這個端點會使用特定 WCF 繫結在特定 URL 上公開該服務介面。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-136">To run a WCF service, you need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="5d2ee-137">繫結會指定用戶端與伺服器通訊用的傳輸、編碼和通訊協定詳細資料。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-137">A binding specifies the transport, encoding and protocol details for the clients and server to communicate.</span></span> <span data-ttu-id="5d2ee-138">您通常會將繫結加入至服務專案的組態檔 (web.config)。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-138">You typically add bindings to the service project’s configuration file (web.config).</span></span> <span data-ttu-id="5d2ee-139">下列範例顯示範例服務的繫結項目：</span><span class="sxs-lookup"><span data-stu-id="5d2ee-139">The following shows a binding entry for the example service:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Server.CustomerService">  
        <endpoint address="http://localhost:8083/CustomerManager"   
                  binding="basicHttpBinding"  
                  contract="Shared.ICustomerManager" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="5d2ee-140">接下來，您必須設定用戶端以符合服務所指定的繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-140">Next, you need to configure the client to match the binding information specified by the service.</span></span> <span data-ttu-id="5d2ee-141">若要這樣做，請將下列內容加入至用戶端應用程式組態檔 (app.config)。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-141">To do so, add the following to the client’s application configuration (app.config) file.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="customermanager"   
                address="http://localhost:8083/CustomerManager"   
                binding="basicHttpBinding"   
                contract="Shared.ICustomerManager"/>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="step-5-run-the-service"></a><span data-ttu-id="5d2ee-142">步驟 5：執行服務</span><span class="sxs-lookup"><span data-stu-id="5d2ee-142">Step 5: Run the service</span></span>  
 <span data-ttu-id="5d2ee-143">最後，您可以將下列幾行加入到服務應用程式並啟動應用程式，以在主控台應用程式自我裝載它。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-143">Finally, you can self-host it in a console application by adding the following lines to the service app, and starting the app.</span></span> <span data-ttu-id="5d2ee-144">如需裝載 WCF 服務應用程式之其他方式的詳細資訊，請參閱[裝載服務](../../../docs/framework/wcf/hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-144">For more information about other ways to host a WCF service application, [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
```  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a><span data-ttu-id="5d2ee-145">步驟 6：從用戶端呼叫服務</span><span class="sxs-lookup"><span data-stu-id="5d2ee-145">Step 6: Call the service from the client</span></span>  
 <span data-ttu-id="5d2ee-146">若要從用戶端呼叫服務，您需要建立服務的通道處理站，並要求通道，這可讓您直接從用戶端呼叫 `GetCustomer` 方法。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-146">To call the service from the client, you need to create a channel factory for the service, and request a channel, which will enable you to directly call the `GetCustomer` method directly from the client.</span></span> <span data-ttu-id="5d2ee-147">通道會實作服務的介面並為您處理基礎要求/回覆邏輯。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-147">The channel implements the service’s interface and handles the underlying request/reply logic for you.</span></span>  <span data-ttu-id="5d2ee-148">從該方法呼叫傳回的值是服務回應的已還原序列化複本。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-148">The return value from that method call is the deserialized copy of the service response.</span></span>  
  
```  
ChannelFactory<ICustomerManager> factory =   
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a><span data-ttu-id="5d2ee-149">用戶端以傳值方式將物件傳送至伺服器</span><span class="sxs-lookup"><span data-stu-id="5d2ee-149">The client sends a by-value object to the server</span></span>  
 <span data-ttu-id="5d2ee-150">在此情節中，用戶端以傳值方式將物件傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-150">In this scenario, the client sends an object to the server, by-value.</span></span> <span data-ttu-id="5d2ee-151">這表示伺服器會收到物件的已還原序列化複本。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-151">This means that the server will receive a deserialized copy of the object.</span></span>  <span data-ttu-id="5d2ee-152">伺服器可以在該複本上呼叫方法，而且保證對用戶端程式碼沒有任何回呼。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-152">The server can call methods on that copy and be guaranteed there is no callback into client code.</span></span> <span data-ttu-id="5d2ee-153">如先前所述，一般 WCF 交換資料是使用傳值方式。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-153">As mentioned previously, normal WCF exchanges of data are by-value.</span></span>  <span data-ttu-id="5d2ee-154">如此可保證在其中一個物件上呼叫方法的作業只會在本機執行，而不會在用戶端上呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-154">This guarantees that calling methods on one of these objects executes locally only – it will not invoke code on the client.</span></span>  
  
 <span data-ttu-id="5d2ee-155">此情節代表下列 COM 方法呼叫：</span><span class="sxs-lookup"><span data-stu-id="5d2ee-155">This scenario represents the following COM method call:</span></span>  
  
```  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 <span data-ttu-id="5d2ee-156">此情節會使用與第一個範例所示相同的服務介面和資料合約。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-156">This scenario uses the same service interface and data contract as shown in the first example.</span></span> <span data-ttu-id="5d2ee-157">此外，用戶端和服務也會以相同的方式設定。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-157">In addition, the client and service will be configured in the same way.</span></span> <span data-ttu-id="5d2ee-158">在此範例中，會建立通道來以相同的方式傳送物件和執行。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-158">In this example, a channel is created to send the object and run the same way.</span></span> <span data-ttu-id="5d2ee-159">不過，此範例中，您將建立呼叫服務的用戶端，並以傳值方式傳遞物件。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-159">However, for this example, you will create a client that calls the service, passing an object by-value.</span></span> <span data-ttu-id="5d2ee-160">用戶端在服務合約中呼叫的服務方法會以粗體顯示：</span><span class="sxs-lookup"><span data-stu-id="5d2ee-160">The service method the client will call in the service contract is shown in bold:</span></span>  
  
```  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a><span data-ttu-id="5d2ee-161">將程式碼加入至以傳值方式傳送物件的用戶端</span><span class="sxs-lookup"><span data-stu-id="5d2ee-161">Add code to the client that sends a by-value object</span></span>  
 <span data-ttu-id="5d2ee-162">下列程式碼顯示用戶端如何建立新的傳值客戶物件、建立與 `ICustomerManager` 服務通訊的通道，並將客戶的物件傳送給它。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-162">The following code shows how the client creates a new by-value customer object, creates a channel to communicate with the `ICustomerManager` service, and sends the customer object to it.</span></span>  
  
 <span data-ttu-id="5d2ee-163">客戶物件會序列化並傳送至服務，在此處，服務會將其還原序列化為該物件的新複本。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-163">The customer object will be serialized, and sent to the service, where it is deserialized by the service into a new copy of that object.</span></span>  <span data-ttu-id="5d2ee-164">服務在此物件上呼叫的任何方法都將只會在伺服器上本機執行。請務必注意，此程式碼說明傳送衍生類型 (`PremiumCustomer`)。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-164">Any methods the service calls on this object will execute only locally on the server.It’s important to note that this code illustrates sending a derived type (`PremiumCustomer`).</span></span>  <span data-ttu-id="5d2ee-165">服務合約需要 `Customer` 物件，但服務資料合約使用 [<xref:System.Runtime.Serialization.KnownTypeAttribute>] 屬性來指出也允許 `PremiumCustomer`。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-165">The service contract expects a `Customer` object, but the service data contract uses the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute to indicate that `PremiumCustomer` is also allowed.</span></span>  <span data-ttu-id="5d2ee-166">WCF 對於透過這個服務介面序列化或還原序列化其他任何類型所做的嘗試都將會失敗。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-166">WCF will fail attempts to serialize or deserialize any other type via this service interface.</span></span>  
  
```  
PremiumCustomer customer = new PremiumCustomer();  
customer.Firstname = "John";  
customer.Lastname = "Doe";  
customer.DefaultBillingAddress = new Address();  
customer.DefaultBillingAddress.Street = "One Microsoft Way";  
customer.DefaultDeliveryAddress = customer.DefaultBillingAddress;  
customer.AccountID = 42;  
  
ChannelFactory<ICustomerManager> factory =  
   new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager customerManager = factory.CreateChannel();  
customerManager.StoreCustomer(customer);  
```  
  
## <a name="the-service-returns-an-object-by-reference"></a><span data-ttu-id="5d2ee-167">服務以傳址方式傳回物件</span><span class="sxs-lookup"><span data-stu-id="5d2ee-167">The service returns an object by reference</span></span>  
 <span data-ttu-id="5d2ee-168">在此情節中，用戶端應用程式會呼叫遠端服務，方法會以傳址方式從服務傳回物件到用戶端。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-168">For this scenario, the client app makes a call to the remote service and the method returns an object, which is passed by reference from the service to the client.</span></span>  
  
 <span data-ttu-id="5d2ee-169">如先前所述，WCF 服務一律會以傳值方式傳回物件。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-169">As mentioned previously, WCF services always return object by value.</span></span>  <span data-ttu-id="5d2ee-170">不過，您可以使用 <xref:System.ServiceModel.EndpointAddress10> 類別達成類似的結果。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-170">However, you can achieve a similar result by using the <xref:System.ServiceModel.EndpointAddress10> class.</span></span>  <span data-ttu-id="5d2ee-171"><xref:System.ServiceModel.EndpointAddress10> 是可序列化的傳值物件，可供用戶端用來取得伺服器上的工作階段傳址物件。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-171">The <xref:System.ServiceModel.EndpointAddress10> is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span>  
  
 <span data-ttu-id="5d2ee-172">在此情節中所示的 WCF 中傳址物件行為與 DCOM 不同。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-172">The behavior of the by-reference object in WCF shown in this scenario is different than DCOM.</span></span>  <span data-ttu-id="5d2ee-173">在 DCOM 中，伺服器可以直接以傳址方式將物件傳回給用戶端，而用戶端可以呼叫該物件的方法，這些方法會在伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-173">In DCOM, the server can return a by-reference object to the client directly, and the client can call that object’s methods, which execute on the server.</span></span>  <span data-ttu-id="5d2ee-174">不過，在 WCF 中一律是以傳值方式傳回物件。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-174">In WCF, however, the object returned is always by-value.</span></span>  <span data-ttu-id="5d2ee-175">用戶端必須接受該傳值物件 (以 <xref:System.ServiceModel.EndpointAddress10> 表示)，並用來建立自己的工作階段傳址物件。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-175">The client must take that by-value object, represented by <xref:System.ServiceModel.EndpointAddress10> and use it to create its own sessionful by-reference object.</span></span>  <span data-ttu-id="5d2ee-176">工作階段物件上的用戶端方法呼叫會在伺服器上執行。換句話說，WCF 中的這個傳址物件是正常的 WCF 服務，其已設定為可以有工作階段。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-176">The client method calls on the sessionful object execute on the server.In other words, this by-reference object in WCF is a normal WCF service that is configured to be sessionful.</span></span>  
  
 <span data-ttu-id="5d2ee-177">在 WCF 中，工作階段是將兩個端點之間傳送的多個訊息相互關聯的方式。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-177">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span>  <span data-ttu-id="5d2ee-178">這表示一旦用戶端取得此服務的連接，便會在用戶端與伺服器之間建立工作階段。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-178">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span>  <span data-ttu-id="5d2ee-179">用戶端會針對這個工作階段內的所有互動，使用伺服器端物件的唯一執行個體。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-179">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span> <span data-ttu-id="5d2ee-180">工作階段的 WCF 合約類似於連線導向的網路要求/回應模式。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-180">Sessionful WCF contracts are similar to connection-oriented network request/response patterns.</span></span>  
  
 <span data-ttu-id="5d2ee-181">此情節由下列 DCOM 方法代表。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-181">This scenario is represented by the following DCOM method.</span></span>  
  
```  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a><span data-ttu-id="5d2ee-182">步驟 1：定義工作階段 WCF 服務介面與實作</span><span class="sxs-lookup"><span data-stu-id="5d2ee-182">Step 1: Define the Sessionful WCF service interface and implementation</span></span>  
 <span data-ttu-id="5d2ee-183">首先，定義包含工作階段物件的 WCF 服務介面。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-183">First, define a WCF service interface that contains the sessionful object.</span></span>  
  
 <span data-ttu-id="5d2ee-184">在此程式碼中，工作階段物件會以 `ServiceContract` 屬性標記，它會識別為一般 WCF 服務介面。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-184">In this code, the sessionful object is marked with the `ServiceContract` attribute, which identifies it as a regular WCF service interface.</span></span>  <span data-ttu-id="5d2ee-185">此外，<xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> 屬性會設定成表示它會是具有工作階段的服務。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-185">In addition, the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> property is set to indicate it will be a sessionful service.</span></span>  
  
```  
[ServiceContract(SessionMode = SessionMode.Allowed)]  
public interface ISessionBoundObject  
{  
    [OperationContract]  
    string GetCurrentValue();  
  
    [OperationContract]  
    void SetCurrentValue(string value);  
}  
```  
  
 <span data-ttu-id="5d2ee-186">下列程式碼顯示服務實作。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-186">The following code shows the service implementation.</span></span>  
  
 <span data-ttu-id="5d2ee-187">服務以 [ServiceBehavior] 屬性標記，且其 InstanceContextMode 屬性設定為 InstanceContextMode.PerSessions 以指出應該為每個工作階段建立此類型的唯一執行個體。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-187">The service is marked with the [ServiceBehavior] attribute, and its InstanceContextMode property set to InstanceContextMode.PerSessions to indicate that a unique instance of this type should be created for each session.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
    public class MySessionBoundObject : ISessionBoundObject  
    {  
        private string _value;  
  
        public string GetCurrentValue()  
        {  
            return _value;  
        }  
  
        public void SetCurrentValue(string val)  
        {  
            _value = val;  
        }  
  
    }  
```  
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a><span data-ttu-id="5d2ee-188">步驟 2：定義工作階段物件的 WCF 處理站服務</span><span class="sxs-lookup"><span data-stu-id="5d2ee-188">Step 2: Define the WCF factory service for the sessionful object</span></span>  
 <span data-ttu-id="5d2ee-189">建立工作階段物件的服務必須定義並實作。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-189">The service that creates the sessionful object must be defined and implemented.</span></span> <span data-ttu-id="5d2ee-190">下列程式碼示範如何執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-190">The following code shows how to do this.</span></span> <span data-ttu-id="5d2ee-191">此程式碼會建立另一個 WCF 服務，傳回 <xref:System.ServiceModel.EndpointAddress10> 物件。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-191">This code creates another WCF service that returns an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  <span data-ttu-id="5d2ee-192">這是端點的可序列化形式，可用來建立工作階段物件。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-192">This is a serializable form of an endpoint the can use to create the session-full object.</span></span>  
  
```  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 <span data-ttu-id="5d2ee-193">以下是此服務的實作：</span><span class="sxs-lookup"><span data-stu-id="5d2ee-193">Following is the implementation of this service.</span></span> <span data-ttu-id="5d2ee-194">這個實作會維護單一通道處理站來建立工作階段物件。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-194">This implementation maintains a singleton channel factory to create sessionful objects.</span></span>  <span data-ttu-id="5d2ee-195">呼叫 `GetInstanceAddress` 時，它會建立通道，並建立指向與這個通道關聯之遠端位址的 <xref:System.ServiceModel.EndpointAddress10> 物件。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-195">When `GetInstanceAddress` is called, it creates a channel and creates an <xref:System.ServiceModel.EndpointAddress10> object that points to the remote address associated with this channel.</span></span>   <span data-ttu-id="5d2ee-196"><xref:System.ServiceModel.EndpointAddress10> 是能夠以傳值方式傳回至用戶端的資料類型。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-196"><xref:System.ServiceModel.EndpointAddress10> is a data type that can be returned to the client by-value.</span></span>  
  
```  
public class SessionBoundFactory : ISessionBoundFactory  
    {  
        public static ChannelFactory<ISessionBoundObject> _factory =   
            new ChannelFactory<ISessionBoundObject>("sessionbound");  
  
        public SessionBoundFactory()  
        {  
        }  
  
        public EndpointAddress10 GetInstanceAddress()  
        {  
            IClientChannel channel = (IClientChannel)_factory.CreateChannel();  
            return EndpointAddress10.FromEndpointAddress(channel.RemoteAddress);  
        }  
    }  
```  
  
### <a name="step-3-configure-and-start-the-wcf-services"></a><span data-ttu-id="5d2ee-197">步驟 3：設定並啟動 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="5d2ee-197">Step 3: Configure and start the WCF services</span></span>  
 <span data-ttu-id="5d2ee-198">若要裝載這些服務，您必須在伺服器的組態檔 (web.config) 加入下列內容。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-198">To host these services, you will need to make the following additions to the server’s configuration file (web.config).</span></span>  
  
1.  <span data-ttu-id="5d2ee-199">加入宣告描述工作階段物件端點的 `<client>` 區段。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-199">Add a `<client>` section that describes the endpoint for the sessionful object.</span></span>  <span data-ttu-id="5d2ee-200">在此情節中，伺服器也做為用戶端，並必須設定為啟用此設定。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-200">In this scenario, the server also acts as a client and must be configured to enable this.</span></span>  
  
2.  <span data-ttu-id="5d2ee-201">在 `<services>` 區段中，宣告處理站和工作階段物件的服務端點。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-201">In the `<services>` section, declare service endpoints for the factory and sessionful object.</span></span>  <span data-ttu-id="5d2ee-202">這可讓用戶端與服務端點進行通訊、 取得 <xref:System.ServiceModel.EndpointAddress10> 並建立工作階段通道。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-202">This enables the client to communicate with the service endpoints, acquire the <xref:System.ServiceModel.EndpointAddress10> and create the sessionful channel.</span></span>  
  
 <span data-ttu-id="5d2ee-203">以下是具有這些設定的範例組態檔：</span><span class="sxs-lookup"><span data-stu-id="5d2ee-203">Following is an example configuration file with these settings:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="sessionbound"  
                address="net.tcp://localhost:8081/SessionBoundObject"  
                binding="netTcpBinding"  
                contract="Shared.ISessionBoundObject"/>  
    </client>  
  
    <services>  
      <service name="Server.MySessionBoundObject">  
        <endpoint address="net.tcp://localhost:8081/SessionBoundObject"  
                  binding="netTcpBinding"   
                  contract="Shared.ISessionBoundObject" />  
      </service>  
      <service name="Server.SessionBoundFactory">  
        <endpoint address="net.tcp://localhost:8081/SessionBoundFactory"  
                  binding="netTcpBinding"   
                  contract="Shared.ISessionBoundFactory" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="5d2ee-204">將下列幾行加入至主控台應用程式，以自我裝載服務，並啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-204">Add the following lines to a console application, to self-host the service, and start the app.</span></span>  
  
```  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a><span data-ttu-id="5d2ee-205">步驟 4：設定用戶端並呼叫服務</span><span class="sxs-lookup"><span data-stu-id="5d2ee-205">Step 4: Configure the client and call the service</span></span>  
 <span data-ttu-id="5d2ee-206">藉由在專案的應用程式組態檔 (app.config) 加入下列項目，設定用戶端與 WCF 服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-206">Configure the client to communicate with the WCF services by making the following entries in the project’s application configuration file (app.config).</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="sessionbound"   
                address="net.tcp://localhost:8081/SessionBoundObject"   
                binding="netTcpBinding"   
                contract="Shared.ISessionBoundObject"/>  
      <endpoint name="factory"   
                address="net.tcp://localhost:8081/SessionBoundFactory"   
                binding="netTcpBinding"   
                contract="Shared.ISessionBoundFactory"/>  
    </client>    
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="5d2ee-207">若要呼叫服務，請將程式碼加入用戶端以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="5d2ee-207">To call the service, add the code to the client to do the following:</span></span>  
  
1.  <span data-ttu-id="5d2ee-208">建立 `ISessionBoundFactory` 服務的通道。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-208">Create a channel to the `ISessionBoundFactory` service.</span></span>  
  
2.  <span data-ttu-id="5d2ee-209">使用通道來呼叫 `ISessionBoundFactory` 服務，並取得 <xref:System.ServiceModel.EndpointAddress10> 物件。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-209">Use the channel to invoke the `ISessionBoundFactory` service an obtain an <xref:System.ServiceModel.EndpointAddress10> bbject.</span></span>  
  
3.  <span data-ttu-id="5d2ee-210">使用 <xref:System.ServiceModel.EndpointAddress10> 建立通道，以取得工作階段物件。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-210">Use the <xref:System.ServiceModel.EndpointAddress10> to create a channel to obtain a sessionful object.</span></span>  
  
4.  <span data-ttu-id="5d2ee-211">呼叫 `SetCurrentValue` 和 `GetCurrentValue` 方法，以示範仍會保持在多個呼叫之間使用相同的物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="5d2ee-211">Call the `SetCurrentValue` and `GetCurrentValue` methods to demonstrate it remains the same object instance is used across multiple calls.</span></span>  
  
```  
ChannelFactory<ISessionBoundFactory> factory =  
        new ChannelFactory<ISessionBoundFactory>("factory");  
  
ISessionBoundFactory sessionBoundFactory = factory.CreateChannel();  
  
EndpointAddress10 address = sessionBoundFactory.GetInstanceAddress();  
  
ChannelFactory<ISessionBoundObject> sessionBoundObjectFactory =  
    new ChannelFactory<ISessionBoundObject>(  
        new NetTcpBinding(),  
        address.ToEndpointAddress());  
  
ISessionBoundObject sessionBoundObject =  
        sessionBoundObjectFactory.CreateChannel();  
  
sessionBoundObject.SetCurrentValue("Hello");  
if (sessionBoundObject.GetCurrentValue() == "Hello")  
{  
    Console.WriteLine("Session-full instance management works as expected");  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d2ee-212">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d2ee-212">See Also</span></span>  
 [<span data-ttu-id="5d2ee-213">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="5d2ee-213">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="5d2ee-214">設計與實作服務</span><span class="sxs-lookup"><span data-stu-id="5d2ee-214">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [<span data-ttu-id="5d2ee-215">建置用戶端</span><span class="sxs-lookup"><span data-stu-id="5d2ee-215">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
 [<span data-ttu-id="5d2ee-216">雙工服務</span><span class="sxs-lookup"><span data-stu-id="5d2ee-216">Duplex Services</span></span>](../../../docs/framework/wcf/feature-details/duplex-services.md)
