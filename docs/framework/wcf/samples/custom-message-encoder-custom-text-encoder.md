---
title: "自訂訊息編碼器：自訂文字編碼器"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: def37608321923017e17a0296a4351cb951d6726
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="custom-message-encoder-custom-text-encoder"></a><span data-ttu-id="6b63f-102">自訂訊息編碼器：自訂文字編碼器</span><span class="sxs-lookup"><span data-stu-id="6b63f-102">Custom Message Encoder: Custom Text Encoder</span></span>
<span data-ttu-id="6b63f-103">這個範例示範如何使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 來實作自訂文字訊息編碼器。</span><span class="sxs-lookup"><span data-stu-id="6b63f-103">This sample demonstrates how to implement a custom text message encoder using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="6b63f-104">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="6b63f-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6b63f-105">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="6b63f-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6b63f-106">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="6b63f-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6b63f-107">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="6b63f-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`  
  
 <span data-ttu-id="6b63f-108"><xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> 的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 只支援 UTF-8、UTF-16 和 Big Endean Unicode 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="6b63f-108">The <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports only the UTF-8, UTF-16 and Big Endean Unicode encodings.</span></span> <span data-ttu-id="6b63f-109">這個範例中的自訂文字訊息編碼器會支援所有平台支援的字元編碼，這是為達成互通性而可能需要的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="6b63f-109">The custom text message encoder in this sample supports all platform-supported character encoding that may be required for interoperability.</span></span> <span data-ttu-id="6b63f-110">這個範例是由用戶端主控台程式 (.exe)、網際網路資訊服務 (IIS) 裝載的服務程式庫 (.dll) 和文字訊息編碼器程式庫 (.dll) 所組成。</span><span class="sxs-lookup"><span data-stu-id="6b63f-110">The sample consists of a client console program (.exe), a service library (.dll) hosted by Internet Information Services (IIS) and a text message encoder library (.dll).</span></span> <span data-ttu-id="6b63f-111">服務會實作定義要求-回覆通訊模式的合約。</span><span class="sxs-lookup"><span data-stu-id="6b63f-111">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="6b63f-112">合約是由 `ICalculator` 介面所定義，這個介面會公開數學運算作業 (加、減、乘、除)。</span><span class="sxs-lookup"><span data-stu-id="6b63f-112">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="6b63f-113">用戶端會對指定的數學運算作業提出同步要求，服務則會以結果回覆。</span><span class="sxs-lookup"><span data-stu-id="6b63f-113">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="6b63f-114">用戶端和服務都會使用 `CustomTextMessageEncoder`，而不使用預設的 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="6b63f-114">Both client and service uses the `CustomTextMessageEncoder` instead of the default <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span>  
  
 <span data-ttu-id="6b63f-115">自訂編碼器的實作是由訊息編碼器處理站、訊息編碼器、訊息編碼繫結項目和組態處理常式所組成，說明如下：</span><span class="sxs-lookup"><span data-stu-id="6b63f-115">The custom encoder implementation consists of a message encoder factory, a message encoder, a message encoding binding element and a configuration handler, and demonstrates the following:</span></span>  
  
-   <span data-ttu-id="6b63f-116">建置自訂編碼器和編碼器處理站。</span><span class="sxs-lookup"><span data-stu-id="6b63f-116">Building a custom encoder and encoder factory.</span></span>  
  
-   <span data-ttu-id="6b63f-117">建立自訂編碼器的繫結項目。</span><span class="sxs-lookup"><span data-stu-id="6b63f-117">Creating a binding element for a custom encoder.</span></span>  
  
-   <span data-ttu-id="6b63f-118">使用自訂繫結組態以整合自訂繫結項目。</span><span class="sxs-lookup"><span data-stu-id="6b63f-118">Using the custom binding configuration for integrating custom binding elements.</span></span>  
  
-   <span data-ttu-id="6b63f-119">開發自訂組態處理常式，以允許自訂繫結項目的檔案組態。</span><span class="sxs-lookup"><span data-stu-id="6b63f-119">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6b63f-120">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="6b63f-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6b63f-121">使用下列命令安裝 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0。</span><span class="sxs-lookup"><span data-stu-id="6b63f-121">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="6b63f-122">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="6b63f-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="6b63f-123">若要建置此方案，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="6b63f-123">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="6b63f-124">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="6b63f-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="message-encoder-factory-and-the-message-encoder"></a><span data-ttu-id="6b63f-125">訊息編碼器處理站和訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="6b63f-125">Message Encoder Factory and the Message Encoder</span></span>  
 <span data-ttu-id="6b63f-126">開啟 <xref:System.ServiceModel.ServiceHost> 或用戶端通道時，設計階段元件 `CustomTextMessageBindingElement` 會建立 `CustomTextMessageEncoderFactory`。</span><span class="sxs-lookup"><span data-stu-id="6b63f-126">When the <xref:System.ServiceModel.ServiceHost> or the client channel is opened, the design time component `CustomTextMessageBindingElement` creates the `CustomTextMessageEncoderFactory`.</span></span> <span data-ttu-id="6b63f-127">處理站則會建立 `CustomTextMessageEncoder`。</span><span class="sxs-lookup"><span data-stu-id="6b63f-127">The factory creates the `CustomTextMessageEncoder`.</span></span> <span data-ttu-id="6b63f-128">訊息編碼器會同時以資料流處理模式和緩衝模式來運作。</span><span class="sxs-lookup"><span data-stu-id="6b63f-128">The message encoder operates both in the streaming mode and the buffered mode.</span></span> <span data-ttu-id="6b63f-129">它會分別使用 <xref:System.Xml.XmlReader> 和 <xref:System.Xml.XmlWriter> 來讀取和寫入訊息。</span><span class="sxs-lookup"><span data-stu-id="6b63f-129">It uses the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to read and write the messages respectively.</span></span> <span data-ttu-id="6b63f-130">正好與僅支援 UTF-8、UTF-16 和 Big-Endean Unicode 之 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的最佳化 XML 讀取器和寫入器相反，這些讀取器和寫入器會支援所有平台支援的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="6b63f-130">As opposed to the optimized XML readers and writers of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] that support only UTF-8, UTF-16 and Big-Endean Unicode these readers and writers support all platform supported encoding.</span></span>  
  
 <span data-ttu-id="6b63f-131">下列程式碼範例示範 CustomTextMessageEncoder。</span><span class="sxs-lookup"><span data-stu-id="6b63f-131">The following code example shows the CustomTextMessageEncoder.</span></span>  
  
```csharp  
public class CustomTextMessageEncoder : MessageEncoder  
{  
    private CustomTextMessageEncoderFactory factory;  
    private XmlWriterSettings writerSettings;  
    private string contentType;  
  
    public CustomTextMessageEncoder(CustomTextMessageEncoderFactory factory)  
    {  
        this.factory = factory;  
  
        this.writerSettings = new XmlWriterSettings();  
        this.writerSettings.Encoding = Encoding.GetEncoding(factory.CharSet);  
        this.contentType = string.Format("{0}; charset={1}",   
            this.factory.MediaType, this.writerSettings.Encoding.HeaderName);  
    }  
  
    public override string ContentType  
    {  
        get  
        {  
            return this.contentType;  
        }  
    }  
  
    public override string MediaType  
    {  
        get   
        {  
            return factory.MediaType;  
        }  
    }  
  
    public override MessageVersion MessageVersion  
    {  
        get   
        {  
            return this.factory.MessageVersion;  
        }  
    }  
  
    public override Message ReadMessage(ArraySegment<byte> buffer, BufferManager bufferManager, string contentType)  
    {     
        byte[] msgContents = new byte[buffer.Count];  
        Array.Copy(buffer.Array, buffer.Offset, msgContents, 0, msgContents.Length);  
        bufferManager.ReturnBuffer(buffer.Array);  
  
        MemoryStream stream = new MemoryStream(msgContents);  
        return ReadMessage(stream, int.MaxValue);  
    }  
  
    public override Message ReadMessage(Stream stream, int maxSizeOfHeaders, string contentType)  
    {  
        XmlReader reader = XmlReader.Create(stream);  
        return Message.CreateMessage(reader, maxSizeOfHeaders, this.MessageVersion);  
    }  
  
    public override ArraySegment<byte> WriteMessage(Message message, int maxMessageSize, BufferManager bufferManager, int messageOffset)  
    {  
        MemoryStream stream = new MemoryStream();  
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);  
        message.WriteMessage(writer);  
        writer.Close();  
  
        byte[] messageBytes = stream.GetBuffer();  
        int messageLength = (int)stream.Position;  
        stream.Close();  
  
        int totalLength = messageLength + messageOffset;  
        byte[] totalBytes = bufferManager.TakeBuffer(totalLength);  
        Array.Copy(messageBytes, 0, totalBytes, messageOffset, messageLength);  
  
        ArraySegment<byte> byteArray = new ArraySegment<byte>(totalBytes, messageOffset, messageLength);  
        return byteArray;  
    }  
  
    public override void WriteMessage(Message message, Stream stream)  
    {  
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);  
        message.WriteMessage(writer);  
        writer.Close();  
    }  
}  
```  
  
 <span data-ttu-id="6b63f-132">下列程式碼範例示範如何建置訊息編碼器處理站。</span><span class="sxs-lookup"><span data-stu-id="6b63f-132">The following code example shows how to build the message encoder factory.</span></span>  
  
```csharp  
public class CustomTextMessageEncoderFactory : MessageEncoderFactory  
{  
    private MessageEncoder encoder;  
    private MessageVersion version;  
    private string mediaType;  
    private string charSet;  
  
    internal CustomTextMessageEncoderFactory(string mediaType, string charSet,  
        MessageVersion version)  
    {  
        this.version = version;  
        this.mediaType = mediaType;  
        this.charSet = charSet;  
        this.encoder = new CustomTextMessageEncoder(this);  
    }  
  
    public override MessageEncoder Encoder  
    {  
        get   
        {   
            return this.encoder;  
        }  
    }  
  
    public override MessageVersion MessageVersion  
    {  
        get   
        {   
            return this.version;  
        }  
    }  
  
    internal string MediaType  
    {  
        get  
        {  
            return this.mediaType;  
        }  
    }  
  
    internal string CharSet  
    {  
        get  
        {  
            return this.charSet;  
        }  
    }  
}  
```  
  
## <a name="message-encoding-binding-element"></a><span data-ttu-id="6b63f-133">訊息編碼繫結項目</span><span class="sxs-lookup"><span data-stu-id="6b63f-133">Message Encoding Binding Element</span></span>  
 <span data-ttu-id="6b63f-134">繫結項目允許設定 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 執行階段堆疊。</span><span class="sxs-lookup"><span data-stu-id="6b63f-134">The binding elements allow the configuration of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] run-time stack.</span></span> <span data-ttu-id="6b63f-135">為了在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式中使用自訂訊息編碼器，繫結項目必須在執行階段堆疊中的適當層級上使用適當的設定來建立訊息編碼器處理站。</span><span class="sxs-lookup"><span data-stu-id="6b63f-135">To use the custom message encoder in a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, a binding element is required that creates the message encoder factory with the appropriate settings at the appropriate level in the run-time stack.</span></span>  
  
 <span data-ttu-id="6b63f-136">`CustomTextMessageBindingElement` 是從 <xref:System.ServiceModel.Channels.BindingElement> 基底類別衍生，而且繼承自 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> 類別。</span><span class="sxs-lookup"><span data-stu-id="6b63f-136">The `CustomTextMessageBindingElement` derives from the <xref:System.ServiceModel.Channels.BindingElement> base class and inherits from the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> class.</span></span> <span data-ttu-id="6b63f-137">這會讓其他 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 元件將此繫結項目看成是訊息編碼繫結項目。</span><span class="sxs-lookup"><span data-stu-id="6b63f-137">This allows other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] components to recognize this binding element as being a message encoding binding element.</span></span> <span data-ttu-id="6b63f-138"><xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> 的實作會傳回相符之訊息編碼器處理站的執行個體，其中包含適當的設定。</span><span class="sxs-lookup"><span data-stu-id="6b63f-138">The implementation of <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> returns an instance of the matching message encoder factory with appropriate settings.</span></span>  
  
 <span data-ttu-id="6b63f-139">`CustomTextMessageBindingElement` 會透過屬性公開 `MessageVersion`、`ContentType` 和 `Encoding` 的設定。</span><span class="sxs-lookup"><span data-stu-id="6b63f-139">The `CustomTextMessageBindingElement` exposes settings for `MessageVersion`, `ContentType`, and `Encoding` through properties.</span></span> <span data-ttu-id="6b63f-140">編碼器同時支援 Soap11Addressing 和 Soap12Addressing1 版本。</span><span class="sxs-lookup"><span data-stu-id="6b63f-140">The encoder supports both Soap11Addressing and Soap12Addressing1 versions.</span></span> <span data-ttu-id="6b63f-141">預設為 Soap11Addressing1。</span><span class="sxs-lookup"><span data-stu-id="6b63f-141">The default is Soap11Addressing1.</span></span> <span data-ttu-id="6b63f-142">`ContentType` 的預設值為 "text/xml"。</span><span class="sxs-lookup"><span data-stu-id="6b63f-142">The default value of the `ContentType` is "text/xml".</span></span> <span data-ttu-id="6b63f-143">`Encoding` 屬性可讓您設定所需的字元編碼值。</span><span class="sxs-lookup"><span data-stu-id="6b63f-143">The `Encoding` property allows you to set the value of the desired character encoding.</span></span> <span data-ttu-id="6b63f-144">範例用戶端與服務會使用 ISO-8859-1 (Latin1) 字元編碼，但是 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> 的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不支援這種編碼方式。</span><span class="sxs-lookup"><span data-stu-id="6b63f-144">The sample client and service uses the ISO-8859-1 (Latin1) character encoding, which is not supported by the <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="6b63f-145">下列程式碼將示範如何使用自訂文字訊息編碼器，透過程式設計方式建立繫結。</span><span class="sxs-lookup"><span data-stu-id="6b63f-145">The following code shows how to programmatically create the binding using the custom text message encoder.</span></span>  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();  
bindingElements.Add(textBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
```  
  
## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a><span data-ttu-id="6b63f-146">在訊息編碼繫結項目中新增中繼資料支援</span><span class="sxs-lookup"><span data-stu-id="6b63f-146">Adding Metadata Support to the Message Encoding Binding Element</span></span>  
 <span data-ttu-id="6b63f-147">任何衍生自 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> 的型別都會負責更新針對服務所產生之 WSDL 文件中的 SOAP 繫結版本。</span><span class="sxs-lookup"><span data-stu-id="6b63f-147">Any type that derives from <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> is responsible for updating the version of the SOAP binding in the WSDL document generated for the service.</span></span> <span data-ttu-id="6b63f-148">藉由實作 `ExportEndpoint` 介面上的 <xref:System.ServiceModel.Description.IWsdlExportExtension> 方法，再修改產生的 WSDL，即可做到這點。</span><span class="sxs-lookup"><span data-stu-id="6b63f-148">This is done by implementing the `ExportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlExportExtension> interface and then modifying the generated WSDL.</span></span> <span data-ttu-id="6b63f-149">在這個範例中，`CustomTextMessageBindingElement` 將使用 `TextMessageEncodingBinidngElement` 的 WSDL 匯出邏輯。</span><span class="sxs-lookup"><span data-stu-id="6b63f-149">In this sample, the `CustomTextMessageBindingElement` uses the WSDL export logic from the `TextMessageEncodingBinidngElement`.</span></span>  
  
 <span data-ttu-id="6b63f-150">在這個範例中，用戶端組態會以手動方式設定。</span><span class="sxs-lookup"><span data-stu-id="6b63f-150">For this sample, the client configuration is hand configured.</span></span> <span data-ttu-id="6b63f-151">由於 `CustomTextMessageBindingElement` 並不匯出原則判斷提示來描述其行為，您將無法使用 Svcutil.exe 產生用戶端組態。</span><span class="sxs-lookup"><span data-stu-id="6b63f-151">You cannot use Svcutil.exe to generate the client configuration because the `CustomTextMessageBindingElement` does not export a policy assertion to describe its behavior.</span></span> <span data-ttu-id="6b63f-152">您通常應該在自訂繫結項目上實作 <xref:System.ServiceModel.Description.IPolicyExportExtension> 介面，以便匯出可描述繫結項目所實作之行為或功能的自訂原則判斷提示。</span><span class="sxs-lookup"><span data-stu-id="6b63f-152">You should generally implement the <xref:System.ServiceModel.Description.IPolicyExportExtension> interface on a custom binding element to export a custom policy assertion that describes the behavior or capability implemented by the binding element.</span></span> <span data-ttu-id="6b63f-153">如需如何匯出原則判斷提示的自訂繫結元素的範例，請參閱[傳輸： UDP](../../../../docs/framework/wcf/samples/transport-udp.md)範例。</span><span class="sxs-lookup"><span data-stu-id="6b63f-153">For an example of how to export a policy assertion for a custom binding element, see the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
## <a name="message-encoding-binding-configuration-handler"></a><span data-ttu-id="6b63f-154">訊息編碼繫結組態處理常式</span><span class="sxs-lookup"><span data-stu-id="6b63f-154">Message Encoding Binding Configuration Handler</span></span>  
 <span data-ttu-id="6b63f-155">上一個區段示範的是如何以程式設計方式使用自訂文字訊息編碼器。</span><span class="sxs-lookup"><span data-stu-id="6b63f-155">The previous section shows how to use the custom text message encoder programmatically.</span></span> <span data-ttu-id="6b63f-156">`CustomTextMessageEncodingBindingSection` 將會實作可讓您在組態檔中指定自訂文字訊息編碼器使用方式的組態處理常式。</span><span class="sxs-lookup"><span data-stu-id="6b63f-156">The `CustomTextMessageEncodingBindingSection` implements a configuration handler that allows you to specify the use of a custom text message encoder within a configuration file.</span></span> <span data-ttu-id="6b63f-157">`CustomTextMessageEncodingBindingSection` 類別衍生自 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> 類別。</span><span class="sxs-lookup"><span data-stu-id="6b63f-157">The `CustomTextMessageEncodingBindingSection` class derives from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="6b63f-158">`BindingElementType` 屬性會通知組態系統要為此區段建立的繫結項目類型。</span><span class="sxs-lookup"><span data-stu-id="6b63f-158">The `BindingElementType` property informs the configuration system of the type of binding element to create for this section.</span></span>  
  
 <span data-ttu-id="6b63f-159">由 `CustomTextMessageBindingElement` 定義的所有設定都會公開為 `CustomTextMessageEncodingBindingSection` 中的屬性。</span><span class="sxs-lookup"><span data-stu-id="6b63f-159">All of the settings defined by `CustomTextMessageBindingElement` are exposed as the properties in the `CustomTextMessageEncodingBindingSection`.</span></span> <span data-ttu-id="6b63f-160"><xref:System.Configuration.ConfigurationPropertyAttribute> 有助於將組態項目屬性 (Attribute) 對應至屬性 (Property)，並可在屬性 (Attribute) 未設定時設定其預設值。</span><span class="sxs-lookup"><span data-stu-id="6b63f-160">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if the attribute is not set.</span></span> <span data-ttu-id="6b63f-161">載入來自組態的值並將這些值套用至型別的屬性時，就會呼叫 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> 方法，而這個方法會將屬性轉換為繫結項目的實體執行個體。</span><span class="sxs-lookup"><span data-stu-id="6b63f-161">After the values from configuration are loaded and applied to the properties of the type, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span>  
  
 <span data-ttu-id="6b63f-162">這個組態處理常式會在服務或用戶端的 App.config 或 Web.config 中對應至下列表示。</span><span class="sxs-lookup"><span data-stu-id="6b63f-162">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>  
  
```xml  
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />  
```  
  
 <span data-ttu-id="6b63f-163">這個範例會使用 ISO-8859-1 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="6b63f-163">The sample uses the ISO-8859-1 encoding.</span></span>  
  
 <span data-ttu-id="6b63f-164">若要使用這個組態處理常式，您必須先使用下列組態項目加以註冊。</span><span class="sxs-lookup"><span data-stu-id="6b63f-164">To use this configuration handler it must be registered using the following configuration element.</span></span>  
  
```xml  
<extensions>  
    <bindingElementExtensions>  
        <add name="customTextMessageEncoding" type="   
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,   
                  CustomTextMessageEncoder" />  
    </bindingElementExtensions>  
</extensions>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b63f-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b63f-165">See Also</span></span>
