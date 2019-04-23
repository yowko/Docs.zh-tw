---
title: 指定服務合約中的資料傳輸
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: 88bdfe6e659e6e83365b3d17c9067581f209d154
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331516"
---
# <a name="specifying-data-transfer-in-service-contracts"></a>指定服務合約中的資料傳輸
Windows Communication Foundation (WCF) 可以視為傳訊基礎結構。 服務作業可以接收訊息、處理訊息，並傳送訊息。 訊息會透過作業合約來加以描述。 例如，請參考下列合約。  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    float GetAirfare(string fromCity, string toCity);  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
  
    <OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
End Interface  
```  
  
 在這裡，`GetAirfare` 作業會接受包含有關 `fromCity` 和 `toCity` 資訊的訊息，然後傳回包含數字的訊息。  
  
 本主題將說明作業合約用來描述訊息的各種不同方式。  
  
## <a name="describing-messages-by-using-parameters"></a>使用參數來描述訊息  
 描述訊息最簡單的方式，就是使用參數清單與傳回值。 在先前的範例中，已使用 `fromCity` 和 `toCity` 字串參數來描述要求訊息，同時使用浮點傳回值來描述回覆訊息。 如果傳回值還不足以描述回覆訊息，則會使用 out 參數。 例如，下列作業在其要求訊息中包含了 `fromCity` 和 `toCity`，並在其回覆訊息中包含了數字與貨幣。  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 此外，您可以使用參考參數，讓參數同時成為要求與回覆訊息的一部分。 參數必須是可以序列化 (轉換為 XML) 的型別。 根據預設，WCF 會使用元件，稱為<xref:System.Runtime.Serialization.DataContractSerializer>類別來執行這項轉換。 支援大多數的基本型別 (例如 `int`、`string`、`float` 和 `DateTime`)。 使用者定義型別通常必須具有資料合約。 如需詳細資訊，請參閱 < [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)。  
  
```csharp
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    float GetAirfare(Itinerary itinerary, DateTime date);  
  
    [DataContract]  
    public class Itinerary  
    {  
        [DataMember]  
        public string fromCity;  
        [DataMember]  
        public string toCity;  
   }  
}  
```  
  
```vb  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    GetAirfare(itinerary as Itinerary, date as DateTime) as Double  
  
    <DataContract()>  
    Class Itinerary  
  
        <DataMember()>  
        Public fromCity As String  
        <DataMember()>  
        Public toCity As String  
    End Class  
End Interface  
```  
  
 有時候，`DataContractSerializer` 並不足以序列化您的型別。 WCF 支援替代的序列化引擎， <xref:System.Xml.Serialization.XmlSerializer>，您也可以使用來序列化參數。 <xref:System.Xml.Serialization.XmlSerializer> 可讓您透過諸如 `XmlAttributeAttribute` 的屬性，針對最後的 XML 格式進行更複雜的控制。 若要切換為針對特定作業或整個服務使用 <xref:System.Xml.Serialization.XmlSerializer>，請將 <xref:System.ServiceModel.XmlSerializerFormatAttribute> 屬性套用到作業或服務。 例如:   
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    [XmlSerializerFormat]  
    float GetAirfare(Itinerary itinerary, DateTime date);  
}  
public class Itinerary  
{  
    public string fromCity;  
    public string toCity;  
    [XmlAttribute]  
    public bool isFirstClass;  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    <XmlSerializerFormat>  
    GetAirfare(itinerary as Itinerary, date as DateTime) as Double  
  
End Interface  
  
Class Itinerary  
  
    Public fromCity As String  
    Public toCity As String  
    <XmlSerializerFormat()>  
    Public isFirstClass As Boolean  
End Class  
```  
  
 如需詳細資訊，請參閱 <<c0> [ 使用 XmlSerializer 類別](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)。 請記住，我們不建議您模仿此處所示做法切換到 <xref:System.Xml.Serialization.XmlSerializer>，除非您有特殊的理由需要按照主題中所述的步驟來執行。  
  
 若要將 .NET 參數名稱從合約名稱中隔離出來，可以使用 <xref:System.ServiceModel.MessageParameterAttribute> 屬性 (Attribute)，並使用 `Name` 屬性 (Property) 來設定合約名稱。 例如，下列作業合約等同於本主題中第一個範例。  
  
```csharp  
[OperationContract]  
public float GetAirfare(  
    [MessageParameter(Name="fromCity")] string originCity,  
    [MessageParameter(Name="toCity")] string destinationCity);  
```  
  
```vb  
<OperationContract()>  
  Function GetAirfare(<MessageParameter(Name := "fromCity")> fromCity As String, <MessageParameter(Name := "toCity")> toCity As String) As Double  
```  
  
## <a name="describing-empty-messages"></a>描述空的訊息  
 您可以不要填入輸入或參考參數，來描述空的要求訊息。 例如，在 C# 中：  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 例如，在 VB 中：  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 您可以包含一個 `void` 傳回值，且不要填入輸出或參考參數來描述空的回覆訊息。 例如在：  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 這與單向作業不同，例如：  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 `SetTemperatureStatus` 作業會傳回空的訊息。 如果在處理輸入訊息時出現問題，此作業可能會傳回錯誤。 `SetLightbulbStatus` 作業不會傳回任何項目。 您無法從此作業傳送任何錯誤狀況。  
  
## <a name="describing-messages-by-using-message-contracts"></a>使用訊息合約來描述訊息  
 您可能想要使用單一型別來代表整個訊息。 儘管您可以透過資料合約來達到這個目的，我們還是建議您使用訊息合約，以避免在最後的 XML 中出現不必要包裝層級。 此外，訊息合約可讓您針對最後的訊息擁有更廣泛的控制能力。 例如，您可以決定訊息本文以及訊息標頭內應該存在哪些資訊片段。 下列範例將說明訊息合約的使用方式。  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    GetAirfareResponse GetAirfare(GetAirfareRequest request);  
}  
  
[MessageContract]  
public class GetAirfareRequest  
{  
    [MessageHeader] public DateTime date;  
    [MessageBodyMember] public Itinerary itinerary;  
}  
  
[MessageContract]  
public class GetAirfareResponse  
{  
    [MessageBodyMember] public float airfare;  
    [MessageBodyMember] public string currency;  
}  
  
[DataContract]  
public class Itinerary  
{  
    [DataMember] public string fromCity;  
    [DataMember] public string toCity;  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    Function GetAirfare(request As GetAirfareRequest) As GetAirfareResponse  
End Interface  
  
<MessageContract()>  
Public Class GetAirfareRequest  
    <MessageHeader()>   
    Public Property date as DateTime  
    <MessageBodyMember()>  
    Public Property itinerary As Itinerary  
End Class  
  
<MessageContract()>  
Public Class GetAirfareResponse  
    <MessageBodyMember()>  
    Public Property airfare As Double  
    <MessageBodyMember()> Public Property currency As String  
End Class  
  
<DataContract()>  
Public Class Itinerary  
    <DataMember()> Public Property fromCity As String  
    <DataMember()> Public Property toCity As String  
End Class  
```  
  
 如需詳細資訊，請參閱 < [Using Message Contracts](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)。  
  
 在先前的範例中，預設仍舊使用 <xref:System.Runtime.Serialization.DataContractSerializer> 類別。 <xref:System.Xml.Serialization.XmlSerializer> 類別也可以搭配訊息合約一起使用。 若要這麼做，請將 <xref:System.ServiceModel.XmlSerializerFormatAttribute> 屬性套用到作業或合約，然後在訊息標頭與本文成員中使用與 <xref:System.Xml.Serialization.XmlSerializer> 類別相容的型別。  
  
## <a name="describing-messages-by-using-streams"></a>使用資料流來描述訊息  
 另一種用來描述作業中訊息的方法，就是使用作業合約中的 <xref:System.IO.Stream> 類別或是由此類別衍生的類別之一，或將這些類別當成訊息合約本文成員來使用 (在此情況下，此成員必須是唯一的成員)。 如果是傳入的訊息，必須是 `Stream` 型別 (您無法使用衍生的類別)。  
  
 而不是叫用序列化程式，WCF 會從資料流中擷取資料和其直接放在外寄訊息，或從內送訊息中擷取資料並將它放直接將資料流。 下列範例說明資料流的使用方式。  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 您無法將 `Stream` 與非資料流資料結合到單一訊息本文中。 請使用訊息合約，將額外的資料放到訊息標頭中。 下列範例將說明在定義作業合約時，不正確的資料流使用方式。  
  
```csharp  
//Incorrect:  
// [OperationContract]  
// public void UploadFile (string fileName, Stream fileData);  
```  
  
```vb  
'Incorrect:  
    '<OperationContract()>  
    Public Sub UploadFile(fileName As String, fileData As StreamingContext)  
```  
  
 下列範例將說明在定義作業合約時，正確的資料流使用方式。  
  
```csharp  
[OperationContract]  
public void UploadFile (UploadFileMessage message);  
//code omitted  
[MessageContract]  
public class UploadFileMessage  
{  
    [MessageHeader] public string fileName;  
    [MessageBodyMember] public Stream fileData;  
}  
```  
  
```vb  
<OperationContract()>  
Public Sub UploadFile(fileName As String, fileData As StreamingContext)  
'Code Omitted  
<MessageContract()>  
Public Class UploadFileMessage  
   <MessageHeader()>  
    Public Property fileName As String  
    <MessageBodyMember()>  
    Public Property fileData As Stream  
End Class  
```  
  
 如需詳細資訊，請參閱 < [Large Data and Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)。  
  
## <a name="using-the-message-class"></a>使用 Message 類別  
 若要對傳送或收到的訊息擁有完整的程式掌控權，可以直接使用 <xref:System.ServiceModel.Channels.Message> 類別，如下列範例程式碼所示。  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 這是進階的案例中，在詳細資料中所述[Using the Message Class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)。  
  
## <a name="describing-fault-messages"></a>描述錯誤訊息  
 除了由傳回值與輸出或參考參數所描述的訊息以外，任何非單向的作業至少會傳回兩個可能的訊息：本身的正常回應訊息與錯誤訊息。 請參考下列作業合約。  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 此作業可能傳回包含 `float` 數字的正常訊息，或是傳回包含錯誤碼與說明的錯誤訊息。 您可以在服務實作中擲回 <xref:System.ServiceModel.FaultException> 來完成。  
  
 您可以使用 <xref:System.ServiceModel.FaultContractAttribute> 屬性，指定可能的額外錯誤訊息。 額外的錯誤必須可透過 <xref:System.Runtime.Serialization.DataContractSerializer> 來序列化，如下列程式碼範例所示。  
  
```csharp  
[OperationContract]  
[FaultContract(typeof(ItineraryNotAvailableFault))]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
  
//code omitted  
  
[DataContract]  
public class ItineraryNotAvailableFault  
{  
    [DataMember]  
    public bool IsAlternativeDateAvailable;  
  
    [DataMember]  
    public DateTime alternativeSuggestedDate;  
}  
```  
  
```vb  
<OperationContract()>  
<FaultContract(GetType(ItineraryNotAvailableFault))>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime) As Double  
  
'Code Omitted  
<DataContract()>  
Public Class  
  <DataMember()>  
  Public Property IsAlternativeDateAvailable As Boolean  
  <DataMember()>  
  Public Property alternativeSuggestedDate As DateTime  
End Class  
```  
  
 這些額外的錯誤可以藉由擲回適當資料合約型別的 <xref:System.ServiceModel.FaultException%601> 來產生。 如需詳細資訊，請參閱 <<c0> [ 處理的例外狀況和錯誤](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)。  
  
 您無法使用 <xref:System.Xml.Serialization.XmlSerializer> 類別來描述錯誤。 <xref:System.ServiceModel.XmlSerializerFormatAttribute> 對錯誤合約沒有任何作用。  
  
## <a name="using-derived-types"></a>使用衍生型別  
 您也許想要在作業或訊息合約中使用基底類型，然後在實際叫用作業時使用衍生型別。 在此情況下，您必須使用 <xref:System.ServiceModel.ServiceKnownTypeAttribute> 屬性或其他替代機制來允許使用衍生型別。 請參考下列作業。  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 假定兩種型別 (`Book` 和 `Magazine`) 都是衍生自 `LibraryItem`。 若要在 `IsLibraryItemAvailable` 作業中使用這些型別，請依下列方式變更作業：  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 另外，當預設的 <xref:System.Runtime.Serialization.KnownTypeAttribute> 正在使用時，您可以使用 <xref:System.Runtime.Serialization.DataContractSerializer>，如下列程式碼範例所示。  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
  
// code omitted   
  
[DataContract]  
[KnownType(typeof(Book))]  
[KnownType(typeof(Magazine))]  
public class LibraryItem  
{  
    //code omitted  
}  
```  
  
```vb  
<OperationContract()>  
Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
  
'Code Omitted  
<DataContract()>  
<KnownType(GetType(Book))>  
<KnownType(GetType(Magazine))>  
Public Class LibraryItem  
  'Code Omitted  
End Class  
```  
  
 您可以在使用 <xref:System.Xml.Serialization.XmlIncludeAttribute> 時，使用 <xref:System.Xml.Serialization.XmlSerializer> 屬性。  
  
 您可以將 <xref:System.ServiceModel.ServiceKnownTypeAttribute> 屬性套用到作業或整個服務上。 它能接受型別或方法名稱，以呼叫並取得已知型別的清單，就像是 <xref:System.Runtime.Serialization.KnownTypeAttribute> 屬性一樣。 如需詳細資訊，請參閱 < [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。  
  
## <a name="specifying-the-use-and-style"></a>指定使用方式與樣式  
 在使用 Web 服務描述語言 (WSDL) 來描述服務時，最常用到的兩種樣式就是文件與遠端程序呼叫 (RPC)。 在文件樣式中，整個訊息本文會透過結構描述來描述，而 WSDL 則是藉由參照結構描述中的項目來描述不同的訊息本文部分。 在 RPC 樣式中，WSDL 會參照每個訊息部分的結構描述型別 (而不是項目)。 在某些情況下，您必須手動選取其中一種樣式。 您可以套用 <xref:System.ServiceModel.DataContractFormatAttribute> 屬性，並設定 `Style` 屬性 (當 <xref:System.Runtime.Serialization.DataContractSerializer> 正在使用時)，或是在 `Style` 屬性上設定 <xref:System.ServiceModel.XmlSerializerFormatAttribute> (當使用 <xref:System.Xml.Serialization.XmlSerializer> 時)，來完成。  
  
 另外，<xref:System.Xml.Serialization.XmlSerializer> 支援兩種格式的序列化 XML：`Literal` 和 `Encoded`。 `Literal` 是最普遍接受的格式，也是 <xref:System.Runtime.Serialization.DataContractSerializer> 唯一支援的格式。 `Encoded` 是 SOAP 規範第 5 節所描述的舊版格式，不建議在新的服務上使用。 若要切換至 `Encoded` 模式，請將 `Use` 屬性 (Attribute) 上的 <xref:System.ServiceModel.XmlSerializerFormatAttribute> 屬性 (Property) 設為 `Encoded`。  
  
 在大部分情況下，您不應該變更 `Style` 和 `Use` 屬性的預設設定。  
  
## <a name="controlling-the-serialization-process"></a>控制序列化處理序  
 您可以用很多方法來自訂資料的序列化方式。  
  
### <a name="changing-server-serialization-settings"></a>變更伺服器序列化設定  
 當預設的 <xref:System.Runtime.Serialization.DataContractSerializer> 正在使用中，您可以藉由將 <xref:System.ServiceModel.ServiceBehaviorAttribute> 屬性套用到服務，來控制序列化處理序的某些層面。 具體來說，您可以使用 `MaxItemsInObjectGraph` 屬性來設定配額，以限制 <xref:System.Runtime.Serialization.DataContractSerializer> 可以還原序列化的最大物件數。 您可以使用 `IgnoreExtensionDataObject` 屬性來關閉反覆存取版本控制功能。 如需配額的詳細資訊，請參閱 [資料的安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)。 如需往返的詳細資訊，請參閱[向前相容資料合約](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)。  
  
```csharp  
[ServiceBehavior(MaxItemsInObjectGraph=100000)]  
public class MyDataService:IDataService  
{  
    public DataPoint[] GetData()  
    {  
       // Implementation omitted  
    }  
}  
```  
  
```vb  
<ServiceBehavior(MaxItemsInObjectGraph:=100000)>  
Public Class MyDataService Implements IDataService  
  
    Function GetData() As DataPoint()  
         ‘ Implementation omitted  
    End Function  
End Interface  
```  
  
### <a name="serialization-behaviors"></a>序列化行為  
 在 WCF 中，有兩種行為<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>而<xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>，自動插入取決於何種序列化程式是針對特定作業的使用中。 由於這些行為是自動套用的，一般來說您不需要知道它們的存在。  
  
 然而，`DataContractSerializerOperationBehavior` 具有 `MaxItemsInObjectGraph`、`IgnoreExtensionDataObject`，和 `DataContractSurrogate` 屬性，可供您用來自訂序列化處理序。 開頭的兩個屬性具有如上一節所述相同的意義。 您可以使用 `DataContractSurrogate` 屬性來啟用資料合約替代，這是一項功能強大的機制，可供您用來自訂與延伸序列化處理序。 如需詳細資訊，請參閱 <<c0> [ 資料合約代理](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)。  
  
 您可以使用 `DataContractSerializerOperationBehavior` 來同時自訂用戶端與伺服器序列化。 下列範例說明如何增加用戶端上的 `MaxItemsInObjectGraph` 配額。  
  
```csharp  
ChannelFactory<IDataService> factory = new ChannelFactory<IDataService>(binding, address);  
foreach (OperationDescription op in factory.Endpoint.Contract.Operations)  
{  
    DataContractSerializerOperationBehavior dataContractBehavior =  
                op.Behaviors.Find<DataContractSerializerOperationBehavior>()  
                as DataContractSerializerOperationBehavior;  
    if (dataContractBehavior != null)  
    {  
        dataContractBehavior.MaxItemsInObjectGraph = 100000;  
    }  
}  
IDataService client = factory.CreateChannel();  
```  
  
```vb  
Dim factory As ChannelFactory(Of IDataService) = New ChannelFactory(Of IDataService)(binding, address)  
For Each op As OperationDescription In factory.Endpoint.Contract.Operations  
        Dim dataContractBehavior As DataContractSerializerOperationBehavior = op.Behaviors.Find(Of DataContractSerializerOperationBehavior)()  
        If dataContractBehavior IsNot Nothing Then  
            dataContractBehavior.MaxItemsInObjectGraph = 100000  
        End If  
     Next  
    Dim client As IDataService = factory.CreateChannel  
```  
  
 下列為相等的服務程式碼 (適用自我裝載案例)。  
  
```csharp  
ServiceHost serviceHost = new ServiceHost(typeof(IDataService))  
foreach (ServiceEndpoint ep in serviceHost.Description.Endpoints)  
{  
foreach (OperationDescription op in ep.Contract.Operations)  
{  
        DataContractSerializerOperationBehavior dataContractBehavior =  
           op.Behaviors.Find<DataContractSerializerOperationBehavior>()  
                as DataContractSerializerOperationBehavior;  
        if (dataContractBehavior != null)  
        {  
            dataContractBehavior.MaxItemsInObjectGraph = 100000;  
        }  
}  
}  
serviceHost.Open();  
```  
  
```vb  
Dim serviceHost As ServiceHost = New ServiceHost(GetType(IDataService))  
        For Each ep As ServiceEndpoint In serviceHost.Description.Endpoints  
            For Each op As OperationDescription In ep.Contract.Operations  
                Dim dataContractBehavior As DataContractSerializerOperationBehavior = op.Behaviors.Find(Of DataContractSerializerOperationBehavior)()  
  
                If dataContractBehavior IsNot Nothing Then  
                    dataContractBehavior.MaxItemsInObjectGraph = 100000  
                End If  
            Next  
        Next  
        serviceHost.Open()  
```  
  
 在 Web 裝載案例中，您可以建立新的 `ServiceHost` 衍生類別，並透過服務主機處理站來將之插入。  
  
### <a name="controlling-serialization-settings-in-configuration"></a>控制組態中的序列化設定  
 您可以使用 `MaxItemsInObjectGraph` 端點或服務行為，並透過組態來控制 `IgnoreExtensionDataObject` 和 `dataContractSerializer`，如下列範例所示。  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="LargeQuotaBehavior">  
                    <dataContractSerializer  
                      maxItemsInObjectGraph="100000" />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <client>  
            <endpoint address="http://example.com/myservice"  
                  behaviorConfiguration="LargeQuotaBehavior"  
                binding="basicHttpBinding" bindingConfiguration=""   
                            contract="IDataService"  
                name="" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a>共用型別序列化、物件圖形保留，與自訂序列化程式  
 <xref:System.Runtime.Serialization.DataContractSerializer> 使用資料合約名稱，而不是 .NET 型別名稱來序列化。 這個做法與服務導向的架構原則相符，而且具有相當大的彈性—.NET 型別可以在不影響 Wire 合約的前提下進行變更。 在很罕見的情況下，您會想要序列化實際的 .NET 型別名稱，以便讓用戶端與伺服器緊密結合在一起 (與 .NET Framework 遠端處理技術類似)。 這不是建議的作法，但在罕見的情況下，通常會發生時從.NET Framework 遠端處理移轉至 WCF。 在此情況中，您必須使用 <xref:System.Runtime.Serialization.NetDataContractSerializer> 類別，而不是使用 <xref:System.Runtime.Serialization.DataContractSerializer> 類別。  
  
 一般來說，<xref:System.Runtime.Serialization.DataContractSerializer> 會將物件圖形序列化為物件樹。 亦即，如果相同的物件被參照一次以上，就會不只一次被序列化。 例如，某個 `PurchaseOrder` 執行個體具有兩個稱為 `billTo` 和 `shipTo` 的 Address 型別欄位。 如果兩個欄位同時設定為相同的 Address 執行個體，就會在序列化與還原序列化之後出現兩個一模一樣的 Address 執行個體。 這是因為 XML 中沒有可表示物件圖形的標準互通方式 (除了 <xref:System.Xml.Serialization.XmlSerializer> 所提供的舊版 SOAP 編碼標準以外，如先前有關`Style`與`Use`的小節說明所示)。 將物件圖形序列化為物件樹會產生特定的缺點，例如，您無法序列化帶有循環參照的圖形。 有時候您還得切換到真實物件圖形序列化，就算此作業無法互通也得照辦。 您可以使用 <xref:System.Runtime.Serialization.DataContractSerializer> (透過將 `preserveObjectReferences` 參數設為 `true` 來加以建構) 來完成。  
  
 有時候內建的序列化程式可能無法滿足您的案例需求。 在大部分情況下，您仍舊可以使用 <xref:System.Runtime.Serialization.XmlObjectSerializer> 抽取作業，來同時衍生 <xref:System.Runtime.Serialization.DataContractSerializer> 和 <xref:System.Runtime.Serialization.NetDataContractSerializer>。  
  
 前三個案例 (.NET 型別保留、物件圖形保留，與完整自訂 `XmlObjectSerializer` 式序列化) 皆需插入自訂序列化程式。 若要完成此項作業，請執行下列步驟：  
  
1. 撰寫自己的行為 (衍生自 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>)。  
  
2. 覆寫兩個 `CreateSerializer` 方法來傳回自己的序列化程式 (可能是 <xref:System.Runtime.Serialization.NetDataContractSerializer>、<xref:System.Runtime.Serialization.DataContractSerializer> 設為 `preserveObjectReferences` 的 `true`，或是自己的自訂 <xref:System.Runtime.Serialization.XmlObjectSerializer>)。  
  
3. 在開啟服務主機或是建立用戶端通道之前，請移除現有的 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> 行為並插入您在先前步驟所建立的自訂衍生類別。  
  
 如需有關進階的序列化概念的詳細資訊，請參閱 <<c0> [ 序列化和還原序列化](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)。  
  
## <a name="see-also"></a>另請參閱

- [使用 XmlSerializer 類別](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)
- [如何：啟用資料流](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
- [如何：建立類別或結構的基本資料合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
