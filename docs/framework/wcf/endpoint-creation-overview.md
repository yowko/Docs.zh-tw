---
title: 端點建立概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: 91e5e45d380ec6a8229a7272c841e1a345423c7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="endpoint-creation-overview"></a>端點建立概觀
所有與 Windows Communication Foundation (WCF) 服務的通訊會透過*端點*的服務。 端點可讓用戶端存取 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務提供的功能。 本章節說明端點的結構，並且摘要說明如何透過組態與程式碼來定義端點。  
  
## <a name="the-structure-of-an-endpoint"></a>端點結構  
 每個端點都包含一個位址用以指出該到何處尋找端點、一個指定用戶端與端點如何進行通訊的繫結，以及一個可識別可用方法的合約。  
  
-   **位址**。 位址會唯一識別端點並告訴潛在取用者服務的位置。 它是由 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 物件模型中的 <xref:System.ServiceModel.EndpointAddress> 位址所代表，內含統一資源識別元 (URI) 與位址屬性，而這些屬性又包含了身分識別、一些 Web 服務描述語言 (WSDL) 項目，以及選用標頭的集合。 選用標頭會提供額外的詳細位址資訊來識別端點或與端點互動。 如需詳細資訊，請參閱[指定端點位址](../../../docs/framework/wcf/specifying-an-endpoint-address.md)。  
  
-   **繫結**。 繫結會指定與端點的通訊方式。 繫結程序會指定端點與世界的通訊方式，包括要使用的傳輸通訊協定 (例如，TCP 或 HTTP)、訊息使用的編碼 (例如，文字或二進位)，以及必要的安全性要求有哪些 (例如，Secure Sockets Layer [SSL] 或 SOAP 訊息安全性)。 如需詳細資訊，請參閱[使用繫結來設定服務和用戶端](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)。  
  
-   **服務合約**。 服務合約會概略說明端點公開哪些功能給用戶端。 合約指定了用戶端可以呼叫的作業、訊息格式與輸入參數型別或是呼叫作業時必要的資料，以及用戶端能夠預期的處理或回應訊息類型。 三種基本合約型別都對應至基本的訊息交換模式 (MEP)：資料包 (單向)、要求/回覆，與雙工 (雙向)。 當服務合約遭到存取，也能使用資料與訊息合約來要求特定資料類型與訊息格式。 如需如何定義服務合約的詳細資訊，請參閱[設計服務合約](../../../docs/framework/wcf/designing-service-contracts.md)。 請注意，用戶端可能也會被要求實作服務定義合約 (稱為回呼合約)，以便在雙工 MEP 中從服務接收訊息。 如需詳細資訊，請參閱[雙工服務](../../../docs/framework/wcf/feature-details/duplex-services.md)。  
  
 您可以透過命令式程式碼或是宣告式組態來指定服務端點。 如果沒有指定端點，則執行階段會針對服務所實作的每個服務合約，為每個基底位址加入一個預設端點，藉以提供預設端點。 在程式碼中定義端點通常不太實用，因為部署之服務的繫結和位址通常與開發服務時所使用的繫結和位址不同。 一般來說，透過組態來定義服務端點會比透過程式碼來得實際一些。 將繫結和位址資訊留在程式碼外面可讓它們直接進行變更，而不需要重新編譯或重新部署應用程式。  
  
> [!NOTE]
>  在新增可執行模擬服務端點時，您必須使用其中一個 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 方法或是 <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> 方法，將合約適當地載入新的 <xref:System.ServiceModel.Description.ServiceDescription> 物件中。  
  
## <a name="defining-endpoints-in-code"></a>在程式碼中定義端點  
 下列範例將說明如何使用下列各項在程式碼中指定端點：  
  
-   定義服務合約`IEcho`接受某人名稱以及回應與回應的服務類型的"Hello\<名稱 > ！"。  
  
-   實作由 `Echo` 合約定義的 `IEcho` 服務型別。  
  
-   指定的端點位址http://localhost:8000/Echo服務。  
  
-   使用 `Echo` 繫結來設定 <xref:System.ServiceModel.WSHttpBinding> 服務。  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   public interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   class Echo : IEcho  
   {  
      public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      public static void Main ()  
      {  
          //Specify the base address for Echo service.  
          Uri echoUri = new Uri("http://localhost:8000/");  
  
          //Create a ServiceHost for the Echo service.  
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);  
  
          // Use a predefined WSHttpBinding to configure the service.  
          WSHttpBinding binding = new WSHttpBinding();  
  
          // Add the endpoint for this service to the service host.  
          serviceHost.AddServiceEndpoint(  
             typeof(IEcho),   
             binding,   
             echoUri  
           );  
  
          // Open the service host to run it.  
          serviceHost.Open();  
     }  
  }  
}  
```  
  
```vb  
' Define the contract for the IEcho service  
    <ServiceContract()> _  
    Public Interface IEcho  
        <OperationContract()> _  
        Function Hello(ByVal name As String) As String  
    End Interface  
  
' Create an Echo service that implements IEcho contract  
    Public Class Echo   
        Implements IEcho  
        Public Function Hello(ByVal name As String) As String _  
 Implements ICalculator.Hello  
            Dim result As String = "Hello" + name + "!"  
            Return result  
        End Function  
  
' Specify the base address for Echo service.  
Dim echoUri As Uri = New Uri("http://localhost:8000/")  
  
' Create a ServiceHost for the Echo service.  
Dim svcHost As ServiceHost = New ServiceHost(GetType(HelloWorld), echoUri)  
  
' Use a predefined WSHttpBinding to configure the service.  
Dim binding As New WSHttpBinding()  
  
' Add the endpoint for this service to the service host.  
serviceHost.AddServiceEndpoint(GetType(IEcho), binding, echoUri)  
  
' Open the service host to run it.  
serviceHost.Open()  
```  
  
> [!NOTE]
>  使用基底位址建立服務主機，然後將相對於基底位址的其餘位址指定為端點的一部分。 這種位址分割方式可讓您更方便地針對主機上的服務定義多個端點。  
  
> [!NOTE]
>  服務應用程式中的 <xref:System.ServiceModel.Description.ServiceDescription> 屬性不得在 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> 上的 <xref:System.ServiceModel.ServiceHostBase> 方法之後修改。 一些成員，像是 <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> 屬性及 `AddServiceEndpoint` 與 <xref:System.ServiceModel.ServiceHostBase> 上的 <xref:System.ServiceModel.ServiceHost> 方法，如果在通過該點之後修改，便會擲回例外狀況。 其他成員可讓您加以修改，但結果仍未定義。  
>   
>  同樣地，您不可以在呼叫 <xref:System.ServiceModel.Description.ServiceEndpoint> 上的 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> 之後修改用戶端上的 <xref:System.ServiceModel.ChannelFactory> 值。 <xref:System.ServiceModel.ChannelFactory.Credentials%2A> 屬性如果在通過該點之後修改，便會擲回例外狀況。 其他的用戶端說明值可以修改而不會造成錯誤，但是結果仍為未定義。  
>   
>  無論是在服務或是用戶端，建議的做法都是在呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> 之前修改說明。  
  
## <a name="defining-endpoints-in-configuration"></a>在組態中定義端點  
 建立應用程式時，您經常會想要延遲負責部署應用程式之系統管理員的決定。 例如，經常無法預先得知服務位址 (URI) 會是怎樣。 這時候，為位址進行硬式編碼並不是理想的作法，較好的作法是讓系統管理員在建立服務後再處理。 這樣的靈活性是透過組態達成。 如需詳細資訊，請參閱[設定 Services](../../../docs/framework/wcf/configuring-services.md)。  
  
> [!NOTE]
>  使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)與`/config:` *filename*`[,`*filename* `]`切換至快速建立組態檔。  
  
## <a name="using-default-endpoints"></a>使用預設端點  
 如果在程式碼或組態中沒有指定端點，則執行階段會針對服務所實作的每個服務合約，為每個基底位址加入一個預設端點，藉以提供預設端點。 基底位址可以在程式碼或組態中指定，而預設端點則會在 <xref:System.ServiceModel.ICommunicationObject.Open> 上呼叫 <xref:System.ServiceModel.ServiceHost> 時加入。 這個範例和上一節的範例相同，但是因為沒有指定端點，所以會加入預設端點。  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   Interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   Class Echo : IEcho  
   {  
      Public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      static void Main ()  
      {  
          //Specify the base address for Echo service.  
          Uri echoUri = new Uri("http://localhost:8000/");  
  
          //Create a ServiceHost for the Echo service.  
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);  
  
          // Open the service host to run it. Default endpoints  
          // are added when the service is opened.  
          serviceHost.Open();  
     }  
  }  
}  
```  
  
```vb  
' Define the contract for the IEcho service  
    <ServiceContract()> _  
    Public Interface IEcho  
        <OperationContract()> _  
        Function Hello(ByVal name As String) As String  
    End Interface  
  
' Create an Echo service that implements IEcho contract  
    Public Class Echo   
        Implements IEcho  
        Public Function Hello(ByVal name As String) As String _  
 Implements ICalculator.Hello  
            Dim result As String = "Hello" + name + "!"  
            Return result  
        End Function  
  
' Specify the base address for Echo service.  
Dim echoUri As Uri = New Uri("http://localhost:8000/")  
  
' Open the service host to run it. Default endpoints  
' are added when the service is opened.  
serviceHost.Open()  
```  
  
 如果沒有明確提供端點，在呼叫 <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> 之前，仍可藉由在 <xref:System.ServiceModel.ServiceHost> 上呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> 來加入預設端點。 如需有關預設端點的詳細資訊，請參閱[簡化的組態](../../../docs/framework/wcf/simplified-configuration.md)和[簡化 WCF 服務的組態](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。  
  
## <a name="see-also"></a>另請參閱  
 [履行服務合約](../../../docs/framework/wcf/implementing-service-contracts.md)
