---
title: 指定服務合約中的資料傳輸
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
caps.latest.revision: 38
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 852519dc1edc499511652f4027f4cd4eed6eef98
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="specifying-data-transfer-in-service-contracts"></a><span data-ttu-id="dcdbe-102">指定服務合約中的資料傳輸</span><span class="sxs-lookup"><span data-stu-id="dcdbe-102">Specifying Data Transfer in Service Contracts</span></span>
<span data-ttu-id="dcdbe-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 可以想成是訊息基礎結構。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] can be thought of as a messaging infrastructure.</span></span> <span data-ttu-id="dcdbe-104">服務作業可以接收訊息、處理訊息，並傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-104">Service operations can receive messages, process them, and send them messages.</span></span> <span data-ttu-id="dcdbe-105">訊息會透過作業合約來加以描述。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-105">Messages are described using operation contracts.</span></span> <span data-ttu-id="dcdbe-106">例如，請參考下列合約。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-106">For example, consider the following contract.</span></span>  
  
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
  
 <span data-ttu-id="dcdbe-107">在這裡，`GetAirfare` 作業會接受包含有關 `fromCity` 和 `toCity` 資訊的訊息，然後傳回包含數字的訊息。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-107">Here, the `GetAirfare` operation accepts a message with information about `fromCity` and `toCity`, and then returns a message that contains a number.</span></span>  
  
 <span data-ttu-id="dcdbe-108">本主題將說明作業合約用來描述訊息的各種不同方式。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-108">This topic explains the various ways in which an operation contract can describe messages.</span></span>  
  
## <a name="describing-messages-by-using-parameters"></a><span data-ttu-id="dcdbe-109">使用參數來描述訊息</span><span class="sxs-lookup"><span data-stu-id="dcdbe-109">Describing Messages by Using Parameters</span></span>  
 <span data-ttu-id="dcdbe-110">描述訊息最簡單的方式，就是使用參數清單與傳回值。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-110">The simplest way to describe a message is to use a parameter list and the return value.</span></span> <span data-ttu-id="dcdbe-111">在先前的範例中，已使用 `fromCity` 和 `toCity` 字串參數來描述要求訊息，同時使用浮點傳回值來描述回覆訊息。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-111">In the preceding example, the `fromCity` and `toCity` string parameters were used to describe the request message, and the float return value was used to describe the reply message.</span></span> <span data-ttu-id="dcdbe-112">如果傳回值還不足以描述回覆訊息，則會使用 out 參數。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-112">If the return value alone is not enough to describe a reply message, out parameters may be used.</span></span> <span data-ttu-id="dcdbe-113">例如，下列作業在其要求訊息中包含了 `fromCity` 和 `toCity`，並在其回覆訊息中包含了數字與貨幣。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-113">For example, the following operation has `fromCity` and `toCity` in its request message, and a number together with a currency in its reply message:</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 <span data-ttu-id="dcdbe-114">此外，您可以使用參考參數，讓參數同時成為要求與回覆訊息的一部分。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-114">Additionally, you may use reference parameters to make a parameter part of both the request and the reply message.</span></span> <span data-ttu-id="dcdbe-115">參數必須是可以序列化 (轉換為 XML) 的型別。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-115">The parameters must be of types that can be serialized (converted to XML).</span></span> <span data-ttu-id="dcdbe-116">根據預設，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用稱為 <xref:System.Runtime.Serialization.DataContractSerializer> 類別的元件執行此轉換。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-116">By default, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses a component called the <xref:System.Runtime.Serialization.DataContractSerializer> class to perform this conversion.</span></span> <span data-ttu-id="dcdbe-117">支援大多數的基本型別 (例如 `int`、`string`、`float` 和 `DateTime`)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-117">Most primitive types (such as `int`, `string`, `float`, and `DateTime`.) are supported.</span></span> <span data-ttu-id="dcdbe-118">使用者定義型別通常必須具有資料合約。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-118">User-defined types must normally have a data contract.</span></span> <span data-ttu-id="dcdbe-119">如需詳細資訊，請參閱[使用資料合約](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-119">For more information, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
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
  
 <span data-ttu-id="dcdbe-120">有時候，`DataContractSerializer` 並不足以序列化您的型別。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-120">Occasionally, the `DataContractSerializer` is not adequate to serialize your types.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dcdbe-121"> 支援替代的序列化引擎 <xref:System.Xml.Serialization.XmlSerializer> (您也可以使用此引擎來序列化參數)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-121"> supports an alternative serialization engine, the <xref:System.Xml.Serialization.XmlSerializer>, which you can also use to serialize parameters.</span></span> <span data-ttu-id="dcdbe-122"><xref:System.Xml.Serialization.XmlSerializer> 可讓您透過諸如 `XmlAttributeAttribute` 的屬性，針對最後的 XML 格式進行更複雜的控制。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-122">The <xref:System.Xml.Serialization.XmlSerializer> allows you to use more control over the resultant XML using attributes such as the `XmlAttributeAttribute`.</span></span> <span data-ttu-id="dcdbe-123">若要切換為針對特定作業或整個服務使用 <xref:System.Xml.Serialization.XmlSerializer>，請將 <xref:System.ServiceModel.XmlSerializerFormatAttribute> 屬性套用到作業或服務。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-123">To switch to using the <xref:System.Xml.Serialization.XmlSerializer> for a particular operation or for the entire service, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to an operation or a service.</span></span> <span data-ttu-id="dcdbe-124">例如: </span><span class="sxs-lookup"><span data-stu-id="dcdbe-124">For example:</span></span>  
  
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
  
 <span data-ttu-id="dcdbe-125">如需詳細資訊，請參閱[使用 XmlSerializer 類別](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-125">For more information, see [Using the XmlSerializer Class](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span></span> <span data-ttu-id="dcdbe-126">請記住，我們不建議您模仿此處所示做法切換到 <xref:System.Xml.Serialization.XmlSerializer>，除非您有特殊的理由需要按照主題中所述的步驟來執行。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-126">Remember that manually switching to the <xref:System.Xml.Serialization.XmlSerializer> as shown here is not recommended unless you have specific reasons to do so as detailed in that topic.</span></span>  
  
 <span data-ttu-id="dcdbe-127">若要將 .NET 參數名稱從合約名稱中隔離出來，可以使用 <xref:System.ServiceModel.MessageParameterAttribute> 屬性 (Attribute)，並使用 `Name` 屬性 (Property) 來設定合約名稱。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-127">To isolate .NET parameter names from contract names, you can use the <xref:System.ServiceModel.MessageParameterAttribute> attribute, and use the `Name` property to set the contract name.</span></span> <span data-ttu-id="dcdbe-128">例如，下列作業合約等同於本主題中第一個範例。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-128">For example, the following operation contract is equivalent to the first example in this topic.</span></span>  
  
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
  
## <a name="describing-empty-messages"></a><span data-ttu-id="dcdbe-129">描述空的訊息</span><span class="sxs-lookup"><span data-stu-id="dcdbe-129">Describing Empty Messages</span></span>  
 <span data-ttu-id="dcdbe-130">您可以不要填入輸入或參考參數，來描述空的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-130">An empty request message can be described by having no input or reference parameters.</span></span> <span data-ttu-id="dcdbe-131">例如，在 C# 中：</span><span class="sxs-lookup"><span data-stu-id="dcdbe-131">For example in C#:</span></span>  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 <span data-ttu-id="dcdbe-132">例如，在 VB 中：</span><span class="sxs-lookup"><span data-stu-id="dcdbe-132">For example in VB:</span></span>  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 <span data-ttu-id="dcdbe-133">您可以包含一個 `void` 傳回值，且不要填入輸出或參考參數來描述空的回覆訊息。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-133">An empty reply message can be described by having a `void` return type and no output or reference parameters.</span></span> <span data-ttu-id="dcdbe-134">例如在：</span><span class="sxs-lookup"><span data-stu-id="dcdbe-134">For example in:</span></span>  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 <span data-ttu-id="dcdbe-135">這與單向作業不同，例如：</span><span class="sxs-lookup"><span data-stu-id="dcdbe-135">This is different from a one-way operation, such as:</span></span>  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 <span data-ttu-id="dcdbe-136">`SetTemperatureStatus` 作業會傳回空的訊息。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-136">The `SetTemperatureStatus` operation returns an empty message.</span></span> <span data-ttu-id="dcdbe-137">如果在處理輸入訊息時出現問題，此作業可能會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-137">It may return a fault instead if there is a problem processing the input message.</span></span> <span data-ttu-id="dcdbe-138">`SetLightbulbStatus` 作業不會傳回任何項目。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-138">The `SetLightbulbStatus` operation returns nothing.</span></span> <span data-ttu-id="dcdbe-139">您無法從此作業傳送任何錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-139">There is no way to communicate a fault condition from this operation.</span></span>  
  
## <a name="describing-messages-by-using-message-contracts"></a><span data-ttu-id="dcdbe-140">使用訊息合約來描述訊息</span><span class="sxs-lookup"><span data-stu-id="dcdbe-140">Describing Messages by Using Message Contracts</span></span>  
 <span data-ttu-id="dcdbe-141">您可能想要使用單一型別來代表整個訊息。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-141">You may want to use a single type to represent the entire message.</span></span> <span data-ttu-id="dcdbe-142">儘管您可以透過資料合約來達到這個目的，我們還是建議您使用訊息合約，以避免在最後的 XML 中出現不必要包裝層級。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-142">While it is possible to use a data contract for this purpose, the recommended way to do this is to use a message contract—this avoids unnecessary levels of wrapping in the resultant XML.</span></span> <span data-ttu-id="dcdbe-143">此外，訊息合約可讓您針對最後的訊息擁有更廣泛的控制能力。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-143">Additionally, message contracts allow you to exercise more control over resultant messages.</span></span> <span data-ttu-id="dcdbe-144">例如，您可以決定訊息本文以及訊息標頭內應該存在哪些資訊片段。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-144">For instance, you can decide which pieces of information should be in the message body and which should be in the message headers.</span></span> <span data-ttu-id="dcdbe-145">下列範例將說明訊息合約的使用方式。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-145">The following example shows the use of message contracts.</span></span>  
  
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
  
 <span data-ttu-id="dcdbe-146">如需詳細資訊，請參閱[使用訊息合約](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-146">For more information, see [Using Message Contracts](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>  
  
 <span data-ttu-id="dcdbe-147">在先前的範例中，預設仍舊使用 <xref:System.Runtime.Serialization.DataContractSerializer> 類別。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-147">In the previous example, the <xref:System.Runtime.Serialization.DataContractSerializer> class is still used by default.</span></span> <span data-ttu-id="dcdbe-148"><xref:System.Xml.Serialization.XmlSerializer> 類別也可以搭配訊息合約一起使用。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-148">The <xref:System.Xml.Serialization.XmlSerializer> class can also be used with message contracts.</span></span> <span data-ttu-id="dcdbe-149">若要這麼做，請將 <xref:System.ServiceModel.XmlSerializerFormatAttribute> 屬性套用到作業或合約，然後在訊息標頭與本文成員中使用與 <xref:System.Xml.Serialization.XmlSerializer> 類別相容的型別。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-149">To do this, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to either the operation or the contract, and use types compatible with the <xref:System.Xml.Serialization.XmlSerializer> class in the message headers and body members.</span></span>  
  
## <a name="describing-messages-by-using-streams"></a><span data-ttu-id="dcdbe-150">使用資料流來描述訊息</span><span class="sxs-lookup"><span data-stu-id="dcdbe-150">Describing Messages by Using Streams</span></span>  
 <span data-ttu-id="dcdbe-151">另一種用來描述作業中訊息的方法，就是使用作業合約中的 <xref:System.IO.Stream> 類別或是由此類別衍生的類別之一，或將這些類別當成訊息合約本文成員來使用 (在此情況下，此成員必須是唯一的成員)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-151">Another way to describe messages in operations is to use the <xref:System.IO.Stream> class or one of its derived classes in an operation contract or as a message contract body member (it must be the only member in this case).</span></span> <span data-ttu-id="dcdbe-152">如果是傳入的訊息，必須是 `Stream` 型別 (您無法使用衍生的類別)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-152">For incoming messages, the type must be `Stream`—you cannot use derived classes.</span></span>  
  
 <span data-ttu-id="dcdbe-153">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不但不叫用序列化程式，還從資料流直接擷取資料並將其放到傳出的訊息中，或從傳入訊息中擷取資料並將其直接放到資料流中。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-153">Instead of invoking the serializer, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] retrieves data from a stream and puts it directly into an outgoing message, or retrieves data from an incoming message and puts it directly into a stream.</span></span> <span data-ttu-id="dcdbe-154">下列範例說明資料流的使用方式。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-154">The following sample shows the use of streams.</span></span>  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 <span data-ttu-id="dcdbe-155">您無法將 `Stream` 與非資料流資料結合到單一訊息本文中。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-155">You cannot combine `Stream` and non-stream data in a single message body.</span></span> <span data-ttu-id="dcdbe-156">請使用訊息合約，將額外的資料放到訊息標頭中。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-156">Use a message contract to put the extra data in message headers.</span></span> <span data-ttu-id="dcdbe-157">下列範例將說明在定義作業合約時，不正確的資料流使用方式。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-157">The following example shows the incorrect usage of streams when defining the operation contract.</span></span>  
  
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
  
 <span data-ttu-id="dcdbe-158">下列範例將說明在定義作業合約時，正確的資料流使用方式。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-158">The following sample shows the correct usage of streams when defining an operation contract.</span></span>  
  
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
  
 <span data-ttu-id="dcdbe-159">如需詳細資訊，請參閱[大型資料和串流處理](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-159">For more information, see [Large Data and Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="using-the-message-class"></a><span data-ttu-id="dcdbe-160">使用 Message 類別</span><span class="sxs-lookup"><span data-stu-id="dcdbe-160">Using the Message Class</span></span>  
 <span data-ttu-id="dcdbe-161">若要對傳送或收到的訊息擁有完整的程式掌控權，可以直接使用 <xref:System.ServiceModel.Channels.Message> 類別，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-161">To have complete programmatic control over messages sent or received, you can use the <xref:System.ServiceModel.Channels.Message> class directly, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 <span data-ttu-id="dcdbe-162">這是進階的案例中將詳細說明[使用 Message 類別](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-162">This is an advanced scenario, which is described in detail in [Using the Message Class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span></span>  
  
## <a name="describing-fault-messages"></a><span data-ttu-id="dcdbe-163">描述錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="dcdbe-163">Describing Fault Messages</span></span>  
 <span data-ttu-id="dcdbe-164">除了由傳回值與輸出或參考參數所描述的訊息以外，任何非單向的作業至少會傳回兩個可能的訊息：本身的正常回應訊息與錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-164">In addition to the messages that are described by the return value and output or reference parameters, any operation that is not one-way can return at least two possible messages: its normal response message and a fault message.</span></span> <span data-ttu-id="dcdbe-165">請參考下列作業合約。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-165">Consider the following operation contract.</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 <span data-ttu-id="dcdbe-166">此作業可能傳回包含 `float` 數字的正常訊息，或是傳回包含錯誤碼與說明的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-166">This operation may either return a normal message that contains a `float` number, or a fault message that contains a fault code and a description.</span></span> <span data-ttu-id="dcdbe-167">您可以在服務實作中擲回 <xref:System.ServiceModel.FaultException> 來完成。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-167">You can accomplish this by throwing a <xref:System.ServiceModel.FaultException> in your service implementation.</span></span>  
  
 <span data-ttu-id="dcdbe-168">您可以使用 <xref:System.ServiceModel.FaultContractAttribute> 屬性，指定可能的額外錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-168">You can specify additional possible fault messages by using the <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span> <span data-ttu-id="dcdbe-169">額外的錯誤必須可透過 <xref:System.Runtime.Serialization.DataContractSerializer> 來序列化，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-169">The additional faults must be serializable using the <xref:System.Runtime.Serialization.DataContractSerializer>, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="dcdbe-170">這些額外的錯誤可以藉由擲回適當資料合約型別的 <xref:System.ServiceModel.FaultException%601> 來產生。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-170">These additional faults can be generated by throwing a <xref:System.ServiceModel.FaultException%601> of the appropriate data contract type.</span></span> <span data-ttu-id="dcdbe-171">如需詳細資訊，請參閱[處理的例外狀況和錯誤](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-171">For more information, see [Handling Exceptions and Faults](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span></span>  
  
 <span data-ttu-id="dcdbe-172">您無法使用 <xref:System.Xml.Serialization.XmlSerializer> 類別來描述錯誤。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-172">You cannot use the <xref:System.Xml.Serialization.XmlSerializer> class to describe faults.</span></span> <span data-ttu-id="dcdbe-173"><xref:System.ServiceModel.XmlSerializerFormatAttribute> 對錯誤合約沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-173">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> has no effect on fault contracts.</span></span>  
  
## <a name="using-derived-types"></a><span data-ttu-id="dcdbe-174">使用衍生型別</span><span class="sxs-lookup"><span data-stu-id="dcdbe-174">Using Derived Types</span></span>  
 <span data-ttu-id="dcdbe-175">您也許想要在作業或訊息合約中使用基底類型，然後在實際叫用作業時使用衍生型別。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-175">You may want to use a base type in an operation or a message contract, and then use a derived type when actually invoking the operation.</span></span> <span data-ttu-id="dcdbe-176">在此情況下，您必須使用 <xref:System.ServiceModel.ServiceKnownTypeAttribute> 屬性或其他替代機制來允許使用衍生型別。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-176">In this case, you must use either the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute or some alternative mechanism to allow the use of derived types.</span></span> <span data-ttu-id="dcdbe-177">請參考下列作業。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-177">Consider the following operation.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 <span data-ttu-id="dcdbe-178">假定兩種型別 (`Book` 和 `Magazine`) 都是衍生自 `LibraryItem`。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-178">Assume that two types, `Book` and `Magazine`, derive from `LibraryItem`.</span></span> <span data-ttu-id="dcdbe-179">若要在 `IsLibraryItemAvailable` 作業中使用這些型別，請依下列方式變更作業：</span><span class="sxs-lookup"><span data-stu-id="dcdbe-179">To use these types in the `IsLibraryItemAvailable` operation, you can change the operation as follows:</span></span>  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 <span data-ttu-id="dcdbe-180">另外，當預設的 <xref:System.Runtime.Serialization.KnownTypeAttribute> 正在使用時，您可以使用 <xref:System.Runtime.Serialization.DataContractSerializer>，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-180">Alternatively, you can use the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute when the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="dcdbe-181">您可以在使用 <xref:System.Xml.Serialization.XmlIncludeAttribute> 時，使用 <xref:System.Xml.Serialization.XmlSerializer> 屬性。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-181">You can use the <xref:System.Xml.Serialization.XmlIncludeAttribute> attribute when using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
 <span data-ttu-id="dcdbe-182">您可以將 <xref:System.ServiceModel.ServiceKnownTypeAttribute> 屬性套用到作業或整個服務上。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-182">You can apply the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute to an operation or to the entire service.</span></span> <span data-ttu-id="dcdbe-183">它能接受型別或方法名稱，以呼叫並取得已知型別的清單，就像是 <xref:System.Runtime.Serialization.KnownTypeAttribute> 屬性一樣。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-183">It accepts either a type or the name of the method to call to get a list of known types, just like the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span> <span data-ttu-id="dcdbe-184">如需詳細資訊，請參閱[資料合約已知型別](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-184">For more information, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="specifying-the-use-and-style"></a><span data-ttu-id="dcdbe-185">指定使用方式與樣式</span><span class="sxs-lookup"><span data-stu-id="dcdbe-185">Specifying the Use and Style</span></span>  
 <span data-ttu-id="dcdbe-186">在使用 Web 服務描述語言 (WSDL) 來描述服務時，最常用到的兩種樣式就是文件與遠端程序呼叫 (RPC)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-186">When describing services using Web Services Description Language (WSDL), the two commonly used styles are Document and remote procedure call (RPC).</span></span> <span data-ttu-id="dcdbe-187">在文件樣式中，整個訊息本文會透過結構描述來描述，而 WSDL 則是藉由參照結構描述中的項目來描述不同的訊息本文部分。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-187">In the Document style, the entire message body is described using the schema, and the WSDL describes the various message body parts by referring to elements within that schema.</span></span> <span data-ttu-id="dcdbe-188">在 RPC 樣式中，WSDL 會參照每個訊息部分的結構描述型別 (而不是項目)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-188">In the RPC style, the WSDL refers to a schema type for each message part rather than an element.</span></span> <span data-ttu-id="dcdbe-189">在某些情況下，您必須手動選取其中一種樣式。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-189">In some cases, you have to manually select one of these styles.</span></span> <span data-ttu-id="dcdbe-190">您可以套用 <xref:System.ServiceModel.DataContractFormatAttribute> 屬性，並設定 `Style` 屬性 (當 <xref:System.Runtime.Serialization.DataContractSerializer> 正在使用時)，或是在 `Style` 屬性上設定 <xref:System.ServiceModel.XmlSerializerFormatAttribute> (當使用 <xref:System.Xml.Serialization.XmlSerializer> 時)，來完成。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-190">You can do this by applying the <xref:System.ServiceModel.DataContractFormatAttribute> attribute and setting the `Style` property (when the <xref:System.Runtime.Serialization.DataContractSerializer> is in use), or by setting `Style` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute (when using the <xref:System.Xml.Serialization.XmlSerializer>).</span></span>  
  
 <span data-ttu-id="dcdbe-191">另外，<xref:System.Xml.Serialization.XmlSerializer> 支援兩種格式的序列化 XML：`Literal` 和 `Encoded`。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-191">Additionally, the <xref:System.Xml.Serialization.XmlSerializer> supports two forms of serialized XML: `Literal` and `Encoded`.</span></span> <span data-ttu-id="dcdbe-192">`Literal` 是最普遍接受的格式，也是 <xref:System.Runtime.Serialization.DataContractSerializer> 唯一支援的格式。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-192">`Literal` is the most commonly accepted form, and is the only form the <xref:System.Runtime.Serialization.DataContractSerializer> supports.</span></span> <span data-ttu-id="dcdbe-193">`Encoded` 是 SOAP 規範第 5 節所描述的舊版格式，不建議在新的服務上使用。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-193">`Encoded` is a legacy form described in section 5 of the SOAP specification, and is not recommended for new services.</span></span> <span data-ttu-id="dcdbe-194">若要切換至 `Encoded` 模式，請將 `Use` 屬性 (Attribute) 上的 <xref:System.ServiceModel.XmlSerializerFormatAttribute> 屬性 (Property) 設為 `Encoded`。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-194">To switch to `Encoded` mode, set the `Use` property on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to `Encoded`.</span></span>  
  
 <span data-ttu-id="dcdbe-195">在大部分情況下，您不應該變更 `Style` 和 `Use` 屬性的預設設定。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-195">In most cases, you should not change the default settings for the `Style` and `Use` properties.</span></span>  
  
## <a name="controlling-the-serialization-process"></a><span data-ttu-id="dcdbe-196">控制序列化處理序</span><span class="sxs-lookup"><span data-stu-id="dcdbe-196">Controlling the Serialization Process</span></span>  
 <span data-ttu-id="dcdbe-197">您可以用很多方法來自訂資料的序列化方式。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-197">You can do a number of things to customize the way data is serialized.</span></span>  
  
### <a name="changing-server-serialization-settings"></a><span data-ttu-id="dcdbe-198">變更伺服器序列化設定</span><span class="sxs-lookup"><span data-stu-id="dcdbe-198">Changing Server Serialization Settings</span></span>  
 <span data-ttu-id="dcdbe-199">當預設的 <xref:System.Runtime.Serialization.DataContractSerializer> 正在使用中，您可以藉由將 <xref:System.ServiceModel.ServiceBehaviorAttribute> 屬性套用到服務，來控制序列化處理序的某些層面。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-199">When the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, you can control some aspects of the serialization process on the service by applying the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the service.</span></span> <span data-ttu-id="dcdbe-200">具體來說，您可以使用 `MaxItemsInObjectGraph` 屬性來設定配額，以限制 <xref:System.Runtime.Serialization.DataContractSerializer> 可以還原序列化的最大物件數。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-200">Specifically, you may use the `MaxItemsInObjectGraph` property to set the quota that limits the maximum number of objects the <xref:System.Runtime.Serialization.DataContractSerializer> deserializes.</span></span> <span data-ttu-id="dcdbe-201">您可以使用 `IgnoreExtensionDataObject` 屬性來關閉反覆存取版本控制功能。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-201">You can use the `IgnoreExtensionDataObject` property to turn off the round-tripping versioning feature.</span></span> <span data-ttu-id="dcdbe-202">如需有關配額的詳細資訊，請參閱[資料的安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-202">For more information about quotas, see [Security Considerations for Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span></span> <span data-ttu-id="dcdbe-203">如需反覆存取的詳細資訊，請參閱[向前相容資料合約](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-203">For more information about round-tripping, see [Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span></span>  
  
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
  
### <a name="serialization-behaviors"></a><span data-ttu-id="dcdbe-204">序列化行為</span><span class="sxs-lookup"><span data-stu-id="dcdbe-204">Serialization Behaviors</span></span>  
 <span data-ttu-id="dcdbe-205">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 提供兩個可用的行為，分別是 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> 和 <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>，而這兩個行為會根據特定作業所使用的序列化程式自動插入。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-205">Two behaviors are available in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> and the <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> that are automatically plugged in depending on which serializer is in use for a particular operation.</span></span> <span data-ttu-id="dcdbe-206">由於這些行為是自動套用的，一般來說您不需要知道它們的存在。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-206">Because these behaviors are applied automatically, you normally do not have to be aware of them.</span></span>  
  
 <span data-ttu-id="dcdbe-207">然而，`DataContractSerializerOperationBehavior` 具有 `MaxItemsInObjectGraph`、`IgnoreExtensionDataObject`，和 `DataContractSurrogate` 屬性，可供您用來自訂序列化處理序。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-207">However, the `DataContractSerializerOperationBehavior` has the `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, and `DataContractSurrogate` properties that you may use to customize the serialization process.</span></span> <span data-ttu-id="dcdbe-208">開頭的兩個屬性具有如上一節所述相同的意義。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-208">The first two properties have the same meaning as discussed in the previous section.</span></span> <span data-ttu-id="dcdbe-209">您可以使用 `DataContractSurrogate` 屬性來啟用資料合約替代，這是一項功能強大的機制，可供您用來自訂與延伸序列化處理序。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-209">You can use the `DataContractSurrogate` property to enable data contract surrogates, which are a powerful mechanism for customizing and extending the serialization process.</span></span> <span data-ttu-id="dcdbe-210">如需詳細資訊，請參閱[資料合約 Surrogate](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-210">For more information, see [Data Contract Surrogates](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span></span>  
  
 <span data-ttu-id="dcdbe-211">您可以使用 `DataContractSerializerOperationBehavior` 來同時自訂用戶端與伺服器序列化。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-211">You can use the `DataContractSerializerOperationBehavior` to customize both client and server serialization.</span></span> <span data-ttu-id="dcdbe-212">下列範例說明如何增加用戶端上的 `MaxItemsInObjectGraph` 配額。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-212">The following example shows how to increase the `MaxItemsInObjectGraph` quota on the client.</span></span>  
  
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
  
 <span data-ttu-id="dcdbe-213">下列為相等的服務程式碼 (適用自我裝載案例)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-213">Following is the equivalent code on the service, in the self-hosted case.</span></span>  
  
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
  
 <span data-ttu-id="dcdbe-214">在 Web 裝載案例中，您可以建立新的 `ServiceHost` 衍生類別，並透過服務主機處理站來將之插入。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-214">In the Web-hosted case, you must create a new `ServiceHost` derived class and use a service host factory to plug it in.</span></span>  
  
### <a name="controlling-serialization-settings-in-configuration"></a><span data-ttu-id="dcdbe-215">控制組態中的序列化設定</span><span class="sxs-lookup"><span data-stu-id="dcdbe-215">Controlling Serialization Settings in Configuration</span></span>  
 <span data-ttu-id="dcdbe-216">您可以使用 `MaxItemsInObjectGraph` 端點或服務行為，並透過組態來控制 `IgnoreExtensionDataObject` 和 `dataContractSerializer`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-216">The `MaxItemsInObjectGraph` and `IgnoreExtensionDataObject` can be controlled through configuration by using the `dataContractSerializer` endpoint or service behavior, as shown in the following example.</span></span>  
  
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
            <endpoint address=http://example.com/myservice  
                  behaviorConfiguration="LargeQuotaBehavior"  
                binding="basicHttpBinding" bindingConfiguration=""   
                            contract="IDataService"  
                name="" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a><span data-ttu-id="dcdbe-217">共用型別序列化、物件圖形保留，與自訂序列化程式</span><span class="sxs-lookup"><span data-stu-id="dcdbe-217">Shared Type Serialization, Object Graph Preservation, and Custom Serializers</span></span>  
 <span data-ttu-id="dcdbe-218"><xref:System.Runtime.Serialization.DataContractSerializer> 使用資料合約名稱，而不是 .NET 型別名稱來序列化。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-218">The <xref:System.Runtime.Serialization.DataContractSerializer> serializes using data contract names and not .NET type names.</span></span> <span data-ttu-id="dcdbe-219">這個做法與服務導向的架構原則相符，而且具有相當大的彈性—.NET 型別可以在不影響 Wire 合約的前提下進行變更。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-219">This is consistent with service-oriented architecture tenets and allows for a great degree of flexibility—the .NET types can change without affecting the wire contract.</span></span> <span data-ttu-id="dcdbe-220">在很罕見的情況下，您會想要序列化實際的 .NET 型別名稱，以便讓用戶端與伺服器緊密結合在一起 (與 .NET Framework 遠端處理技術類似)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-220">In rare cases, you may want to serialize actual .NET type names, thereby introducing a tight coupling between the client and the server, similar to the .NET Framework remoting technology.</span></span> <span data-ttu-id="dcdbe-221">除了當您需要從 .NET Framework 遠端處理移轉至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 時以外 (這種情況非常罕見)，我們不建議您這麼做。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-221">This is not a recommended practice, except in rare cases that usually occur when migrating to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] from .NET Framework remoting.</span></span> <span data-ttu-id="dcdbe-222">在此情況中，您必須使用 <xref:System.Runtime.Serialization.NetDataContractSerializer> 類別，而不是使用 <xref:System.Runtime.Serialization.DataContractSerializer> 類別。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-222">In this case, you must use the <xref:System.Runtime.Serialization.NetDataContractSerializer> class instead of the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 <span data-ttu-id="dcdbe-223">一般來說，<xref:System.Runtime.Serialization.DataContractSerializer> 會將物件圖形序列化為物件樹。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-223">The <xref:System.Runtime.Serialization.DataContractSerializer> normally serializes object graphs as object trees.</span></span> <span data-ttu-id="dcdbe-224">亦即，如果相同的物件被參照一次以上，就會不只一次被序列化。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-224">That is, if the same object is referred to more than once, it is serialized more than once.</span></span> <span data-ttu-id="dcdbe-225">例如，某個 `PurchaseOrder` 執行個體具有兩個稱為 `billTo` 和 `shipTo` 的 Address 型別欄位。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-225">For example, consider a `PurchaseOrder` instance that has two fields of type Address called `billTo` and `shipTo`.</span></span> <span data-ttu-id="dcdbe-226">如果兩個欄位同時設定為相同的 Address 執行個體，就會在序列化與還原序列化之後出現兩個一模一樣的 Address 執行個體。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-226">If both fields are set to the same Address instance, there are two identical Address instances after serialization and deserialization.</span></span> <span data-ttu-id="dcdbe-227">這是因為 XML 中沒有可表示物件圖形的標準互通方式 (除了 <xref:System.Xml.Serialization.XmlSerializer> 所提供的舊版 SOAP 編碼標準以外，如先前有關`Style`與`Use`的小節說明所示)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-227">This is done because there is no standard interoperable way to represent object graphs in XML (except for the legacy SOAP encoded standard available on the <xref:System.Xml.Serialization.XmlSerializer>, as described in the previous section on `Style` and `Use`).</span></span> <span data-ttu-id="dcdbe-228">將物件圖形序列化為物件樹會產生特定的缺點，例如，您無法序列化帶有循環參照的圖形。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-228">Serializing object graphs as trees has certain disadvantages, for example, graphs with circular references cannot be serialized.</span></span> <span data-ttu-id="dcdbe-229">有時候您還得切換到真實物件圖形序列化，就算此作業無法互通也得照辦。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-229">Occasionally, it is necessary to switch to true object graph serialization, even though it is not interoperable.</span></span> <span data-ttu-id="dcdbe-230">您可以使用 <xref:System.Runtime.Serialization.DataContractSerializer> (透過將 `preserveObjectReferences` 參數設為 `true` 來加以建構) 來完成。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-230">This can be done by using the <xref:System.Runtime.Serialization.DataContractSerializer> constructed with the `preserveObjectReferences` parameter set to `true`.</span></span>  
  
 <span data-ttu-id="dcdbe-231">有時候內建的序列化程式可能無法滿足您的案例需求。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-231">Occasionally, the built-in serializers are not enough for your scenario.</span></span> <span data-ttu-id="dcdbe-232">在大部分情況下，您仍舊可以使用 <xref:System.Runtime.Serialization.XmlObjectSerializer> 抽取作業，來同時衍生 <xref:System.Runtime.Serialization.DataContractSerializer> 和 <xref:System.Runtime.Serialization.NetDataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-232">In most cases, you can still use the <xref:System.Runtime.Serialization.XmlObjectSerializer> abstraction from which both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Runtime.Serialization.NetDataContractSerializer> derive.</span></span>  
  
 <span data-ttu-id="dcdbe-233">前三個案例 (.NET 型別保留、物件圖形保留，與完整自訂 `XmlObjectSerializer` 式序列化) 皆需插入自訂序列化程式。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-233">The previous three cases (.NET type preservation, object graph preservation, and completely custom `XmlObjectSerializer`-based serialization) all require a custom serializer be plugged in.</span></span> <span data-ttu-id="dcdbe-234">若要執行這項操作，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="dcdbe-234">To do this, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="dcdbe-235">撰寫自己的行為 (衍生自 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-235">Write your own behavior deriving from the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span></span>  
  
2.  <span data-ttu-id="dcdbe-236">覆寫兩個 `CreateSerializer` 方法來傳回自己的序列化程式 (可能是 <xref:System.Runtime.Serialization.NetDataContractSerializer>、<xref:System.Runtime.Serialization.DataContractSerializer> 設為 `preserveObjectReferences` 的 `true`，或是自己的自訂 <xref:System.Runtime.Serialization.XmlObjectSerializer>)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-236">Override the two `CreateSerializer` methods to return your own serializer (either the <xref:System.Runtime.Serialization.NetDataContractSerializer>, the <xref:System.Runtime.Serialization.DataContractSerializer> with `preserveObjectReferences` set to `true`, or your own custom <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span></span>  
  
3.  <span data-ttu-id="dcdbe-237">在開啟服務主機或是建立用戶端通道之前，請移除現有的 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> 行為並插入您在先前步驟所建立的自訂衍生類別。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-237">Before opening the service host or creating a client channel, remove the existing <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> behavior and plug in the custom derived class that you created in the previous steps.</span></span>  
  
 <span data-ttu-id="dcdbe-238">如需進階的序列化概念的詳細資訊，請參閱[序列化和還原序列化](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)。</span><span class="sxs-lookup"><span data-stu-id="dcdbe-238">For more information about advanced serialization concepts, see [Serialization and Deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcdbe-239">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcdbe-239">See Also</span></span>  
 [<span data-ttu-id="dcdbe-240">使用 XmlSerializer 類別</span><span class="sxs-lookup"><span data-stu-id="dcdbe-240">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 [<span data-ttu-id="dcdbe-241">如何：啟用資料流</span><span class="sxs-lookup"><span data-stu-id="dcdbe-241">How to: Enable Streaming</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)  
 [<span data-ttu-id="dcdbe-242">如何：建立類別或結構的基本資料合約</span><span class="sxs-lookup"><span data-stu-id="dcdbe-242">How to: Create a Basic Data Contract for a Class or Structure</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
