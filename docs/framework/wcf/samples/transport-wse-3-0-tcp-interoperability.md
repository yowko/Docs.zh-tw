---
title: 傳輸：WSE 3.0 TCP 互通性
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: b727da998736944afd23f7dcfbf45a1f6049d1d0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43533011"
---
# <a name="transport-wse-30-tcp-interoperability"></a>傳輸：WSE 3.0 TCP 互通性
WSE 3.0 TCP 互通性傳輸範例示範如何實作 TCP 雙工工作階段做為自訂的 Windows Communication Foundation (WCF) 傳輸。 也會示範如何使用通道層的擴充性，透過網路與現有的已部署系統相連結。 下列步驟示範如何建置此自訂 WCF 傳輸：  
  
1.  從 TCP 通訊端 (Socket) 開始，建立會使用 DIME 框架來描述訊息界限之 <xref:System.ServiceModel.Channels.IDuplexSessionChannel> 的用戶端和伺服器實作。  
  
2.  建立會連接至 WSE TCP 服務，並透過用戶端 <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s 傳送框架處理訊息的通道處理站。  
  
3.  建立通道接聽程式，以接受連入的 TCP 連線並產生對應的通道。  
  
4.  確認已將所有網路特定例外狀況正規化為適當的 <xref:System.ServiceModel.CommunicationException> 衍生類別。  
  
5.  新增繫結項目，而此繫結項目會將自訂傳輸新增至通道堆疊。 如需詳細資訊，請參閱 [新增繫結項目]。  
  
## <a name="creating-iduplexsessionchannel"></a>建立 IDuplexSessionChannel  
 撰寫 WSE 3.0 TCP 互通性傳輸的第一個步驟，就是在 <xref:System.ServiceModel.Channels.IDuplexSessionChannel> 之上建立 <xref:System.Net.Sockets.Socket> 的實作。 `WseTcpDuplexSessionChannel` 是衍生自 <xref:System.ServiceModel.Channels.ChannelBase>。 傳送訊息的邏輯由兩個主要部分所組成：(1) 將訊息編碼成位元組，以及 (2) 框架處理這些位元組並在網路上傳送。  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 此外也可使用鎖定，讓 Send() 呼叫可依序保留 IDuplexSessionChannel 保證，這樣便可正確地同步處理基礎通訊端的呼叫。  
  
 `WseTcpDuplexSessionChannel` 會使用 <xref:System.ServiceModel.Channels.MessageEncoder>，從 byte[] 來回轉換 <xref:System.ServiceModel.Channels.Message>。 由於這是一種傳輸功能，`WseTcpDuplexSessionChannel` 也會負責套用設定通道所使用的遠端位址。 `EncodeMessage` 會封裝這個轉換的邏輯。  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 一旦將 <xref:System.ServiceModel.Channels.Message> 編碼為位元組，就必須在網路上傳輸。 此時需要系統來定義訊息界限。 WSE 3.0 會使用新版[DIME](https://go.microsoft.com/fwlink/?LinkId=94999)做為其框架通訊協定。 `WriteData` 會封裝框架邏輯，以將 byte[] 包裝在一組 DIME 記錄中。  
  
 接收訊息的邏輯也十分類似。 主要的複雜度是在於處理通訊端讀取會傳回少於所要求之位元組的情況。 若要接收訊息，`WseTcpDuplexSessionChannel` 會讀取網路上的位元組、解碼 DIME 框架，然後使用 <xref:System.ServiceModel.Channels.MessageEncoder> 將 byte[] 轉換為 <xref:System.ServiceModel.Channels.Message>。  
  
 基底 `WseTcpDuplexSessionChannel` 會假設是接收連線的通訊端。 基底類別接著會處理通訊端關閉。 有三個部分與通訊端關閉相關：  
  
-   OnAbort -- 以非正常程序關閉通訊端 (強制關閉)。  
  
-   On[Begin]Close -- 以正常程序關閉通訊端 (軟關閉)。  
  
-   session.CloseOutputSession -- 關閉傳出資料流 (半關閉)。  
  
## <a name="channel-factory"></a>通道處理站  
 撰寫 TCP 傳輸的下一個步驟為，建立用戶端通道的 <xref:System.ServiceModel.Channels.IChannelFactory> 實作。  
  
-   `WseTcpChannelFactory` 衍生自<xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel >。 這是覆寫 `OnCreateChannel` 以產生用戶端通道的處理站。  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
-   `ClientWseTcpDuplexSessionChannel` 將邏輯加入至基底`WseTcpDuplexSessionChannel`連接至 TCP 伺服器在`channel.Open`時間。 首先會將主機名稱解析為 IP 位址，如下列程式碼所示。  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
-   接著將主機名稱連接至迴圈中第一個可用的 IP 位址，如下列程式碼所示。  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
-   包裝網域特定的例外狀況，例如 `SocketException` 中的 <xref:System.ServiceModel.CommunicationException>，以充當為通道合約的一部分。  
  
## <a name="channel-listener"></a>通道接聽程式  
 撰寫 TCP 傳輸的下一個步驟為，建立可接受伺服器通道的 <xref:System.ServiceModel.Channels.IChannelListener> 實作。  
  
-   `WseTcpChannelListener` 衍生自<xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel > 和覆寫 [Begin] Open 和 On [Begin] Close 以控制其接聽通訊端的存留期。 在 OnOpen 中，您會建立通訊端以接聽 IP_ANY。 更進階的實作則可以建立第二個通訊端，就也可以階聽 IPv6。 這些實作也允許在主機名稱中指定 IP 位址。  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 接受新的通訊端時，就會使用此通訊端初始化伺服器通道。 在基底類別中已實作所有輸入和輸出，因此這個通道可以負責初始化通訊端。  
  
## <a name="adding-a-binding-element"></a>新增繫結項目  
 現在已建置處理站和通道，就必須透過繫結公開至 ServiceModel 執行階段。 繫結是繫結項目的集合，表示與服務位址相關聯的通訊堆疊。 堆疊中的每個項目都是由繫結項目表示。  
  
 在此範例中，繫結項目為 `WseTcpTransportBindingElement`，其衍生自 <xref:System.ServiceModel.Channels.TransportBindingElement>。 此繫結項目支援 <xref:System.ServiceModel.Channels.IDuplexSessionChannel> 並會覆寫下列方法，以建置與繫結相關聯的處理站。  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 它還包含可以用來複製 `BindingElement` 以及傳回結構描述 (wse.tcp) 的成員。  
  
## <a name="the-wse-tcp-test-console"></a>WSE TCP 測試主控台  
 您可以在 TestCode.cs 中找到使用這個範例傳輸的測試程式碼。 下列指示說明如何設定 WSE `TcpSyncStockService` 範例。  
  
 測試程式碼會建立使用 MTOM 做為編碼，並使用 `WseTcpTransport` 做為傳輸的自訂繫結。 這也會將 AddressingVersion 設定為符合 WSE 3.0，如下列程式碼所示。  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 其中包含兩個測試：第一個測試會使用 WSE 3.0 WSDL 產生的程式碼來設定具型別的用戶端。 第二項測試會使用 WCF 作為用戶端和伺服器傳送的訊息，直接在通道 Api 之上。  
  
 執行範例時，預期會產生下列輸出。  
  
 用戶端：  
  
```  
Calling soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Symbol: FABRIKAM  
        Name: Fabrikam, Inc.  
        Last Price: 120  
  
Symbol: CONTOSO  
        Name: Contoso Corp.  
        Last Price: 50.07  
Press enter.  
  
Received Action: http://SayHello  
Received Body: to you.  
Hello to you.  
Press enter.  
  
Received Action: http://NotHello  
Received Body: to me.  
Press enter.  
```  
  
 伺服器:  
  
```  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  如果要執行這個範例，您必須已安裝 WSE 3.0 和 WSE `TcpSyncStockService` 範例。 您可以下載[從 MSDN 的 WSE 3.0](https://go.microsoft.com/fwlink/?LinkId=95000)。  
  
> [!NOTE]
>  由於 [!INCLUDE[lserver](../../../../includes/lserver-md.md)] 上不支援 WSE 3.0，因此您無法在該作業系統上安裝或執行 `TcpSyncStockService` 範例。  
  
1.  在安裝 `TcpSyncStockService` 範例之後，請執行下列步驟：  
  
    1.  開啟 Visual Studio 中的 `TcpSyncStockService` (請注意，TcpSyncStockService 範例是隨著 WSE 3.0 一起安裝， 它不屬於此範例程式碼的一部分)。  
  
    2.  將 StockService 專案設定為啟始專案。  
  
    3.  開啟 StockService 專案中的 StockService.cs，並將 `StockService` 類別中的 [Policy] 屬性標記為註解。 這樣就會停用範例的安全性。 雖然 WCF 與 WSE 3.0 安全端點相互操作，將此範例著重於自訂 TCP 傳輸已停用安全性。  
  
    4.  按 F5 以啟動 `TcpSyncStockService`。 將在新主控台視窗中啟動服務。  
  
    5.  在 Visual Studio 中開啟此 TCP 傳輸範例。  
  
    6.  更新 TestCode.cs 中的 "hostname" 變數，以符合執行 `TcpSyncStockService` 的電腦名稱。  
  
    7.  按 F5 以啟動 TCP 傳輸範例。  
  
    8.  會在新主控台中啟動 TCP 傳輸測試用戶端。 用戶端要求積存會從服務進行引用，並在其主控台視窗中顯示結果。  
  
## <a name="see-also"></a>另請參閱
