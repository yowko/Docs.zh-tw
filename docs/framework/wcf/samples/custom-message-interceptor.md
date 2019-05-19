---
title: 自訂訊息攔截器
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: 530c626a1f134190bb90fcee3a4e3bbba91d9516
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878298"
---
# <a name="custom-message-interceptor"></a>自訂訊息攔截器
這個範例示範通道擴充性模型的使用方式。 尤其，這個範例會示範如何實作建立通道處理站和通道接聽程式的自訂繫結項目，以攔截執行階段堆疊中特定點的所有傳入與傳出訊息。 範例也包含用戶端和伺服器，以示範這些自訂處理站的使用方式。  
  
 在這個範例中，用戶端和服務都是主控台程式 (.exe)。 用戶端和服務都會使用含有自訂繫結項目及其相關執行階段物件的通用程式庫 (.dll)。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 此範例說明建立自訂層次的通道的設定，在 Windows Communication Foundation (WCF) 中，使用通道架構並遵循 WCF 的最佳做法的建議程序。 建立自訂層次通道的步驟如下：  
  
1. 決定通道處理站和通道接聽項所要支援的通道類型。  
  
2. 建立支援您通道類型的通道處理站和通道接聽項。  
  
3. 新增繫結項目，而此繫結項目會將自訂層次通道新增至通道堆疊。  
  
4. 新增繫結元素延伸區段，即可將新的繫結元素公開至組態系統。  
  
## <a name="channel-shapes"></a>通道形狀  
 撰寫自訂層次通道時的第一個步驟是，決定通道所需要的類型。 對於訊息偵測器，我們支援下面層次所支援的任何類型 (例如，如果下面的層次可以建置 <xref:System.ServiceModel.Channels.IOutputChannel> 和 <xref:System.ServiceModel.Channels.IDuplexSessionChannel>，則也會公開 <xref:System.ServiceModel.Channels.IOutputChannel> 和 <xref:System.ServiceModel.Channels.IDuplexSessionChannel>)。  
  
## <a name="channel-factory-and-listener-factory"></a>通道處理站和接聽項處理站  
 撰寫自訂層次通道的下一個步驟是，建立用戶端通道的 <xref:System.ServiceModel.Channels.IChannelFactory> 實作以及服務通道的 <xref:System.ServiceModel.Channels.IChannelListener> 實作。  
  
 這些類別會接受內部處理站和接聽項，並且將除了 `OnCreateChannel` 和 `OnAcceptChannel` 以外的所有呼叫委派至內部處理站和接聽項。  
  
```  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ ... }  
class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ ... }  
```  
  
## <a name="adding-a-binding-element"></a>新增繫結項目  
 範例會定義自訂繫結項目：`InterceptingBindingElement`。 `InterceptingBindingElement` 會採用`ChannelMessageInterceptor`做為輸入，並使用這個`ChannelMessageInterceptor`來操作通過它的訊息。 這是唯一必須為公用的類別。 處理站、接聽項和通道全部都可以是公用執行階段介面的內部實作。  
  
```  
public class InterceptingBindingElement : BindingElement  
```  
  
## <a name="adding-configuration-support"></a>新增組態支援  
 為了與繫結組態整合，程式庫會將組態區段處理常式定義為繫結項目延伸區段。 用戶端和伺服器組態檔必須向組態系統註冊繫結項目延伸。 想要將其繫結項目公開給組態系統的實作器都可以衍生自這個類別。  
  
```  
public abstract class InterceptingElement : BindingElementExtensionElement { ... }  
```  
  
## <a name="adding-policy"></a>新增原則  
 為了與原則系統整合，`InterceptingBindingElement` 會實作 IPolicyExportExtension 以表示必須參與產生原則。 若要在產生的用戶端上支援匯入原則，使用者可以註冊 `InterceptingBindingElementImporter` 的衍生類別，並覆寫 `CreateMessageInterceptor`() 來產生啟用原則的 `ChannelMessageInterceptor` 類別。  
  
## <a name="example-droppable-message-inspector"></a>範例：可卸除的訊息偵測器  
 範例中包含了會卸除訊息的 `ChannelMessageInspector` 的範例實作。  
  
```  
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 您可以從組態中存取，如下所示：  
  
```xml  
<configuration>  
    ...  
    <system.serviceModel>  
        ...  
        <extensions>  
            <bindingElementExtensions>  
                <add name="droppingInterceptor"   
                   type=  
          "Microsoft.ServiceModel.Samples.DroppingServerElement, library"/>  
            </bindingElementExtensions>  
        </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
 用戶端和伺服器都會使用這個新建立的組態區段，將自訂處理站插入至執行階段通道堆疊的最下一層 (在傳輸層級之上)。  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 用戶端會使用 `MessageInterceptor` 程式庫，將自訂標頭新增至偶數編號的訊息。 另一方面，服務則會使用 `MessageInterceptor` 程式庫來卸除任何沒有這個特殊標頭的訊息。  
  
 在依序執行服務和用戶端之後，您應該看見下列用戶端輸出。  
  
```  
Reporting the next 10 wind speed  
100 kph  
Server dropped a message.  
90 kph  
80 kph  
Server dropped a message.  
70 kph  
60 kph  
Server dropped a message.  
50 kph  
40 kph  
Server dropped a message.  
30 kph  
20 kph  
Server dropped a message.  
10 kph  
Press ENTER to shut down client  
```  
  
 用戶端會向服務報告 10 種不同的風速，但是只將其中半數標記以特殊標頭。  
  
 您應該會在服務上看見下列輸出：  
  
```  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 安裝 ASP.NET 4.0 使用下列命令。  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. 請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
3. 若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
4. 若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
5. 先執行 Service.exe，然後執行 Client.exe，再查看兩個主控台視窗上的輸出。  
