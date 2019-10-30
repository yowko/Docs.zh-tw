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
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040648"
---
# <a name="how-to-configure-network-tracing"></a>如何：設定網路追蹤

應用程式或電腦組態檔都會保存可決定網路追蹤格式和內容的設定。 在執行這個程序之前，請確認已啟用追蹤。 如需詳細資訊，請參閱[啟用網路追蹤](enabling-network-tracing.md)。

電腦配置*檔 machine.config 會*儲存在 *%windir%\Microsoft.NET\Framework*資料夾中。 針對電腦上安裝的每個 .NET Framework 版本， *%windir%\Microsoft.NET\Framework*下的資料夾中有個別的*machine.config*檔案，例如：

- *C：\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*
- *C：\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*

您也可以在應用程式的組態檔中進行這些設定，它的優先順序高於電腦組態檔。

## <a name="configure-network-tracing"></a>設定網路追蹤

若要設定網路追蹤，請將下列幾行新增至適當的設定檔。 下表中會說明這些設定的值和選項。

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

### <a name="trace-output-from-methods"></a>方法的追蹤輸出

當您將名稱加入至 `<switches>` 區塊時，追蹤輸出就會包括來自與該名稱相關的某些方法的資訊。 下表描述輸出：

|[屬性]|輸出來源|
|----------|-----------------|
|`System.Net.Sockets`|<xref:System.Net.Sockets.Socket>、<xref:System.Net.Sockets.TcpListener>、<xref:System.Net.Sockets.TcpClient>和 <xref:System.Net.Dns> 類別的一些公用方法。|
|`System.Net`|<xref:System.Net.HttpWebRequest>、<xref:System.Net.HttpWebResponse>、<xref:System.Net.FtpWebRequest>和 <xref:System.Net.FtpWebResponse> 類別的一些公用方法，以及 SSL 的調試資訊（不正確憑證、缺少的簽發者清單，以及用戶端憑證錯誤）。|
|`System.Net.HttpListener`|<xref:System.Net.HttpListener>、<xref:System.Net.HttpListenerRequest> 和 <xref:System.Net.HttpListenerResponse> 類別的一些公用方法。|
|`System.Net.Cache`|`System.Net.Cache` 中的一些私用和內部方法。|
|`System.Net.Http`|<xref:System.Net.Http.HttpClient>、<xref:System.Net.Http.DelegatingHandler>、<xref:System.Net.Http.HttpClientHandler>、<xref:System.Net.Http.HttpMessageHandler>、<xref:System.Net.Http.MessageProcessingHandler> 和 <xref:System.Net.Http.WebRequestHandler> 類別的一些公用方法。|
|`System.Net.WebSockets.WebSocket`|<xref:System.Net.WebSockets.ClientWebSocket> 和 <xref:System.Net.WebSockets.WebSocket> 類別的一些公用方法。|

### <a name="trace-output-attributes"></a>追蹤輸出屬性

下表所列的屬性會設定追蹤輸出：

|屬性名稱|屬性值|
|--------------------|---------------------|
|`value`|必要的 <xref:System.String> 屬性。 設定輸出的詳細等級。 合法值為 `Critical`、`Error`、`Verbose`、`Warning` 和 `Information`。<br /><br />這個屬性必須在 switch 元素的**add** **元素上**設定。 如果在**來源**元素上設定此屬性，則會擲回例外狀況。<br/><br/>範例：`<add name="System.Net" value="Verbose"/>`|
|`maxdatasize`|選擇性 <xref:System.Int32> 屬性。 設定每一行追蹤所包含之網路資料的最大位元組數。 預設值為 1024。<br /><br />必須在**來源**元素上設定這個屬性。 如果**在 switch 元素下**的專案上設定這個屬性，則會擲回例外狀況。<br/><br/>範例：`<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|
|`tracemode`|選擇性 <xref:System.String> 屬性。 設定為 `includehex` 以便使用十六進位和文字格式來顯示通訊協定追蹤。 設定為 `protocolonly` 則只會顯示文字。 預設值是 `includehex`。<br /><br />必須在**來源**元素上設定這個屬性。 如果**在 switch 元素下**的專案上設定這個屬性，則會擲回例外狀況。<br/><br/>範例：`<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|

## <a name="see-also"></a>請參閱

- [解譯網路追蹤](interpreting-network-tracing.md)
- [以 .NET Framework 進行網路追蹤](network-tracing.md)
- [啟用網路追蹤](enabling-network-tracing.md)
- [追蹤和檢測應用程式](../debug-trace-profile/tracing-and-instrumenting-applications.md)
