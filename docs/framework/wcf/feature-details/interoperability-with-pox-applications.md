---
title: 與 POX 應用程式的互通性
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: b7fdb4e16bce52025515ced065d0f48cffb7fa3f
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2018
ms.locfileid: "49372160"
---
# <a name="interoperability-with-pox-applications"></a>與 POX 應用程式的互通性

"Plain Old XML"(POX) 應用程式，則交換只包含 XML 應用程式資料未隨附在 SOAP envelope 內的原始 HTTP 訊息來進行通訊。 Windows Communication Foundation (WCF) 可以提供使用 POX 訊息的用戶端和服務。 在服務上，WCF 可以用於實作公開端點，例如網頁瀏覽器的用戶端的服務和傳送和接收 POX 訊息的指令碼語言。 在用戶端，WCF 程式設計模型可用來實作與 POX 式服務進行通訊的用戶端。  
  
> [!NOTE]
> 本文件原本是針對 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0 而撰寫。  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.5 具有可使用 POX 應用程式的內建支援。 如需詳細資訊，請參閱關於[WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)。
  
## <a name="pox-programming-with-wcf"></a>使用 WCF 的 POX 程式撰寫

透過使用 POX 訊息的 HTTP 通訊的 WCF 服務[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)。

```xml
<customBinding>
   <binding name="poxServerBinding">
       <textMessageEncoding messageVersion="None" />
       <httpTransport />
   </binding>
</customBinding>
```

此自訂繫結包含兩個項目：

- [\<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)

- [\<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)

WCF 的文字訊息編碼器特別設定為使用的標準<xref:System.ServiceModel.Channels.MessageVersion.None%2A>值，使其可以處理 XML 訊息承載不會抵達包裝在 SOAP 封套。

使用 POX 訊息透過 HTTP 進行通訊的 WCF 用戶端會使用類似的繫結 （如下列命令式程式碼所示）。

```csharp
private static Binding CreatePoxBinding()
{
    TextMessageEncodingBindingElement encoder =
        new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );
    HttpTransportBindingElement transport = new HttpTransportBindingElement();
    transport.ManualAddressing = true;
    return new CustomBinding( new BindingElement[] { encoder, transport } );
}
```

由於 POX 用戶端必須指定它們傳送訊息所至的 URI，因此它們通常必須在項目上將 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> 屬性設定為 <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A>，以便將 `true` 設定為手動定址模式。 這樣做使應用程式程式碼可以明確將訊息定址，而且不需要在每次應用程式傳送訊息至不同的 HTTP URI 時都建立新的 <xref:System.ServiceModel.ChannelFactory>。

由於 POX 訊息不使用 SOA 標頭傳送重要的通訊協定資訊，因此 POX 用戶端和服務經常必須管理基礎 HTTP 要求的片段以傳送或接收訊息。 例如 HTTP 標頭和狀態碼的 HTTP 特定通訊協定資訊呈現在 WCF 程式設計模型，透過兩個類別中：

- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty>，包含有關 HTTP 要求的資訊，例如 HTTP 方法和要求標頭。

- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty>，包含有關 HTTP 回應的資訊，例如 HTTP 狀態代碼、狀態說明與任何 HTTP 回應標頭。
  
下列程式碼範例示範如何建立 HTTP GET 要求訊息定址到`http://localhost:8100/customers`。

```csharp
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );
request.Headers.To = "http://localhost:8100/customers";

HttpRequestMessageProperty property = new HttpRequestMessageProperty();
property.Method = "GET";
property.SuppressEntityBody = true;
request.Properties.Add( HttpRequestMessageProperty.Name, property );
```

首先呼叫 <xref:System.ServiceModel.Channels.Message> 來建立空白的要求 <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>。 <xref:System.ServiceModel.Channels.MessageVersion.None%2A> 可用於指示不需要 SOAP 封套，並且傳遞 <xref:System.String.Empty> 參數做為動作。 然後，將 <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> 標頭設定為所需的 URI 以便將要求訊息定址。 接著，建立 <xref:System.ServiceModel.Channels.HttpRequestMessageProperty>，並且將 <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> 設定為 HTTP 動詞 GET 方法，以及將 <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> 設定為 `true`，以指示不應在傳出 HTTP 要求訊息的本文中傳送任何資料。 最後將要求屬性新增至要求訊息的 <xref:System.ServiceModel.Channels.Message.Properties%2A> 集合中，因此可影響 HTTP 傳輸如何傳送要求。 然後準備好透過 <xref:System.ServiceModel.Channels.IRequestChannel> 的適當執行個體傳送訊息。

可在服務上使用類似的技巧，以擷取來自傳入訊息的 <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> 並建構回應。
