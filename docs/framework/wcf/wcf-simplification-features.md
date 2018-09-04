---
title: WCF 簡化功能
ms.date: 03/30/2017
ms.assetid: 4535a511-6064-4da0-b361-80262a891663
ms.openlocfilehash: 010f941850dedd73e9cc203ea2b180dae7d4742c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526349"
---
# <a name="wcf-simplification-features"></a>WCF 簡化功能
本主題探討讓撰寫 WCF 應用程式更簡單的新功能。  
  
## <a name="simplified-generated-configuration-files"></a>簡化產生的組態檔  
 當您在 Visual Studio 中加入服務參考，或使用 SvcUtil.exe 工具時，用戶端組態檔就會產生。 在舊版 WCF 中，這些組態檔會包含所有繫結屬性的值，即使值為預設值，也是如此。 在 WCF 4.5 中產生的組態檔只會包含那些設定成非預設值的繫結屬性。  
  
 下列是 WCF 3.0 所產生之組態檔的範例。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <basicHttpBinding>  
                <binding name="BasicHttpBinding_IService1" closeTimeout="00:01:00"  
                    openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00"  
                    allowCookies="false" bypassProxyOnLocal="false"   
                    hostNameComparisonMode="StrongWildcard" maxBufferSize="65536"   
                    maxBufferPoolSize="524288" maxReceivedMessageSize="65536"  
                    messageEncoding="Text" textEncoding="utf-8" transferMode="Buffered"  
                    useDefaultWebProxy="true">  
                    <readerQuotas maxDepth="32" maxStringContentLength="8192"   
                        maxArrayLength="16384" maxBytesPerRead="4096"  
                        maxNameTableCharCount="16384" />  
                    <security mode="None">  
                        <transport clientCredentialType="None" proxyCredentialType="None"  
                            realm="" />  
                        <message clientCredentialType="UserName" algorithmSuite="Default" />  
                    </security>  
                </binding>  
            </basicHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="http://localhost:36906/Service1.svc" binding="basicHttpBinding"  
                bindingConfiguration="BasicHttpBinding_IService1" contract="IService1"  
                name="BasicHttpBinding_IService1" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
 下列是 WCF 4.5 所產生之相同組態檔的範例。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <basicHttpBinding>  
                <binding name="BasicHttpBinding_IService1" />  
            </basicHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="http://localhost:36906/Service1.svc" binding="basicHttpBinding"  
                bindingConfiguration="BasicHttpBinding_IService1" contract="IService1"  
                name="BasicHttpBinding_IService1" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="contract-first-development"></a>合約優先開發  
 WCF 現可支援合約優先開發。 svcutl.exe 工具有 /serviceContract 參數可讓您從 WSDL 文件產生服務與資料合約。  
  
## <a name="add-service-reference-from-a-portable-subset-project"></a>從可攜式子集專案加入服務參考  
 可攜式子集專案可讓.NET 組件的程式設計人員維護單一來源樹狀結構，並建置系統，同時仍可支援多個.NET 實作 （桌上型電腦、 Silverlight、 Windows Phone 和 XBOX）。 可攜式子集專案僅參考也就是可以使用任何.NET 實作的.NET framework 組件的.NET 可攜式程式庫。 開發人員的體驗與在任何其他 WCF 用戶端應用程式內加入服務參考相同。 如需詳細資訊，請參閱 <<c0> [ 可攜式子集專案中加入服務參考](../../../docs/framework/wcf/add-service-reference-in-a-portable-subset-project.md)。  
  
## <a name="aspnet-compatibility-mode-default-changed"></a>ASP.NET 相容模式預設值已變更  
 WCF 會在寫入 WCF 服務時提供 ASP.NET 相容模式，將 ASP.NET HTTP 管線功能的完整存取權限授與開發人員。 若要使用此模式中，您必須設定`aspNetCompatibilityEnabled`屬性設為 true，在[ \<serviceHostingEnvironment >](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) web.config 區段。此外，這個 appDomain 中的任何服務還必須將其 `RequirementsMode` 上的 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> 屬性設定為 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> 或 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>。 依預設<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>現在已設定為<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>和預設 WCF 服務應用程式範本集`aspNetCompatibilityEnabled`屬性設定為`true`。 如需詳細資訊，請參閱 < [What's New in Windows Communication Foundation 4.5](../../../docs/framework/wcf/whats-new.md)並[WCF 服務與 ASP.NET](../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)。  
  
## <a name="streaming-improvements"></a>資料流的改進  
  
-   WCF 已新增對非同步資料流的支援。 若要啟用非同步資料流，請將 <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> 端點行為加入至服務主機，並將其 <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> 屬性設定為 `true`。  當服務將已進行資料流處理的訊息傳送到多個用戶端，而這些用戶端的讀取速度緩慢時，這個做法可以提高延展性。 WCF 不再針對個別用戶端封鎖執行緒，並且會釋放執行緒以服務另一個用戶端。  
  
-   已移除訊息緩衝在服務由 IIS 裝載時的限制。 在舊版 WCF 中，當收到使用資料流訊息傳輸之 IIS 裝載服務的訊息時，ASP.NET 在傳送訊息到 WCF 之前會緩衝整個訊息。 這將導致大量記憶體消耗。 這種緩衝處理已在 .NET 4.5 中移除，現在 IIS 裝載的 WCF 服務可以在接收到整個訊息之前處理傳入資料流，藉此啟用真實的資料流處理。 這允許 WCF 立即對訊息做出回應，並使效能有所提升。 此外，您不再需要指定 `maxRequestLength` (ASP.NET 對傳入要求的大小限制) 的值。 如果設定這個屬性，則會將其忽略。 如需詳細資訊`maxRequestLength`請參閱 < [ \<httpRuntime > 組態項目](https://go.microsoft.com/fwlink/?LinkId=223344)。 您仍然必須設定 maxAllowedContentLength，如需詳細資訊，請參閱 < [IIS 要求限制](https://go.microsoft.com/fwlink/?LinkId=225908)。  
  
## <a name="new-transport-default-values"></a>新的傳輸預設值  
 下列資料表說明已變更的設定以及可找到其他資訊的位置。  
  
|屬性|開啟|新的預設值|更多資訊|  
|--------------|--------|-----------------|----------------------|  
|channelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 秒|這個屬性決定 TCP 連接可以花費多少時間來使用 .Net Framing 通訊協定自行驗證。 用戶端必須先傳送一些初始資料，讓伺服器有足夠的資訊來執行驗證。 逾時會故意設定為小於 ReceiveTimeout (10 分鐘)，使未經驗證的惡意用戶端無法長時間保持與伺服器的連接。 預設值為 30 秒。 如需詳細資訊 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|  
|listenBacklog|<xref:System.ServiceModel.NetTcpBinding>|16 * 處理器數量|此為通訊端層級的屬性，用來說明要排入佇列之「擱置接受」要求的數目。 如果接聽待辦項目佇列已滿，將會拒絕新的通訊端要求。 如需詳細資訊 <xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|  
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * 用於傳輸的處理器數量<br /><br /> 4\*用於 SMSvcHost.exe 的處理器數量|這個屬性會限制伺服器可以在接聽程式上等待的通道數量。 MaxPendingAccepts 太低時，會有一小段時間間隔讓所有等待中的通道開始提供連接服務，但不會有任何新的通道開始接聽。 在這段時間間隔內出現的連接都會失敗，因為伺服器上沒有任何要等待的連接。 這個屬性可以藉由將 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A> 屬性設為較大數目的方式進行設定。 如需詳細資訊，請參閱 <<c0> <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A> 和[設定 Net.TCP Port Sharing Service](https://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)|  
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * 處理器的數量|這個屬性控制傳輸已接受但未經 ServiceModel 發送器擷取的連接數量。 若要設定這個值，請使用繫結上的 `MaxConnections` 或繫結項目上的 `maxOutboundConnectionsPerEndpoint`。 如需詳細資訊 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|  
|receiveTimeout|SMSvcHost.exe|30 秒|這個屬性會指定讀取 TCP 框架資料以及從基礎連線執行連線分派的逾時。 這個屬性的用途是設定 SMSvcHost.exe 服務持續投入讀取傳入連接之前序編碼資料的時間上限。 如需詳細資訊，請參閱 <<c0> [ 設定 Net.TCP Port Sharing Service](https://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)。|  
  
> [!NOTE]
>  只有在包含 .NET Framework 4.5 的電腦上部署 WCF 服務時，才會使用這些新的預設值。 如果您在包含 .NET Framework 4.0 的電腦上部署相同服務，就會使用 .NET Framework 4.0 的預設值。 在這些情況下，建議您明確地設定這些設定。  
  
## <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas  
 <xref:System.Xml.XmlDictionaryReaderQuotas> 包含 XML 字典讀取器的可設定配額值，這些值會限制編碼器在建立訊息時使用的記憶體量。 雖然這些配額是可設定的，但變更為預設值可降低開發人員必須明確設定這些值的機率。 目前尚未變更 `MaxReceivedMessageSize` 配額，因此這個配額仍然可以限制記憶體耗用，避免您遇到必須處理 <xref:System.Xml.XmlDictionaryReaderQuotas> 的複雜狀況。 下表顯示配額、新的預設值和每個配額用途的簡要說明。  
  
|配額名稱|預設值|描述|  
|----------------|-------------------|-----------------|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>|Int32.MaxValue|取得和設定允許的陣列長度上限。 這個配額會限制 XML 讀取器將會傳回之基本陣列的大小上限，包括位元組陣列。 這個配額不會限制 XML 讀取器本身的記憶體消耗，但會限制正在使用讀取器之任何元件中的記憶體消耗。 例如，當 <xref:System.Runtime.Serialization.DataContractSerializer> 使用以 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>保護的讀取器時，它不會還原序列化大於這個配額的位元組陣列。|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>|Int32.MaxValue|取得和設定允許每個讀取動作傳回的位元組上限。 這個配額會限制讀取項目開始標記和其屬性時，在單一「讀取」作業中讀取的位元組數目。 (在非資料流處理的情況中，項目名稱本身不會納入配額的計數)。 使用太多 XML 屬性可能會耗盡不當比例的處理時間，因為必須檢查屬性名稱的唯一性。 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> 可降低這個威脅。|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>|128 個節點深|這個配額會限制 XML 項目的最大巢狀結構深度。  <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> 會與 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> 互動：由於讀取器永遠會為目前項目和其所有祖系將資料保存在記憶體中，因此讀取器的最大記憶體消耗與這兩個設定的產品是成比例的。 當還原序列化深度巢狀物件圖形時，會強制還原序列化程式存取整個堆疊並擲回無法復原的 <xref:System.StackOverflowException>。 XML 巢狀結構和物件兩者的巢狀之間存在直接的相互關聯<xref:System.Runtime.Serialization.DataContractSerializer>而<!--zz <xref:System.Runtime.Serialization.XmlSerializer>--> `System.Runtime.Serialization.XmlSerializer`。 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> 是用來降低這個威脅。|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>|Int32.MaxValue|這個配額會限制名稱表格中允許的最大字元數目。 名稱表格包含會在處理 XML 文件時遇到的特定字串 (例如命名空間和前置詞)。 當這些字串在記憶體中緩衝時可使用這個配額，以防止在應該進行資料流處理時過度緩衝處理。|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>|Int32.MaxValue|這個配額會限制 XML 讀取器傳回的字串大小上限。 這個配額不會限制 XML 讀取器本身的記憶體消耗，但會限制正在使用讀取器之元件中的記憶體消耗。 例如，當 <xref:System.Runtime.Serialization.DataContractSerializer> 使用以 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>保護的讀取器時，它不會還原序列化大於這個配額的字串。|  
  
> [!IMPORTANT]
>  請參閱 「 安全使用 XML > 底下[資料的安全性考量](../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)如需有關保護資料安全。  
  
> [!NOTE]
>  只有在包含 .NET Framework 4.5 的電腦上部署 WCF 服務時，才會使用這些新的預設值。 如果您在包含 .NET Framework 4.0 的電腦上部署相同服務，就會使用 .NET Framework 4.0 的預設值。 在這些情況下，建議您明確地設定這些設定。  
  
## <a name="wcf-configuration-validation"></a>WCF 組態驗證  
 Visual Studio 現在有一部分建置流程會驗證 WCF 組態檔。 如果驗證失敗，將會在 Visual Studio 中顯示驗證錯誤或警告的清單。  
  
## <a name="xml-editor-tooltips"></a>XML 編輯器工具提示  
 為了協助新的和現有的 WCF 服務開發人員設定其服務，現在每個屬於服務組態檔之一部分的組態項目及其屬性，Visual Studio XML 編輯器都有提供工具提示。  
  
## <a name="basichttpbinding-improvements"></a>BasicHttpBinding 的改進  
  
1.  可讓單一 WCF 端點回應不同的驗證模式。  
  
2.  可讓 WCF 服務的安全性設定由 IIS 來控制
