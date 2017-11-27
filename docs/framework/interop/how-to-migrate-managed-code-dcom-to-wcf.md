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
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a>如何：將 Managed 程式碼 DCOM 移轉至 WCF
對於分散式環境中伺服器與用戶端之間的 Managed 程式碼呼叫，Windows Communication Foundation (WCF) 是比分散式元件物件模型 (DCOM) 更建議使用的安全選擇。 本文將說明如何在下列情節中將程式碼從 DCOM 移轉至 WCF。  
  
-   遠端服務以傳值方式將物件傳回給用戶端  
  
-   用戶端以傳值方式將物件傳送至遠端服務  
  
-   遠端服務以傳址方式將物件傳回給用戶端  
  
 基於安全性理由，在 WCF 中不允許以傳址方式將物件從用戶端傳送至服務。 如果需要在用戶端與伺服器之間來回溝通，可透過雙工服務在 WCF 中達成。  如需雙工服務的詳細資訊，請參閱[雙工服務](../../../docs/framework/wcf/feature-details/duplex-services.md)。  
  
 如需為那些服務建立 WCF 服務和用戶端的詳細資料，請參閱[基本 WCF 程式設計](../../../docs/framework/wcf/basic-wcf-programming.md)、[設計與實作服務](../../../docs/framework/wcf/designing-and-implementing-services.md)和[建置用戶端](../../../docs/framework/wcf/building-clients.md)。  
  
## <a name="dcom-example-code"></a>DCOM 範例程式碼  
 針對這些情節，使用 WCF 說明的 DCOM 介面有下列結構：  
  
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
  
## <a name="the-service-returns-an-object-by-value"></a>服務以傳值方式傳回物件  
 在此情節中，您呼叫服務，而它的物件會從伺服器以傳值方式將物件傳回給用戶端。 此情節代表下列 COM 呼叫：  
  
```  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 在此情節中，用戶端會收到來自遠端服務的已還原序列化物件複本。 用戶端可以與這個本機複本互動，而無需回呼服務。  換句話說，用戶端保證在呼叫本機複本上的方法時，將不會以任何方式影響到服務。 WCF 一律會以傳值方式從服務傳回物件，因此下列步驟說明如何建立一般 WCF 服務。  
  
### <a name="step-1-define-the-wcf-service-interface"></a>步驟 1：定義 WCF 服務介面  
 定義 WCF 服務的公用介面並以 [<xref:System.ServiceModel.ServiceContractAttribute>] 屬性標記。  將您想要公開給用戶端的方法以 [<xref:System.ServiceModel.OperationContractAttribute>] 屬性標記。 下列範例顯示使用這些屬性來識別伺服器端介面，以及用戶端可以呼叫的介面方法。 此情節中所使用的方法是以粗體顯示。  
  
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
  
### <a name="step-2-define-the-data-contract"></a>步驟 2：定義資料合約  
 接下來，您應該建立服務的資料合約，它將說明如何在服務及其用戶端之間交換資料。  資料合約中所述的類別應該以 [<xref:System.Runtime.Serialization.DataContractAttribute>] 屬性標記。 您想讓用戶端和伺服器所看到的個別屬性或欄位應該以 [<xref:System.Runtime.Serialization.DataMemberAttribute>] 屬性標記。如果您想允許從資料合約中的類別所衍生的類型，您必須以 [<xref:System.Runtime.Serialization.KnownTypeAttribute>] 屬性標記它們。 WCF 只會序列化或還原序列化服務介面中的類型和已識別為已知類型的類型。 如果您嘗試使用的類型不是已知的類型，會發生例外狀況。  
  
 如需資料合約的詳細資訊，請參閱[資料合約](../../../docs/framework/wcf/samples/data-contracts.md)。  
  
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
  
### <a name="step-3-implement-the-wcf-service"></a>步驟 3：實作 WCF 服務  
 接下來，您應該實作 WCF 服務類別，以實作您在上個步驟中定義的介面。  
  
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
  
### <a name="step-4-configure-the-service-and-the-client"></a>步驟 4：設定服務和用戶端  
 若要執行 WCF 服務，您需要宣告一個端點，這個端點會使用特定 WCF 繫結在特定 URL 上公開該服務介面。 繫結會指定用戶端與伺服器通訊用的傳輸、編碼和通訊協定詳細資料。 您通常會將繫結加入至服務專案的組態檔 (web.config)。 下列範例顯示範例服務的繫結項目：  
  
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
  
 接下來，您必須設定用戶端以符合服務所指定的繫結資訊。 若要這樣做，請將下列內容加入至用戶端應用程式組態檔 (app.config)。  
  
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
  
### <a name="step-5-run-the-service"></a>步驟 5：執行服務  
 最後，您可以將下列幾行加入到服務應用程式並啟動應用程式，以在主控台應用程式自我裝載它。 如需裝載 WCF 服務應用程式之其他方式的詳細資訊，請參閱[裝載服務](../../../docs/framework/wcf/hosting-services.md)。  
  
```  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a>步驟 6：從用戶端呼叫服務  
 若要從用戶端呼叫服務，您需要建立服務的通道處理站，並要求通道，這可讓您直接從用戶端呼叫 `GetCustomer` 方法。 通道會實作服務的介面並為您處理基礎要求/回覆邏輯。  從該方法呼叫傳回的值是服務回應的已還原序列化複本。  
  
```  
ChannelFactory<ICustomerManager> factory =   
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a>用戶端以傳值方式將物件傳送至伺服器  
 在此情節中，用戶端以傳值方式將物件傳送至伺服器。 這表示伺服器會收到物件的已還原序列化複本。  伺服器可以在該複本上呼叫方法，而且保證對用戶端程式碼沒有任何回呼。 如先前所述，一般 WCF 交換資料是使用傳值方式。  如此可保證在其中一個物件上呼叫方法的作業只會在本機執行，而不會在用戶端上呼叫程式碼。  
  
 此情節代表下列 COM 方法呼叫：  
  
```  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 此情節會使用與第一個範例所示相同的服務介面和資料合約。 此外，用戶端和服務也會以相同的方式設定。 在此範例中，會建立通道來以相同的方式傳送物件和執行。 不過，此範例中，您將建立呼叫服務的用戶端，並以傳值方式傳遞物件。 用戶端在服務合約中呼叫的服務方法會以粗體顯示：  
  
```  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a>將程式碼加入至以傳值方式傳送物件的用戶端  
 下列程式碼顯示用戶端如何建立新的傳值客戶物件、建立與 `ICustomerManager` 服務通訊的通道，並將客戶的物件傳送給它。  
  
 客戶物件會序列化並傳送至服務，在此處，服務會將其還原序列化為該物件的新複本。  服務在此物件上呼叫的任何方法都將只會在伺服器上本機執行。請務必注意，此程式碼說明傳送衍生類型 (`PremiumCustomer`)。  服務合約需要 `Customer` 物件，但服務資料合約使用 [<xref:System.Runtime.Serialization.KnownTypeAttribute>] 屬性來指出也允許 `PremiumCustomer`。  WCF 對於透過這個服務介面序列化或還原序列化其他任何類型所做的嘗試都將會失敗。  
  
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
  
## <a name="the-service-returns-an-object-by-reference"></a>服務以傳址方式傳回物件  
 在此情節中，用戶端應用程式會呼叫遠端服務，方法會以傳址方式從服務傳回物件到用戶端。  
  
 如先前所述，WCF 服務一律會以傳值方式傳回物件。  不過，您可以使用 <xref:System.ServiceModel.EndpointAddress10> 類別達成類似的結果。  <xref:System.ServiceModel.EndpointAddress10> 是可序列化的傳值物件，可供用戶端用來取得伺服器上的工作階段傳址物件。  
  
 在此情節中所示的 WCF 中傳址物件行為與 DCOM 不同。  在 DCOM 中，伺服器可以直接以傳址方式將物件傳回給用戶端，而用戶端可以呼叫該物件的方法，這些方法會在伺服器上執行。  不過，在 WCF 中一律是以傳值方式傳回物件。  用戶端必須接受該傳值物件 (以 <xref:System.ServiceModel.EndpointAddress10> 表示)，並用來建立自己的工作階段傳址物件。  工作階段物件上的用戶端方法呼叫會在伺服器上執行。換句話說，WCF 中的這個傳址物件是正常的 WCF 服務，其已設定為可以有工作階段。  
  
 在 WCF 中，工作階段是將兩個端點之間傳送的多個訊息相互關聯的方式。  這表示一旦用戶端取得此服務的連接，便會在用戶端與伺服器之間建立工作階段。  用戶端會針對這個工作階段內的所有互動，使用伺服器端物件的唯一執行個體。 工作階段的 WCF 合約類似於連線導向的網路要求/回應模式。  
  
 此情節由下列 DCOM 方法代表。  
  
```  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a>步驟 1：定義工作階段 WCF 服務介面與實作  
 首先，定義包含工作階段物件的 WCF 服務介面。  
  
 在此程式碼中，工作階段物件會以 `ServiceContract` 屬性標記，它會識別為一般 WCF 服務介面。  此外，<xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> 屬性會設定成表示它會是具有工作階段的服務。  
  
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
  
 下列程式碼顯示服務實作。  
  
 服務以 [ServiceBehavior] 屬性標記，且其 InstanceContextMode 屬性設定為 InstanceContextMode.PerSessions 以指出應該為每個工作階段建立此類型的唯一執行個體。  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a>步驟 2：定義工作階段物件的 WCF 處理站服務  
 建立工作階段物件的服務必須定義並實作。 下列程式碼示範如何執行這項操作。 此程式碼會建立另一個 WCF 服務，傳回 <xref:System.ServiceModel.EndpointAddress10> 物件。  這是端點的可序列化形式，可用來建立工作階段物件。  
  
```  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 以下是此服務的實作： 這個實作會維護單一通道處理站來建立工作階段物件。  呼叫 `GetInstanceAddress` 時，它會建立通道，並建立指向與這個通道關聯之遠端位址的 <xref:System.ServiceModel.EndpointAddress10> 物件。   <xref:System.ServiceModel.EndpointAddress10> 是能夠以傳值方式傳回至用戶端的資料類型。  
  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a>步驟 3：設定並啟動 WCF 服務  
 若要裝載這些服務，您必須在伺服器的組態檔 (web.config) 加入下列內容。  
  
1.  加入宣告描述工作階段物件端點的 `<client>` 區段。  在此情節中，伺服器也做為用戶端，並必須設定為啟用此設定。  
  
2.  在 `<services>` 區段中，宣告處理站和工作階段物件的服務端點。  這可讓用戶端與服務端點進行通訊、 取得 <xref:System.ServiceModel.EndpointAddress10> 並建立工作階段通道。  
  
 以下是具有這些設定的範例組態檔：  
  
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
  
 將下列幾行加入至主控台應用程式，以自我裝載服務，並啟動應用程式。  
  
```  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a>步驟 4：設定用戶端並呼叫服務  
 藉由在專案的應用程式組態檔 (app.config) 加入下列項目，設定用戶端與 WCF 服務進行通訊。  
  
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
  
 若要呼叫服務，請將程式碼加入用戶端以執行下列動作：  
  
1.  建立 `ISessionBoundFactory` 服務的通道。  
  
2.  使用通道來呼叫 `ISessionBoundFactory` 服務，並取得 <xref:System.ServiceModel.EndpointAddress10> 物件。  
  
3.  使用 <xref:System.ServiceModel.EndpointAddress10> 建立通道，以取得工作階段物件。  
  
4.  呼叫 `SetCurrentValue` 和 `GetCurrentValue` 方法，以示範仍會保持在多個呼叫之間使用相同的物件執行個體。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [基本 WCF 程式設計](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [設計與實作服務](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [建置用戶端](../../../docs/framework/wcf/building-clients.md)  
 [雙工服務](../../../docs/framework/wcf/feature-details/duplex-services.md)
