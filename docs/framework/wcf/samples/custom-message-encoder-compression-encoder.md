---
title: 自訂訊息編碼器：壓縮編碼器
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: b70875e385fa32256476f6d1ae53e8cc1f5ff9de
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43735870"
---
# <a name="custom-message-encoder-compression-encoder"></a><span data-ttu-id="4e3a6-102">自訂訊息編碼器：壓縮編碼器</span><span class="sxs-lookup"><span data-stu-id="4e3a6-102">Custom Message Encoder: Compression Encoder</span></span>
<span data-ttu-id="4e3a6-103">此範例示範如何實作自訂編碼器，使用 Windows Communication Foundation (WCF) 平台。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-103">This sample demonstrates how to implement a custom encoder using the Windows Communication Foundation (WCF) platform.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4e3a6-104">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4e3a6-105">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4e3a6-106">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4e3a6-107">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="sample-details"></a><span data-ttu-id="4e3a6-108">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="4e3a6-108">Sample Details</span></span>  
 <span data-ttu-id="4e3a6-109">這個範例中包括用戶端主控台程式 (.exe)、自我裝載的服務主控台程式 (.exe) 和壓縮訊息編碼器程式庫 (.dll)。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-109">This sample consists of a client console program (.exe), a self-hosted service console program (.exe) and a compression message encoder library (.dll).</span></span> <span data-ttu-id="4e3a6-110">服務會實作定義要求-回覆通訊模式的合約。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-110">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="4e3a6-111">合約是由 `ISampleServer` 介面所定義，而該介面會公開基本字串回應作業 (`Echo` 和 `BigEcho`)。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-111">The contract is defined by the `ISampleServer` interface, which exposes basic string echoing operations (`Echo` and `BigEcho`).</span></span> <span data-ttu-id="4e3a6-112">用戶端會對指定的作業提出同步要求，而服務則會透過重複訊息回覆至用戶端。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-112">The client makes synchronous requests to a given operation and the service replies by repeating the message back to the client.</span></span> <span data-ttu-id="4e3a6-113">主控台視窗上可同時看見用戶端和服務活動。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-113">Client and service activity is visible in the console windows.</span></span> <span data-ttu-id="4e3a6-114">此範例的目的為顯示如何撰寫自訂編碼器，並示範在網路上壓縮訊息的影響。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-114">The intent of this sample is to show how to write a custom encoder and demonstrate the impact of compression of a message on the wire.</span></span> <span data-ttu-id="4e3a6-115">您可以將檢測新增至壓縮訊息編碼器，以計算訊息大小、處理時間或同時計算這兩者。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-115">You can add instrumentation to the compression message encoder to calculate message size, processing time, or both.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e3a6-116">在.NET Framework 4 中，自動解壓縮已啟用 WCF 用戶端上如果伺服器傳送壓縮的回應 （使用 GZip 或 Deflate 之類的演算法建立）。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-116">In the .NET Framework 4, automatic decompression has been enabled on a WCF client if the server is sending a compressed response (created with an algorithm such as GZip or Deflate).</span></span> <span data-ttu-id="4e3a6-117">如果服務在 Internet Information Server (IIS) 中是以 Web 裝載的，則可以為服務將 IIS 設定為傳送壓縮回應。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-117">If the service is Web-hosted in Internet Information Server (IIS), then IIS can be configured for the service to send a compressed response.</span></span> <span data-ttu-id="4e3a6-118">如果需要同時在用戶端和服務上執行壓縮和解壓縮，或者如果服務是自我裝載的，則可以使用此範例。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-118">This sample can be used if the requirement is to do compression and decompression on both the client and the service or if the service is self-hosted.</span></span>  
  
 <span data-ttu-id="4e3a6-119">此範例示範如何建置和整合的 WCF 應用程式的自訂訊息編碼器。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-119">The sample demonstrates how to build and integrate a custom message encoder into a WCF application.</span></span> <span data-ttu-id="4e3a6-120">將同時使用用戶端和服務來部署程式庫 GZipEncoder.dll。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-120">The library GZipEncoder.dll is deployed with both the client and the service.</span></span> <span data-ttu-id="4e3a6-121">這個範例也會顯示壓縮訊息所造成的影響。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-121">This sample also demonstrates the impact of compressing messages.</span></span> <span data-ttu-id="4e3a6-122">GZipEncoder.dll 中的程式碼會示範下列各項：</span><span class="sxs-lookup"><span data-stu-id="4e3a6-122">The code in GZipEncoder.dll demonstrates the following:</span></span>  
  
-   <span data-ttu-id="4e3a6-123">建置自訂編碼器和編碼器處理站。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-123">Building a custom encoder and encoder factory.</span></span>  
  
-   <span data-ttu-id="4e3a6-124">針對自訂編碼器開發繫結項目。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-124">Developing a binding element for a custom encoder.</span></span>  
  
-   <span data-ttu-id="4e3a6-125">使用自訂繫結組態以整合自訂繫結項目。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-125">Using the custom binding configuration for integrating custom binding elements.</span></span>  
  
-   <span data-ttu-id="4e3a6-126">開發自訂組態處理常式，以允許自訂繫結項目的檔案組態。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-126">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>  
  
 <span data-ttu-id="4e3a6-127">如前所述，在自訂編碼器中會實作多個層級。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-127">As indicated previously, there are several layers that are implemented in a custom encoder.</span></span> <span data-ttu-id="4e3a6-128">為了更清楚說明這些層級之間的關係，下列清單中會提供啟動服務的簡化事件順序：</span><span class="sxs-lookup"><span data-stu-id="4e3a6-128">To better illustrate the relationship between each of these layers, a simplified order of events for service start-up is in the following list:</span></span>  
  
1.  <span data-ttu-id="4e3a6-129">啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-129">The server starts.</span></span>  
  
2.  <span data-ttu-id="4e3a6-130">讀取組態資訊。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-130">The configuration information is read.</span></span>  
  
    1.  <span data-ttu-id="4e3a6-131">服務組態註冊自訂組態處理常式。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-131">The service configuration registers the custom configuration handler.</span></span>  
  
    2.  <span data-ttu-id="4e3a6-132">建立及開啟服務主機。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-132">The service host is created and opened.</span></span>  
  
    3.  <span data-ttu-id="4e3a6-133">自訂組態項目建立及傳回自訂繫結項目。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-133">The custom configuration element creates and returns the custom binding element.</span></span>  
  
    4.  <span data-ttu-id="4e3a6-134">自訂繫結項目會建立及傳回訊息編碼器處理站。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-134">The custom binding element creates and returns a message encoder factory.</span></span>  
  
3.  <span data-ttu-id="4e3a6-135">收到訊息。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-135">A message is received.</span></span>  
  
4.  <span data-ttu-id="4e3a6-136">訊息編碼器處理站傳回訊息編碼器，以在訊息中閱讀及寫出回應。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-136">The message encoder factory returns a message encoder for reading in the message and writing out the response.</span></span>  
  
5.  <span data-ttu-id="4e3a6-137">編碼器層會實作為類別處理站。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-137">The encoder layer is implemented as a class factory.</span></span> <span data-ttu-id="4e3a6-138">只需要對自訂編碼器對大眾公開編碼器累別處理站。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-138">Only the encoder class factory must be publicly exposed for the custom encoder.</span></span> <span data-ttu-id="4e3a6-139">建立 <xref:System.ServiceModel.ServiceHost> 或 <xref:System.ServiceModel.ChannelFactory%601> 物件時，繫結項目會傳回處理站物件。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-139">The factory object is returned by the binding element when the <xref:System.ServiceModel.ServiceHost> or <xref:System.ServiceModel.ChannelFactory%601> object is created.</span></span> <span data-ttu-id="4e3a6-140">您可以在緩衝處理或資料流處理模式中操作訊息編碼器。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-140">Message encoders can operate in a buffered or streaming mode.</span></span> <span data-ttu-id="4e3a6-141">這個範例會同時示範緩衝處理模式和資料流處理模式。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-141">This sample demonstrates both buffered mode and streaming mode.</span></span>  
  
 <span data-ttu-id="4e3a6-142">在每個模式中，抽象 `ReadMessage` 類別上會伴隨 `WriteMessage` 和 `MessageEncoder` 方法。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-142">For each mode there is an accompanying `ReadMessage` and `WriteMessage` method on the abstract `MessageEncoder` class.</span></span> <span data-ttu-id="4e3a6-143">主要的編碼工作都會透過這些方法進行。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-143">A majority of the encoding work takes place in these methods.</span></span> <span data-ttu-id="4e3a6-144">此範例會包裝現有的文字和二進位訊息編碼器。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-144">The sample wraps the existing text and binary message encoders.</span></span> <span data-ttu-id="4e3a6-145">這樣可讓範例將訊息之網路表示的讀取和撰寫委派給內部編碼器，並讓壓縮編碼器可壓縮或解壓縮結果。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-145">This allows the sample to delegate the reading and writing of the wire representation of messages to the inner encoder and allows the compression encoder to compress or decompress the results.</span></span> <span data-ttu-id="4e3a6-146">因為沒有任何管線的訊息編碼，這是在 WCF 中使用多個編碼器的唯一模型。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-146">Because there is no pipeline for message encoding, this is the only model for using multiple encoders in WCF.</span></span> <span data-ttu-id="4e3a6-147">一旦解壓縮訊息，產生的訊息就會傳遞至堆疊上層，以供通道堆疊處理。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-147">Once the message has been decompressed, the resulting message is passed up the stack for the channel stack to handle.</span></span> <span data-ttu-id="4e3a6-148">在壓縮期間，產生的已壓縮訊息會直接寫入提供的資料流。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-148">During compression, the resulting compressed message is written directly to the stream provided.</span></span>  
  
 <span data-ttu-id="4e3a6-149">這個範例會使用 Helper 方法 (`CompressBuffer` 和 `DecompressBuffer`)，將緩衝區轉換為資料流以使用 `GZipStream` 類別。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-149">This sample uses helper methods (`CompressBuffer` and `DecompressBuffer`) to perform conversion from buffers to streams to use the `GZipStream` class.</span></span>  
  
 <span data-ttu-id="4e3a6-150">緩衝處理的 `ReadMessage` 和 `WriteMessage` 類別則會使用 `BufferManager` 類別。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-150">The buffered `ReadMessage` and `WriteMessage` classes make use of the `BufferManager` class.</span></span> <span data-ttu-id="4e3a6-151">您只能透過編碼器處理站來存取編碼器。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-151">The encoder is accessible only through the encoder factory.</span></span> <span data-ttu-id="4e3a6-152">抽象 `MessageEncoderFactory` 類別會提供名稱為 `Encoder` 的屬性以讓您存取目前的編碼器，並提供名稱為 `CreateSessionEncoder` 的方法，讓您可建立支援工作階段的編碼器。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-152">The abstract `MessageEncoderFactory` class provides a property named `Encoder` for accessing the current encoder and a method named `CreateSessionEncoder` for creating an encoder that supports sessions.</span></span> <span data-ttu-id="4e3a6-153">您可以在通道支援工作階段的案例中，依序且可靠地使用這類編碼器。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-153">Such an encoder can be used in the scenario where the channel supports sessions, is ordered and is reliable.</span></span> <span data-ttu-id="4e3a6-154">此案例在資料寫入至網路的每個工作階段中，都能達到最佳的效果。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-154">This scenario allows for optimization in each session of the data written to the wire.</span></span> <span data-ttu-id="4e3a6-155">如果不需要這樣做，則不應該多載基底方法。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-155">If this is not desired, the base method should not be overloaded.</span></span> <span data-ttu-id="4e3a6-156">`Encoder` 屬性提供的機制可讓您存取無工作階段的編碼器，並讓 `CreateSessionEncoder` 方法的預設實作可傳回屬性的值。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-156">The `Encoder` property provides a mechanism for accessing the session-less encoder and the default implementation of the `CreateSessionEncoder` method returns the value of the property.</span></span> <span data-ttu-id="4e3a6-157">由於範例會包裝現有的編碼器以提供壓縮功能，`MessageEncoderFactory` 實作便會接受表示內部編碼器處理站的 `MessageEncoderFactory`。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-157">Because the sample wraps an existing encoder to provide compression, the `MessageEncoderFactory` implementation accepts a `MessageEncoderFactory` that represents the inner encoder factory.</span></span>  
  
 <span data-ttu-id="4e3a6-158">現在，定義編碼器和編碼器處理站，它們可以搭配 WCF 用戶端和服務。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-158">Now that the encoder and encoder factory are defined, they can be used with a WCF client and service.</span></span> <span data-ttu-id="4e3a6-159">不過，您必須將這些編碼器新增至通道堆疊。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-159">However, these encoders must be added to the channel stack.</span></span> <span data-ttu-id="4e3a6-160">您可以從 <xref:System.ServiceModel.ServiceHost> 和 <xref:System.ServiceModel.ChannelFactory%601> 類別衍生類別，並覆寫 `OnInitialize` 方法以手動新增此編碼器處理站。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-160">You can derive classes from the <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.ChannelFactory%601> classes and override the `OnInitialize` methods to add this encoder factory manually.</span></span> <span data-ttu-id="4e3a6-161">您也可以透過自訂繫結項目來公開編碼器處理站。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-161">You can also expose the encoder factory through a custom binding element.</span></span>  
  
 <span data-ttu-id="4e3a6-162">若要建立新的自訂繫結項目，請從 <xref:System.ServiceModel.Channels.BindingElement> 類別衍生類別。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-162">To create a new custom binding element, derive a class from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="4e3a6-163">會有幾種類型的繫結項目。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-163">There are, however, several types of binding elements.</span></span> <span data-ttu-id="4e3a6-164">若要確定自訂繫結項目已辨識為訊息編碼繫結項目，您也必須實作 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-164">To ensure that the custom binding element is recognized as a message encoding binding element, you also must implement the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span></span> <span data-ttu-id="4e3a6-165"><xref:System.ServiceModel.Channels.MessageEncodingBindingElement> 會公開方法以建立新的訊息編碼器處理站 (`CreateMessageEncoderFactory`)，您會實作此訊息編碼器處理站以傳回相符之訊息編碼器處理站的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-165">The <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> exposes a method for creating a new message encoder factory (`CreateMessageEncoderFactory`), which is implemented to return an instance of the matching message encoder factory.</span></span> <span data-ttu-id="4e3a6-166">此外，<xref:System.ServiceModel.Channels.MessageEncodingBindingElement> 具有可指出定址版本的屬性。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-166">Additionally, the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> has a property to indicate the addressing version.</span></span> <span data-ttu-id="4e3a6-167">由於這個範例會包裝現有的編碼器，範例實作也會包裝現有的編碼器繫結項目，並採用內部編碼器繫結項目做為建構函式的參數，並經由屬性來公開此建構函式。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-167">Because this sample wraps the existing encoders, the sample implementation also wraps the existing encoder binding elements and takes an inner encoder binding element as a parameter to the constructor and exposes it through a property.</span></span> <span data-ttu-id="4e3a6-168">下列範例程式碼會顯示 `GZipMessageEncodingBindingElement` 類別的實作。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-168">The following sample code shows the implementation of the `GZipMessageEncodingBindingElement` class.</span></span>  
  
```  
public sealed class GZipMessageEncodingBindingElement   
                        : MessageEncodingBindingElement //BindingElement  
                        , IPolicyExportExtension  
{  
  
    //We use an inner binding element to store information   
    //required for the inner encoder.  
    MessageEncodingBindingElement innerBindingElement;  
  
        //By default, use the default text encoder as the inner encoder.  
        public GZipMessageEncodingBindingElement()  
            : this(new TextMessageEncodingBindingElement()) { }  
  
    public GZipMessageEncodingBindingElement(MessageEncodingBindingElement messageEncoderBindingElement)  
    {  
        this.innerBindingElement = messageEncoderBindingElement;  
    }  
  
    public MessageEncodingBindingElement InnerMessageEncodingBindingElement  
    {  
        get { return innerBindingElement; }  
        set { innerBindingElement = value; }  
    }  
  
    //Main entry point into the encoder binding element.   
    // Called by WCF to get the factory that creates the  
    //message encoder.  
    public override MessageEncoderFactory CreateMessageEncoderFactory()  
    {  
        return new   
GZipMessageEncoderFactory(innerBindingElement.CreateMessageEncoderFactory());  
    }  
  
    public override MessageVersion MessageVersion  
    {  
        get { return innerBindingElement.MessageVersion; }  
        set { innerBindingElement.MessageVersion = value; }  
    }  
  
    public override BindingElement Clone()  
    {  
        return new   
        GZipMessageEncodingBindingElement(this.innerBindingElement);  
    }  
  
    public override T GetProperty<T>(BindingContext context)  
    {  
        if (typeof(T) == typeof(XmlDictionaryReaderQuotas))  
        {  
            return innerBindingElement.GetProperty<T>(context);  
        }  
        else   
        {  
            return base.GetProperty<T>(context);  
        }  
    }  
  
    public override IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
    {  
        if (context == null)  
            throw new ArgumentNullException("context");  
  
        context.BindingParameters.Add(this);  
        return context.BuildInnerChannelFactory<TChannel>();  
    }  
  
    public override IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
    {  
        if (context == null)  
            throw new ArgumentNullException("context");  
  
        context.BindingParameters.Add(this);  
        return context.BuildInnerChannelListener<TChannel>();  
    }  
  
    public override bool CanBuildChannelListener<TChannel>(BindingContext context)  
    {  
        if (context == null)  
            throw new ArgumentNullException("context");  
  
        context.BindingParameters.Add(this);  
        return context.CanBuildInnerChannelListener<TChannel>();  
    }  
  
    void IPolicyExportExtension.ExportPolicy(MetadataExporter exporter, PolicyConversionContext policyContext)  
    {  
        if (policyContext == null)  
        {  
            throw new ArgumentNullException("policyContext");  
        }  
       XmlDocument document = new XmlDocument();  
       policyContext.GetBindingAssertions().Add(document.CreateElement(  
            GZipMessageEncodingPolicyConstants.GZipEncodingPrefix,  
            GZipMessageEncodingPolicyConstants.GZipEncodingName,  
            GZipMessageEncodingPolicyConstants.GZipEncodingNamespace));  
    }  
}  
```  
  
 <span data-ttu-id="4e3a6-169">請注意，`GZipMessageEncodingBindingElement` 類別會實作 `IPolicyExportExtension` 介面，因此此繫結項目便可公開為中繼資料中的原則，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-169">Note that `GZipMessageEncodingBindingElement` class implements the `IPolicyExportExtension` interface, so that this binding element can be exported as a policy in metadata, as shown in the following example.</span></span>  
  
```xml  
<wsp:Policy wsu:Id="BufferedHttpSampleServer_ISampleServer_policy">  
    <wsp:ExactlyOne>  
      <wsp:All>  
        <gzip:text xmlns:gzip=  
        "http://schemas.microsoft.com/ws/06/2004/mspolicy/netgzip1" />   
       <wsaw:UsingAddressing />   
     </wsp:All>  
   </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="4e3a6-170">`GZipMessageEncodingBindingElementImporter` 類別會實作 `IPolicyImportExtension` 介面，而且會匯入 `GZipMessageEncodingBindingElement` 的原則。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-170">The `GZipMessageEncodingBindingElementImporter` class implements the `IPolicyImportExtension` interface, this class imports policy for `GZipMessageEncodingBindingElement`.</span></span> <span data-ttu-id="4e3a6-171">您可以使用 Svcutil.exe 工具將原則匯入組態檔以處理 `GZipMessageEncodingBindingElement`，並應該將下列項目新增至 Svcutil.exe.config。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-171">Svcutil.exe tool can be used to import policies to the configuration file, to handle `GZipMessageEncodingBindingElement`, the following should be added to Svcutil.exe.config.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="gzipMessageEncoding"   
          type=  
            "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </bindingElementExtensions>  
    </extensions>  
    <client>  
      <metadata>  
        <policyImporters>  
          <remove type=  
"System.ServiceModel.Channels.MessageEncodingBindingElementImporter, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
          <extension type=  
"Microsoft.ServiceModel.Samples.GZipMessageEncodingBindingElementImporter, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="4e3a6-172">現在已有用於壓縮編碼器的相符繫結項目，透過建構新的自訂繫結物件並在其中新增自訂繫結項目，便可經由程式設計的方式將相符的繫結項目連結至服務或用戶端，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-172">Now that there is a matching binding element for the compression encoder, it can be programmatically hooked into the service or client by constructing a new custom binding object and adding the custom binding element to it, as shown in the following sample code.</span></span>  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
GZipMessageEncodingBindingElement compBindingElement = new GZipMessageEncodingBindingElement ();  
bindingElements.Add(compBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
binding.Name = "SampleBinding";  
binding.Namespace = "http://tempuri.org/bindings";  
```  
  
 <span data-ttu-id="4e3a6-173">雖然這樣做對大多數使用者案例來說已足夠，但在 Web 裝載服務的情況下，支援檔案組態仍然相當重要。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-173">While this may be sufficient for the majority of user scenarios, supporting a file configuration is critical if a service is to be Web-hosted.</span></span> <span data-ttu-id="4e3a6-174">若要支援 Web 裝載的案例，您必須開發自訂組態處理常式，讓自訂繫結項目可在檔案中進行設定。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-174">To support the Web-hosted scenario, you must develop a custom configuration handler to allow a custom binding element to be configurable in a file.</span></span>  
  
 <span data-ttu-id="4e3a6-175">您可以在 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] 提供的組態系統最上方，建立用於繫結項目的組態處理常式。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-175">You can build a configuration handler for the binding element on top of the configuration system provided by the [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span> <span data-ttu-id="4e3a6-176">繫結項目的組態處理常式必須衍生自 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> 類別。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-176">The configuration handler for the binding element must derive from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="4e3a6-177">您可以使用 `BindingElementType` 屬性，對組態系統通知要對此區段建立的繫結項目型別。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-177">The `BindingElementType` property is used to inform the configuration system of the type of binding element to create for this section.</span></span> <span data-ttu-id="4e3a6-178">`BindingElement` 中可以設定的所有項目，都應該公開為 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> 衍生類別中的屬性。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-178">All aspects of the `BindingElement` that can be set should be exposed as properties in the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class.</span></span> <span data-ttu-id="4e3a6-179">您可以使用 <xref:System.Configuration.ConfigurationPropertyAttribute>，在遺失屬性 (Attribute) 的情況下，幫助將組態項目屬性 (Attribute) 對應至屬性 (Properties) 並設定預設值。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-179">The <xref:System.Configuration.ConfigurationPropertyAttribute> is used to assist in mapping the configuration element attributes to the properties and setting default values if attributes are missing.</span></span> <span data-ttu-id="4e3a6-180">載入來自組態的值並將這些值套用至屬性時，就會呼叫 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> 方法，而這個方法會將屬性轉換為繫結項目的具象執行個體。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-180">After the values from configuration are loaded and applied to the properties, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span> <span data-ttu-id="4e3a6-181">您可以使用 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> 方法，將 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> 衍生類別上的屬性轉換為要在新建立之繫結元素上設定的值。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-181">The <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> method is used to convert the properties on the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class into the values to be set on the newlycreated binding element.</span></span>  
  
 <span data-ttu-id="4e3a6-182">下列範例程式碼會顯示 `GZipMessageEncodingElement` 實作。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-182">The following sample code shows the implementation of the `GZipMessageEncodingElement`.</span></span>  
  
```  
public class GZipMessageEncodingElement : BindingElementExtensionElement  
{  
    public GZipMessageEncodingElement()  
    {  
    }  
  
//Called by the WCF to discover the type of binding element this   
//config section enables  
    public override Type BindingElementType  
    {  
        get { return typeof(GZipMessageEncodingBindingElement); }  
    }  
  
    //The only property we need to configure for our binding element is   
    //the type of inner encoder to use. Here, we support text and  
    //binary.  
    [ConfigurationProperty("innerMessageEncoding",   
                         DefaultValue = "textMessageEncoding")]  
    public string InnerMessageEncoding  
    {  
        get { return (string)base["innerMessageEncoding"]; }  
        set { base["innerMessageEncoding"] = value; }  
    }  
  
    //Called by the WCF to apply the configuration settings (the   
    //property above) to the binding element  
    public override void ApplyConfiguration(BindingElement bindingElement)  
    {  
        GZipMessageEncodingBindingElement binding =   
                (GZipMessageEncodingBindingElement)bindingElement;  
        PropertyInformationCollection propertyInfo =   
                    this.ElementInformation.Properties;  
        if (propertyInfo["innerMessageEncoding"].ValueOrigin !=   
                                     PropertyValueOrigin.Default)  
        {  
            switch (this.InnerMessageEncoding)  
            {  
                case "textMessageEncoding":  
                    binding.InnerMessageEncodingBindingElement =   
                      new TextMessageEncodingBindingElement();  
                    break;  
                case "binaryMessageEncoding":  
                    binding.InnerMessageEncodingBindingElement =   
                         new BinaryMessageEncodingBindingElement();  
                    break;  
            }  
        }  
    }  
  
    //Called by the WCF to create the binding element  
    protected override BindingElement CreateBindingElement()  
    {  
        GZipMessageEncodingBindingElement bindingElement =   
                new GZipMessageEncodingBindingElement();  
        this.ApplyConfiguration(bindingElement);  
        return bindingElement;  
    }  
}   
```  
  
 <span data-ttu-id="4e3a6-183">這個組態處理常式會在服務或用戶端的 App.config 或 Web.config 中對應至下列表示。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-183">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>  
  
```xml  
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />  
```  
  
 <span data-ttu-id="4e3a6-184">若要使用這個組態處理常式，則必須註冊內[ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)項目，如下列範例組態所示。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-184">To use this configuration handler, it must be registered within the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, as shown in the following sample configuration.</span></span>  
  
```xml  
<extensions>  
    <bindingElementExtensions>  
       <add   
           name="gzipMessageEncoding"   
           type=  
           "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement,  
           GZipEncoder, Version=1.0.0.0, Culture=neutral,   
           PublicKeyToken=null" />  
      </bindingElementExtensions>  
</extensions>  
```  
  
 <span data-ttu-id="4e3a6-185">當您執行伺服器時，作業要求和回應會顯示在主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-185">When you run the server, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="4e3a6-186">在每一個視窗中按 ENTER 鍵，關閉伺服器。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-186">Press ENTER in the window to shut down the server.</span></span>  
  
```  
Press Enter key to Exit.  
  
        Server Echo(string input) called:  
        Client message: Simple hello  
  
        Server BigEcho(string[] input) called:  
        64 client messages  
```  
  
 <span data-ttu-id="4e3a6-187">當您執行用戶端時，作業要求和回應會顯示在主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-187">When you run the client, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="4e3a6-188">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-188">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Calling Echo(string):  
Server responds: Simple hello Simple hello  
  
Calling BigEcho(string[]):  
Server responds: Hello 0  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4e3a6-189">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="4e3a6-189">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4e3a6-190">使用下列命令安裝 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0：</span><span class="sxs-lookup"><span data-stu-id="4e3a6-190">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command:</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="4e3a6-191">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-191">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="4e3a6-192">若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-192">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="4e3a6-193">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-193">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4e3a6-194">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-194">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4e3a6-195">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-195">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4e3a6-196">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4e3a6-197">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="4e3a6-197">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="see-also"></a><span data-ttu-id="4e3a6-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e3a6-198">See Also</span></span>
