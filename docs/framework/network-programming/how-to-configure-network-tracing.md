---
title: 如何：設定網路追蹤
ms.date: 03/30/2017
helpviewer_keywords:
- formatting [.NET Framework], network tracing
- network tracing, configuring
- level attribute
- app.config files, network tracing
- configuration files [.NET Framework], network tracing
- protocol-level trace output
- application configuration files, network tracing
- sockets, trace output
ms.assetid: 5ef9fe4b-8d3d-490e-9259-1d014b2181af
ms.openlocfilehash: 06132509860b16d1e22cfdf7e3226c968d16b7cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73040648"
---
# <a name="how-to-configure-network-tracing"></a>如何：配置網路跟蹤

應用程式或電腦組態檔都會保存可決定網路追蹤格式和內容的設定。 在執行這個程序之前，請確認已啟用追蹤。 有關詳細資訊，請參閱[啟用網路跟蹤](enabling-network-tracing.md)。

電腦設定檔 *，電腦.config*，存儲在 *%windir%\Microsoft.NET_Framework*資料夾中。 *在 %windir%_Microsoft.NET_Framework*的資料夾中，對於電腦上安裝的每個版本的 .NET Framework，有一個單獨的*電腦.config*檔，例如：

- *C：_WINDOWS_微軟.NET_Framework_v2.0.50727_機器。*
- *C：_WINDOWS_微軟.NET_Framework64_v4.0.30319\機器。*

您也可以在應用程式的組態檔中進行這些設定，它的優先順序高於電腦組態檔。

## <a name="configure-network-tracing"></a>配置網路跟蹤

要配置網路跟蹤，請將以下行添加到相應的設定檔。 下表中會說明這些設定的值和選項。

```xml
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.Net" tracemode="includehex" maxdatasize="1024">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Cache">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Http">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Sockets">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.WebSockets">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
   </sources>
    <switches>
      <add name="System.Net" value="Verbose"/>
      <add name="System.Net.Cache" value="Verbose"/>
      <add name="System.Net.Http" value="Verbose"/>
      <add name="System.Net.Sockets" value="Verbose"/>
      <add name="System.Net.WebSockets" value="Verbose"/>
    </switches>
    <sharedListeners>
      <add name="System.Net"
        type="System.Diagnostics.TextWriterTraceListener"
        initializeData="network.log"
        traceOutputOptions="ProcessId, DateTime"
      />
    </sharedListeners>
    <trace autoflush="true"/>
  </system.diagnostics>
</configuration>
```

### <a name="trace-output-from-methods"></a>從方法跟蹤輸出

當您將名稱加入至 `<switches>` 區塊時，追蹤輸出就會包括來自與該名稱相關的某些方法的資訊。 下表描述了輸出：

|名稱|輸出來源|
|----------|-----------------|
|`System.Net.Sockets`|<xref:System.Net.Sockets.Socket>、<xref:System.Net.Sockets.TcpListener>和<xref:System.Net.Sockets.TcpClient><xref:System.Net.Dns>類的一些公共方法。|
|`System.Net`|<xref:System.Net.HttpWebRequest>、<xref:System.Net.HttpWebResponse>和<xref:System.Net.FtpWebRequest>類以及<xref:System.Net.FtpWebResponse>SSL 調試資訊（無效證書、缺少頒發者清單和用戶端憑證錯誤）的某些公共方法。|
|`System.Net.HttpListener`|<xref:System.Net.HttpListener>、<xref:System.Net.HttpListenerRequest> 和 <xref:System.Net.HttpListenerResponse> 類別的一些公用方法。|
|`System.Net.Cache`|`System.Net.Cache` 中的一些私用和內部方法。|
|`System.Net.Http`|<xref:System.Net.Http.HttpClient>、<xref:System.Net.Http.DelegatingHandler>、<xref:System.Net.Http.HttpClientHandler>、<xref:System.Net.Http.HttpMessageHandler>、<xref:System.Net.Http.MessageProcessingHandler> 和 <xref:System.Net.Http.WebRequestHandler> 類別的一些公用方法。|
|`System.Net.WebSockets.WebSocket`|<xref:System.Net.WebSockets.ClientWebSocket> 和 <xref:System.Net.WebSockets.WebSocket> 類別的一些公用方法。|

### <a name="trace-output-attributes"></a>跟蹤輸出屬性

下表中列出的屬性配置跟蹤輸出：

|屬性名稱|屬性值|
|--------------------|---------------------|
|`value`|必要的 <xref:System.String> 屬性。 設定輸出的詳細等級。 合法值為 `Critical`、`Error`、`Verbose`、`Warning` 和 `Information`。<br /><br />必須在**交換器**元素的**添加**元素上設置此屬性。 如果在**源**元素上設置了此屬性，則引發異常。<br/><br/>範例： `<add name="System.Net" value="Verbose"/>`|
|`maxdatasize`|選擇性 <xref:System.Int32> 屬性。 設定每一行追蹤所包含之網路資料的最大位元組數。 預設值為 1024。<br /><br />必須在**源**元素上設置此屬性。 如果在**交換器**元素下的元素上設置此屬性，則引發異常。<br/><br/>範例： `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|
|`tracemode`|選擇性 <xref:System.String> 屬性。 設定為 `includehex` 以便使用十六進位和文字格式來顯示通訊協定追蹤。 設定為 `protocolonly` 則只會顯示文字。 預設值是 `includehex`。<br /><br />必須在**源**元素上設置此屬性。 如果在**交換器**元素下的元素上設置此屬性，則引發異常。<br/><br/>範例： `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|

## <a name="see-also"></a>另請參閱

- [解譯網路追蹤](interpreting-network-tracing.md)
- [以 .NET Framework 進行網路追蹤](network-tracing.md)
- [啟用網路追蹤](enabling-network-tracing.md)
- [追蹤和稽核應用程式](../debug-trace-profile/tracing-and-instrumenting-applications.md)
