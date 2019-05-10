---
title: 區塊處理通道
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: 4640135ec693233017bf38548a9b1684d941ff50
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626013"
---
# <a name="chunking-channel"></a>區塊處理通道
傳送使用 Windows Communication Foundation (WCF) 的大型訊息時，它通常會限制用來緩衝處理這些訊息的記憶體數量。 一個可能的方案為以資料流處理訊息本文 (假設本文中有大量資料)。 然而，有些通訊協定需要緩衝處理整個訊息。 例如，可靠的傳訊和安全性。 另一個可能的方案為將較大訊息分成較小的訊息 (稱為區塊 (Chunk))，一次以單一區塊傳送這些區塊，然後在接收端重新構成較大訊息。 應用程式本身便可執行此區塊處理和取消區塊處理，或可以使用自訂通道來進行此作業。 區塊處理通道範例會顯示如何使用自訂通訊協定或層次通道，以便區塊處理和取消區塊處理任意較大訊息。  
  
 區塊處理應該只能在要傳送的整個訊息已建構完成之後運用。 區塊處理通道應該只能是安全性通道和可靠工作階段通道下的一層。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`  
  
## <a name="chunking-channel-assumptions-and-limitations"></a>區塊處理通道假設前提和限制  
  
### <a name="message-structure"></a>訊息結構  
 區塊處理通道會對要區塊處理的訊息假設下列訊息結構：  
  
```xml  
<soap:Envelope ...>  
  <!-- headers -->  
  <soap:Body>  
    <operationElement>  
      <paramElement>data to be chunked</paramElement>  
    </operationElement>  
  </soap:Body>  
</soap:Envelope>  
```  
  
 使用 ServiceModel 時，只有一個輸入參數的合約作業會針對其輸入訊息，遵守此訊息類型。 同樣地，具有一個輸出參數或傳回值的合約作業會針對其輸出訊息，遵守此訊息類型。 下列是這類作業的範例：  
  
```  
[ServiceContract]  
interface ITestService  
{  
    [OperationContract]  
    Stream EchoStream(Stream stream);  
  
    [OperationContract]  
    Stream DownloadStream();  
  
    [OperationContract(IsOneWay = true)]  
    void UploadStream(Stream stream);  
}  
```  
  
### <a name="sessions"></a>工作階段  
 區塊處理通道需要以排序的訊息 (區塊) 傳遞順序，確實傳遞訊息一次。 這表示基礎通道堆疊必須可為工作階段。 傳輸 (例如，TCP 傳輸) 或工作階段通訊協定通道 (例如，ReliableSession 通道) 可提供工作階段。  
  
### <a name="asynchronous-send-and-receive"></a>非同步傳送和接收  
 不會在此版本的區塊處理通道範例中實作非同步傳送和接收方法。  
  
## <a name="chunking-protocol"></a>區塊處理通訊協定  
 區塊處理通道所定義的通訊協定，會指定一連串區塊的開始和結束，以及每個區塊的序號。 下列三個範例訊息會示範開始、區塊和結束訊息，其中的註解會描述每一項的主要概念。  
  
### <a name="start-message"></a>開始訊息  
  
```xml  
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"   
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
<!--Original message action is replaced with a chunking-specific action. -->  
    <a:Action s:mustUnderstand="1">http://samples.microsoft.com/chunkingAction</a:Action>  
<!--  
Original message is assigned a unique id that is transmitted   
in a MessageId header. Note that this is different from the WS-Addressing MessageId header.  
-->  
    <MessageId s:mustUnderstand="1" xmlns="http://samples.microsoft.com/chunking">  
53f183ee-04aa-44a0-b8d3-e45224563109  
</MessageId>  
<!--  
ChunkingStart header signals the start of a chunked message.  
-->  
    <ChunkingStart s:mustUnderstand="1" i:nil="true" xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://samples.microsoft.com/chunking" />  
<!--  
Original message action is transmitted in OriginalAction.  
This is required to re-create the original message on the other side.  
-->  
    <OriginalAction xmlns="http://samples.microsoft.com/chunking">  
http://tempuri.org/ITestService/EchoStream  
    </OriginalAction>  
   <!--  
    All original message headers are included here.  
   -->  
  </s:Header>  
  <s:Body>  
<!--  
Chunking assumes this structure of Body content:  
<element>  
  <childelement>large data to be chunked<childelement>  
</element>  
The start message contains just <element> and <childelement> without  
the data to be chunked.  
-->  
    <EchoStream xmlns="http://tempuri.org/">  
      <stream />  
    </EchoStream>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="chunk-message"></a>區塊訊息  
  
```xml  
<s:Envelope   
  xmlns:a="http://www.w3.org/2005/08/addressing"   
  xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
   <!--  
    All chunking protocol messages have this action.  
   -->  
    <a:Action s:mustUnderstand="1">  
      http://samples.microsoft.com/chunkingAction  
    </a:Action>  
<!--  
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.  
-->  
    <MessageId s:mustUnderstand="1"   
               xmlns="http://samples.microsoft.com/chunking">  
      53f183ee-04aa-44a0-b8d3-e45224563109  
    </MessageId>  
<!--  
The sequence number of the chunk.  
This number restarts at 1 with each new sequence of chunks.  
-->  
    <ChunkNumber s:mustUnderstand="1"   
                 xmlns="http://samples.microsoft.com/chunking">  
      1096  
    </ChunkNumber>  
  </s:Header>  
  <s:Body>  
<!--  
The chunked data is wrapped in a chunk element.  
The encoding of this data (and the entire message)   
depends on the encoder used. The chunking channel does not mandate an encoding.  
-->  
    <chunk xmlns="http://samples.microsoft.com/chunking">  
kfSr2QcBlkHTvQ==  
    </chunk>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="end-message"></a>結束訊息  
  
```xml  
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"   
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://samples.microsoft.com/chunkingAction  
    </a:Action>  
<!--  
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.  
-->  
    <MessageId s:mustUnderstand="1"   
               xmlns="http://samples.microsoft.com/chunking">  
      53f183ee-04aa-44a0-b8d3-e45224563109  
    </MessageId>  
<!--  
ChunkingEnd header signals the end of a chunk sequence.  
-->  
    <ChunkingEnd s:mustUnderstand="1" i:nil="true"   
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance"   
                 xmlns="http://samples.microsoft.com/chunking" />  
<!--  
ChunkingEnd messages have a sequence number.  
-->  
    <ChunkNumber s:mustUnderstand="1"   
                 xmlns="http://samples.microsoft.com/chunking">  
      79  
    </ChunkNumber>  
  </s:Header>  
  <s:Body>  
<!--  
The ChunkingEnd message has the same <element><childelement> structure  
as the ChunkingStart message.  
-->  
    <EchoStream xmlns="http://tempuri.org/">  
      <stream />  
    </EchoStream>  
  </s:Body>  
</s:Envelope>  
```  
  
## <a name="chunking-channel-architecture"></a>區塊處理通道架構  
 區塊處理通道是一種高層級的 `IDuplexSessionChannel`，並會遵循一般通道架構。 `ChunkingBindingElement` 則可以建置 `ChunkingChannelFactory` 和 `ChunkingChannelListener`。 要求 `ChunkingChannelFactory` 時，可建立 `ChunkingChannel` 的執行個體。 接受新的內部通道時，`ChunkingChannelListener` 會建立 `ChunkingChannel` 的執行個體。 `ChunkingChannel` 本身則是負責傳送和接收訊息。  
  
 在下一個層級中，`ChunkingChannel` 需要數個元件才能實作區塊處理通訊協定。 在傳送端中，通道會使用名稱為 <xref:System.Xml.XmlDictionaryWriter> 且執行實際區塊處理的自訂 `ChunkingWriter`。 `ChunkingWriter` 會使用內部通道直接傳送區塊。 使用自訂 `XmlDictionaryWriter` 可讓您在寫入原始訊息的較大本文時，傳送出區塊。 這表示您不會緩衝處理整個原始訊息。  
  
 ![此圖顯示區塊處理通道傳送架構。](./media/chunking-channel/chunking-channel-send.gif)  
  
 在接收端上，`ChunkingChannel` 會從內部通道提取訊息，並將這些訊息傳遞給自訂 <xref:System.Xml.XmlDictionaryReader> (稱為 `ChunkingReader`)，而這個項目會將傳入的區塊重新構成原始訊息。 `ChunkingChannel` 會將此 `ChunkingReader` 包裝在自訂 `Message` 實作 (稱為 `ChunkingMessage`)，並將此訊息傳回上一層。 `ChunkingReader` 和 `ChunkingMessage` 的組合可讓您在上一層讀取原始訊息本文時，進行取消區塊處理，而不需要緩衝處理整個原始訊息本文。 您可在 `ChunkingReader` 擁有的佇列中，緩衝處理傳入的區塊，最多為已緩衝處理區塊可設定數目的最大值。 達到此上限時，讀取器會等待讓上一層清空佇列中的訊息 (也就是只從原始訊息本文讀取)，或直到到達接收逾時上限為止。  
  
 ![此圖顯示區塊處理通道接收架構。](./media/chunking-channel/chunking-channel-receive.gif)  
  
## <a name="chunking-programming-model"></a>區塊處理程式設計模型  
 服務開發人員可以將 `ChunkingBehavior` 屬性套用至合約內的作業，即可指定要區塊處理的訊息。 屬性 (Attribute) 會公開 `AppliesTo` 屬性 (Property)，讓開發人員指定是否要將區塊處理套用至輸入訊息、輸出訊息或兩者皆套用。 下列範例會示範 `ChunkingBehavior` 屬性的用法：  
  
```  
[ServiceContract]  
interface ITestService  
{  
    [OperationContract]  
    [ChunkingBehavior(ChunkingAppliesTo.Both)]  
    Stream EchoStream(Stream stream);  
  
    [OperationContract]  
    [ChunkingBehavior(ChunkingAppliesTo.OutMessage)]  
    Stream DownloadStream();  
  
    [OperationContract(IsOneWay=true)]  
    [ChunkingBehavior(ChunkingAppliesTo.InMessage)]  
    void UploadStream(Stream stream);  
  
}  
```  
  
 從這個程式設計模型中，`ChunkingBindingElement` 會編譯動作 URI 的清單，而這些動作 URI 會識別要區塊處理的訊息。 每個傳出訊息的動作都會與此清單進行比較，以判斷應該區塊處理訊息或直接傳送訊息。  
  
## <a name="implementing-the-send-operation"></a>實作傳送作業  
 在高層級中，傳送作業會先檢查是否必須區塊處理傳出訊息，如果不需要，會使用內部通道直接傳送訊息。  
  
 如果必須區塊處理訊息，傳送作業會建立新的 `ChunkingWriter`，並在傳出訊息上呼叫 `WriteBodyContents`，以傳遞至此 `ChunkingWriter`。 `ChunkingWriter` 接著會執行訊息區塊處理 (包括將原始訊息標頭複製至開始區塊訊息)，然後使用內部通道傳送區塊。  
  
 一些不太重要的詳細資訊：  
  
- 傳送作業會先呼叫 `ThrowIfDisposedOrNotOpened`，確認已開啟 `CommunicationState`。  
  
- 傳送會經過同步處理，以便每次只會為一個工作階段傳送一個訊息。 傳送區塊處理訊息時，會重設名稱為 `ManualResetEvent` 的 `sendingDone`。 傳送結束區塊訊息之後，就會設定此事件。 傳送方法在嘗試傳送傳出訊息之前，會先等待設定此事件。  
  
- 傳送會鎖定 `CommunicationObject.ThisLock`，以在傳送時避免變更同步狀態。 如需 <xref:System.ServiceModel.Channels.CommunicationObject> 狀態和狀態機器的詳細資訊，請參閱 <xref:System.ServiceModel.Channels.CommunicationObject> 文件。  
  
- 傳遞至傳送作業的逾時會當做整個傳送作業的逾時，而這包括傳送所有區塊。  
  
- 已選擇自訂 <xref:System.Xml.XmlDictionaryWriter> 設計，可避免緩衝處理整個原始訊息本文。 如果要使用 <xref:System.Xml.XmlDictionaryReader> 取得本文上的 `message.GetReaderAtBodyContents`，將會緩衝處理整個本文。 相反地，我們有自訂<xref:System.Xml.XmlDictionaryWriter>傳遞至`message.WriteBodyContents`。 當訊息呼叫寫入器上的 WriteBase64 時，寫入器會將區塊封裝至訊息，然後使用內部通道傳送這些訊息。 傳送區塊之前，會封鎖 WriteBase64。  
  
## <a name="implementing-the-receive-operation"></a>實作接收作業  
 在高層級中，接收作業會先檢查傳入訊息不是 `null`，而且其動做為 `ChunkingAction`。 如果不符合這兩個準則，會從接收作業傳回未變更的訊息。 否則，接收作業會建立新的 `ChunkingReader` 和包裝住的新 `ChunkingMessage` (透過呼叫 `GetNewChunkingMessage`)。 傳回新的 `ChunkingMessage` 之前，接收作業會使用執行緒集區的執行緒來執行 `ReceiveChunkLoop`，而它會呼叫迴圈中的 `innerChannel.Receive`，並在接收結束區塊訊息或達到接收逾時之前將區塊傳回 `ChunkingReader`。  
  
 一些不太重要的詳細資訊：  
  
- 和傳送作業一樣，接收作業會先呼叫 `ThrowIfDisposedOrNotOepned`，確認已開啟 `CommunicationState`。  
  
- 接收也會經過同步處理，以便一次只能從工作階段接收一個訊息。 其重要性在於，一旦接收開始區塊訊息，所有後續接收的訊息預期都會在此新區塊序列內進行區塊處理，直到接收結束區塊訊息為止。 在接收到目前屬於已取消區塊處理之訊息的所有區塊之前，接收作業無法從內部通道中提取訊息。 若要完成此作業，接收作業會使用名稱為 `ManualResetEvent` 的 `currentMessageCompleted`，此項目會在接收結束區塊訊息時設定，並在接收新的開始區塊訊息時重設。  
  
- 和傳送作業不同，接收作業在接收時不會制止同步處理的狀態轉換。 例如，接收時可以呼叫關閉作業，並等待直到完成接收擱置的原始訊息，或達到指定的逾時值為止。  
  
- 傳遞至接收作業的逾時會當做整個接收作業的逾時，而這包括接收所有區塊。  
  
- 如果使用訊息的層級正在以低於傳入區塊訊息的速率使用訊息本文，`ChunkingReader` 會緩衝處理這些傳入區塊，而且最多可緩衝處理 `ChunkingBindingElement.MaxBufferedChunks` 所限制的區塊數。 一旦達到該限制，在使用緩衝處理的區塊或達到接收逾時之前，就不會再從較低層級提取區塊。  
  
## <a name="communicationobject-overrides"></a>CommunicationObject 覆寫  
  
### <a name="onopen"></a>OnOpen  
 `OnOpen` 會呼叫 `innerChannel.Open`，以開啟內部通道。  
  
### <a name="onclose"></a>OnClose  
 `OnClose` 會先將 `stopReceive` 設定為 `true`，以將擱置的 `ReceiveChunkLoop` 標示為停止。 接著會等待`receiveStopped` <xref:System.Threading.ManualResetEvent>，此值會設定當`ReceiveChunkLoop`會停止。 假設在指定的逾時內停止 `ReceiveChunkLoop`，`OnClose` 會利用剩下的逾時呼叫 `innerChannel.Close`。  
  
### <a name="onabort"></a>OnAbort  
 `OnAbort` 會呼叫 `innerChannel.Abort`，以中止內部通道。 如果有擱置的 `ReceiveChunkLoop`，會從擱置的 `innerChannel.Receive` 呼叫中收到例外狀況。  
  
### <a name="onfaulted"></a>OnFaulted  
 通道發生錯誤時，`ChunkingChannel` 不需要特殊行為，因此不會覆寫 `OnFaulted`。  
  
## <a name="implementing-channel-factory"></a>實作通道處理站  
 `ChunkingChannelFactory` 會負責建立 `ChunkingDuplexSessionChannel` 的執行個體，並負責將狀態轉換串聯 (Cascade) 至內部通道處理站。  
  
 `OnCreateChannel` 會使用內部通道處理站來建立 `IDuplexSessionChannel` 內部通道。 接著會建立新的 `ChunkingDuplexSessionChannel`，傳遞此內部通道和要區塊處理的訊息動作清單，以及接收時要緩衝處理的區塊數上限。 要區塊處理的訊息動作清單以及要緩衝處理的區塊數上限，是在其建構函式中傳遞至 `ChunkingChannelFactory` 的兩個參數。 `ChunkingBindingElement` 上的區段會描述取得這些值的位置。  
  
 `OnOpen`、`OnClose`、`OnAbort` 與其非同步對等項目，會在內部通道處理站上呼叫相對應的狀態轉換方法。  
  
## <a name="implementing-channel-listener"></a>實作通道接聽程式  
 `ChunkingChannelListener` 是內部通道接聽程式周圍的包裝函式。 除了該內部通道接聽程式的委派呼叫以外，其主要函式會包裝新的 `ChunkingDuplexSessionChannels` (從內部通道接聽程式接受之通道的周圍)。 會在 `OnAcceptChannel` 和 `OnEndAcceptChannel` 中進行此動作。 新建立的 `ChunkingDuplexSessionChannel` 會傳遞內部通道，以及先前描述的其他參數。  
  
## <a name="implementing-binding-element-and-binding"></a>實作繫結項目和繫結  
 `ChunkingBindingElement` 會負責建立 `ChunkingChannelFactory` 和 `ChunkingChannelListener`。 `ChunkingBindingElement`檢查是否在 T `CanBuildChannelFactory` \<T > 和`CanBuildChannelListener` \<T > 的類型`IDuplexSessionChannel`（僅支援區塊處理通道的通道） 和繫結中的其他繫結項目支援此通道型別。  
  
 `BuildChannelFactory`\<T > 先檢查要求的通道型別可以建置，然後取得要區塊處理的訊息動作清單。 如需詳細資訊，請參閱下列章節。 接著會建立新的 `ChunkingChannelFactory`，並傳遞內部通道處理站 (從 `context.BuildInnerChannelFactory<IDuplexSessionChannel>` 傳回)、訊息動作清單和要緩衝處理的區塊數上限。 從 `MaxBufferedChunks` 屬性取得的區塊數上限會由 `ChunkingBindingElement` 公開。  
  
 `BuildChannelListener<T>` 擁有可建立 `ChunkingChannelListener` 並傳遞至內部通道接聽程式的相似實作。  
  
 此範例中包含範例繫結，名稱為 `TcpChunkingBinding`。 此繫結是由兩個繫結項目所組成：`TcpTransportBindingElement` 和 `ChunkingBindingElement`。 除了公開 `MaxBufferedChunks` 屬性以外，繫結也會設定一些 `TcpTransportBindingElement` 屬性，例如 `MaxReceivedMessageSize` (針對標頭將它設定為 `ChunkingUtils.ChunkSize` + 100KB 位元組)。  
  
 `TcpChunkingBinding` 也會實作 `IBindingRuntimePreferences`，並從 `ReceiveSynchronously` 方法傳回 true，而這個方法指出只會實作同步接收呼叫。  
  
### <a name="determining-which-messages-to-chunk"></a>判斷要區塊處理的訊息  
 區塊處理通道只會區塊處理透過 `ChunkingBehavior` 屬性識別的訊息。 `ChunkingBehavior` 類別會實作 `IOperationBehavior`，並可透過呼叫 `AddBindingParameter` 方法來實作。 在此方法中，`ChunkingBehavior` 會檢查其 `AppliesTo` 屬性的值 (`InMessage`、`OutMessage` 或這兩者)，以判斷應該區塊處理的訊息。 接著會取得每個訊息的動作 (從 `OperationDescription` 上的訊息集合)，並將該動作新增至 `ChunkingBindingParameter` 執行個體中所含的字串集合。 接著會將此 `ChunkingBindingParameter` 新增至提供的 `BindingParameterCollection`。  
  
 當繫結項目建置通道處理站或通道接聽程式時，此 `BindingParameterCollection` 會從 `BindingContext` 內部傳遞至繫結中的每個繫結項目。 `ChunkingBindingElement`的實作`BuildChannelFactory<T>`並`BuildChannelListener<T>`提取此`ChunkingBindingParameter`共`BindingContext’`s `BindingParameterCollection`。 `ChunkingBindingParameter` 中內含的動作集合接著會傳遞至 `ChunkingChannelFactory` 或 `ChunkingChannelListener`，後者接著會將動作集合傳遞至 `ChunkingDuplexSessionChannel`。  
  
## <a name="running-the-sample"></a>執行範例  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 使用下列命令安裝 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0。  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. 請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
3. 若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
4. 若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
5. 先執行 Service.exe，然後執行 Client.exe，再查看兩個主控台視窗上的輸出。  
  
 執行範例時，預期會產生下列輸出。  
  
 用戶端：  
  
```  
Press enter when service is available  
  
 > Sent chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
```  
  
 伺服器：  
  
```  
Service started, press enter to exit  
 < Received chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
```  
