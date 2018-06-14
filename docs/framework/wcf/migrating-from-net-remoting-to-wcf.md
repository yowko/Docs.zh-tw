---
title: 從 .NET 遠端處理移轉到 WCF
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: 6041cd9ac066d932811cc489222c8cbf03debb75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509134"
---
# <a name="migrating-from-net-remoting-to-wcf"></a>從 .NET 遠端處理移轉到 WCF
此文章說明如何將使用 .NET 遠端處理的應用程式移轉為使用 Windows Communication Foundation (WCF)。 此文章會先比較這這些產品的類似概念，再說明如何在 WCF 中完成幾個常見的遠端處理案例。  
  
 .NET 遠端處理是僅為了回溯相容性所支援的舊版產品。 此產品由於無法在用戶端與伺服器之間維護個別的信任層級，因此會因為跨受信任與未受信任的環境而不安全。 例如，您絕不能將 .NET 遠端處理端點公開給網際網路或未受信任的用戶端。 建議將現有的遠端處理應用程式移轉至更新且更安全的技術。 如果應用程式的設計只使用 HTTP 並且符合 REST 規範，則建議使用 ASP.NET Web API。 如需詳細資訊，請參閱＜ASP.NET Web API＞。 如果應用程式是以 SOAP 為基礎，或需要非 Http 通訊協定 (例如 TCP)，則建議使用 WCF。  

## <a name="comparing-net-remoting-to-wcf"></a>比較 .NET 遠端處理與 WCF  
 本節將 .NET 遠端處理的基本建置組塊與其 WCF 對應項進行比較。 我們稍後將使用這些建置組塊，在 WCF 中建立一些常見的用戶端和伺服器案例。下表摘要說明 .NET 遠端處理和 WCF 之間的主要相似性和差異。  
  
||.NET 遠端處理|WCF|  
|-|-------------------|---------|  
|伺服器類型|子類別 MarshalByRefObject|以 [ServiceContract] 屬性標記|  
|服務作業|伺服器類型的公用方法|以 [OperationContract] 屬性標記|  
|序列化|ISerializable 或 [Serializable]|DataContractSerializer 或 XmlSerializer|  
|已傳遞的物件|傳值或傳址|僅限傳值|  
|錯誤/例外狀況|任何可序列化的例外狀況|FaultContract\<TDetail>|  
|用戶端 Proxy 物件|強型別 Transparent Proxy 是從 MarshalByRefObjects 自動建立|產生強型別的 proxy 是隨使用 ChannelFactory\<TChannel >|  
|所需的平台|用戶端和伺服器都必須使用 Microsoft 作業系統與 .NET|跨平台|  
|訊息格式|Private|業界標準 (SOAP、WS-* 等)|  
  
### <a name="server-implementation-comparison"></a>伺服器實作比較  
  
#### <a name="creating-a-server-in-net-remoting"></a>在 .NET 遠端處理中建立伺服器  
 .NET 遠端處理伺服器類型必須衍生自 MarshalByRefObject 並定義用戶端可呼叫的方法 (如下所示)：  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 此伺服器類型的公用方法會變成用戶端可用的公用合約。  伺服器的公用介面與其實作之間沒有區隔 (一種類型處理兩者)。  
  
 定義伺服器類型之後，便可將類型提供給用戶端，如下列範例所示：  
  
```csharp
TcpChannel channel = new TcpChannel(8080);  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingConfiguration.RegisterWellKnownServiceType(  
    typeof(RemotingServer),   
    "RemotingServer",   
    WellKnownObjectMode.Singleton);  
Console.WriteLine("RemotingServer is running.  Press ENTER to terminate...");  
Console.ReadLine();  
```  
  
 有許多方法可將遠端處理類型當做伺服器來提供，包括使用組態檔。 這只是其中一個範例。  
  
#### <a name="creating-a-server-in-wcf"></a>在 WCF 中建立伺服器  
 在 WCF 中的對應步驟包含建立兩種類型：公用「服務合約」與具體實作。 第一種類型會宣告為以 [ServiceContract] 標記的介面。 提供給用戶端的的方法會以 [OperationContract] 標記：  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 伺服器的實作會在個別的具體類別中定義，如下列範例所示：  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 定義這些類型之後，便可將 WCF 伺服器提供給用戶端，如下列範例所示：  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
Uri baseAddress = new Uri("net.tcp://localhost:8000/wcfserver");  
  
using (ServiceHost serviceHost = new ServiceHost(typeof(WCFServer), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(IWCFServer), binding, baseAddress);  
    serviceHost.Open();  
  
    Console.WriteLine(String.Format("The WCF server is ready at {0}.",  
                                    baseAddress));  
    Console.WriteLine("Press <ENTER> to terminate service...");  
    Console.WriteLine();  
    Console.ReadLine();  
}  
```  
  
> [!NOTE]
>  TCP 會用於這兩個範例中，以盡可能保持這兩個範例類似。 如需使用 HTTP 的範例，請參閱本主題稍後的案例逐步解說。  
  
 設定及裝載 WCF 服務的方法有許多種。 這只是其中一個範例，稱為「自我裝載」。 如需詳細資訊，請參閱下列主題：  
  
-   [如何：定義服務合約](how-to-define-a-wcf-service-contract.md)  
  
-   [使用設定檔設定服務](configuring-services-using-configuration-files.md)  
  
-   [裝載服務](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a>用戶端實作比較  
  
#### <a name="creating-a-client-in-net-remoting"></a>在 .NET 遠端處理中建立用戶端  
 提供 .NET 遠端處理伺服器物件之後，用戶端便可使用這個物件，如下列範例所示：  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine(String.Format("Customer {0} {1} received.",   
                                 customer.FirstName, customer.LastName));  
```  
  
 從 Activator.GetObject() 傳回的 RemotingServer 執行個體稱為 "Transparent Proxy"。 它會針對用戶端上的 RemotingServer 類型實作公用 API，但所有方法都會呼叫在不同處理序或電腦中執行的伺服器物件。  
  
#### <a name="creating-a-client-in-wcf"></a>在 WCF 中建立用戶端  
 在 WCF 中的對應步驟包含使用通道處理站明確建立 Proxy。 如同遠端處理，Proxy 物件可用來叫用伺服器上的作業，如下列範例所示：  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
String url = "net.tcp://localhost:8000/wcfserver";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<IWCFServer> channelFactory =   
    new ChannelFactory<IWCFServer>(binding, address);  
IWCFServer server = channelFactory.CreateChannel();  
  
Customer customer = server.GetCustomer(42);  
Console.WriteLine(String.Format("  Customer {0} {1} received.",  
                    customer.FirstName, customer.LastName));  
```  
  
 此範例顯示如何在通道層級進行程式設計，因為它最類似遠端處理範例。 也可以使用**加入服務參考**會產生可簡化程式設計的用戶端程式碼的 Visual Studio 中的方法。 如需詳細資訊，請參閱下列主題：  
  
-   [用戶端通道層級的程式設計](./extending/client-channel-level-programming.md)  
  
-   [如何： 加入、 更新或移除服務參考](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a>序列化使用方式  
 雖然 .NET 遠端處理與 WCF 都是使用序列化在用戶端與伺服器之間傳送物件，但是它們在下列幾個重要方面有所不同：  
  
1.  它們使用不同的序列化程式與慣例，來指出要序列化的項目。  
  
2.  .NET 遠端處理支援「傳址」序列化，允許在某個階層上存取方法或屬性，以在另一個階層上執行程式碼，也就是跨安全性界限。 此功能有安全性弱點，這也是為什麼絕不能將遠端處理端點公開給未受信任的用戶端的主要原因之一。  
  
3.  遠端處理所使用的序列化必須選擇退出 (明確排除不要序列化的項目)，而 WCF 序列化必須選擇加入 (明確標記要序列化的成員)。  
  
#### <a name="serialization-in-net-remoting"></a>.NET 遠端處理的序列化  
 .NET 遠端處理支援以兩種方式在用戶端與伺服器之間序列化及還原序列化物件：  
  
-   *依值*-跨階層界限序列化物件的值，並在另一個階層上建立該物件的新執行個體。 對新執行個體的方法或屬性所做的任何呼叫只會在本機執行，並不會影響原始物件或階層。  
  
-   *傳址*– 跨階層界限序列化特殊 「 物件參考 」。 當某個階層與該物件的方法或屬性互動時，它會回到原始階層與原始物件通訊。 傳址物件流向可為任一方向 (從伺服器到用戶端，或從用戶端到伺服器)。  
  
 遠端處理的傳值類型是以 [Serializable] 屬性標記或實作 ISerializable，如下列範例所示：  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 傳址類型衍生自 MarshalByRefObject 類別，如下列範例所示：  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 請務必了解遠端處理之傳址物件的含意。 如果其中一個階層 (用戶端或伺服器) 將傳址物件傳送至另一個階層，則會回到擁有該物件的階層上執行所有方法呼叫。 例如，當用戶端對伺服器所傳回的傳址物件呼叫方法時，會在伺服器上執行程式碼。 同樣地，當伺服器對用戶端所提供的傳址物件呼叫方法時，也會回到用戶端執行程式碼。 因此，建議只在完全信任的環境中使用 .NET 遠端處理。 將公用 .NET 遠端處理端點公開給未受信任的用戶端，會使遠端處理伺服器容易受到攻擊。  
  
#### <a name="serialization-in-wcf"></a>WCF 中的序列化  
 WCF 只支援傳值序列化。 若要定義在用戶端和伺服器之間交換的類型，最常見的方法如下列範例所示：  
  
```csharp
[DataContract]  
public class WCFCustomer  
{  
    [DataMember]  
    public string FirstName { get; set; }  
  
    [DataMember]  
    public string LastName { get; set; }  
  
    [DataMember]  
    public int CustomerId { get; set; }  
}  
```  
  
 [DataContract] 屬性將此類型識別為可在用戶端與伺服器之間序列化及還原序列化的類型。 [DataMember] 屬性識別要序列化的個別屬性或欄位。  
  
 當 WCF 跨階層傳送物件時，它只會序列化值，並在另一個階層上建立新的物件執行個體。 與物件值的任何互動只會在本機進行，而不會和 .NET 遠端處理傳址物件一樣與另一個階層通訊。 如需詳細資訊，請參閱下列主題：  
  
-   [序列化和還原序列化](./feature-details/serialization-and-deserialization.md)  
  
-   [Windows Communication Foundation 序列化](http://msdn.microsoft.com/magazine/cc163569.aspx)  
  
### <a name="exception-handling-capabilities"></a>例外狀況處理功能  
  
#### <a name="exceptions-in-net-remoting"></a>.NET 遠端處理中的例外狀況  
 遠端處理伺服器所擲回的例外狀況和其他任何例外狀況一樣，會序列化、傳送至用戶端，然後在用戶端本機擲回。 您可以將例外狀況類型分為子類別並標記為 [Serializable]，來建立自訂例外狀況。   大多數的架構例外狀況已透過這種方式標記，以允許大部分的例外狀況由伺服器擲回、序列化，並在用戶端上重新擲回。 雖然這種設計在開發期間很方便，但可能會將伺服器端資訊不慎洩漏給用戶端。 這就是遠端處理只能在完全信任的環境中使用的原因之一。  
  
#### <a name="exceptions-and-faults-in-wcf"></a>WCF 中的例外狀況與錯誤  
 WCF 不允許將任意例外狀況類型從伺服器傳回至用戶端，因為這樣做可能會導致不慎洩漏資訊。 如果服務作業擲回未預期的例外狀況，則會導致在用戶端上擲回一般目的 FaultException。 這個例外狀況不會傳達有關發生問題之原因和位置的任何資訊，這對於某些應用程式而言便已足夠。 如果應用程式必須對用戶端傳達更豐富的錯誤資訊，則可以透過定義錯誤合約來達成目的。  
  
 若要這樣做，請先建立要傳達錯誤資訊的 [DataContract] 類型。  
  
```csharp
[DataContract]  
public class CustomerServiceFault  
{  
    [DataMember]  
    public string ErrorMessage { get; set; }  
  
    [DataMember]  
    public int CustomerId {get;set;}  
}  
```  
  
 指定每個服務作業所要使用的錯誤合約。  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 伺服器會擲回 FaultException 來報告錯誤狀況。  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 此外，當用戶端對伺服器提出要求時，它會攔截錯誤，就像是攔截一般例外狀況一樣。  
  
```csharp
try  
{  
    Customer customer = server.GetCustomer(-1);  
}  
catch (FaultException<CustomerServiceFault> fault)  
{  
    Console.WriteLine(String.Format("Fault received: {0}",  
    fault.Detail.ErrorMessage));  
}  
```  
  
 如需錯誤合約的詳細資訊，請參閱 <xref:System.ServiceModel.FaultException>。  
  
### <a name="security-considerations"></a>安全性考量  
  
#### <a name="security-in-net-remoting"></a>.NET 遠端處理中的安全性  
 某些 .NET 遠端處理通道支援安全性功能，例如通道層 (IPC 和 TCP) 的驗證和加密。 HTTP 通道需要 Internet Information Service (IIS) 來進行驗證與加密。 儘管有此支援，您還是應該將 .NET 遠端處理視為不安全的通訊協定，並只在完全信任的環境中使用。 絕對不要將公用遠端處理端點公開給網際網路或未受信任的用戶端。  
  
#### <a name="security-in-wcf"></a>WCF 的安全性  
 WCF 的設計將安全性納入考量，部分是為了解決 .NET 遠端處理中所發現的安全性弱點類型。 WCF 在傳輸與訊息層級提供安全性，並提供驗證、授權、加密等許多選項。 如需詳細資訊，請參閱下列主題：  
  
-   [安全性](./feature-details/security.md)  
  
-   [WCF 安全性指導方針](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a>移轉至 WCF  
  
### <a name="why-migrate-from-remoting-to-wcf"></a>為什麼要從遠端處理移轉至 WCF？  
  
-   **.NET 遠端處理是舊版產品。** 中所述[.NET 遠端處理](http://msdn.microsoft.com/library/vstudio/72x4h507\(v=vs.100\).aspx)，它會被視為舊版產品，並不建議用於新的開發。 建議針對新的和現有的應用程式使用 WCF 或 ASP.NET Web 應用程式開發介面。  
  
-   **WCF 使用跨平台標準。** WCF 的設計將跨平台互通性納入考量，並支援許多業界標準 (SOAP、WS-Security、WS-Trust 等)。 WCF 服務可以與在非 Windows 作業系統上執行的用戶端互通。 遠端處理的設計主要是針對在 Windows 作業系統上使用 .NET Framework 執行伺服器和用戶端應用程式的環境。  
  
-   **WCF 具有內建的安全性。** WCF 的設計將安全性納入考量，並提供驗證、傳輸層級安全性、訊息層級安全性等許多選項。遠端處理的設計是為了讓應用程式輕鬆地互通，而不是為了確保在未受信任環境中的安全性。 WCF 的設計是為了在受信任和未受信任的環境中都能夠正常運作。  
  
### <a name="migration-recommendations"></a>移轉建議  
 以下是從 .NET 遠端處理移轉至 WCF 的建議步驟：  
  
-   **建立服務合約。** 定義您的服務介面類型並以 [ServiceContract] 屬性標記。將用戶端可使用 [OperationContract] 呼叫的所有方法都加以標記。  
  
-   **建立資料合約。** 定義要在伺服器與用戶端之間交換的資料類型，並以 [DataContract] 屬性標記這些類型。 將用戶端可搭配 [DataMember] 使用之所有欄位和屬性都加以標記。  
  
-   **建立錯誤合約 （選擇性）。** 建立遇到錯誤時，要在伺服器與用戶端之間交換的類型。 以 [DataContract] 和 [DataMember] 標記這些類型，使這些類型可序列化。 針對已標記為 [OperationContract] 的所有服務作業，您也應該將它們標記為 [FaultContract]，以指出這些服務作業可能傳回的錯誤。  
  
-   **設定及裝載服務。** 建立服務合約之後，下一個步驟是設定繫結，以公開端點上的服務。 如需詳細資訊，請參閱[端點： 位址、 繫結和合約](./feature-details/endpoints-addresses-bindings-and-contracts.md)。  
  
 將遠端處理應用程式移轉至 WCF 之後，還必須移除與 .NET 遠端處理的相依性。 如此可確保移除應用程式中的任何遠端處理安全性弱點。 這些步驟包括：  
  
-   **停用 MarshalByRefObject。** MarshalByRefObject 類型只適用於遠端處理，而且不會由 WCF 使用。 任何具有子類別 MarshalByRefObject 的應用程式類型都應予以移除或變更。 MarshalByRefObject 類型只適用於遠端處理，而且不會由 WCF 使用。 任何具有子類別 MarshalByRefObject 的應用程式類型都應予以移除或變更。  
  
-   **停止使用 [Serializable] 與 ISerializable。** [Serializable] 屬性與 ISerializable 介面原本是為了在信任的環境中序列化類型所設計，而且由遠端處理使用。 WCF 序列化必須以 [DataContract] 與 [DataMember] 來標記類型。 應用程式所使用的資料類型應該修改為使用 [DataContract]，而不是使用 ISerializable 或 [Serializable]。 [Serializable] 屬性與 ISerializable 介面原本是為了在信任的環境中序列化類型所設計，而且由遠端處理使用。 WCF 序列化必須以 [DataContract] 與 [DataMember] 來標記類型。 應用程式所使用的資料類型應該修改為使用 [DataContract]，而不是使用 ISerializable 或 [Serializable]。  
  
### <a name="migration-scenarios"></a>移轉案例  
 現在我們來看看如何在 WCF 中完成下列常見的遠端處理案例：  
  
1.  伺服器以傳值方式將物件傳回至用戶端  
  
2.  伺服器以傳址方式將物件傳回至用戶端  
  
3.  用戶端以傳值方式將物件傳送至伺服器  
  
> [!NOTE]
>  在 WCF 中不允許以傳址方式將物件從用戶端傳送至伺服器。  
  
 閱讀這些案例時，請假設 .NET 遠端處理的基準介面如下列範例所示。 .NET 遠端處理實作在這裡並不重要，因為我們只想要說明如何使用 WCF 來實作對應功能。  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    // Demonstrates server returning object by-value  
    public Customer GetCustomer(int customerId) {…}  
  
    // Demonstrates server returning object by-reference  
    public CustomerReference GetCustomerReference(int customerId) {…}  
  
    // Demonstrates client passing object to server by-value  
    public bool UpdateCustomer(Customer customer) {…}  
}  
```  
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a>案例 1：服務以傳值方式傳回物件  
 這個案例示範伺服器如何以傳值方式將物件傳回至用戶端。 WCF 一律會以傳值方式從伺服器傳回物件，因此下列步驟只會說明如何建置一般 WCF 服務。  
  
1.  一開始請定義 WCF 服務的公用介面並以 [ServiceContract] 屬性標記。 我們會使用 [OperationContract] 來識別用戶端將呼叫的伺服器端方法。  
  
   ```csharp
   [ServiceContract]  
   public interface ICustomerService  
   {  
       [OperationContract]  
       Customer GetCustomer(int customerId);  
  
       [OperationContract]  
       bool UpdateCustomer(Customer customer);  
   }  
   ```  
  
2.  下一個步驟是建立此服務的資料合約。 若要執行此作業，請建立以 [DataContract] 屬性標記的類別 (而不是介面)。 我們想要顯示給用戶端與伺服器的個別屬性或欄位都會以 [DataMember] 標記。 如果我們想要允許衍生類型，則必須使用 [KnownType] 屬性加以識別。 WCF 唯一可讓此服務序列化或還原序列化的類型是服務介面中的類型或「已知類型」。 嘗試交換不在這個清單中的其他任何類型都會遭到拒絕。  
  
   ```csharp
   [DataContract]  
   [KnownType(typeof(PremiumCustomer))]  
   public class Customer  
   {  
       [DataMember]  
       public string FirstName { get; set; }  
  
       [DataMember]  
       public string LastName { get; set; }  
  
       [DataMember]  
       public int CustomerId { get; set; }  
   }  
  
   [DataContract]  
   public class PremiumCustomer : Customer   
   {  
       [DataMember]  
       public int AccountId { get; set; }  
   }  
   ```  
  
3.  接下來，我們將提供服務介面的實作。  
  
   ```csharp  
   public class CustomerService : ICustomerService  
   {  
       public Customer GetCustomer(int customerId)  
       {  
           // read from database  
       }  
  
       public bool UpdateCustomer(Customer customer)  
       {  
           // write to database  
       }  
   }  
   ```  
  
4.  若要執行 WCF 服務，我們需要宣告一個端點，這個端點會使用特定 WCF 繫結在特定 URL 上公開該服務介面。 將下列區段加入到伺服器專案的 web.config 檔案通常可達成目的。  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
5.  接著會使用下列程式碼來啟動 WCF 服務：  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     當啟動這個 ServiceHost 時，它會使用 web.config 檔案來建立適當的合約、繫結與端點。 如需組態檔的詳細資訊，請參閱[設定服務使用組態檔](./configuring-services-using-configuration-files.md)。 這種啟動伺服器的方式稱為自我裝載。 若要深入了解裝載 WCF 服務的其他選項，請參閱[裝載服務](./hosting-services.md)。  
  
6.  用戶端專案的 app.config 必須宣告服務端點的相符繫結資訊。 若要這樣做的 Visual Studio 中的最簡單方式是使用**加入服務參考**，這會自動更新 app.config 檔案。 您也可以手動加入這些相同的變更。  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     如需有關使用**加入服務參考**，請參閱[如何： 加入、 更新或移除服務參考](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)。  
  
7.  現在我們可以從用戶端呼叫 WCF 服務。 若要執行此作業，請建立該服務的通道處理站，針對通道要求通道處理站，然後在該通道上直接呼叫所需的方法。 我們可以這樣做的原因，是因為通道會實作服務的介面並為我們處理基礎要求/回覆邏輯。 從該方法呼叫傳回的值是伺服器回應的已還原序列化複本。  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine(String.Format("  Customer {0} {1} received.",  
           customer.FirstName, customer.LastName));  
   ```  
  
 WCF 一律會以傳值方式將物件從伺服器傳回至用戶端。 這些物件是伺服器所傳送之資料的已還原序列化複本。 用戶端可以對這些本機複本呼叫方法，而不會有透過回呼叫用伺服器程式碼的任何危險。  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a>案例 2：伺服器以傳址方式傳回物件  
 這個案例示範伺服器如何以傳址方式將物件提供給用戶端。 在 .NET 遠端處理中，所有衍生自以傳址方式序列化之 MarshalByRefObject 的類型都將自動處理。 這個案例的範例是讓多個用戶端具有獨立工作階段的伺服器端物件。 如前所述，WCF 服務所傳回的物件一律為傳值物件，因此沒有傳址物件的直接對應項，但這個物件可能取得與使用 <xref:System.ServiceModel.EndpointAddress10> 物件之傳址語意類似的結果。 這是可序列化的傳值物件，可供用戶端用來取得伺服器上的工作階段傳址物件。 如此一來，便可讓多個用戶端具有獨立工作階段的伺服器端物件。  
  
1.  首先，我們需要定義對應到工作階段物件本身的 WCF 服務合約。  
  
   ```csharp
   [ServiceContract(SessionMode = SessionMode.Allowed)]  
       public interface ISessionBoundObject  
       {  
           [OperationContract]  
           string GetCurrentValue();  
  
           [OperationContract]  
           void SetCurrentValue(string value);  
       }  
   ```  
  
    > [!TIP]
    >  請注意，工作階段物件是以 [ServiceContract] 標記，因此是一般 WCF 服務介面。 設定 SessionMode 屬性表示它將會是工作階段服務。 在 WCF 中，工作階段是將兩個端點之間傳送的多個訊息相互關聯的方式。 這表示一旦用戶端取得此服務的連接，便會在用戶端與伺服器之間建立工作階段。 用戶端會針對此單一工作階段內的所有互動，使用伺服器端物件的唯一執行個體。  
  
2.  接下來，我們需要提供此服務介面的實作。 我們透過以 [ServiceBehavior] 標記並設定 InstanceContextMode，來告知 WCF 將要為每個工作階段使用此類型的唯一執行個體。  
  
   ```csharp
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
  
3.  現在我們需要設法取得此工作階段物件的執行個體。 若要執行此作業，請建立傳回 EndpointAddress10 物件的另一個 WCF 服務介面。 這是端點的可序列化形式，可供用戶端用來建立工作階段物件。  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     此外，我們會實作此 WCF 服務：  
  
   ```csharp
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
  
     此實作會維護單一通道處理站來建立工作階段物件。 呼叫 GetInstanceAddress() 時，它會建立通道，並建立有效指向與這個通道關聯之遠端位址的 EndpointAddress10 物件。 EndpointAddress10 是能夠以傳值方式傳回至用戶端的資料類型。  
  
4.  我們需要執行下列兩個動作，來修改伺服器的組態檔，如下列範例所示：  
  
    1.  宣告\<用戶端 > 一節描述工作階段物件端點。 由於在這種情況下伺服器也會當做用戶端，因此必須執行這個動作。  
  
    2.  宣告處理站與工作階段物件的端點。 這樣才能讓用戶端與服務端點通訊，以取得 EndpointAddress10 並建立工作階段通道。  
  
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
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
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
  
     接著我們可以啟動這些服務：  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5.  我們藉由在用戶端之專案的 app.config 檔案中宣告這些相同的端點，來設定用戶端。  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
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
  
6.  若要建立及使用這個工作階段物件，用戶端必須執行下列步驟：  
  
    1.  建立 ISessionBoundFactory 服務的通道。  
  
    2.  使用該通道叫用服務，以取得 EndpointAddress10。  
  
    3.  使用 EndpointAddress10 建立通道，以取得工作階段物件。  
  
    4.  與工作階段物件互動，以示範它在多個呼叫會保持相同的執行個體。  
  
   ```csharp
   ChannelFactory<ISessionBoundFactory> channelFactory =   
       new ChannelFactory<ISessionBoundFactory>("factory");  
   ISessionBoundFactory sessionFactory = channelFactory.CreateChannel();  
  
   EndpointAddress10 address1 = sessionFactory.GetInstanceAddress();  
   EndpointAddress10 address2 = sessionFactory.GetInstanceAddress();  
  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory1 =   
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),   
                                               address1.ToEndpointAddress());  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory2 =   
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),   
                                               address2.ToEndpointAddress());  
  
   ISessionBoundObject sessionInstance1 = sessionObjectFactory1.CreateChannel();  
   ISessionBoundObject sessionInstance2 = sessionObjectFactory2.CreateChannel();  
  
   sessionInstance1.SetCurrentValue("Hello");  
   sessionInstance2.SetCurrentValue("World");  
  
   if (sessionInstance1.GetCurrentValue() == "Hello" &&  
       sessionInstance2.GetCurrentValue() == "World")  
   {  
       Console.WriteLine("sessionful server object works as expected");  
   }  
   ```  
  
 WCF 一律會以傳值方式傳回物件，但是可透過使用 EndpointAddress10 來支援傳址語意的對應項。 這可讓用戶端要求工作階段 WCF 服務執行個體，在這之後，便可像任何其他 WCF 服務一樣與其互動。  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a>案例 3：用戶端將傳值執行個體傳送至伺服器  
 這個案例示範用戶端如何以傳值方式將非基本物件執行個體傳送至伺服器。 由於 WCF 只會以傳值方式傳送物件，因此這個案例會示範一般 WCF 使用方式。  
  
1.  使用案例 1 中的相同 WCF 服務。  
  
2.  使用用戶端來建立新的傳值物件 (客戶)，建立要與 ICustomerService 服務通訊的通道，然後將物件傳送至通道。  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   PremiumCustomer customer = new PremiumCustomer {   
   FirstName = "Bob",   
   LastName = "Jones",   
   CustomerId = 43,   
   AccountId = 99};  
   bool success = service.UpdateCustomer(customer);  
   Console.WriteLine(String.Format("  Server returned {0}.", success));  
   ```  
  
     客戶物件會序列化並傳送至伺服器，再於其中還原序列化為該物件的新複本。  
  
    > [!NOTE]
    >  這個程式碼也會說明如何傳送衍生類型 (PremiumCustomer)。 服務介面必須有 Customer 物件，但 Customer 類別上的 [KnownType] 屬性表示也允許 PremiumCustomer。 WCF 對於透過這個服務介面序列化或還原序列化其他任何類型所做的任何嘗試都將會失敗。  
  
 一般 WCF 交換資料的方式是傳值。 如此可確保在其中一個資料物件上叫用方法的作業只會在本機執行，而不會在另一個階層上叫用程式碼。 雖然可以達到所傳回的傳址物件類似*從*伺服器，不可能將傳址物件傳送用戶端*至*伺服器。 如果需要在用戶端與伺服器之間來回溝通，可透過雙工服務在 WCF 中達成。 如需詳細資訊，請參閱[雙工服務](./feature-details/duplex-services.md)。  
  
## <a name="summary"></a>總結  
 .NET 遠端處理是只能在完全信任的環境中使用的通訊架構。 它是只為了回溯相容性所支援的舊版產品。 不應該用來建置新的應用程式。 相反地，WCF 的設計將安全性納入考量，建議針對新的與現有的應用程式使用。 Microsoft 建議將現有的遠端處理應用程式移轉為改用 WCF 或 ASP.NET Web API。