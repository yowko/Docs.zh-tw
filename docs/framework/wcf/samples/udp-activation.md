---
title: UDP 啟用
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: 127516b79bcb15406bfade09bc1309e55aac3dcf
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881010"
---
# <a name="udp-activation"></a>UDP 啟用
此樣本根據[傳輸：UDP](../../../../docs/framework/wcf/samples/transport-udp.md)範例。 它會擴充[傳輸：UDP](../../../../docs/framework/wcf/samples/transport-udp.md)範例，以支援使用 Windows Process Activation Service (WAS) 處理序啟動。  
  
 此範例包含三個主要部分：  
  
- UDP 通訊協定啟動程式，這是代表要啟動之應用程式接收 UDP 訊息的獨立處理序。  
  
- 用戶端，會使用 UDP 自訂傳輸以傳送訊息。  
  
- 服務 (在 WAS 啟動的背景工作處理序中裝載)，會透過 UDP 自訂傳輸來接收訊息。  
  
## <a name="udp-protocol-activator"></a>UDP 通訊協定啟動程式  
 UDP 通訊協定啟動程式是 WCF 用戶端與 WCF 服務之間的橋樑。 可提供在傳輸層中，透過 UDP 通訊協定進行資料通訊。 這個啟動程式有兩個主要功能：  
  
- WAS 接聽程式配接器 (LA)，會與 WAS 共同作業以啟動處理序，進而回應傳入訊息。  
  
- UDP 通訊協定接聽程式，代表要啟動的應用程式接受 UDP 訊息。  
  
 啟動程式必須當做伺服器電腦上的獨立程式來執行。 一般來說，WAS 接聽程式配接器 (例如 NetTcpActivator 和 NetPipeActivator) 會在長時間執行的 Windows 服務中實作。 不過，為了簡化和避免困擾，這個範例會實作通訊協定啟動程式以做為獨立應用程式。  
  
### <a name="was-listener-adapter"></a>WAS 接聽程式配接器  
 會在 `UdpListenerAdapter` 類別中實作 UDP 的 WAS 接聽程式配接器。 這是與 WAS 互動的模組，可對 UDP 通訊協定執行應用程式啟動。 呼叫下列 Webhost API 即可達到此作用：  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 初始呼叫 `WebhostRegisterProtocol` 之後，接聽程式配接器會針對 applicationHost.config (位於 %windir%\system32\inetsrv) 中註冊的所有應用程式，從 WAS 中接收回呼 `ApplicationCreated`。 在此範例中，只會處理已啟用 UDP 通訊協定 (通訊協定識別碼為 "net.udp") 的應用程式。 如果實作回應至應用程式的動態組態變更 (例如，應用程式從已停用轉換為已啟用)，則可能會以不同的方式處理這類實作。  
  
 接收回呼 `ConfigManagerInitializationCompleted` 時，會指出 WAS 已完成初始化通訊協定的所有告知。 此時，接聽程式配接器便準備處理啟動要求。  
  
 第一次有應用程式的新要求時，接聽程式配接器會在 WAS 中呼叫 `WebhostOpenListenerChannelInstance`，而若尚未啟動背景工作處理序，則 WAS 會啟動該處理序。 接著會載入通訊協定處理常式，便可已啟動接聽程式配接器和虛擬應用程式之間的通訊。  
  
 接聽程式配接器在 %SystemRoot%\System32\inetsrv\ApplicationHost.config 中註冊 <`listenerAdapters`> 區段如下所示：  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a>通訊協定接聽程式  
 UDP 通訊協定接聽程式是通訊協定啟動程式內部的模組，會代表虛擬應用程式接聽 UDP 端點。 會在類別 `UdpSocketListener` 中實作此項。 端點會表示為 `IPEndpoint`，而這是針對站台從通訊協定繫結擷取的連接埠號。  
  
### <a name="control-service"></a>控制服務  
 在此範例中，我們可以使用 WCF 啟動程式和 WAS 背景工作處理序之間進行通訊。 常駐在啟動程式中的服務稱為「控制服務」。  
  
## <a name="protocol-handlers"></a>通訊協定處理常式  
 在接聽程式配接器呼叫 `WebhostOpenListenerChannelInstance` 之後，WAS 處理序管理員就會啟動背景工作處理序 (如果尚未啟動)。 背景工作處理序內的應用程式管理員接著會載入 UDP 處理序通訊協定處理常式 (PPH)，以及針對該 `ListenerChannelId` 所發出的要求。 Pph 接著會呼叫`IAdphManager`。`StartAppDomainProtocolListenerChannel` 若要啟動 UDP AppDomain 通訊協定處理常式 (ADPH)。  
  
## <a name="hostedudptransportconfiguration"></a>HostedUDPTransportConfiguration  
 會在 Web.config 中註冊相關資訊，如下所示：  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a>針對本範例的特殊安裝  
 此範例只能在 Windows Vista、Windows Server 2008 或 Windows 7 上建立和執行。 若要執行範例，您必須先正確設定所有元件。 請使用下列步驟來安裝範例。  
  
#### <a name="to-set-up-this-sample"></a>若要安裝這個範例  
  
1. 安裝 ASP.NET 4.0 使用下列命令。  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. 在 Windows Vista 上建置專案。 進行編譯之後，也會在建置後階段中執行下列作業：  
  
    - 將 UDP 繫結安裝至「預設的網站」這個站台。  
  
    - 建立虛擬應用程式 "ServiceModelSamples" 以指向實際路徑："%SystemDrive%\inetpub\wwwroot\servicemodelsamples"。  
  
    - 也會對此虛擬應用程式啟用 "net.udp" 通訊協定。  
  
3. 啟動使用者介面應用程式 "WasNetActivator.exe"。 按一下 **安裝程式**索引標籤上，勾選下列核取方塊，然後按一下**安裝**安裝它們：  
  
    - UDP 接聽程式配接器  
  
    - UDP 通訊協定處理常式  
  
4. 按一下 **啟用**的使用者介面應用程式"WasNetActivator.exe"的索引標籤。 按一下 **啟動**按鈕以啟動接聽程式配接器。 您現在可以準備執行程式。  
  
    > [!NOTE]
    >  完成這個範例時，必須執行 Cleanup.bat 以移除「預設的網站」的 net.udp 繫結。  
  
## <a name="sample-usage"></a>範例用法  
 進行編譯之後，會產生四個不同的二進位碼檔案：  
  
- Client.exe：用戶端程式碼。 App.config 會編譯至用戶端的 Client.exe.config 組態檔。  
  
- UDPActivation.dll：包含所有主要 UDP 實作的程式庫。  
  
- Service.dll:服務程式碼。 這個檔案會複製至虛擬應用程式 ServiceModelSamples 的 \bin 目錄。 服務檔為 Service.svc，而組態檔為 Web.config。進行編譯之後，會將這些檔案複製至下列位置：%SystemDrive%\Inetpub\wwwroot\ServiceModelSamples。  
  
- WasNetActivator:UDP 啟動程式。  
  
- 請確定已正確安裝所有必要的部分。 下列步驟會顯示如何執行範例：  
  
1. 請確定已啟動下列 Windows 服務：  
  
    - Windows Process Activation Service (WAS)。  
  
    - Internet Information Services (IIS):W3SVC.  
  
2. 接著啟動啟動程式：WasNetActivator.exe。 底下**啟用**索引標籤，唯一的通訊協定**UDP**，在下拉式清單中選取。 按一下 [**啟動**] 按鈕來開始啟動程式。  
  
3. 一旦開始執行啟動程式，就可以從命令視窗中執行 Client.exe 以執行用戶端程式碼。 下列是範例輸出：  
  
    ```  
    Testing Udp Activation.  
    Start the status service.  
    Sending UDP datagrams.  
    Type a word that you want to say to the server: Hello, world!  
        Sending datagram: Hello, world![0]  
        Sending datagram: Hello, world![1]  
        Sending datagram: Hello, world![2]  
        Sending datagram: Hello, world![3]  
        Sending datagram: Hello, world![4]  
    Calling UDP duplex contract (ICalculatorContract).  
        0 + 0 = 0  
        1 + 2 = 3  
        2 + 4 = 6  
        3 + 6 = 9  
        4 + 8 = 12  
    Getting status and dump server traces:  
        Operation 'Hello' is called: Hello, world![0]  
        Operation 'Hello' is called: Hello, world![1]  
        Operation 'Hello' is called: Hello, world![2]  
        Operation 'Hello' is called: Hello, world![3]  
        Operation 'Hello' is called: Hello, world![4]  
        Operation 'Add' is called: 0 + 0  
        Operation 'Add' is called: 1 + 2  
        Operation 'Add' is called: 2 + 4  
        Operation 'Add' is called: 3 + 6  
        Operation 'Add' is called: 4 + 8  
    Press <ENTER> to complete test.  
    ```  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
